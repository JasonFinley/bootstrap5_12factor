<template>
<div class="container">
  <div class="row">
    <div class="col-4 d-none d-md-block">
      <div id="menu_list" class="menu_bar">
        <div class="menu_item fs-4"><a href="#list-forword">12 Factor</a></div>
        <div class="menu_item"><a href="#list-codebase">I. 程式碼</a></div>
        <div class="menu_item"><a href="#list-dependencies">II. 相依性</a></div>
        <div class="menu_item"><a href="#list-config">III. 配置變數</a></div>
        <div class="menu_item"><a href="#list-backing">IV. 後端支援服務</a></div>
        <div class="menu_item"><a href="#list-build">V. 構建，發行，執行</a></div>
        <div class="menu_item"><a href="#list-processes">VI. 處理序</a></div>
        <div class="menu_item"><a href="#list-port">VII. 連接埠</a></div>
        <div class="menu_item"><a href="#list-concurrency">VIII. 同步執行</a></div>
        <div class="menu_item"><a href="#list-disposability">IX. 快捷啟用與終止</a></div>
        <div class="menu_item"><a href="#list-devprod">X. 環境的一致性</a></div>
        <div class="menu_item"><a href="#list-logs">XI. 記錄</a></div>
        <div class="menu_item"><a href="#list-admin">XII. 系統管理者</a></div>
      </div>
    </div>
    <div class="col">
      <div data-bs-spy="scroll" data-bs-target="#menu_list" data-bs-offset="0" class="scrollspy-example" tabindex="0">
        <section id="list-forword" class="container-fluid bg-primary text-white text-start" style="padding:100px 20px;">
        <h1>十二因子應用程式</h1>
        <h4>The 12 Factor App</h4>
        <p>“十二因子應用程式”源自於Heroku開發團隊在收集及觀察大量的SaaS(Software as a Service)應用程式開發與執行過程之後，所整理出來的十二條開發SaaS應用程式時的方針。</p>
        <p>遵守這些方針可以增進應用程式本身的穩定性及擴充性(Scalibility)，從程式開發的到系統上線過程也會快捷很多。</p>
        <p>原文：The 12 Factor App</p>
      </section>
      <section id="list-codebase" class="container-fluid bg-secondary text-white text-start" style="padding:100px 20px;">
        <h1>i. 程式碼(Codebase)</h1>
        <h4>一對一的程式碼版本管理</h4>
          <p>“十二因子”的程式碼必須儲存在原始碼版本管理系統，例如 Git, Subversion. 程式碼(codebase)與應用程式(application) 應該以“ㄧ對一”的關係儲存著：</p>
          <ul>  
            <li>如果你的系統需要有多個原始碼管理系統，那你的系統就是個分散式系統(Distributed System)， 分散式系統由多個應用程式(application)組成，而這些應用程式都應各別套用“十二因子”。</li>
            <li>“十二因子”反對一套程式的原始碼有多個應用程式在使用。如果需要分享部分的程式碼，正確的解決方式應該為把共享的程式碼包裝成程式庫(library, 例如JAVA的.jar檔案)， 然後有需要的其他應用程式以“相依性”(dependency)的程式庫來使用。</li>
          </ul>
        <p>每個"十二因子應用程式“都有屬於它專屬的程式碼，透過專有的原始碼版本管理，可以清楚的安裝(deploy)在不同的環境。 也許每個環境有不同的版本，但每個系統的所擁有的程式碼還是非常清楚乾淨的。有問題出現時，也可以簡單的回朔到之前的版本去。</p>
      </section>
      <section id="list-dependencies" class="container-fluid bg-success text-white text-start" style="padding:100px 20px;">
        <h1>ii. 相依性(dependencies)</h1>
        <h4>明確定義所有相依的程式庫(library)</h4>
        <p>程式語言通常都會有專屬的包裝(packaging)與相依性程式庫管理系統，例如Java的Maven，或是Ruby的Rubygems。 “十二因子”要求應用程式必須使用類似的管理系統，而且所有的第三方程式庫必須都明確定義出來，即使有些來自系統的程式庫也應列出來管理。 這樣一來當新的工程師加入開發時，隨時都可以透過管理系統簡單的安裝該程式在自己的環境，無論是任何平台都不會有衝突。</p>
        <p>一般來說容易被疏忽的部分是系統本身的程式庫或是工具，“十二因子應用程式”必須將這些有相依性的程式以第三方程式庫的方式安裝，以避免 應用程式被安裝在不支援的系統上。例如Linux的curl command如果直接在程式碼裡面使用，那這個應用程式有無法輕易的安裝在windows的環境。</p>
      </section>
      <section id="list-config" class="container-fluid bg-danger text-white text-start" style="padding:100px 20px;">
        <h1>iii. 配置變數(Config)</h1>
        <h4>將配置變數(Config)儲存在環境變數(Environment Variables)</h4>
        <p>配置變數(Config)所指的是每個應用軟體在不同的安裝環境(例如 production vs QA)會設定的變數。</p>
        <p>一般常見的例子：</p>
        <ul>
          <li>資料庫的連結設定，例如URL，帳號，密碼。</li>
          <li>第三方服務的連結設定，例如Facebook API的URL，帳號，密碼等。</li>
        </ul>
        <p>“十二因子應用程式”反對將這些配置變數儲存在原始碼裡面。建議的所有的配置變數應該儲存在環境變數(Environment Variables)中。 將配置變數儲存在原始碼中會有安全性的問題，一但程式碼開放給其他團體或個人時，這些機密的帳號密碼也容易不小心外洩。 另外配置變數是隨著環境在改變的，而應用程式的程式碼跟版本的關係是固定的，同版本的應用程式在任何安裝的環境都是一樣的， 所以配置變數需要另外管理。一般來說要個別定義在伺服器的環境變數中，如此也可以改善應用程式的擴充性(Scalability)。</p>
        <p>有些應用程式有屬於該程式結構使用的變數，例如Java Spring的config。這類的變數必須和程式碼共生，而不在以上提到的“十二因子”的規範內。</p>
      </section>
      <section id="list-backing" class="container-fluid bg-warning text-dark text-start" style="padding:100px 20px;">
        <h1>iv. 後端支援服務(Backing Services)</h1>
        <h4>所有後端支援系統都應視為外接的資源</h4>
        <p>所謂的後端支援服務(backing service)是指於應用程式透過網路傳輸得到的服務，例如資料庫，SMTP，快速儲存記憶體(cache)，API(Facebook,Google)之類的服務。</p>
        <p>負責管理這些支援服務的種類主要有本地的(local)跟第三方(3rd party)，例如資料庫通常是同公司的系統工程師在管理。但如果 主機架在雲端，大多數服務就都是透過第三方提供的了。“十二因子”的程式碼對待所有這些服務的種類必須是一致的，所有的後端支援系統，無論是本地管理或是第三方管理， 都一律視為外接的資源，用一樣的程式碼來執行。唯一不同的地方只有連線的方式，url，帳號，密碼透過Config來管理。</p>
        <p>由於程式碼一致，“十二因子應用程式“可以簡單的切換提供服務的來源。例如：如果要把MySQL提供者從自己local的換到Amazon提供的，只要改連結的資料可以了。或是要 把 Gmail 的 SMTP 換成 Yahoo! 的，也只要改連結的資料。關鍵就在於”十二因子“的程式碼一律視這些後端支援服務為外接的資源，無論是本地管理還是第三方管理的。</p>
      </section>
      <section id="list-build" class="container-fluid bg-info text-dark text-start" style="padding:100px 20px;">
        <h1>v. 構建，發行，執行(Build,Release,Run)</h1>
        <h4>確實分離建構與執行的階段</h4>
        <p>應用程式的從程式碼到發行(Release)與執行可以分為以下三階段：</p>
        <p>第一階段：“構建”(Build)，所指的是透過構建系統將程式碼及有相依性的程式庫包裝起來在一起。例如將package JAVA程式為.jar或是.war檔。</p>
        <p>第二階段：“發行”(Release)，將包裝好的程式庫，加上環境特有的配置變數(Config)，透過發行管理系統將檔案上傳至要執行的環境裡面。 一般來說發行管理系統另的一個主要工作是將每個發行版本(Release Version)規範定義好。每一個不同版本的程式碼都應有對應的發行版本， 版本定義可以用日期(2012-1-1-11:59:01)或是漸進的數字(v1.1.3)來定義。</p>
        <p>第三階段：“執行”(Run)，所指的是發行的版本(包含code+config)，在該環境中執行。</p>
        <p>“十二因子應用程式”強調這三個階段必須清楚地分開與定義好。例如在執行階段不容許有任何的程式碼改變。如果這三個階段可以分別設定好， 應用程式就可以進入自動化的發行與執行，工程師開發新的功能，構建系統自動包裝，發行系統自動定義版本，然後新版本的應用程式跟config一起 發行到執行的環境中。出問題時也可以在發行系統中選擇之前的版本回朔回去。</p>
      </section> 
      <section id="list-processes" class="container-fluid bg-light text-dark text-start" style="padding:100px 20px;">
        <h1>vi. 處理序(Processes)</h1>
        <h4>應用程式必須以“無狀態”的方式在處理序上執行</h4>
        <p>一般應用程式會在一個或多個處理序(Process)上執行，例如在工程師的local開發環境通常會用一個處理序，而正式上線時系統通常會有多個處理序來執行。</p>
        <p>”無狀態“(Stateless)指的是應用程式不會有預設任何的狀態，每個request在執行完後，執行過程中所用到的狀態(State)都不會被儲存下來。</p>
        <p>執行”十二因子應用程式“的處理序絕對是”無狀態“且不直接分享資料的，每個處理序之間不會有任何的溝通，也不會預設互通的狀態。有需要互通的資料一律由 後端支援服務(Backing Service)儲存，例如資料庫或是快速儲存記憶體(cache)。因為應用程式會由多個處理序執行，而無法預期下個request來時會由哪 一個處理序執行。唯有透過共通的Backing Service，才可以確保資料的完整性。</p>
        <p>另外應用程式可以在上線(Live)的狀態下隨時增加處理序甚至是新的硬體，如果依靠暫存的記憶體，則無法保證執行所需的資料的完整性。 例如說一般常見的http session，就不應該直接儲存在記憶體裡面，而應該利用可設定自動失效的Memcached或是Redis來儲存。</p>
      </section> 
      <section id="list-port" class="container-fluid bg-primary text-white text-start" style="padding:100px 20px;">
        <h1>vii. 連接埠(Port Binding)</h1>
        <h4>透過連接埠提供對外服務</h4>
        <p>”十二因子應用程式“的服務一律都已完整定義在程式碼中，要對外提供服務時，只要網路伺服器透過連接埠就可以執行。 例如一般的Java的網頁通常是透過Tomcat或是Jetty之類的伺服器，將連接埠綁在8080上，對外就可以透過 對外路徑設定(Route)到該應用程式上。如果在本地一般就是直接連上http://localhost:8080/。 由於是透過伺服器的連接埠來定義上線的程式，一個伺服器也可以同時擁有多個應用程式。一個常見的例子就是 一個伺服器同時有客戶(Customer)使用的應用程式跟管理者(Admin)使用的應用程式，只是綁在不同的連接埠上罷了。</p>
        <p>連接埠的應用不只限於網頁程式，也可以是各種的網路服務，例如FTP，或是各種客制的服務。”十二因子應用程式“也可以 成為其他應用程式的”後端支援服務“(Backing Service)，例如很多應用程式本生的服務只有有提供Restful API，而沒有 任何使用者界面。</p>
      </section> 
      <section id="list-concurrency" class="container-fluid bg-secondary text-white text-start" style="padding:100px 20px;">
        <h1>viii. 同步執行(Concurrency)</h1>
        <h4>透過同步執行來加速應用程式</h4>
        <p>一般程式的執行環境都支援使用多數處理序(Process)來執行應用程式，例如JAVA的JVM就是透過Thread讓軟體同步執行多項作業(Task)。</p>
        <p>“十二因子應用程式”利用這些同步執行的工能來增進應用程式的效率跟擴充性(Scalability)。例如Http Request由一個處理序執行， 需要定期執行的作業由另一個處理序執行。</p>
        <p>這樣的設計配合“十二因子”中的無狀態(Stateless)跟不直接分享執行資源的原則，應用程式則可以簡單地透過增加硬體資源或雲端上的執行單位來 最佳化(Optimize)執行的效能。</p>
      </section>
      <section id="list-disposability" class="container-fluid bg-success text-white text-start" style="padding:100px 20px;">
        <h1>ix. 快捷啟用與終止(Disposability)</h1>
        <h4>達到快速啟用與安全終止服務</h4>
        <p>“十二因子應用程式”在開發的任何階段，都要確實的保持程式啟動的速度，同時要確保程式終止時不會有無法復原或失去重要資料的狀況。 如果可以保持這兩個原則，應用程式本身就可以簡單的達到擴充性(Scalibility)，或者是硬體遷移(Migration)的過程也會簡化很多。</p>
        <p>應用程式的啟用時間應該要可以在幾秒內完成，這樣除了當流量變大時，可以快速的增加執行的單位，另外在構建跟發行的過程也會快速很多， 更新的版本可以快速的上線。</p>
        <p>應用程式在終止時要確認資料跟作業的完整度，透過後端支援服務(Backing Service)來分享狀態，這樣當一個處理序終止後，其他執行中的 處理序也可以接著完成作業。例如有些程式有很多在後端執行的作業，可以透過Queuing Service(例如RabbitMQ)來分配要執行的工作， 而無論哪一個處理序都可以分別的執行，這樣應用程式才可以個別安全的終止服務。</p>
      </section>
      <section id="list-devprod" class="container-fluid bg-danger text-white text-start" style="padding:100px 20px;">
        <h1>x. 環境的一致性(Dev/Prod Parity)</h1>
        <h4>保持不同環境(Dev，QA，Staging，Production)的一致性</h4>
        <p>傳統應用軟體的開發環境(Dev)通常會跟Production環境不同，通常原因可能是資源跟人員的分配的差異性。這差異性會造成三個軟體開發的落差：</p>
        <ul>
          <li>時間：從工程師的軟體開發環境到可以發行到production需要很長的時間，有時候要幾周甚至幾個月才可以發行新的版本。</li>
          <li>人力資源：軟體工程師負責開發軟體，需要透過系統工程師來發行軟體到production環境。</li>
          <li>工具：軟體工程師在開發時使用較輕便的工具，而production環境則使用功能較完整的工具。例如工程師用SQLite開發，而production用MySQL</li>
        </ul>
        <p>“十二因子應用程式” 強調 “無間斷的發行環境”(Continous Deployment)，發行的環境設定一律自動化，測試過的新功能會包裝成米你的版本自動發行到production， 有時一天發行一個版本，有時甚至可以一天發行多個版本。</p>
        <p>另外“十二因子應用程式” 強調任何環境都應該使用相同的工具或後端支援服務(Backing Service)，例如資料庫或是Cache。如果工具不同，會發生 新版本在開發環境測試都通過了，但發行到production就出現問題的狀況。如果真正要確保 “無間斷發行”的穩定性，就要儘量達到在各環境都使用與production一樣的工具或後端服務。</p>
        <p>謹守“十二因子”的原則，則應用程式開發的環境就會穩定很多，且之前提到的落差就會減低：</p>
        <ul>
          <li>時間：從開發到發行時間減為一天內。</li>
          <li>人力資源：發行環境設定好後，軟體工程師就可以自行發行新版本，不需要透過系統工程師。</li>
          <li>工具：任何環境的工具都與production的一樣。</li>
        </ul>
      </section>
      <section id="list-logs" class="container-fluid bg-warning text-dark text-start" style="padding:100px 20px;">
        <h1>xi. 記錄(Logs)</h1>
        <h4>透過外接服務將記錄整合起來</h4>
        <p>應用程式的執行過程通常都是透過記錄(Logs)儲存起來，一般的儲存方式為將記錄寫在伺服器的檔案內，一旦記錄檔(Log file)開啟後， 應用程式的執行內容就會一行一行的寫在檔案內，在程式終止前都會不斷的記錄著程式開發者認為重要的訊息，例如錯誤資訊或是未來可以 用來分析的資料。由於SAAS的應用程式通常會在多個主機上執行，造成記錄檔案很可能處於不連續的狀態，所以需要有額外的服務來將記錄整合起來。</p>
        <p>“十二因子應用程式”本身不管理任何關於整合記錄的服務，將這類整合的任務交給執行環境去處理。“十二因子”只負責將記錄寫入該執行環境 的記錄檔內。</p>
        <p>目前已有很多整合記錄檔的工具(例如Logplex或是Fluent)，這些工具可以將每個主機上的記錄檔傳輸到在單一伺服器上，將每筆記錄的內容依據發生時間整合起來， 提供未來除錯或是分析使用。</p>
      </section>
      <section id="list-admin" class="container-fluid bg-info text-dark text-start" style="padding:100px 20px;">
        <h1>xii. 系統管理者(Admin Processes)</h1>
        <h4>在相同環境下執行管理者作業(Task)</h4>
        <p>應用程式在上線一段時間過後，難免需要執行一些管理者(Admin)的作業，例如資料庫遷移，或是需要登錄控制台(Admin Console)之類的界面管理系統資料之類的。 有時候工程師為了方便，在local環境執行更新其他環境的工作，這樣的結果會造成應用程式本身的不穩定，且嚴重影響程式碼版本的一致性。</p>
        <p>“十二因子應用程式”的管理者作業必須跟程式本身在同一個環境執行，例如在QA的環境執行QA的管理作業，production的管理作業就在production環境執行。 關於管理者作業的程式碼必須跟應用程式本身的程式碼以同一個版本發行(Release)到該環境，配合該環境的配置變數(Config)來執行。</p>
      </section>
      </div>
    </div>
  </div>
  <footer>
    <section id="myfooter" class="d-none d-md-block">
      <div class="text-info">轉載</div>
      <div><a href="http://www.the12factorapp.com/">The12Facter</a></div>
    </section>
  </footer>
</div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },


}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "~bootstrap/scss/bootstrap";

.menu_bar{
  position : fixed;
  width: 20%;
  background-color: #373737;
  max-width: 200px;
  min-width: 200px;
  height: 100%;
}

#myfooter{
  position: fixed;
  bottom: 10px;
  margin: 10px 0;
  width: 20%;
  max-width: 200px;
  min-width: 200px;
  text-align: center;
  background: none;
  z-index: 0;
  padding: 0;
}

</style>
