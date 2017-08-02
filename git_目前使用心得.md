本心得是從clone專案到改完東西，然後下commit，最後push回去到遠端的一套動作

1. git clone <git網址>

2. clone下來的東西如果做了更改，要上傳回去需要利用以下做新增更改的動作:
git add .
當然也可以指定特定的檔案
git add <file>
如果有任何刪除、新增或更改檔案則需要以下:
git add .

PS.想確認有哪些變更可以打git status檢視狀態。


3. 針對剛剛更改的動作做commit的動作
git commit -m "訊息bla bla bla"

4. 將更改送回遠端，完成一套動作
(預設值情況會將clone下來的設定遠端名稱為origin,branch為master,所以就直接打以下指令就可以push回去)
git push

PS.clone的時候也可以指定要特定的branch這個另外再查指令就可以了~


--------------------------------------------------

如果需要在一個工作目錄直接用新增本地git的工作區，那麼需要初始化當前的目錄(其實就是產生一些隱藏檔案)
git init

然後再跟遠端"已經"存在的專案做連結則需要以下:
git remote add <方便辨識的遠端名稱> <git網址或ssh連結>
(用起來像這樣 git remote add test https://github.com/663321765/test.git)

上面的步驟做完之後先不要急著做修改的動作，要先記得做以下動作先跟遠端同步:
git pull <方便辨識的遠端名稱> <branch分支名稱，如:master>
(用起來像這樣 git pull test master)
PS.如果沒先這樣做，先做了修改然後下了commit然後，之後再做git pull的動作的話則會出現錯誤訊息:fatal: refusing to merge unrelated histories

之後做檔案修改或新增就跟最上面講的一樣，
要做git add . (用來應付所有狀況，刪除、更改、新增檔案都可以用!)
或 git add -u (這是用來應付有刪除以及更改檔案的狀況)
然後一樣要記得commit，最後再push回去，完成一套動作:
commit指令是一樣的就不多說，push的部分比較不一樣變成:
git push <方便辨識的遠端名稱> <branch分支名稱，如:master>
(用起來像這樣 git push test master)

***
當然如果當前工作的專案短時間內不會改變，那麼可以設定git push指令預設是要push到哪個遠端的git和指定branch，如下:
git push --set-upstream <方便辨識的名稱> <branch分支名稱，如:master>
(用起來像: git push --set-upstream test master)
PS.其實沒設定的狀況下直接打git push他也是會提示要怎麼設定!

