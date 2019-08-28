---
title: İşe Alma İşlemi
ms.date: 03/30/2017
ms.assetid: d5fcacbb-c884-4b37-a5d6-02b1b8eec7b4
ms.openlocfilehash: 16975aaa56c8fde09fa6f57781f13280c147e73e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038169"
---
# <a name="hiring-process"></a>İşe Alma İşlemi
Bu örnek, bir iş sürecinin ileti etkinlikleri ve iş akışı hizmetleri olarak barındırılan iki iş akışı kullanarak nasıl uygulanacağını gösterir. Bu iş akışları, contoso, Inc adlı kurgusal bir şirketin BT altyapısının bir parçasıdır.  
  
 İş akışı işlemi (bir <xref:System.Activities.Statements.Flowchart>olarak uygulandı), kuruluştaki çeşitli yöneticilerin yetkilendirilmesini ister. `HiringRequest` Bu hedefe ulaşmak için, iş akışı kuruluştaki diğer mevcut hizmetleri (bizim örneğimizde, bir gelen kutusu hizmeti ve düz Windows Communication Foundation (WCF) Hizmetleri olarak uygulanan bir kurumsal veri hizmeti) kullanır.  
  
 İş `ResumeRequest` akışı ( <xref:System.Activities.Statements.Sequence>olarak uygulandı), contoso 'nun dış gelişme Web sitesinde bir iş nakli yayımlar ve devam eden alımı yönetir. Bir iş nakli, dış Web sitesinde sabit bir süre (bir zaman aşımı süresi dolana kadar) veya bir contoso çalışanı tarafından kaldırmaya karar verdiğinde kullanılabilir.  
  
 Bu örnek, aşağıdaki özelliklerini [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]gösterir:  
  
- <xref:System.Activities.Statements.Flowchart>iş süreçlerini modellemeye yönelik işakışları.<xref:System.Activities.Statements.Sequence>  
  
- İş akışı hizmetleri.  
  
- Mesajlaşma etkinlikleri.  
  
- İçerik tabanlı bağıntı.  
  
- Özel Etkinlikler (bildirime dayalı ve kod tabanlı).  
  
- Sistem tarafından sağlanmış SQL Server kalıcılığı.  
  
- Özel <xref:System.Activities.Persistence.PersistenceParticipant>.  
  
- Özel izleme.  
  
- Windows için olay Izleme (ETW) Izleme.  
  
- Etkinliklerin oluşturulması.  
  
- <xref:System.Activities.Statements.Parallel>işlemleri.  
  
- <xref:System.Activities.Statements.CancellationScope>etkinlik.  
  
- Dayanıklı zamanlayıcılar<xref:System.Activities.Statements.Delay> (etkinlik).  
  
- Hareket.  
  
- Aynı çözümde birden fazla iş akışı.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\HiringProcess`  
  
## <a name="description-of-the-process"></a>Işlemin açıklaması  
 Contoso, Inc., departmanlarının her birinde bulunan soyad 'un denetimini kapatmasını istiyor. Bu nedenle, herhangi bir çalışan her zaman yeni bir işe alma işlemi başlatmak istediğinde, işe almanın gerçekten gerçekleşebilmesi için bir işe alma isteği işlem onayına gitmeleri gerekir. Bu işleme işlem isteği alma (Maingrequestservice projesinde tanımlanan) adı verilir ve aşağıdaki adımlardan oluşur:  
  
1. Bir çalışan (istek sahibi), işe alma işlemi isteğini başlatır.  
  
2. İstek sahibinin yöneticisinin isteği onaylaması gerekir:  
  
    1. Yönetici, isteği reddedebilir.  
  
    2. Yönetici, ek bilgi için isteği istek sahibine döndürebilir:  
  
        1. İstek sahibi gözden geçirir ve isteği yöneticiye geri gönderir.  
  
    3. Yönetici onaylayabilir.  
  
3. İstek sahibinin Yöneticisi onayladıktan sonra, departmanın sahibi isteği onaylaması gerekir:  
  
    1. Departman sahibi reddedebilirler.  
  
    2. Departman sahibi onaylayabilirler.  
  
4. Departman sahibi onaylandıktan sonra, işlem 2 HR yöneticilerinin veya CEO 'nun onayını gerektirir:  
  
    1. İşlem kabul edilen veya reddedilmiş duruma geçirebilir.  
  
    2. İşlem kabul edilirse, `ResumeRequest` iş akışının yeni bir örneği başlatılır (`ResumeRequest` bir hizmet başvurusu aracılığıyla maingrequest. csproj öğesine bağlanır.)  
  
 Yöneticiler yeni bir çalışanın işe alım düzeyini onayladıktan sonra, HR uygun adayı bulmalıdır. Bu işlem ikinci iş akışı (`ResumeRequest`, ResumeRequestService. csproj içinde tanımlanan) tarafından gerçekleştirilir. Bu iş akışı, contoso 'nun dış önişlemcisi Web sitesi için bir kariyer fırsatına sahip bir iş gönderme sürecini tanımlar, başvuranlardan devam eden özgeçmişleri alır ve iş naklinin durumunu izler. Pozisyonlar, sabit bir zaman diliminde (bir süre sona erene kadar) veya contoso 'dan bir çalışan tarafından kaldırmaya karar verdiğinde kullanılabilir. `ResumeRequest` İş akışı aşağıdaki adımlardan oluşur:  
  
1. Konum ve zaman aşımı süresi hakkında bilgi için Contoso türlerinden bir çalışan. Çalışan bu bilgiyi yazdığında, konum, bu web sitesinde gönderilir.  
  
2. Bilgiler yayımlandıktan sonra ilgilenen taraflar, devam etmesini gönderebilirler. Bir özgeçmişi gönderildiğinde, iş açmaya bağlı bir kayıtta depolanır.  
  
3. Başvuranlar, zaman aşımı süresi dolana veya Contoso HR departmanından birisinin, işlemi durdurarak nakli kaldırmaya karar verdiği sürece devam edebilir.  
  
## <a name="projects-in-the-sample"></a>Örnekteki projeler  
 Aşağıdaki tabloda, örnek çözümdeki projeler gösterilmektedir.  
  
|Project|Açıklama|  
|-------------|-----------------|  
|ContosoHR|Veri sözleşmeleri, iş nesneleri ve depo sınıflarını içerir.|  
|Maingrequestservice|Işe alma Isteği Işlemi iş akışının tanımını içerir.<br /><br /> Bu proje, iş akışını (XAML dosyası) bir hizmet olarak barındırtığı bir konsol uygulaması olarak uygulanır.|  
|ResumeRequestService|Bir zaman aşımı süresi dolana kadar veya başka biri işlemin durdurulması gerektiğini belirten adaylardan özgeçmişler toplayan bir iş akışı hizmetidir.<br /><br /> Bu proje bildirim temelli bir iş akışı hizmeti (xamlx) olarak uygulanır.|  
|OrgService|Kuruluş bilgilerini (çalışanlar, pozisyonlar, PositionTypes ve departmanlar) kullanıma sunan bir hizmet. Bu hizmeti bir kurumsal kaynak planının (ERP) Şirket kuruluş modülü olarak düşünebilirsiniz.<br /><br /> Bu proje, bir Windows Communication Foundation (WCF) hizmetini kullanıma sunan bir konsol uygulaması olarak uygulanır.|  
|InboxService|Çalışanlar için eyleme dönüştürülebilir görevler içeren bir gelen kutusu.<br /><br /> Bu proje, bir WCF hizmetini kullanıma sunan bir konsol uygulaması olarak uygulanır.|  
|InternalClient|İşlemle etkileşimde bulunmak için bir Web uygulaması. Kullanıcılar, Maingprocess iş akışlarını başlatabilir, katılabilir ve görüntüleyebilir. Bu uygulamayı kullanarak, ResumeRequest süreçlerini de başlatabilir ve izleyebilirler.<br /><br /> Bu site contoso intraneti için dahili olarak uygulanır. Bu proje bir ASP.NET Web sitesi olarak uygulanır.|  
|Umuersweb sitesi|Contoso 'da açık konumları kullanıma sunan bir dış Web sitesi. Potansiyel aday, bu siteye gidebilir ve bir özgeçmişi gönderebilir.|  
  
## <a name="feature-summary"></a>Özellik Özeti  
 Aşağıdaki tabloda her bir özelliğin bu örnekte nasıl kullanıldığı açıklanmaktadır.  
  
|Özellik|Açıklama|Project|  
|-------------|-----------------|-------------|  
|Akış Çizelgesi|İş süreci bir akış çizelgesi olarak temsil edilir. Bu akış çizelgesi açıklaması, bir işletmenin bir beyaz tahtada çizileceği şekilde işlemi temsil eder.|Maingrequestservice|  
|İş akışı hizmetleri|İşlem tanımına sahip akış çizelgesi bir hizmette barındırılır (Bu örnekte hizmet bir konsol uygulamasında barındırılır).|Maingrequestservice|  
|Mesajlaşma etkinlikleri|Akış çizelgesi mesajlaşma etkinliklerini iki şekilde kullanır:<br /><br /> -Kullanıcıdan bilgi almak için (her onay adımında kararları ve ilgili bilgileri almak için).<br />-Hizmet başvuruları aracılığıyla kullanılan diğer mevcut hizmetlerle (InboxService ve OrgDataService) etkileşim kurmak için.|Maingrequestservice|  
|İçerik tabanlı bağıntı|Onay iletileri, işe alma isteğinin ID özelliği ile bağıntılı:<br /><br /> -Bir işlem başlatıldığında bağıntı tanıtıcısı, isteğin KIMLIĞIYLE başlatılır.<br />-Gelen onay iletileri kendi KIMLIĞIYLE bağıntılı (her onay iletisinin ilk parametresi isteğin KIMLIĞIDIR).|HiringRequestService/ResumeRequestService|  
|Özel Etkinlikler (bildirime dayalı ve kod tabanlı)|Bu örnekte birkaç özel etkinlik vardır:<br /><br /> -   `SaveActionTracking`: Bu etkinlik özel <xref:System.Activities.Tracking.TrackingRecord> (kullanarak <xref:System.Activities.NativeActivityContext.Track%2A>) yayar. Bu etkinlik, zorunlu kod genişletme <xref:System.Activities.NativeActivity>kullanılarak yazıldı.<br />-   `GetEmployeesByPositionTypes`: Bu etkinlik konum türü kimliklerinin bir listesini alır ve contoso 'da bu konuma sahip kişilerin listesini döndürür. Bu etkinlik bildirimli olarak yazıldı (etkinlik Tasarımcısı kullanılarak).<br />-   `SaveHiringRequestInfo`: Bu etkinlik bir `HiringRequest` (kullanarak `HiringRequestRepository.Save`) bilgilerini kaydeder. Bu etkinlik, zorunlu kod genişletme <xref:System.Activities.CodeActivity>kullanılarak yazıldı.|Maingrequestservice|  
|Sistem tarafından sağlanmış SQL Server kalıcılığı|Akış çizelgesi işlem tanımını barındıran örnek,sistemtarafındanbelirtilenSQLServerkalıcılığıkullanacakşekildeyapılandırılmıştır.<xref:System.ServiceModel.Activities.WorkflowServiceHost>|HiringRequestService/ResumeRequestService|  
|Özel İzleme|Örnek, a `HiringRequestProcess` geçmişini kaydeden bir özel izleme katılımcısı içerir (Bu, ne zaman yapıldığını, kim tarafından ve ne zaman yapıldığını kaydeder). Kaynak kodu, Maingrequestservice Izleme klasöründedir.|Maingrequestservice|  
|ETW Izleme|Sistem tarafından belirtilen ETW Izleme, Maingrequestservice hizmetindeki App. config dosyasında yapılandırılır.|Maingrequestservice|  
|Etkinliklerin kompozisyonu|İşlem tanımı, öğesinin <xref:System.Activities.Activity>serbest birleşimini kullanır. Akış çizelgesi, aynı anda diğer etkinlikleri (vb.) içeren birkaç sıra ve paralel etkinlikler içerir.|Maingrequestservice|  
|Paralel etkinlikler|-   <xref:System.Activities.Statements.ParallelForEach%601>, GM ve HR yöneticilerinin gelen kutusuna paralel olarak (iki HR yöneticilerinin onay adımını bekliyor) kaydolmak için kullanılır.<br />-   <xref:System.Activities.Statements.Parallel>Tamamlanan ve reddedilen adımlarda bazı temizleme görevleri yapmak için kullanılır|Maingrequestservice|  
|Model Iptali|Akış çizelgesi, <xref:System.Activities.Statements.CancellationScope> iptal davranışı oluşturmak için kullanır (Bu durumda bazı temizleme yapar.)|Maingrequestservice|  
|Müşteri kalıcılığı Katılımcısı|`HiringRequestPersistenceParticipant`bir iş akışı değişkenindeki verileri Contoso HR veritabanında depolanan bir tabloya kaydeder.|Maingrequestservice|  
|İş Akışı Hizmetleri|`ResumeRequestService`, iş akışı hizmetleri kullanılarak uygulanır. İş akışı tanımı ve hizmet bilgileri ResumeRequestService. xamlx içinde yer alır. Hizmet, kalıcılığı ve izlemeyi kullanacak şekilde yapılandırıldı.|ResumeRequestService|  
|Dayanıklı zamanlayıcılar|`ResumeRequestService`, bir Iş naklinin süresini tanımlamak için dayanıklı zamanlayıcılar kullanır (bir zaman aşımı süresi dolarsa, Iş nakli kapatılır).|ResumeRequestService|  
|İşlemler|<xref:System.Activities.Statements.TransactionScope>, birkaç etkinliğin yürütülmesi içindeki verilerin tutarlılığını sağlamak için kullanılır (yeni bir özgeçmişi alındığında).|ResumeRequestService|  
|İşlemler|Özel Kalıcılık Katılımcısı (`HiringRequestPersistenceParticipant`) ve özel izleme katılımcısı (`HistoryFileTrackingParticipant`) aynı işlemi kullanır.|Maingrequestservice|  
|ASP.net [!INCLUDE[wf1](../../../../includes/wf1-md.md)] uygulamalarında kullanma.|İş akışlarına iki ASP.NET uygulamasından erişilir.|InternalClient/Umuersweb sitesi|  
  
## <a name="data-storage"></a>Veri depolama  
 Veriler adlı `ContosoHR` bir SQL Server veritabanında depolanır (Bu veritabanını oluşturmak için komut dosyası `DbSetup` klasöründe bulunur). İş akışı örnekleri, adlı `InstanceStore` bir SQL Server veritabanında depolanır (örnek deposu oluşturmaya yönelik betikler [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] dağıtımın bir parçasıdır).  
  
 Her iki veritabanı de Visual Studio için bir Geliştirici Komut İstemi Setup. cmd betiği çalıştırılarak oluşturulur.  
  
## <a name="running-the-sample"></a>Örnek çalıştırma  
  
#### <a name="to-create-the-databases"></a>Veritabanlarını oluşturmak için  
  
1. Visual Studio için bir Geliştirici Komut İstemi açın.  
  
2. Örnek klasöre gidin.  
  
3. Setup. cmd ' i çalıştırın.  
  
4. İki veritabanının `ContosoHR` `InstanceStore` SQL Express 'te oluşturulduğunu doğrulayın.  
  
#### <a name="to-set-up-the-solution-for-execution"></a>Çözümü yürütmeye ayarlamak için  
  
1. Visual Studio'yu yönetici olarak çalıştırın. Maingrequest. sln öğesini açın.  
  
2. **Çözüm Gezgini** ' de çözüme sağ tıklayın ve **Özellikler**' i seçin.  
  
3. **Birden çok başlangıç projesi** seçeneğini belirleyin ve ersan **Web sitesini**, **InternalClient**, **HiringRequestService**ve **ResumeRequestService** ' i **Başlangıç**olarak ayarlayın. **ContosoHR**, **InboxService**ve **OrgService** ' i None olarak bırakın.  
  
4. CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun. Yapılandırmanın başarılı olduğunu doğrulayın.  
  
#### <a name="to-run-the-solution"></a>Çözümü çalıştırmak için  
  
1. Çözüm oluşturulduktan sonra, hata ayıklamadan çalıştırmak için CTRL + F5 tuşlarına basın. Tüm hizmetlerin başlatıldığını doğrulayın.  
  
2. Çözümdeki **InternalClient** öğesine sağ tıklayın ve ardından **Tarayıcıda görüntüle**' yi seçin. Varsayılan sayfası `InternalClient` görüntülenir. Hizmetlerin çalıştığından emin olun ve bağlantıya tıklayın.  
  
3. **HiringRequest** modülü görüntülenir. Burada ayrıntılı senaryoyu izleyebilirsiniz.  
  
4. Tamamlandıktan sonra, ' yi `ResumeRequest`başlatabilirsiniz. `HiringRequest` Burada ayrıntılı senaryoyu izleyebilirsiniz.  
  
5. `ResumeRequest` Gönderildiğinde, genel web sitesinde (contoso gelişme Web sitesi) kullanılabilir. Iş gönderme Işlemini görmek için (ve konum için geçerlidir), kariyer web sitesine gidin.  
  
6. Çözümdeki **gelişme Web sitesini** sağ tıklatın ve **Tarayıcıda görüntüle**' yi seçin.  
  
7. Çözümdeki **InternalClient** öğesine `InternalClient` sağ tıklayıp **Tarayıcıda görüntüle**' yi seçerek öğesine geri gidin.  
  
8. Gelen kutusu üst menüsündeki **Iş nakilleri** bağlantısına tıklayarak **jobnakiller** bölümüne gidin. Burada ayrıntılı senaryoyu izleyebilirsiniz.  
  
## <a name="scenarios"></a>Senaryolar  
  
### <a name="hiring-request"></a>İşe Alım isteği  
  
1. Michael Alexander (yazılım mühendisi), en az 3 yıllık deneyim içeren Mühendislik bölümünde test (SDET) içinde bir yazılım mühendisi sağlamak için yeni bir konum istemek istiyor C#.  
  
2. Oluşturulduktan sonra, istek Michael 'nin gelen kutusunda görünür (isteği görmüyorsanız **Yenile** ' ye tıklayın) kemal 'in Yöneticisi olan Peter Brehm onayını bekliyor.  
  
3. Peter, Michael 'ın isteğine göre hareket etmek istiyor. Konumun 3 yılı yerine 5 yıl boyunca C# deneyim verdiğini düşünüyor. bu nedenle açıklamalarını gözden geçirilmek üzere geri gönderir.  
  
4. Michael, gelen kutusunda yöneticisinden bir ileti görüyor ve işlem yapmak istiyor. Michael, konum isteği geçmişini görüyor ve Peter ile kabul eder. Michael, açıklamayı 5 yıllık C# deneyim gerektirecek şekilde değiştirir ve değişikliği kabul eder.  
  
5. Peter, Michael 'in değiştirilmiş isteği üzerinde davranır ve bunu kabul eder. İsteğin şimdi mühendislik, Tsvi Reiter müdürü tarafından onaylanması gerekir.  
  
6. Tsvı Reiter isteği hızlandırmak istiyor, bu nedenle isteğin acil olduğunu ve kabul ettiğini söylemek için bir açıklama koyar.  
  
7. İsteğin şimdi iki HR Yöneticisi veya CEO tarafından onaylanması gerekebilir. CEO, Brian Richard Goldstein, Tsvi tarafından acil istek görür. Bunu kabul ederek istek üzerinde davranır ve bu sayede onay iki HR Yöneticisi tarafından atlanarak yapılır.  
  
8. İstek, Michael 'ın gelen kutusundan kaldırılır ve bir SDET işe alma işlemi artık başlamış olur.  
  
### <a name="start-resume-request"></a>Yeniden başlatma Isteği  
  
1. Şimdi, iş konumu kişilerin uygulayabileceği bir dış Web sitesine gönderilmesini bekliyor ( **Iş nakilleri** bağlantısına tıklamasını istediğinizi görebilirsiniz). Şu anda iş konumu, iş konumunun sonuçlandırmasından ve deftere naklinden sorumlu bir ık temsilcisiyle birlikte çalışıyor.  
  
2. HR, 60 dakikalık bir zaman aşımı ayarlayarak ( **düzenleme** bağlantısına tıklayarak) bu iş konumunu düzenlemek istiyor (gerçek hayatta bu, gün veya hafta olabilir). Zaman aşımı, iş konumunun, belirtilen saate göre dış Web sitesinden alınmasını sağlar.  
  
3. Düzenlenmiş iş konumunu kaydettikten sonra, bu işlem **alma devam** ediyor sekmesinde görünür (yeni iş konumunu görmek için Web sayfasını yenileyin).  
  
### <a name="collecting-resumes"></a>Özgeçmişler toplanıyor  
  
1. İş konumu dış Web sitesinde görünmelidir. İş için uygulama ile ilgilenen bir kişi olarak, bu konum için uygulayabilir ve özgeçmişinizi gönderebilirsiniz.  
  
2. Iş nakilleri listesi hizmetine geri giderseniz, şimdiye kadar toplanmış "özgeçmişleri görüntüleyebilirsiniz".  
  
3. HR Ayrıca, devam eden (örneğin, doğru aday tanımlandıktan sonra) geri özgeçmişler toplamayı durdurabilir.  
  
## <a name="troubleshooting"></a>Sorun giderme  
  
1. Visual Studio 'Yu yönetici ayrıcalıklarıyla çalıştırıyor olduğunuzdan emin olun.  
  
2. Çözüm derlemezse, aşağıdakileri doğrulayın:  
  
    - Başvurusu `ContosoHR` `InternalClient` veya projelerinde`CareersWebSite` yok.  
  
3. Çözüm yürütülemezse, aşağıdakileri doğrulayın:  
  
    1. Tüm hizmetler çalışıyor.  
  
    2. Hizmet başvuruları güncelleştirildi.  
  
        1. App_WebReferences klasörünü açın  
  
        2. **Contoso** öğesine sağ tıklayın ve **Web/hizmet başvurularını Güncelleştir**' i seçin.  
  
        3. Visual Studio 'da CTRL + SHIFT + B tuşlarına basarak çözümü yeniden oluşturun.  
  
## <a name="uninstalling"></a>Kaldırıyor  
  
1. DbSetup klasöründe bulunan Cleanup. bat dosyasını çalıştırarak SQL Server örnek deposunu silin.  
  
2. Sabit sürücünüzün kaynak kodunu silin.
