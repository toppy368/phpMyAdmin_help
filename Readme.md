#phpMyAdmin (MySQL Database) 的 Readme.md (使用說明)
本專案是由phpMyAdmin分支出來的，因為SQL相關的教學內容實在太多，佔了原本Blog Project太多章節，為了整理章節，所以把專案關於SQL的內容複製出來成這一支分支專案  

Blog Project為網頁開發專案，會帶到一些SQL相關語法，但主要為網頁程式碼操作資料庫，我會將部分SQL內容移到這裡  

本專案為phpMyAdmin操作說明書，如果不知如何操作phpMyAdmin，MySQL 資料庫，就來這專案吧 !   

##授權方式
<等說明寫完才會編輯這一行>


##開發環境
作業系統：Windows 7 家用進階版  
WAMP軟體：(**以下兩者並存，但同時開啟會相衝突**)  
1. Wamp server2.5 64bit  
2. XAMPP for Windows v5.6.8  
開發SDK：Notepad++  



#開發語言
前端：HTML、CSS  
後端：PHP、MySQL

編碼：一律採用UTF-8


###MySQL 登入資訊  


##安全性警告

  


##SQL 相關
每個瀏覽器的SQL登入路徑都不同，加上資料安全的疑慮，所以就不寫出登入連結了，請參考各網頁伺服器的phpMyAdmin登入方法

**Q：為什麼這個專案需要SQL資料庫呢 ? **  
**A:** 這個專案是要自己建立一個部落格後台系統，類似商業網誌如無名小站(已倒站)及痞客邦，或類似部落格架站軟體Wordpress的一種Blog系統，不過本專案不會有那麼多功能，只是想建立一個小型的Blog架站機制，練習互動式網頁語法  

如果只透過HTML或網頁設計丙級所設計出來的網站，也許只用到了HTML跟CSS跟少量的繪圖軟體(PhotoImpact)，但是HTML只能建立簡易表單，**按下"送出"後，文件卻無法送出**，因為**資料沒有儲存的地方，所以按了也無法送出資料**  

如果網友在討論版透過HTML輸入表單後，留言能顯示在網頁上，那一定得透過程式碼儲存(**參見Tips第1項**)，在本專案中**你在HTML表單輸入資料後，會透過PHP傳到SQL後端伺服器**(參見Tips第2項)，部分網站可能會用到ASP.NET，可達到同樣的效果  

**Tips：**  
1. 建議把此機制想成Google Docs，填好內容按下"送出"後，Google Docs的主人可透過Docs的試算表看到你的回應  
2. 部分 [內容管理系統] (http://zh.wikipedia.org/wiki/%E5%86%85%E5%AE%B9%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F) ，或架站平台，如部落格架站軟體 [**Wordpress**] (https://tw.wordpress.org/) 、 **論壇**架站軟體 [**Discuz**] (http://www.discuz.net/forum.php) 、 商業網站架站軟體 [**Joomla!**] (http://www.joomla.org.tw/) 也採用HTML+PHP+MySQL架構


###初始設定：修改phpMyAdmin預設的root密碼
####1. 進入phpMyAdmin後台  
![image] (https://github.com/toppy368/Blog_Project/blob/master/Readme_image/root_pw_error_head.JPG)

直接把路徑網址複製到瀏覽器上，就能進入phpMyAdmin登入畫面  

一進去會直接看到錯誤訊息：**您的設定檔當中使用了** (**無設定密碼的 root**) **的設定，該設定是 MySQL 預設的管理帳號。若您繼續使用預設 MySQL 管理帳號執行伺服器，可能會導致伺服器被入侵，強烈建議您設定管理者帳號 'root' 的密碼以避免這個安全性的漏洞。**  

因為root是管理員權限，預設沒有設定密碼，因此必須修改root密碼以策安全(**參見註解第3條**)  
一般來說，通常會由伺服器後台(**參見註解1、2說明**)設定SQL帳號密碼，但WAMP則是要求從phpMyAdmin設定，所以比較麻煩，本章節將說明如何從phpMyAdmin設定SQL的root帳密  

####註解說明：   
1. 各WAMP系統的SQL帳密申請方式不同，如Appserv(已停止開發)是透過安裝軟體的指示設定phpMyAdmin、xampp是透過localhost根目錄的安全選項來設定SQL帳密  
2. 虛擬主機則是依照主機商指示(E-mail內含帳密)或cpanel(主機商網站後台之一)的SQL的帳密設定來新增帳號與權限   
3. **root**為SQL伺服器預設的**管理員帳號**，這個帳號持有**最高權限**，以網路遊戲來說，你就是代表**"官方"**了(類似GM，搞不好比GM還大)，因此請保護好這組帳號  


####2. 進入使用者頁面，選擇"修改root權限"  
![image] (https://github.com/toppy368/Blog_Project/blob/master/Readme_image/root_pw_error_2.JPG)  
進入phpMyAdmin之後，請按下"使用者"進入此頁面，本次要修改root帳號是**主機位置在localhost的root帳號**，請按下**"修改權限"**，或紅框圈起來的這一行，勾選之後按下**"執行"**就能修改該帳號的權限了  

**Q： 畫面中有其他root帳號，那其他root也有管理員權限嗎 ? 錯誤訊息說沒有密碼的root會有安全性問題，怎麼不處裡其他root帳號 ?**   
**A：** 在寫這章節時，我實驗了好幾次，但是每次把root帳號刪除掉就會出現錯誤訊息，而且改了下面章節的config.inc.php還是沒用，最後實驗的原因是**你必須有root管理員權限才能刪除帳號，如果刪除所有root帳號，將無人有管理員權限，也無權限登入後台**(當然就無法編輯帳號權限了)，所以我目前的作法是，**先修改其中一個root，確定此帳號有辦法運作，再刪除其他不安全的帳號，確保此root是唯一一組管理員**


####3. 確認root帳號是否擁有全域權限  
![image] (https://github.com/toppy368/Blog_Project/blob/master/Readme_image/root_pw_error_3.JPG)  
請確定你要修改的帳號是否正確 ? 這次要修改的是**'root'@'localhost'**這組帳號，表示是這台機器的**root管理員帳號**，如果沒錯，請檢查權限是否全選 ? 如果有問題，請按照圖片指示修改權限，如果沒問題，請將頁面往下轉到修改密碼的地方

####4. 修改root密碼
![image] (https://github.com/toppy368/Blog_Project/blob/master/Readme_image/root_pw_error_4.JPG)  
頁面捲到最下面，有兩個表單，第一個表單是**修改密碼**，這個表單是**只能修改密碼的欄位**，另一個表單**能修改帳號與密碼**，如果你想**新增使用者**請填這個表單  

填寫"修改登入資訊/複製使用者"表單時，帳號我這裡一樣是root (**參見Tips**)，主機位置請選擇**"本機"**，欄位請填寫**localhost**，再設定密碼，而無論上面的**"修改密碼"**表單或下面的**"修改使用者/複製使用者"**表單，密碼欄就跟一般申請帳號一樣，需要輸入兩組密碼，而phpMyAdmin則多了一組產生器，可以產生複雜的強密碼(理論上安全性比較高)，不過需要注意一點，一旦按下了**產生**，你自己**輸入的密碼將會被產生器的密碼取代掉**，而產生器旁面會顯示產生出來的密碼，**請將設定好的密碼抄下來妥善保存或背起來，待會修改congig.inc.php會用到**  

Tips：因為root是預設帳號，因此有可能有不肖人士會不斷用root這組帳號去測你的管理員密碼，所以有些人可能會設定別組帳號，但權限一樣是root


####5. ERROR  
![image] (https://github.com/toppy368/Blog_Project/blob/master/Readme_image/root_pw_error_5.JPG)  
錯誤訊息：**1045 - Access denied for user 'root'@'localhost'** (**using password: NO**) 
一旦設定完成之後，底下root無密碼的提示會消失，但是重新整理頁面會顯示另一組錯誤訊息，原因是phpMyAdmin已幫我設定好了root帳號，但帳號跟預設在congig.inc.php設定檔的初始設定不同，所以會出現錯誤，將新密碼填入該檔案就OK了 ! 


####8. 開啟phpMyAdmin根目錄
![image] (https://github.com/toppy368/Blog_Project/blob/master/Readme_image/config.inc_1.jpg)  
WAMP的phpMyAdmin資料夾在此目錄下：C:\wamp\apps\phpMyAdmin4.1.14  

在任何WAMP伺服器中，管理SQL的後台為phpMyAdmin，而config.inc.php就存在phpMyAdmin資料夾中，請找到該資料夾才能找到該檔案  


####9. 開啟並修改congig.inc.php設定檔
![image] (https://github.com/toppy368/Blog_Project/blob/master/Readme_image/config.inc_2.jpg)  

請透過搜尋方式找到並修改這幾行：  

**藍色部分**  
第32行的**['uset']**，等號右邊請填寫你的root帳號(建議改成別的名字)，帳號請用單引號包起來  
第33行的**['password']**，等號右邊請填寫你root的**密碼**，**一旦遺失密碼，整個SQL資料庫就無法登入**，請把你抄下來的密碼填入此欄位  

**橘色部分**  
第35行的**['host']**，等號右邊請修改成**'localhost';**  
第40行的**[AllowNoPassword]**，等號右邊請設定為**false;**作用為**關閉**此功能(不過剛才經實驗過，無論true或false，都不會要求輸入帳號密碼的視窗)  


####10. 回到phpMyAdmin使用者頁面，檢查root帳號是否已設定密碼  
![image] (https://github.com/toppy368/Blog_Project/blob/master/Readme_image/Delete_root_1.JPG)  
回到phpMyAdmin頁面，確定能正常進入後台之後，按下"使用者"回到權限管理頁面，確定root帳號的密碼變成"有"，確定上面把root設定密碼的操作正確無誤  

**最後一個帳號確定有密碼，因此予以保留**


####11. 刪除其他使用者(包含root)  
![image] (https://github.com/toppy368/Blog_Project/blob/master/Readme_image/Delete_root_2.JPG)  
接下來這個步驟是倒數第二步了，這裡要解決第2步的疑問，因為只有最後一個主機位置在localhost帳號有設定密碼，所以我打算**刪除其他帳號，只保留有密碼的root**  

把上面其他帳號打勾好之後，在**"刪除選中的使用者"**的選項打勾，此時會出現警語：  
![image] (https://github.com/toppy368/Blog_Project/blob/master/Readme_image/Delete_root_3.JPG)  
警語內容：  
**您正要刪除**(**DESTROY**)**一個完整的資料庫！**  
**您確定要執行 "DROP DATABASE"？**

請按下**"確定"**，回到使用者頁面
![image] (https://github.com/toppy368/Blog_Project/blob/master/Readme_image/Delete_root_2.JPG) 
確定上面的**帳號勾選無誤**，且**刪除使用者**的選項也勾選無誤後，請按下左下角的**執行**，**刪除**勾選的帳號


####12. 完成設定  
![image] (https://github.com/toppy368/Blog_Project/blob/master/Readme_image/Delete_root_4.JPG)  
警語：**1064 - You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '' at line 1 #1064 - You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '' at line 1**  
此時會出現警語，但這警語按一下就會關閉，而且重新整理也沒出現異常  

之後按下**"使用者"**，就會出現這個畫面
![image] (https://github.com/toppy368/Blog_Project/blob/master/Readme_image/Delete_root_5.JPG)
確認帳號只剩下我這一組位於localhost的root帳號之後，所有設定root帳號密碼及刪除其他帳號的動作都完成了 !   

如果大家還是不放心，可以重新進入phpMyAdmin，應該是可以正常運作才對，SQL章節**修改root密碼**的**所有步驟**都完成了 !   

**本章節到此結束，下一章將說明SQL檔的匯入匯出**  


###透過phpMyAdmin匯入SQL檔

####1.進入phpMyAdmin主畫面
![image] (https://github.com/toppy368/Blog_Project/blob/master/Readme_image/SQL_import_1.JPG)

####2. 新增資料庫
![image] (https://github.com/toppy368/Blog_Project/blob/master/Readme_image/SQL_import_2.JPG)
可用此SQL指令替代：**CREATE DATABASE 資料庫名稱；**  
請到左邊資料庫選單中選擇"新增"選項，然後到右邊紅框框起來的地方，**最左邊第一格**請輸入你想新增的**資料庫名稱**、**第二項**請選擇**資料庫編碼**，考慮到使用者可能是不同國籍的人，為了語言相容性，所以本專案的資料庫設定成**utf8_unicode_ci**(**參見註解**)，**想採用utf8mb4的開發者，請將編碼資料庫設定為utf8mb4_unicode**  

註解：
1. 在還沒有Unicode概念時，每個電腦系統使用各自的編碼語言，比方說台灣的正體中文使用Big5、日本使用Shift_JIS、中國大陸簡體中文使用GB18030及GB2312、英文使用的是[ASCII] (http://zh.wikipedia.org/zh-tw/ASCII)，不同的語言，2進位代碼不同，如果編碼設錯，瀏覽器讀不出來將造成 [亂碼] (http://zh.wikipedia.org/zh-tw/%E4%BA%82%E7%A2%BC)，後來為了將這些語言統一才推出 [Unicode編碼] (http://zh.wikipedia.org/zh-tw/Unicode) ，可在同頁面上顯示不同語言的文字  
2. phpMyAdmin在5.5以後開始支援utf8mb4編碼，而 [Wordpress也採用此編碼] (https://tw.wordpress.org/2015/04/29/wordpress-4-2/) ，不過我目前還是以UTF-8為主(想採用utf8mb4的開發者，請將編碼資料庫設定為utf8mb4_unicode)  

####3. 匯入資料庫
![image] (https://github.com/toppy368/Blog_Project/blob/master/Readme_image/SQL_import_3.JPG)
新增資料庫看到成功訊息之後，請直接到右邊的資料庫選擇區中，選擇剛才建立的資料庫，選好之後，請按下**匯入**進到此頁面  

確定現在要匯入的位置是剛才剛新建好的資料庫後，請選擇**要匯入的檔案**，我選擇同樣名稱的blog_project.sql，根據後台說明，從虛擬主機下載下來的.zip檔也可以匯入  

之後請檢查**檔案編碼**，可以透過Notepad++或其他文字編輯器開啟sql檔，因為匯入檔案編碼必須與原檔案的編碼相同，**原始檔案如果是Big5，匯入選項也只能選擇Big5；如果資料庫檔案是UTF-8，那檔案編碼也請選UTF-8**  

如果上面這些選項都沒有問題，請按下"執行"，將SQL檔匯入此資料庫

####4. 匯入成功
![image] (https://github.com/toppy368/Blog_Project/blob/master/Readme_image/SQL_import_4.JPG)  
看到這訊息，就成功了 ! 成功將檔案匯入到剛才建好的資料庫當中，現在你可以直接從phpMyAdmin編輯這個資料庫
###透過phpMyAdmin匯出SQL檔(備份成 *.sql檔)
舊文網址：[WordPress 多種方式的網誌備份教學<<toppy368的研究書房] (http://www.toppy368.tw/archives/1437)  
我之前在我的Blog寫過備份方法，雖然是針對Wordpress的筆記文，但只要是基於SQL語法運作的網站或採用SQL資料庫運作的 [內容管理系統 CMS] (http://zh.wikipedia.org/zh-tw/%E5%86%85%E5%AE%B9%E7%AE%A1%E7%90%86%E7%B3%BB%E7%BB%9F) 都可以利用此方法備份網站資料庫為SQL檔  
 

####1. 進入phpMyAdmin主頁面
![image] (https://github.com/toppy368/Blog_Project/blob/master/Readme_image/SQL_Backup_1.JPG)
這裡假設大家已經在自己的電腦裡安裝好伺服器軟體或WAMP架構並可進入phpMyAdmin，或申請好虛擬主機並設定好root帳密者，如果無法進入，請看前面章節  

**請大家先以root帳號登入phpMyadmin首頁**，確定正確登入再進行第二步  


####2. phpMyAdmin資料庫介面說明
![image] (https://github.com/toppy368/Blog_Project/blob/master/Readme_image/SQL_Backup_2.JPG)
先說明資料庫的介面好了：  
左邊紅框顯示的是**資料庫選單**，一台SQL主機可能有好幾個資料庫，包含運作此資料庫的必要資料庫在內，你可以在此選擇你想備份的資料庫  
右邊上面紅框框起來的是**功能選單，**按下SQL可以下達SQL指令、也有匯出資料或匯入資料或搜尋等功能
右邊中間是**資料表編輯區**，你選中資料庫之後，資料表顯示區會顯示這個資料庫有幾張資料表等內容，空的資料庫也會顯示  


####3. 選定資料庫並按下"匯出"
![image] (https://github.com/toppy368/Blog_Project/blob/master/Readme_image/SQL_Backup_3.JPG)
請按下右邊的資料庫，本專案的資料庫名稱為"blog_project"，選中之後，會顯示裏頭的資料表，接下來請按下"匯出"，匯出資料庫

####4. 匯出選項
按下匯出之後，請檢查你要匯出的資料庫是否正確，本專案的資料庫檔案為"blog_project"  

新版phpMyAdmin的**匯出選項**區分為**"快速"**及**"自訂"**兩種，以下將針對這兩種選項說明

**4A. 快速匯出**
![image] (https://github.com/toppy368/Blog_Project/blob/master/Readme_image/SQL_Backup_4A.JPG)  
快速匯出只要檢查資料庫名稱是否正確，再確認格式是否為SQL(下載為 .sql 檔)，之後按下執行，就會跳出下載畫面，直接下載.sql檔就好

**4B. 自訂匯出**
![image] (https://github.com/toppy368/Blog_Project/blob/master/Readme_image/SQL_Backup_4B.JPG)
自訂匯出選項可以讓你自訂匯出的資料表、檔案編碼等等，你可以檢查資料表是否全選(如果漏選可能會造成網站異常)，還有檔案編碼是否正確等等(匯出的編碼要與匯入的格式相同)  

確定沒問題，就跟快速匯出一樣，畫面移動到最下方，按下**"執行"**，下載.sql檔就完成了  