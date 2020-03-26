---
title: İşe Alma İşlemi
ms.date: 03/30/2017
ms.assetid: d5fcacbb-c884-4b37-a5d6-02b1b8eec7b4
ms.openlocfilehash: ade72422d29d170e9c80f602f151ce765a1a00f7
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291696"
---
# <a name="hiring-process"></a>İşe Alma İşlemi
Bu örnek, ileti etkinliklerini ve iş akışı hizmetleri olarak barındırılan iki iş akışını kullanarak bir iş sürecinin nasıl uygulanacağını gösterir. Bu iş akışları Contoso, Inc. adlı kurgusal bir şirketin BT altyapısının bir parçasıdır.  
  
 İş `HiringRequest` akışı işlemi (a <xref:System.Activities.Statements.Flowchart>olarak uygulanır) kuruluştaki birkaç yöneticiden yetki ister. Bu amaca ulaşmak için, iş akışı kuruluştaki diğer varolan hizmetleri (bizim durumumuzda, bir gelen kutusu hizmeti ve düz Windows Communication Foundation (WCF) hizmetleri olarak uygulanan bir kuruluş veri hizmeti) kullanır.  
  
 İş `ResumeRequest` akışı (bir <xref:System.Activities.Statements.Sequence>olarak uygulanır) Contoso'nun dış kariyer Web sitesinde bir iş ilanı yayınlar ve özgeçmiş edinimi yönetir. Bir iş ilanı, dış Web sitesinde belirli bir süre için (zaman aşımı süresi dolana kadar) veya Contoso'dan bir çalışan onu kaldırmaya karar verene kadar kullanılabilir.  
  
 Bu örnek aşağıdaki özellikleri [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]göstermektedir:  
  
- <xref:System.Activities.Statements.Flowchart>ve <xref:System.Activities.Statements.Sequence> iş süreçlerini modellemek için iş akışları.  
  
- İş Akışı Hizmetleri.  
  
- Mesajlaşma Etkinlikleri.  
  
- İçerik tabanlı korelasyon.  
  
- Özel etkinlikler (bildirimsel ve kod tabanlı).  
  
- Sistem sağlanan SQL sunucu kalıcılığı.  
  
- Özel <xref:System.Activities.Persistence.PersistenceParticipant>.  
  
- Özel izleme.  
  
- Windows (ETW) İzleme için Olay İzleme.  
  
- Faaliyetlerin bileşimi.  
  
- <xref:System.Activities.Statements.Parallel>Faaliyetleri.  
  
- <xref:System.Activities.Statements.CancellationScope>Etkinlik.  
  
- Dayanıklı zamanlayıcılar (aktivite).<xref:System.Activities.Statements.Delay>  
  
- Hareket.  
  
- Aynı çözümde birden fazla iş akışı.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\HiringProcess`  
  
## <a name="description-of-the-process"></a>Sürecin Açıklaması  
 Contoso, Inc. departmanlarının her birinde sayım üzerinde yakın kontrole sahip olmak istiyor. Bu nedenle, herhangi bir çalışan yeni bir işe alma süreci başlatmak istiyor, onlar işe alma aslında olabilir önce bir işe alma isteği süreci onayı geçmesi gerekir. Bu işleme işe alma süreci isteği (HiringRequestService projesinde tanımlanan) denir ve aşağıdaki adımlardan oluşur:  
  
1. Bir çalışan (talepçi) işe alma işlemi isteğini başlatır.  
  
2. İstekliyöneticinin isteği onaylaması gerekir:  
  
    1. Yönetici isteği reddedebilir.  
  
    2. Yönetici, ek bilgi için isteği talep edene iade edebilir:  
  
        1. İstekçi, isteği gözden geçirir ve yöneticiye geri gönderir.  
  
    3. Yönetici onaylayabilir.  
  
3. İsteksahibinin yöneticisi onayladıktan sonra, bölüm sahibinin isteği onaylaması gerekir:  
  
    1. Bölüm sahibi reddedebilir.  
  
    2. Bölüm sahibi onaylayabilir.  
  
4. Bölüm sahibi onayladıktan sonra, işlem 2 İk yöneticisinin veya CEO'nun onayını gerektirir:  
  
    1. İşlem kabul edilen veya reddedilen duruma geçiş yapabilir.  
  
    2. İşlem Kabul edilirse, iş akışının `ResumeRequest` yeni bir örneği`ResumeRequest` başlatılır (bir hizmet başvurusu ile HiringRequest.csproj'a bağlanır.)  
  
 Yöneticiler yeni bir çalışanın işe alınmasını onayladıktan sonra, İk uygun adayı bulmak zorundadır. Bu işlem, ResumeRequestService.csproj'da tanımlanan ikinci iş akışı tarafından`ResumeRequest`gerçekleştirilir. Bu iş akışı, Contoso'nun dış Kariyer Web sitesine kariyer fırsatı olan bir iş ilanı gönderme işlemini tanımlar, başvuru sahiplerinden özgeçmiş alır ve iş ilanının durumunu izler. Pozisyonlar belirli bir süre için (bir süre sona erene kadar) veya Contoso'dan bir çalışan onu kaldırmaya karar verene kadar kullanılabilir. İş `ResumeRequest` akışı aşağıdaki adımlardan oluşur:  
  
1. Contoso'dan bir çalışan, pozisyon ve zaman çıkış süresi yle ilgili bilgileri tipler. Çalışan bu bilgileri yazdıktan sonra, pozisyon Kariyer Web sitesinde deftere nakledilir.  
  
2. Bilgiler yayınlandıktan sonra, ilgili taraflar özgeçmişlerini sunabilirler. Özgeçmiş gönderildiğinde, iş açmayla bağlantılı bir kayıtta depolanır.  
  
3. Başvuru sahipleri, zaman aşımı süresi dolana veya Contoso İk departmanından biri süreci durdurarak ilanı kaldırmaya karar verene kadar özgeçmiş sunabilir.  
  
## <a name="projects-in-the-sample"></a>Örnekteki projeler  
 Aşağıdaki tablo, örnek çözümdeki projeleri gösterir.  
  
|Project|Açıklama|  
|-------------|-----------------|  
|ContosoHR|Veri sözleşmeleri, iş nesneleri ve depo sınıfları içerir.|  
|İşe AlmaRequestService|İşe Alma İstek Süreci iş akışının tanımını içerir.<br /><br /> Bu proje, iş akışını (xaml dosyası) bir hizmet olarak kendi kendine barındıran bir konsol uygulaması olarak uygulanır.|  
|ResumeRequestService|Bir zaman aşımı süresi dolana veya birisi işlemin durdurulması gerektiğine karar verene kadar adaylardan özgeçmiş toplayan bir iş akışı hizmeti.<br /><br /> Bu proje bir bildirimsel iş akışı hizmeti (xamlx) olarak uygulanmaktadır.|  
|OrgService|Kuruluş bilgilerini (Çalışanlar, Pozisyonlar, Pozisyon Türleri ve Bölümler) ortaya çıkaran bir hizmet. Bu hizmeti, Kurumsal Kaynak Planı'nın (ERP) Şirket Organizasyonu modülü olarak düşünebilirsiniz.<br /><br /> Bu proje, bir Windows Communication Foundation (WCF) hizmetini ortaya çıkaran bir konsol uygulaması olarak uygulanmaktadır.|  
|Gelen KutusuServisi|Çalışanlar için eyleme geçirilebilir görevler içeren bir gelen kutusu.<br /><br /> Bu proje, bir WCF hizmetini ortaya çıkaran bir konsol uygulaması olarak uygulanır.|  
|Dahili Müşteri|İşlemle etkileşim kurmak için bir Web uygulaması. Kullanıcılar HiringProcess iş akışlarını başlatabilir, katılabilir ve görüntüleyebilir. Bu uygulamayı kullanarak ResumeRequest işlemlerini başlatabilir ve izleyebilirler.<br /><br /> Bu site Contoso intranet iç olmak için uygulanmaktadır. Bu proje bir ASP.NET Web sitesi olarak uygulanmaktadır.|  
|KariyerWebSitesi|Contoso'daki açık pozisyonları ortaya çıkaran harici bir Web sitesi. Herhangi bir potansiyel aday bu siteye gidebilir ve özgeçmiş gönderebilir.|  
  
## <a name="feature-summary"></a>Özellik özeti  
 Aşağıdaki tabloda, her özelliğin bu örnekte nasıl kullanıldığı açıklanmaktadır.  
  
|Özellik|Açıklama|Project|  
|-------------|-----------------|-------------|  
|Akış Çizelgesi|İş süreci bir akış şeması olarak temsil edilir. Bu akış şeması açıklaması, bir işletmenin onu beyaz tahtaya çizdiği şekilde süreci temsil eder.|İşe AlmaRequestService|  
|İş akışı hizmetleri|İşlem tanımına sahip Akış Şeması bir hizmette barındırılır (bu örnekte, hizmet bir konsol uygulamasında barındırılır).|İşe AlmaRequestService|  
|Mesajlaşma etkinlikleri|Akış şeması mesajlaşma etkinliklerini iki şekilde kullanır:<br /><br /> - Kullanıcıdan bilgi almak için (her onay adımında kararları ve ilgili bilgileri almak için).<br />- Mevcut diğer hizmetlerle etkileşimkurmak için (Hizmet referansları aracılığıyla kullanılan Gelen Kutusu Hizmeti ve OrgDataService).|İşe AlmaRequestService|  
|İçerik tabanlı korelasyon|Onay iletileri işe alma isteğinin kimlik özelliği yle ilişkilidir:<br /><br /> - Bir işlem başlatıldığında, korelasyon tutamacı isteğin kimliği ile başlatılır.<br />- Gelen onay iletileri kimlikleri üzerinde ilişkilidir (her onay iletisinin ilk parametresi isteğin kimliğidir).|HiringRequestService / ResumeRequestService|  
|Özel etkinlikler (bildirim ve kod tabanlı)|Bu örnekte birkaç özel etkinlik vardır:<br /><br /> -   `SaveActionTracking`: Bu etkinlik bir <xref:System.Activities.Tracking.TrackingRecord> özel <xref:System.Activities.NativeActivityContext.Track%2A>(kullanarak) yayır. Bu etkinlik, zorunlu kod genişletme <xref:System.Activities.NativeActivity>kullanılarak yazılmış.<br />-   `GetEmployeesByPositionTypes`: Bu etkinlik konum türü iT'lerin listesini alır ve Contoso'da bu konuma sahip kişilerin listesini döndürür. Bu etkinlik bildirimsel olarak (etkinlik tasarımcısı kullanılarak) yatılmıştır.<br />-   `SaveHiringRequestInfo`: Bu etkinlik bir `HiringRequest` (kullanarak) `HiringRequestRepository.Save`bilgilerini kaydeder. Bu etkinlik, zorunlu kod genişletme <xref:System.Activities.CodeActivity>kullanılarak yazılmış.|İşe AlmaRequestService|  
|Sistem sağlanan SQL Server Kalıcılığı|Flowchart işlem tanımını barındıran <xref:System.ServiceModel.Activities.WorkflowServiceHost> örnek, sistem tarafından sağlanan SQL Server kalıcılığını kullanacak şekilde yapılandırılır.|HiringRequestService / ResumeRequestService|  
|Özel İzleme|Örnek, bir eylemin geçmişini kaydeden özel bir `HiringRequestProcess` izleme katılımcısı içerir (bu, eylemin ne zaman yapıldığını, kim tarafından ve ne zaman yapıldığını kaydeder). Kaynak kodu HiringRequestService'in İzleme klasöründedir.|İşe AlmaRequestService|  
|ETW Takip|Sistem tarafından sağlanan ETW İzleme, HiringRequestService hizmetindeki App.config dosyasında yapılandırılır.|İşe AlmaRequestService|  
|Etkinliklerin Bileşimi|İşlem tanımı serbest bileşimi <xref:System.Activities.Activity>ni kullanır. Akış Şeması, aynı anda başka etkinlikler (vb.) içeren birkaç Sıra ve Paralel etkinlik içerir.|İşe AlmaRequestService|  
|Paralel Faaliyetler|-   <xref:System.Activities.Statements.ParallelForEach%601>paralel olarak CEO ve İk Yöneticilerinin Gelen Kutusuna kaydolmak için kullanılır (Iki İk Yöneticisinin Onay Adımını Beklerken).<br />-   <xref:System.Activities.Statements.Parallel>Tamamlanan ve Reddedilen adımlardaki bazı temizleme görevlerini yapmak için kullanılır|İşe AlmaRequestService|  
|Model İptali|Flowchart iptal <xref:System.Activities.Statements.CancellationScope> davranışı oluşturmak için kullanır (bu durumda bazı temizleme yapar.)|İşe AlmaRequestService|  
|Müşteri Kalıcılığı Katılımcısı|`HiringRequestPersistenceParticipant`verileri iş akışı değişkeninden Contoso İK veritabanında depolanan bir tabloya kaydeder.|İşe AlmaRequestService|  
|İş Akışı Hizmetleri|`ResumeRequestService`iş akışı hizmetleri kullanılarak uygulanır. İş akışı tanımı ve hizmet bilgileri ResumeRequestService.xamlx'ta bulunur. Hizmet kalıcılık ve izleme kullanmak üzere yapılandırılır.|ResumeRequestService|  
|Dayanıklı Zamanlayıcılar|`ResumeRequestService`Bir İş Gönderme süresini tanımlamak için dayanıklı zamanlayıcılar kullanır (bir zaman aşımı sona erdiğinde, İş Gönderme kapatılır).|ResumeRequestService|  
|İşlemler|<xref:System.Activities.Statements.TransactionScope>çeşitli etkinliklerin yürütülmesi içinde veri tutarlılığı sağlamak için kullanılır (yeni bir özgeçmiş aldığında).|ResumeRequestService|  
|İşlemler|Özel kalıcılık katılımcısı (`HiringRequestPersistenceParticipant`)`HistoryFileTrackingParticipant`ve özel izleme katılımcısı ( ) aynı hareketi kullanır.|İşe AlmaRequestService|  
|ASP.NET [!INCLUDE[wf1](../../../../includes/wf1-md.md)] uygulamalarda kullanma.|İş akışlarına iki ASP.NET uygulamadan erişilir.|InternalClient / CareersWebSite|  
  
## <a name="data-storage"></a>Veri Depolama  
 Veriler, (bu veritabanını oluşturmak `ContosoHR` için komut dosyası `DbSetup` klasöründe bulunur) adlı bir SQL Server veritabanında depolanır. İş akışı örnekleri, SQL Server veritabanında `InstanceStore` depolanır (örnek deposu oluşturmak için [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] komut dosyaları dağıtımın bir parçasıdır).  
  
 Her iki veritabanı da Visual Studio için Geliştirici Komut Komut Ustem'den Setup.cmd komut dosyası çalıştırılarak oluşturulur.  
  
## <a name="running-the-sample"></a>Örneği çalıştırma  
  
#### <a name="to-create-the-databases"></a>Veritabanlarını oluşturmak için  
  
1. Visual Studio için geliştirici komut istemini açın.  
  
2. Örnek klasörüne gidin.  
  
3. Setup.cmd çalıştırın.  
  
4. İki veritabanının `ContosoHR` ve `InstanceStore` SQL Express'te oluşturulduğunu doğrulayın.  
  
#### <a name="to-set-up-the-solution-for-execution"></a>Yürütme için çözüm ayarlamak için  
  
1. Visual Studio'yu yönetici olarak çalıştırın. Açık HiringRequest.sln.  
  
2. **Çözüm Gezgini'nde** çözüme sağ tıklayın ve **Özellikler'i**seçin.  
  
3. **Birden Fazla Başlangıç Projeleri** seçeneğini seçin ve **CareersWebSite,** **InternalClient,** **HiringRequestService**ve **ResumeRequestService'i** **başlatın.** **ContosoHR,** **InboxService**ve **OrgService'i** Yok olarak bırakın.  
  
4. CTRL+SHIFT+B tuşuna basarak çözümü oluşturun. Yapının başarılı olduğunu doğrulayın.  
  
#### <a name="to-run-the-solution"></a>Çözümü çalıştırmak için  
  
1. Çözüm yapıldıktan sonra hata ayıklamadan çalıştırmak için CTRL+F5 tuşuna basın. Tüm hizmetlerin başladığını doğrulayın.  
  
2. Çözümde **InternalClient'a** sağ tıklayın ve **ardından Tarayıcıda Görüntüle'yi**seçin. Varsayılan sayfa `InternalClient` görüntülenir. Hizmetlerin çalıştığını emin olun ve bağlantıyı tıklatın.  
  
3. **HiringRequest** modülü görüntülenir. Burada ayrıntılı senaryoyu takip edebilirsiniz.  
  
4. `HiringRequest` Tamamlandıktan sonra, `ResumeRequest`başlatabilirsiniz. Burada ayrıntılı senaryoyu takip edebilirsiniz.  
  
5. `ResumeRequest` Yayınlandığında, genel Web sitesinde (Contoso Careers Web Sitesi) kullanılabilir. İş Gönderme'yi (ve pozisyona başvurmak) görmek için Kariyer Web Sitesine gidin.  
  
6. Çözümde **CareersWebSite'ye** sağ tıklayın ve **Tarayıcıda Görüntüle'yi**seçin.  
  
7. Çözümde `InternalClient` **InternalClient'ı** sağ tıklayarak ve **Tarayıcıda Görünüm'i**seçerek geri gidin.  
  
8. Gelen kutusu üst menüsündeki İş **Defterleri** bağlantısını tıklayarak **İş Gönderileri** bölümüne gidin. Burada ayrıntılı senaryoyu takip edebilirsiniz.  
  
## <a name="scenarios"></a>Senaryolar  
  
### <a name="hiring-request"></a>İşe alma talebi  
  
1. Michael Alexander (Yazılım Mühendisi), Mühendislik bölümünde C#'da en az 3 yıllık deneyime sahip bir Yazılım Mühendisi (SDET) almak için yeni bir pozisyon talep etmek istiyor.  
  
2. Oluşturulduktan sonra, istek Michael'ın gelen kutusunda görünür (isteği görmüyorsanız **Yenile'yi** tıklatın) Michael'ın yöneticisi olan Peter Brehm'in onayını bekler.  
  
3. Peter, Michael'ın isteği üzerine harekete geçsin istiyor. Pozisyonun 3 yerine 5 yıllık C# deneyimi gerektirdiğini düşünüyor, bu yüzden yorumlarını gözden geçiriliyor.  
  
4. Michael gelen kutusunda menajerinden gelen bir mesaj görür ve harekete geçer. Michael pozisyon isteğinin geçmişini görür ve Peter ile aynı fikirdedir. Michael, açıklamayı 5 yıllık C# deneyimi gerektirecek şekilde değiştirir ve değişikliği kabul eder.  
  
5. Peter, Michael'ın değiştirilmiş isteğini yerine koyar ve kabul eder. Talep şimdi Mühendislik Direktörü Tsvi Reiter tarafından onaylanmalıdır.  
  
6. Tsvi Reiter isteği hızlandırmak istiyor, bu yüzden bir yorum isteği acil olduğunu söylemek koyar ve kabul eder.  
  
7. İstek şimdi iki İk yöneticileri veya CEO tarafından onaylanması gerekir. CEO, Brian Richard Goldstein, Tsvi tarafından acil istek görür. İsteğe göre hareket ederek kabul eder ve böylece iki İk yöneticisinin onayını atlar.  
  
8. İstek Michael'ın gelen kutusundan kaldırılır ve bir SDET işe alma işlemi şimdi başladı.  
  
### <a name="start-resume-request"></a>Özgeçmiş İsteğini Başlat  
  
1. Şimdi, iş pozisyonu insanların başvurabileceği harici bir Web sitesine gönderilmeyi bekliyor **(İş Ilanları** bağlantısını tıklatarak görebilirsiniz). Şu anda, iş pozisyonu iş konumunu sonuçlandırıp göndermekten sorumlu bir İk temsilcisiyle birlikte oturuyor.  
  
2. İk bu iş konumunu **(Düzenleme** bağlantısını tıklayarak) 60 dakika (gerçek hayatta, bu gün veya hafta olabilir) bir zaman-out ayarlayarak düzenlemek istiyor. Zaman ayarı, iş konumunun belirtilen zamana göre dış Web sitesinden alınmasını sağlar.  
  
3. Düzenlenen iş konumunu kurtardıktan sonra, **Gelen Devamlar** sekmesinde görünür (yeni iş konumunu görmek için Web sayfasını yenileyin).  
  
### <a name="collecting-resumes"></a>Özgeçmiş Toplama  
  
1. İş konumu dış Web sitesinde görünmelidir. İş başvurusunda bulunmak isteyen biri olarak, bu pozisyona başvurabilir ve özgeçmişinizi gönderebilirsiniz.  
  
2. İş Ilanları Listesi hizmetine geri dönerseniz, şimdiye kadar toplanan "özgeçmişleri görüntüleyebilirsiniz".  
  
3. İk ayrıca özgeçmiş toplamayı da durdurabilir (örneğin, doğru aday belirlendikten sonra).  
  
## <a name="troubleshooting"></a>Sorun giderme  
  
1. Visual Studio'yı yönetici ayrıcalıklarıyla çalıştırdığınızdan emin olun.  
  
2. Çözüm oluşturamazsa, aşağıdakileri doğrulayın:  
  
    - Başvuru `ContosoHR` `InternalClient` veya `CareersWebSite` projelerde eksik değildir.  
  
3. Çözüm yürütülmezse, aşağıdakileri doğrulayın:  
  
    1. Tüm hizmetler çalışıyor.  
  
    2. Hizmet başvuruları güncelleştirildi.  
  
        1. App_WebReferences klasörünü açma  
  
        2. **Contoso'ya** sağ tıklayın ve **Web/Hizmet Başvurularını Güncelleştir'i**seçin.  
  
        3. Visual Studio'da CTRL+SHIFT+B tuşuna basarak çözümü yeniden oluşturun.  
  
## <a name="uninstalling"></a>Kaldırma  
  
1. DbSetup klasöründe bulunan Cleanup.bat'ı çalıştırarak SQL Server örnek deposunu silin.  
  
2. Sabit diskinizin kaynak kodunu silin.
