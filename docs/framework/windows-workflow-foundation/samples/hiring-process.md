---
title: İşe Alma İşlemi
ms.date: 03/30/2017
ms.assetid: d5fcacbb-c884-4b37-a5d6-02b1b8eec7b4
ms.openlocfilehash: c6f542cef8e1417ed9c8d3a185252a91062e2161
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62005062"
---
# <a name="hiring-process"></a>İşe Alma İşlemi
Bu örnek nasıl uygulanacağını Mesajlaşma etkinlikleri ve iş akışı hizmetlerinde barındırılan iki iş akışlarını kullanarak bir iş sürecini gösterir. Bu iş akışları Contoso, Inc. adlı kurgusal bir şirkette BT altyapısını bir parçasıdır  
  
 `HiringRequest` İş akışı işlemi (olarak uygulanan bir <xref:System.Activities.Statements.Flowchart>) yetkilendirme için birkaç yöneticilerin kuruluş içindeki ister. Bu hedefe ulaşmak için var olan diğer hizmetleri iş akışını kuruluştaki (bizim durumumuzda, bir gelen kutusu hizmeti ve düz Windows Communication Foundation (WCF) Hizmetleri uygulanan bir kurumsal veri hizmeti) kullanır.  
  
 `ResumeRequest` İş akışı (olarak uygulanan bir <xref:System.Activities.Statements.Sequence>) Contoso'nun dış kariyerleri Web sitesinde yayınlayarak bir işi yayımlar ve sürdürür alımını yönetir. Bir işin aktarım dış Web site (bir zaman aşımı süresi dolana kadar) zaman veya şubeden çalışana kadar sabit bir süre için kaldırmaya karar kullanılabilir.  
  
 Bu örnek, aşağıdaki özellikleri gösterir. [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]:  
  
- <xref:System.Activities.Statements.Flowchart> ve <xref:System.Activities.Statements.Sequence> iş süreçlerini modelleme için iş akışları.  
  
- İş akışı hizmetleri.  
  
- Mesajlaşma etkinlikleri.  
  
- İçerik temelli bağıntı.  
  
- Özel etkinlikler (bildirim ve kod tabanlı).  
  
- Sistem tarafından sağlanan SQL server Kalıcılık.  
  
- Özel <xref:System.Activities.Persistence.PersistenceParticipant>.  
  
- Özel izleme.  
  
- Windows (ETW) izleme için izleme olayı.  
  
- Etkinlik oluşturma.  
  
- <xref:System.Activities.Statements.Parallel> etkinlikler.  
  
- <xref:System.Activities.Statements.CancellationScope> Etkinlik.  
  
- Dayanıklı zamanlayıcılar (<xref:System.Activities.Statements.Delay> etkinliği).  
  
- İşlem.  
  
- Aynı çözümdeki birden çok iş akışı.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\HiringProcess`  
  
## <a name="description-of-the-process"></a>İşlem açıklaması  
 Contoso, Inc. Kapat personel kendi bölümlerin her denetiminiz ister. Yeni bir işe alma işlemini başlatmak herhangi bir çalışanın istediği zaman, bu nedenle, bunlar gerçekten işe oluşabilir önce bir işe alma isteği işlemi onay gitmeniz gerekiyor. Bu işlem, işe alma işlemi istek (HiringRequestService projede tanımlanan) olarak adlandırılır ve aşağıdaki adımlardan oluşur:  
  
1. Bir çalışan (istek) işe alma işlem isteğini başlatır.  
  
2. İstek sahibinin Yöneticisi isteği onaylamanız gerekir:  
  
    1. Yönetici isteği reddedebilir.  
  
    2. Yönetici isteği belirtmesine ek bilgi için dönebilirsiniz:  
  
        1. İstek sahibinin inceler ve Yöneticisi isteği gönderir.  
  
    3. Yönetici onaylayabilirsiniz.  
  
3. İstek sahibinin manager onayladıktan sonra Departman sahibi isteği onaylamanız gerekir:  
  
    1. Departman sahibi reddedebilirsiniz.  
  
    2. Departman sahibi onaylayabilirsiniz.  
  
4. Departman sahibi onayladıktan sonra işlemi 2 ik yöneticileri veya CEO onayını gerektirir:  
  
    1. İşlem, kabul edilen veya reddedilen durumuna geçiş yapabilirsiniz.  
  
    2. İşlem kabul edilirse, yeni bir örneğini `ResumeRequest` iş akışı başlatılır (`ResumeRequest` HiringRequest.csproj için bir hizmet başvurusu ile bağlantılıdır.)  
  
 Yeni bir çalışan işe alma yöneticileri onayladıktan sonra ik uygun aday bulmanız gerekir. Bu işlem ikinci bir iş akışı tarafından gerçekleştirilir (`ResumeRequest`ResumeRequestService.csproj içinde tanımlanmış). Bu iş akışı Contoso'nun dış Kariyerleri Web sitesine bir kariyer fırsatla gönderen bir iş göndermek için bir işlemi tanımlar, başvuran sürdürür alır ve iş posta durumunu izler. Konumları (bir süresi dolana kadar) bir sabit bir zaman aralığı için kullanılabilir veya bir çalışan şubeden kaldırmaya karar kadar. `ResumeRequest` İş akışı, aşağıdaki adımlardan oluşur:  
  
1. Bir çalışan Contoso türlerinden konumu ve bir zaman aşımı süresi hakkında bilgi. Bu bilgi çalışanı türlerinde Kariyerleri Web sitesinde konumu gönderildikten sonra.  
  
2. Bilgi yayımlandıktan sonra ilgili tarafların kendi sürdürür gönderebilirsiniz. Bir özgeçmiş gönderildiğinde iş açılış bağlı bir kayıt depolanır.  
  
3. Başvuranları sürdürür Contoso ik departmanı birinden açıkça işlemini durdurarak posta kaldırmaya karar veya zaman aşımı süresi dolana kadar gönderebilirsiniz.  
  
## <a name="projects-in-the-sample"></a>Örnek projeleri  
 Aşağıdaki tabloda, örnek çözümdeki projeleri gösterir.  
  
|Project|Açıklama|  
|-------------|-----------------|  
|ContosoHR|Veri sözleşmeleri, iş nesneleri ve depo sınıfları içerir.|  
|HiringRequestService|İşe alma isteği işlemi iş akışının tanımını içerir.<br /><br /> Bu proje, iş akışı (xaml dosyası) bir hizmet olarak kendi kendini barındıran bir konsol uygulaması olarak uygulanır.|  
|ResumeRequestService|Bir zaman aşımı süresi dolana kadar adayları veya birisi sürdürür toplayan bir iş akışı hizmeti, işlem durdurulacak olduğunu karar verir.<br /><br /> Bu proje bir bildirim temelli bir iş akışı hizmeti (xamlx) uygulanır.|  
|OrgService|Kurumsal bilgilerin (çalışanlar, konumları, PositionTypes ve Departmanlar) hizmetidir. Bu hizmet şirket kuruluş modülü, bir kurumsal kaynak planlama (ERP) olarak düşünebilirsiniz.<br /><br /> Bu proje bir Windows Communication Foundation (WCF) hizmeti sunan bir konsol uygulaması uygulanır.|  
|InboxService|Çalışanlar için eyleme geçirilebilir görevleri içeren bir gelen kutusu.<br /><br /> Bu proje bir WCF hizmeti sunan bir konsol uygulaması uygulanır.|  
|InternalClient|İşlem ile etkileşim kurmak için kullanabileceğiniz bir Web uygulaması. Kullanıcılar, Başlat, katılmak ve HiringProcess iş akışlarını görüntüleme. Bu uygulamayı kullanarak, bunlar da başlatabilir ve ResumeRequest işlemcilerini izler.<br /><br /> Bu site, Contoso'nun intranet için dahili olarak uygulanır. Bu proje, bir ASP.NET Web sitesi uygulanır.|  
|CareersWebSite|Bir dış Web ortaya koyan açık pozisyonları contoso'da sitesi. Olası tüm aday, bu siteye gidin ve bir özgeçmiş gönderin.|  
  
## <a name="feature-summary"></a>Özellik Özeti  
 Aşağıdaki tabloda, bu örnekte, her bir özelliğin nasıl kullanıldığı açıklanmaktadır.  
  
|Özellik|Açıklama|Project|  
|-------------|-----------------|-------------|  
|Akış Çizelgesi|İş süreci akış grafiği olarak temsil edilir. Bu akış tanımı bir iş, Beyaz Tahta üzerinde çizilen aynı şekilde işlem temsil eder.|HiringRequestService|  
|İş akışı Hizmetleri|Akış işlem tanımıyla birlikte bir hizmette barındırılıyorsa (Bu örnekte, hizmeti bir konsol uygulamasında barındırılan).|HiringRequestService|  
|Mesajlaşma etkinlikleri|Akış iki yolla Mesajlaşma etkinlikleri kullanır:<br /><br /> -(Her onay adımda kararlarını ve ilgili bilgi almak için) kullanıcıdan bilgi almak için.<br />-Var olan diğer hizmetler (InboxService ve hizmet başvuruları kullanılan OrgDataService,) ile etkileşim kurmak için.|HiringRequestService|  
|İçerik dayalı bağıntı|Onay iletilerini işe alma isteği kimliği özelliği ilişkilendirin:<br /><br /> -İşlem başlatıldığında, bağıntı tanıtıcı istek kimliği ile başlatıldı.<br />-Gelen onay iletiler (her onay iletisi ilk parametresi istek kimliğidir) Kimliklerine ilişkilendirin.|HiringRequestService / ResumeRequestService|  
|Özel etkinlikler (bildirim ve kod tabanlı)|Bu örnekte, birkaç özel etkinlikler vardır:<br /><br /> -   `SaveActionTracking`: Bu etkinlik bir özel yayan <xref:System.Activities.Tracking.TrackingRecord> (kullanarak <xref:System.Activities.NativeActivityContext.Track%2A>). Kesinlik temelli Kodun genişletme kullanılarak yazılan bu etkinlik <xref:System.Activities.NativeActivity>.<br />-   `GetEmployeesByPositionTypes`: Bu etkinlik, konum türü kimlikleri listesini alır ve söz konusu pozisyondaki Contoso sahip kişilerin listesini döndürür. Bu etkinlik bildirimli olarak yazılmış (etkinlik Tasarımcısı'nı kullanarak).<br />-   `SaveHiringRequestInfo`: Bu etkinlik bilgilerini kaydeder. bir `HiringRequest` (kullanarak `HiringRequestRepository.Save`). Kesinlik temelli Kodun genişletme kullanılarak yazılan bu etkinlik <xref:System.Activities.CodeActivity>.|HiringRequestService|  
|Sistem tarafından sağlanan SQL Server Kalıcılık|<xref:System.ServiceModel.Activities.WorkflowServiceHost> Akış işlem tanımını barındıran örneği sistem tarafından sağlanan SQL Server Kalıcılık kullanacak şekilde yapılandırıldı.|HiringRequestService / ResumeRequestService|  
|Özel İzleme|Örnek geçmişini kaydeden özel izleme katılımcı içeren bir `HiringRequestProcess` (Bu ne, kim tarafından gerçekleştirilmedi kaydeder ve ne zaman). Kaynak kodu HiringRequestService İzleme klasöründe bulunur.|HiringRequestService|  
|ETW İzleme|Sistem tarafından sağlanan ETW İzleme HiringRequestService hizmet App.config dosyasında yapılandırılır.|HiringRequestService|  
|Etkinlik oluşturma|Ücretsiz oluşumunu işlem tanımını kullanan <xref:System.Activities.Activity>. Akış birkaç dizisi ve aynı zamanda diğer etkinlikleri içeren (vb.) paralel etkinlikler içerir.|HiringRequestService|  
|Paralel etkinlikler|-   <xref:System.Activities.Statements.ParallelForEach%601> paralel (iki ik yöneticileri açık onay adımı için bekleniyor) CEO ve ik yöneticileri gelen kutusunda kaydetmek için kullanılır.<br />-   <xref:System.Activities.Statements.Parallel> Tamamlanan ve reddedildi adımlarda bazı temizleme görevlerini yapmak için kullanılır|HiringRequestService|  
|Model iptal|Akış kullanan <xref:System.Activities.Statements.CancellationScope> (Bu durumda yaptığını bazı temizleme.) iptal davranışı oluşturmak için|HiringRequestService|  
|Müşteri Kalıcılık Katılımcısı|`HiringRequestPersistenceParticipant` verileri bir iş akışı değişkeninin Contoso ik veritabanında depolanan bir tabloya kaydeder.|HiringRequestService|  
|İş Akışı Hizmetleri|`ResumeRequestService` İş akışı Hizmetleri kullanılarak uygulanır. İş akışı tanımı ve hizmet bilgileri ResumeRequestService.xamlx içinde yer alır. Hizmet, Kalıcılık ve izleme kullanmak için yapılandırılır.|ResumeRequestService|  
|Dayanıklı zamanlayıcılar|`ResumeRequestService` dayanıklı süreölçer işi bir uyarı yayınlayarak süresini tanımlamak için kullanır (zaman aşımı süresi sona erdiğinde, işi gönderme kapalı).|ResumeRequestService|  
|İşlemler|<xref:System.Activities.Statements.TransactionScope> (yeni bir özgeçmiş alındığında) içinde birkaç etkinliği yürütülmesi veri tutarlılığını sağlamak için kullanılır.|ResumeRequestService|  
|İşlemler|Özel Kalıcılık Katılımcısı (`HiringRequestPersistenceParticipant`) ve özel izleme katılımcı (`HistoryFileTrackingParticipant`) aynı işlem kullanın.|HiringRequestService|  
|Kullanarak [!INCLUDE[wf1](../../../../includes/wf1-md.md)] içinde [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulamalar.|İş akışları iki erişilir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulamalar.|InternalClient / CareersWebSite|  
  
## <a name="data-storage"></a>Veri depolama  
 Verileri, adlı bir SQL Server veritabanında depolandığı `ContosoHR` (Bu veritabanını oluşturmak için betik bulunan `DbSetup` klasörü). İş akışı örnekleri olarak adlandırılan bir SQL Server veritabanında depolanan `InstanceStore` (örnek deposu oluşturma komut dosyaları parçası olan [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] dağıtım).  
  
 Her iki veritabanı, Visual Studio için geliştirici Komut İstemi'nden Setup.cmd betiği çalıştırarak oluşturulur.  
  
## <a name="running-the-sample"></a>Örneği çalıştırma  
  
#### <a name="to-create-the-databases"></a>Veritabanı oluşturma  
  
1. Visual Studio için geliştirici komut istemi açın.  
  
2. Örnek klasörüne gidin.  
  
3. Setup.cmd'yi çalıştırın.  
  
4. İki veritabanı doğrulayın `ContosoHR` ve `InstanceStore` SQL Express'te oluşturulan.  
  
#### <a name="to-set-up-the-solution-for-execution"></a>Yürütme için çözüm ayarlamak için  
  
1. Visual Studio'yu yönetici olarak çalıştırın. Open HiringRequest.sln.  
  
2. Çözüme sağ **Çözüm Gezgini** seçip **özellikleri**.  
  
3. Seçeneğini **birden fazla başlangıç projesi** ayarlayıp **CareersWebSite**, **InternalClient**, **HiringRequestService**, ve **ResumeRequestService** için **Başlat**. Bırakın **ContosoHR**, **InboxService**, ve **OrgService** olarak yok.  
  
4. CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun. Derleme başarılı olduğunu doğrulayın.  
  
#### <a name="to-run-the-solution"></a>Çözümü çalıştırmak için  
  
1. Çözüm oluşturduktan sonra hata ayıklama olmadan çalıştırmak için CTRL + F5 tuşlarına basın. Tüm hizmetlerin başlatıldığından emin olun.  
  
2. Sağ tıklayın **InternalClient** çözüm ve ardından **tarayıcıda görüntüle**. Varsayılan sayfanın `InternalClient` görüntülenir. Hizmetlerinin çalışmakta olduğunu ve bağlantıyı emin olun.  
  
3. **HiringRequest** modülü görüntülenir. Burada ayrıntıları senaryoyu izleyebilirsiniz.  
  
4. Bir kez `HiringRequest` olan tam başlatabilirsiniz `ResumeRequest`. Burada ayrıntıları senaryoyu izleyebilirsiniz.  
  
5. Zaman `ResumeRequest` olan gönderilen, genel Web sitesinde (Contoso Kariyerleri Web sitesi) kullanılabilir. İş gönderme bakın (ve konumunu uygulamak için), Kariyerleri Web sitesine gidin.  
  
6. Sağ **CareersWebSite** çözüm seçip **tarayıcıda görüntüle**.  
  
7. Geri gidin `InternalClient` sağ tıklanarak **InternalClient** çözümdeki seçerek **tarayıcıda görüntüle**.  
  
8. Git **JobPostings** bölümüne tıklayarak **iş gönderilerinin** gelen üst menüdeki bağlantı. Burada ayrıntıları senaryoyu izleyebilirsiniz.  
  
## <a name="scenarios"></a>Senaryolar  
  
### <a name="hiring-request"></a>İşe alma isteği  
  
1. Michael Alexander (yazılım mühendisi) yeni bir konuma sahip en az 3 yıllık deneyim C# dilinde mühendislik departmanındaki yazılım mühendisi testi (SDET) işe alma isteği ister.  
  
2. Oluşturulduktan sonra istek Michael'ın gelen kutunuzda görünen (tıklayın **Yenile** istek görmüyorsanız) Michael'ın yöneticisi olan Peter Brehm'ın onay bekliyor.  
  
3. Peter, Michael'in istek üzerine hareket ister. He kendi açıklamaları gözden geçirilmek üzere geri gönderir. Bu nedenle o konum taleplerini C# deneyimi, 3 yerine 5 yıl düşünüyor.  
  
4. Michael kendi Manager'dan kendi gelen kutunuzda bir ileti görür ve yapmasını istemektedir. Michael geçmişini konumu isteği göreceğini ve Peter ile kabul eder. Michael açıklama C# deneyimi 5 yıl gerektirecek şekilde değiştirir ve değişikliği kabul eder.  
  
5. Peter, Michael'ın değiştirilmiş istek üzerinde çalışır ve bunu kabul eder. İstek artık mühendislik Direktörü, tarafından Tsvi Reiter onaylanmalıdır.  
  
6. He bir açıklama isteği Acil değildir ve kabul ettiği söylemek koyar için istek hızlandırmak Tsvi Reiter istiyor.  
  
7. İstek artık iki ik yöneticileri veya CEO tarafından onaylanması gerekir. CEO, Brian Richard Goldstein Tsvi Acil isteğiyle görür. He isteği kabul ederek, bu nedenle iki ik yöneticileri onayını atlama işlevi görür.  
  
8. İstek Michael'ın kutunuzdan ve SDET işe alma işlemi artık başladı.  
  
### <a name="start-resume-request"></a>Sürdürme isteği Başlat  
  
1. İş konumu şimdi, kişilerin yeri uygulayabilirsiniz bir dış Web sitesine yayınlanabilir bekliyor ('i tıklatarak gördüğünüz **iş gönderilerinin** bağlantı). Şu anda iş konumu tamamlanıyor ve bu ileti gönderme için sorumlu ik temsilcisi ile iş konumu yer.  
  
2. İK istediği bu iş konumu düzenlemek (tıklayarak **Düzenle** bağlantı) olarak ayarlayarak 60 dakikalık bir zaman aşımı (gerçek hayatta bu günler veya haftalar olabilir). Zaman aşımı dış Web sitesi belirtilen saate kapalı gerçekleştirilecek iş konumu sağlar.  
  
3. Düzenlenen iş konumu kaydettikten sonra görünür **alma sürdürür** sekmesinde (Web yeni iş konumu görmek için sayfayı yenileyin).  
  
### <a name="collecting-resumes"></a>Toplama sürdürür  
  
1. Proje konumu dış Web sitesinde görüntülenmesi gerekir. Proje için uygulama isteyen bir kişi özgeçmişinizi gönderin ve bu konum için geçerli.  
  
2. İş gönderilerinin listesini hizmete geri dönün, "sürdürür görüntüleyebileceğiniz", toplanmış olabilir kadar.  
  
3. İK, ayrıca sürdürür (örneğin, doğru aday belirlendikten sonra) toplamayı durdurabilirsiniz.  
  
## <a name="troubleshooting"></a>Sorun giderme  
  
1. Visual Studio'yu yönetici ayrıcalıklarıyla çalıştığından emin olun.  
  
2. Çözüm yapı başarısız olursa aşağıdakileri doğrulayın:  
  
    - Başvuru `ContosoHR` gelen eksik `InternalClient` veya `CareersWebSite` projeleri.  
  
3. Yürütülecek çözümü başarısız olursa aşağıdakileri doğrulayın:  
  
    1. Tüm hizmetler çalışıyor.  
  
    2. Hizmet başvurularını güncelleştirilir.  
  
        1. App_WebReferences klasörünü açın  
  
        2. Sağ **Contoso** seçip **Web/hizmet başvurularını güncelleştirme**.  
  
        3. Visual Studio'da CTRL + SHIFT + B tuşlarına basarak çözümü yeniden oluşturun.  
  
## <a name="uninstalling"></a>Kaldırma  
  
1. SQL Server örnek deposuna Cleanup.bat DbSetup klasöründe yer alan, çalıştırarak silin.  
  
2. Kaynak kod şeklinde sabit silin.
