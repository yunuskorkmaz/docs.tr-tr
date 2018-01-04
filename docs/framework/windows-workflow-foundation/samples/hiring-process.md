---
title: "İşe alma işlemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5fcacbb-c884-4b37-a5d6-02b1b8eec7b4
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 30cad662a9cca679f7e8ce720cfde3d369b9ba60
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="hiring-process"></a>İşe alma işlemi
Bu örnek, Mesajlaşma etkinlikleri ve iş akışı Hizmetleri olarak barındırılan iki iş akışlarını kullanarak bir iş sürecini uygulamak gösterilmiştir. Bu iş akışları Contoso Ltd. adlı kurgusal bir şirkette BT altyapısının bir parçasıdır  
  
 `HiringRequest` İş akışı işlemi (olarak uygulanan bir <xref:System.Activities.Statements.Flowchart>) yetkilendirme için birkaç yöneticilerin kuruluştaki sorar. İş akışı bu hedefe ulaşmak için kuruluşunuzdaki diğer mevcut Hizmetleri kullanır (bizim durumda, bir gelen kutusu hizmeti ve düz uygulanan bir kurumsal veri hizmeti [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Hizmetleri).  
  
 `ResumeRequest` İş akışı (olarak uygulanan bir <xref:System.Activities.Statements.Sequence>) Contoso'nun dış gelişme alanları Web sitenizi gönderme iş yayımlar ve sürdürür alımını yönetir. Bir iş aktarımı dış Web sitesi (bir zaman aşımı süresi doluncaya kadar) saat veya contoso çalışana kadar sabit bir süre için kaldırmaya karar kullanılabilir.  
  
 Bu örnek, aşağıdaki özellikleri gösteren [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]:  
  
-   <xref:System.Activities.Statements.Flowchart>ve <xref:System.Activities.Statements.Sequence> iş süreçlerini modelleme için iş akışları.  
  
-   İş akışı hizmetleri.  
  
-   Mesajlaşma etkinlikleri.  
  
-   Bağıntı içerik tabanlı.  
  
-   Özel etkinlikler (bildirim temelli ve kod tabanlı).  
  
-   Sistem tarafından sağlanan SQL server Kalıcılık.  
  
-   Özel <xref:System.Activities.Persistence.PersistenceParticipant>.  
  
-   Özel izleme.  
  
-   Windows (ETW) izleme için izleme olay.  
  
-   Birleşim etkinlikler.  
  
-   <xref:System.Activities.Statements.Parallel>etkinlikler.  
  
-   <xref:System.Activities.Statements.CancellationScope>Etkinlik.  
  
-   Dayanıklı zamanlayıcılar (<xref:System.Activities.Statements.Delay> etkinlik).  
  
-   İşlemler.  
  
-   Birden çok iş akışı aynı çözüm içinde.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\HiringProcess`  
  
## <a name="description-of-the-process"></a>İşleminin açıklaması  
 Contoso, Ltd. Kapat çalışan her kendi Departmanlar denetiminiz istiyor. Yeni bir işe alma işlemini başlatmak herhangi bir personel istediği zaman, bu nedenle, işe alma gerçekte oluşabilir önce bir işe alma isteği işlemi onay gitmek ihtiyaç duyar. Bu işlem, işe alma işlemi isteği (HiringRequestService proje tanımlanan) olarak adlandırılır ve aşağıdaki adımlardan oluşur:  
  
1.  (İstek) bir çalışan işe alma işlem isteğini başlatır.  
  
2.  Sahibinin Yöneticisi isteği onaylamanız gerekir:  
  
    1.  Yöneticisi isteği reddedebilirsiniz.  
  
    2.  Yöneticisi ek bilgi için istek için istek döndürebilirsiniz:  
  
        1.  İstek sahibinin gözden geçirir ve yöneticiye geri isteği gönderir.  
  
    3.  Yöneticisi onaylayabilirsiniz.  
  
3.  Sahibinin Yöneticisi onayladıktan sonra Departman sahibi isteği onaylamanız gerekir:  
  
    1.  Departman sahibi reddedebilirsiniz.  
  
    2.  Departman sahibi onaylayabilirsiniz.  
  
4.  Departman sahibi onayladıktan sonra işlemi 2 HR yöneticileri veya CEO onayını gerektirir:  
  
    1.  İşlem kabul edilen veya reddedilen durumuna geçiş yapabilir.  
  
    2.  İşlem kabul edilirse, yeni bir örneğini `ResumeRequest` iş akışı başlatıldığında (`ResumeRequest` HiringRequest.csproj için hizmet başvurusu bağlanır.)  
  
 Yöneticileri yeni bir çalışan işe alma onayladığınızda, ik uygun adayı bulmanız gerekir. Bu işlem ikinci iş akışı tarafından gerçekleştirilen (`ResumeRequest`, ResumeRequestService.csproj tanımlıysa). Bu iş akışı bir kariyer fırsat Contoso'nun dış gelişme alanları Web sitesine ile nakil bir işi göndermek için bir işlemi tanımlar, başvuran sürdürür alır ve iş nakil durumunu izler. Konumlar (bir süresi sona erene kadar) bir sabit süre için kullanılabilir veya kaldırmak bir çalışan contoso karar kadar. `ResumeRequest` İş akışı aşağıdaki adımlardan oluşur:  
  
1.  Bir çalışan Contoso türlerinden konumu ve bir zaman aşımı süresi hakkında bilgi. Bu bilgi çalışanı türlerinde konumu gelişme alanları Web sitesinde yayınlanan sonra.  
  
2.  Bilgi yayımlandığında taraflara kendi sürdürür gönderebilirsiniz. Bir sürdürme gönderildiğinde iş açılış bağlı bir kayıt depolanır.  
  
3.  Başvuran sürdürür zaman aşımı süresi veya Contoso ik departmanı birinden işlemini durdurarak nakil kaldırmak açıkça verirse kadar gönderebilirsiniz.  
  
## <a name="projects-in-the-sample"></a>Örnek Proje  
 Aşağıdaki tabloda örnek çözümde projeleri gösterir.  
  
|Proje|Açıklama|  
|-------------|-----------------|  
|ContosoHR|Veri sözleşmeleri, iş nesneleri ve depo sınıflarını içerir.|  
|HiringRequestService|İşe alma isteği işlemi iş akışı tanımını içerir.<br /><br /> Bu proje iş akışı (xaml dosyası) bir hizmet olarak kendi kendini barındıran bir konsol uygulaması olarak uygulanır.|  
|ResumeRequestService|Bir zaman aşımı süresi doluncaya kadar adaylar veya birisi sürdürür toplayan bir iş akışı hizmeti işlemi durdurulacak olduğunu belirler.<br /><br /> Bu proje bir bildirim temelli iş akışı hizmeti (xamlx) uygulanır.|  
|OrgService|Kuruluş bilgilerini (çalışanlar, konumları, PositionTypes ve Departmanlar) sunan bir hizmet. Bu hizmet şirket kuruluş modülü, bir kurumsal kaynak planlama (ERP) olarak düşünebilirsiniz.<br /><br /> Bu proje kullanıma sunan bir konsol uygulaması uygulanan bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmet.|  
|InboxService|Çalışanlar için yapılabilir görevleri içeren bir gelen kutusu.<br /><br /> Bu proje bir WCF hizmeti sunan bir konsol uygulaması uygulanır.|  
|InternalClient|İşlem ile etkileşim için bir Web uygulaması. Kullanıcıların Başlat katılır ve kendi HiringProcess iş akışları görüntüleyin. Bu uygulamayı kullanarak, bunlar da başlatabilir ResumeRequest işlemcilerini izler.<br /><br /> Bu site, Contoso'nun intranet için dahili olarak uygulanır. Bu proje bir ASP.NET Web sitesi olarak uygulanır.|  
|CareersWebSite|Bir dış Web Contoso açık konumda gösteren sitesi. Olası tüm aday bu siteye gidin ve bir sürdürme gönderin.|  
  
## <a name="feature-summary"></a>Özellik Özeti  
 Aşağıdaki tabloda, bu örnekte her bir özelliğin nasıl kullanıldığı açıklanmaktadır.  
  
|Özellik|Açıklama|Proje|  
|-------------|-----------------|-------------|  
|Akış Çizelgesi|İş sürecini bir akış temsil edilir. Bu akış çizelgesi açıklama içinde bir iş, Beyaz Tahta üzerinde çizilen aynı şekilde işlem temsil eder.|HiringRequestService|  
|İş akışı Hizmetleri|Akış işlemi tanımıyla birlikte bir hizmette barındırılıyorsa (Bu örnekte, bir konsol uygulamasında hizmet barındırılıyor).|HiringRequestService|  
|Mesajlaşma etkinlikleri|Akış Mesajlaşma etkinlikleri iki yolla kullanır:<br /><br /> -(Her onay adımda kararları ve ilgili bilgileri almak üzere) kullanıcıdan bilgi almak için.<br />-(InboxService ve hizmet başvuruları kullanılan OrgDataService) var olan diğer hizmetlerle etkileşim için.|HiringRequestService|  
|İçerik dayalı bağıntı|Onay iletileri işe alma isteği kimliği özellikte ilişkilendirmek:<br /><br /> -Bir işlem başlatıldığında, bağıntı tanıtıcı istek kimliği ile başlatıldı.<br />-Gelen onay iletileri (ilk her onay iletisi isteğin kimliği parametredir) ID'LERİNİ ilişkilendirmek.|HiringRequestService / ResumeRequestService|  
|Özel etkinlikler (bildirim temelli ve temel kodu)|Bu örnekte birkaç özel etkinlikler vardır:<br /><br /> -   `SaveActionTracking`: Bu etkinlik bir özel yayar <xref:System.Activities.Tracking.TrackingRecord> (kullanarak <xref:System.Activities.NativeActivityContext.Track%2A>). Kesinlik temelli kodu genişletme kullanılarak yazılan bu etkinliği <xref:System.Activities.NativeActivity>.<br />-   `GetEmployeesByPositionTypes`: Bu etkinlik, konum türü kimlikleri listesini alır ve Contoso, bu konumda sahip kişilerin listesini döndürür. Bu etkinlik bildirimli olarak yazılan (etkinlik Tasarımcısı'nı kullanarak).<br />-   `SaveHiringRequestInfo`: Bu etkinliği ilgili bilgileri kaydeder bir `HiringRequest` (kullanarak `HiringRequestRepository.Save`). Kesinlik temelli kodu genişletme kullanılarak yazılan bu etkinliği <xref:System.Activities.CodeActivity>.|HiringRequestService|  
|Sistem tarafından sağlanan SQL Server kalıcılığı|<xref:System.ServiceModel.Activities.WorkflowServiceHost> Akış çizelgesi işlem tanımı barındıran örneği sistem tarafından sağlanan SQL Server Kalıcılık kullanacak şekilde yapılandırıldı.|HiringRequestService / ResumeRequestService|  
|Özel İzleme|Örnek geçmişini kaydeden özel izleme katılımcı içeren bir `HiringRequestProcess` (Bu eylemi, kim tarafından gerçekleştirildi kaydeder ve ne zaman). Kaynak kodu HiringRequestService İzleme klasöründe bulunur.|HiringRequestService|  
|ETW İzleme|Sistem tarafından sağlanan ETW İzleme HiringRequestService hizmet App.config dosyasında yapılandırılır.|HiringRequestService|  
|Etkinlik oluşturma|İşlem tanımı boş oluşumunu kullanan <xref:System.Activities.Activity>. Akış birkaç dizisi ve aynı zamanda diğer etkinlikleri (vb.) içeren paralel etkinlikleri içerir.|HiringRequestService|  
|Paralel etkinlikler|-   <xref:System.Activities.Statements.ParallelForEach%601>paralel (iki HR yöneticileri onay adım bekleniyor) CEO ve HR yöneticilerinin gelen kutunuzda kaydetmek için kullanılır.<br />-   <xref:System.Activities.Statements.Parallel>Tamamlanan ve reddedildi adımlarda bazı temizleme görevleri yapmak için kullanılır|HiringRequestService|  
|Model iptali|Akış kullanan <xref:System.Activities.Statements.CancellationScope> iptal davranışı (Bu durumda bunu yapar bazı temizleyin.) oluşturmak için|HiringRequestService|  
|Müşteri Kalıcılık katılımcı|`HiringRequestPersistenceParticipant`verileri bir iş akışı değişkeninden Contoso HR veritabanında depolanan bir tabloya kaydeder.|HiringRequestService|  
|İş Akışı Hizmetleri|`ResumeRequestService`İş akışı Hizmetleri kullanılarak uygulanır. İş akışı tanımı ve hizmet bilgilerini ResumeRequestService.xamlx içinde yer alır. Hizmeti Kalıcılık ve izleme kullanmak üzere yapılandırılır.|ResumeRequestService|  
|Dayanıklı zamanlayıcılar|`ResumeRequestService`dayanıklı zamanlayıcılar nakil iş süresini tanımlamak için kullanır (bir zaman aşımı süresi dolduktan sonra iş nakil kapalı).|ResumeRequestService|  
|İşlemler|<xref:System.Activities.Statements.TransactionScope>(yeni Sürdür alındığında) birkaç etkinlik yürütülmesini içinde veri tutarlılığını sağlamak için kullanılır.|ResumeRequestService|  
|İşlemler|Özel Kalıcılık katılımcı (`HiringRequestPersistenceParticipant`) ve özel izleme katılımcı (`HistoryFileTrackingParticipant`) aynı işlem kullanın.|HiringRequestService|  
|Kullanarak [!INCLUDE[wf1](../../../../includes/wf1-md.md)] içinde [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulamalar.|İş akışları iki erişilir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulamalar.|InternalClient / CareersWebSite|  
  
## <a name="data-storage"></a>Veri depolama  
 Veri adlı bir SQL Server veritabanında depolanan `ContosoHR` (Bu veritabanını oluşturmak için komut dosyası bulunan `DbSetup` klasörü). İş akışı örnekleri olarak adlandırılan bir SQL Server veritabanında depolanan `InstanceStore` (örnek deposuna oluşturma komut dosyaları parçası olan [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] dağıtım).  
  
 Her iki veritabanı Setup.cmd komut dosyasını çalıştırarak oluşturulan bir [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] komut istemi.  
  
## <a name="running-the-sample"></a>Örnek çalışıyor  
  
#### <a name="to-create-the-databases"></a>Veritabanı oluşturma  
  
1.  Açık bir [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] komut istemi.  
  
2.  Örnek klasöre gidin.  
  
3.  Setup.cmd çalıştırın.  
  
4.  İki veritabanları doğrulayın `ContosoHR` ve `InstanceStore` SQL Express oluşturulmuş.  
  
#### <a name="to-set-up-the-solution-for-execution"></a>Yürütme için çözüm ayarlamak için  
  
1.  Çalıştırma [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] yönetici olarak. HiringRequest.sln açın.  
  
2.  Çözüme sağ **Çözüm Gezgini** seçip **özellikleri**.  
  
3.  Seçeneğini **birden fazla başlangıç projesi** ve **CareersWebSite**, **InternalClient**, **HiringRequestService**, ve **ResumeRequestService** için **Başlat**. Bırakın **ContosoHR**, **InboxService**, ve **OrgService** hiçbiri olarak.  
  
4.  CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun. Yapı başarılı olduğunu doğrulayın.  
  
#### <a name="to-run-the-solution"></a>Çözümü çalıştırmak için  
  
1.  Çözüm oluşturduktan sonra hata ayıklama olmadan çalıştırmak için CTRL + F5 tuşuna basın. Tüm hizmetler başladıktan doğrulayın.  
  
2.  Sağ tıklayın **InternalClient** çözüm seçip ardından **tarayıcıda görüntüle**. Varsayılan sayfa için `InternalClient` görüntülenir. Hizmetlerinin çalışmakta olduğunu ve bağlantıya tıklayın emin olun.  
  
3.  **HiringRequest** modülü görüntülenir. Burada ayrıntılı senaryoyu izleyebilirsiniz.  
  
4.  Bir kez `HiringRequest` olan tam, başlatabilirsiniz `ResumeRequest`. Burada ayrıntılı senaryoyu izleyebilirsiniz.  
  
5.  Zaman `ResumeRequest` olan gönderilen, genel Web sitesinde (Contoso gelişme alanları Web sitesi) kullanılabilir. İş bkz (ve konumunu uygulamak için) gelişme alanları Web sitesine gidin.  
  
6.  Sağ **CareersWebSite** çözüm seçip **tarayıcıda görüntüle**.  
  
7.  Geri gidin `InternalClient` sağ tıklanarak **InternalClient** çözümdeki seçerek **tarayıcıda görüntüle**.  
  
8.  Git **JobPostings** tıklatarak bölüm **iş aktarımlar** gelen kutusu üst menüsündeki bağlantısı. Burada ayrıntılı senaryoyu izleyebilirsiniz.  
  
## <a name="scenarios"></a>Senaryolar  
  
### <a name="hiring-request"></a>İşe alma isteği  
  
1.  Michael Alexander (yazılım mühendisi) yeni bir konuma sahip en az 3 yıllık deneyimi C# ' ta mühendislik departmanında yazılım mühendisi Test (SDET) işe alma isteği istiyor.  
  
2.  Oluşturulduktan sonra istek Michael'ın gelen kutusunda görüntülenir (tıklatın **Yenile** istek görmüyorsanız) Michael'ın yöneticisi olan Peter Brehm'ın onay bekleniyor.  
  
3.  Peter Michael'in istek üzerine hareket istiyor. Kendisine onun açıklamaları gözden geçirme için geri gönderir şekilde kendisinin konumu taleplerini deneyiminin C# 3, yerine 5 yıl düşünmektedir.  
  
4.  Michael kendi gelen kutunuzda kendi Yöneticisi'nden bir ileti görür ve hareket istiyor. Michael konumu isteği geçmişini görür ve Peter ile kabul eder. Michael C# deneyimi 5 yıllık gerektirecek şekilde açıklama değiştirir ve değişikliği kabul eder.  
  
5.  Peter Michael'ın değiştirilmiş isteğinde görevi görür ve onu kabul eder. İstek artık Director, mühendislik tarafından Tsvi Reiter onaylanması gerekir.  
  
6.  İsteği kendisinin istek acildir ve kabul ettiği söylemek için bir açıklama koyar şekilde hızlandırmak Tsvi Reiter istemektedir.  
  
7.  İstek artık iki HR yöneticileri veya CEO tarafından onaylanması gerekir. Brian Richard Goldstein CEO Tsvi Acil isteğiyle görür. Kendisine isteği kabul ederek, böylece iki HR yöneticileri tarafından onay atlayarak yapar.  
  
8.  İstek Michael'ın Kutusu'ndan kaldırılır ve artık bir SDET işe alma işlemi başladı.  
  
### <a name="start-resume-request"></a>Sürdürme isteği Başlat  
  
1.  İş pozisyonu şimdi, kişilerin burada uygulayabilirsiniz bir dış Web sitesine postalama bekliyor ('i tıklatarak görebilirsiniz **iş aktarımlar** bağlantı). Şu anda iş pozisyonu tamamlanıyor ve bu nakil sorumlu olan bir HR temsilcisi ile iş pozisyonu durduğunu.  
  
2.  HR istediği bu işi konumu düzenlemek (tıklayarak **Düzenle** bağlantı) 60 dakikalık bir zaman aşımı ayarlayarak (gerçek hayatta bu gün veya hafta olabilir). Zaman aşımı belirtilen süreye göre dış Web sitesi devre dışı gerçekleştirilecek işi konumunu sağlar.  
  
3.  Düzenlenmiş iş pozisyonu kaydedildikten sonra görünür **alma sürdürür** sekmesinde (yenileme yeni proje konumuna görmek için bu Web sayfası).  
  
### <a name="collecting-resumes"></a>Toplama sürdürür  
  
1.  İş pozisyonu dış Web sitesinde görüntülenmesi gerekir. İş için uygulama ilgilenen bir kişi bu konum için geçerli ve, Sürdür gönderin.  
  
2.  İş aktarımlar listesi hizmete geri dönün, "sürdürür görüntüleyebileceğiniz", toplanan kadarki.  
  
3.  HR ayrıca sürdürür (örneğin, doğru adayı belirlendikten sonra) toplama durdurabilirsiniz.  
  
## <a name="troubleshooting"></a>Sorun giderme  
  
1.  Çalıştığından emin olun [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] yönetici ayrıcalıklarına sahip.  
  
2.  Çözümü derleme işlemi başarısız olursa aşağıdakileri doğrulayın:  
  
    -   Başvuru `ContosoHR` gelen eksik değil `InternalClient` veya `CareersWebSite` projeleri.  
  
3.  Çözüm yürütme başarısız olursa aşağıdakileri doğrulayın:  
  
    1.  Tüm hizmetler çalışıyor.  
  
    2.  Hizmet başvuruları güncelleştirilir.  
  
        1.  App_WebReferences klasörünü açın  
  
        2.  Sağ **Contoso** seçip **güncelleştirme Web/hizmet başvuruları**.  
  
        3.  CTRL + SHIFT + B tuşuna basarak çözümü yeniden derleyin [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].  
  
## <a name="uninstalling"></a>Kaldırma  
  
1.  SQL Server örnek deposuna DbSetup klasöründe Cleanup.bat çalıştırarak silin.  
  
2.  Kaynak kodu biçiminde sabit silin.