---
title: Yöneticiler için .NET Framework Dağıtım Kılavuzu
ms.date: 04/10/2018
helpviewer_keywords:
- administrator's guide, deploying .NET Framework
- deployment [.NET Framework], administrator's guide
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9b4c2d4205e87d8be21f82eaf74b17e316d9057e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394338"
---
# <a name="net-framework-deployment-guide-for-administrators"></a>Yöneticiler için .NET Framework Dağıtım Kılavuzu
Bu adım adım makalede bir sistem yöneticisi nasıl dağıtabileceğini açıklar [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ve Microsoft System Center Configuration Manager kullanarak ağ üzerinden sistem bağımlılıklarını. Bu makalede tüm istemci bilgisayarların .NET Framework için gerekli olan minimum sistem gereksinimlerini karşıladığı varsayılmıştır. Yüklemek için yazılım ve donanım gereksinimlerinin listesi için [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], bkz: [sistem gereksinimleri](../../../docs/framework/get-started/system-requirements.md).  
  
> [!NOTE]
>  Bunlarla sınırlı olmamak kaydıyla dahil olmak üzere bu belgede başvurulan yazılım [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], System Center Configuration Manager ve Active Directory olan her lisans hüküm ve koşullara tabidir. Bu yönergeler, bu tür lisans koşullarını ve koşulları gözden geçirilmiş yazılımların sahipleri tarafından kabul edildiği varsaymaktadır. Bu yönergeler, bu tür lisans anlaşmalarının koşullarından feragat etmiş sayılmaz.  
>   
>  .NET Framework desteği hakkında daha fazla bilgi için bkz: [Microsoft .NET Framework destek yaşam döngüsü ilkesi](http://go.microsoft.com/fwlink/?LinkId=196607) Microsoft Support Web sitesinde.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
 [Dağıtım işlemi](#the_deployment_process)  
 [.NET Framework'ü dağıtma](#deploying_in_a_test_environment)  
 [Bir koleksiyon oluşturma](#creating_a_collection)  
 [Bir paket ve program oluşturma](#creating_a_package)  
 [Bir dağıtım noktası seçin](#select_dist_point)  
 [Paketi dağıtma](#deploying_package)  
[Kaynaklar](#resources)  
[Sorun giderme](#troubleshooting)  
  
<a name="the_deployment_process"></a>   
## <a name="the-deployment-process"></a>Dağıtım işlemi  
 Yerinde destek altyapısı varsa, ağ üzerinden .NET Framework dağıtılabilir paketini bilgisayarlara dağıtmak için Sistem Merkezi 2012 Yapılandırma Yöneticisi'ni kullanın. Altyapının oluşturulması, beş birincil alanın oluşturulmasını ve tanımlanmasını gerektirir: koleksiyonlar, yazılım için bir paket ve program, dağıtım noktaları ve dağıtımlar.  
  
-   **Koleksiyonları** kullanıcılar, kullanıcı grupları veya bilgisayarlar, .NET Framework dağıtıldığı gibi Configuration Manager kaynakları gruplarıdır. Daha fazla bilgi için bkz: [Configuration Manager'da koleksiyonlar](http://technet.microsoft.com/library/gg682169.aspx) Configuration Manager Belge Kitaplığı'nda.  
  
-   **Paketler ve programlar** normalde bir istemci bilgisayarda yüklü yazılım uygulamaları temsil eder, ancak ayrıca tek dosyalar, güncelleştirmeleri veya hatta tek tek komutlar içerirler. Daha fazla bilgi için bkz: [paketleri ve programları Configuration Manager'da](http://technet.microsoft.com/library/gg699369.aspx) Configuration Manager Belge Kitaplığı'nda.  
  
-   **Dağıtım noktaları** Configuration Manager site yazılımın istemci bilgisayarlarında çalışması gereken dosyaları depolayan sistemi rolleridir. Yapılandırma Yöneticisi istemcisi bir yazılım dağıtımı alıp işlediğinde, yazılımla ilişkili içeriği indirmek ve kurulum işlemini başlatmak için bir dağıtım noktasıyla temasa geçer. Daha fazla bilgi için bkz: [Configuration Manager'da içerik yönetimi giriş](http://technet.microsoft.com/library/gg682083.aspx) Configuration Manager Belge Kitaplığı'nda.  
  
-   **Dağıtımları** yazılım paketi yüklemek için geçerli belirtilen hedef koleksiyonun üyeleri isteyin. Daha fazla bilgi için bkz: [Configuration Manager'da uygulamaları dağıtmak için nasıl](http://technet.microsoft.com/library/gg682082.aspx) Configuration Manager Belge Kitaplığı'nda.  
  
> [!IMPORTANT]
>  Bu konudaki yordamlar, bir paket ve program oluşturmak ve dağıtmak için normal ayarları içerir ve tüm olası ayarları kapsamayabilir. Diğer Configuration Manager dağıtım seçenekleri için bkz: [Configuration Manager belge kitaplığı](http://technet.microsoft.com/library/gg682041.aspx).  
  
<a name="deploying_in_a_test_environment"></a>   
## <a name="deploying-the-net-framework"></a>.NET Framework'ü dağıtma  
 System Center 2012 Configuration Manager bir sessiz yüklemesi dağıtmak için kullanabileceğiniz [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], burada kullanıcıların yükleme işlemi ile etkileşim değil. Aşağıdaki adımları uygulayın:  
  
1.  [Bir koleksiyon oluşturma](#creating_a_collection).  
  
2.  [Bir paket ve program için .NET Framework yeniden dağıtılabilir oluşturmak](#creating_a_package).  
  
3.  [Bir dağıtım noktası seçin](#select_dist_point).  
  
4.  [Paketi dağıtmak](#deploying_package).  
  
<a name="creating_a_collection"></a>   
### <a name="create-a-collection"></a>Koleksiyon oluşturma  
 Bu adımda, paket ve program dağıtacağınız bilgisayarları seçersiniz ve onları bir aygıt koleksiyonunda gruplandırırsınız. Yapılandırma Yöneticisi'nde bir koleksiyon oluşturmak için, doğrudan üyelik kurallarını (koleksiyon üyelerini el ile belirtirsiniz) veya sorgu kurallarını (koleksiyon üyelerini sizin belirttiğiniz ölçütlere göre Yapılandırma Yöneticisi belirler) kullanabilirsiniz. Sorgular ve doğrudan kuralları da dahil olmak üzere, üyelik kuralları hakkında daha fazla bilgi için bkz: [Configuration Manager'da koleksiyonlara giriş](http://technet.microsoft.com/library/gg682177.aspx) Configuration Manager Belge Kitaplığı'nda.  
  
 Bir koleksiyon oluşturmak için:  
  
1.  Configuration Manager konsolunda seçin **varlıklar ve uyum**.  
  
2.  İçinde **varlıklar ve Uyumluluk** çalışma alanı seçin **cihaz koleksiyonları**.  
  
3.  Üzerinde **giriş** sekmesinde **oluşturma** grubunda, seçin **cihaz Koleksiyonu Oluştur**.  
  
4.  Üzerinde **genel** sayfasında **cihaz koleksiyonu Oluşturma Sihirbazı**, koleksiyon için bir ad girin.  
  
5.  Seçin **Gözat** bir sınırlama koleksiyonu belirtmek için.  
  
6.  Üzerinde **Üyelik kuralları** sayfasında, **Kuralı Ekle**ve ardından **doğrudan kural** açmak için **doğrudan üyelik kuralı oluşturma Sihirbazı**. Seçin **sonraki**.  
  
7.  Üzerinde **kaynaklar için arama** sayfasında **kaynak sınıfı** listesinde, seçin **sistem kaynağı**. İçinde **öznitelik adı** listesinde, seçin **adı**. İçinde **değeri** alanına, `%`ve ardından **sonraki**.  
  
8.  Üzerinde **Kaynak Seç** sayfasında, .NET Framework dağıtmak istediğiniz her bilgisayar için onay kutusunu seçin. Seçin **sonraki**ve ardından Sihirbazı tamamlayın.  
  
9. Üzerinde **Üyelik kuralları** sayfasında **cihaz koleksiyonu Oluşturma Sihirbazı**, seçin **sonraki**ve ardından Sihirbazı tamamlayın.  
  
 Koleksiyonlar hakkında daha fazla bilgi için bkz: [Configuration Manager'da koleksiyonlar](http://technet.microsoft.com/library/bb693730.aspx) Configuration Manager Belge Kitaplığı'nda.  
  
<a name="creating_a_package"></a>   
### <a name="create-a-package-and-program-for-the-net-framework-redistributable-package"></a>.NET Framework yeniden dağıtılabilir paketi için paket ve program oluşturma  
 Aşağıdaki adımlar, .NET Framework yeniden dağıtılabilir için el ile bir paket oluşturur. Paket, .NET Framework'ün kurulumu için belirtilen parametreleri ve paketin hedef bilgisayarlara nereden dağıtılacağını içerir.  
  
 Bir paket oluşturmak için:  
  
1.  Configuration Manager konsolunda seçin **yazılım Kitaplığı**...  
  
2.  İçinde **yazılım Kitaplığı** çalışma alanında, genişletin **Uygulama Yönetimi**ve ardından **paketleri**.  
  
3.  Üzerinde **giriş** sekmesinde **oluşturma** grubunda, seçin **Paket Oluştur**.  
  
4.  Üzerinde **paket** sayfasında **paket ve Program Sihirbazı Oluştur**, aşağıdaki bilgileri girin:  
  
    -   Ad: `.NET Framework 4.5`  
  
    -   Üretici: `Microsoft`  
  
    -   Dil. `English (US)`  
  
5.  Seçin **bu paket kaynak dosyalarını içeren**ve ardından **Gözat** yerel seçin veya ağ .NET Framework yükleme dosyalarını içeren klasörü. Klasörü seçildiğinde seçin **Tamam**ve ardından **sonraki**.  
  
6.  Üzerinde **Program türü** sayfasında sihirbazın seçin **standart Program**ve ardından **sonraki**.  
  
7.  Üzerinde **Program** sayfasında **paket ve Program Sihirbazı Oluştur**, aşağıdaki bilgileri girin:  
  
    1.  **Ad:** `.NET Framework 4.5`  
  
    2.  **Komut satırı:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (komut satırı seçenekleri açıklanmıştır tabloda sonra aşağıdaki adımları)  
  
    3.  **Çalıştır:** seçin **gizli**.  
  
    4.  **Program çalışabilir:** program kullanıcının oturum açmış bağımsız olarak çalışabilir belirten seçeneği belirleyin.  
  
8.  Üzerinde **gereksinimleri** sayfasında, **sonraki** varsayılan değerleri kabul edin ve ardından Sihirbazı tamamlayın.  
  
 Aşağıdaki tablo, 7. adımda belirtilen komut satırı seçeneklerini açıklar.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/q**|Sessiz modu ayarlar. Hiçbir kullanıcı girişine gerek yoktur ve hiçbir çıktı gösterilmez.|  
|**/ norestart**|Kurulum programının otomatik olarak yeniden başlatılmasını önler. Bu seçeneği kullanırsanız, Yapılandırma Yöneticisi'nin bilgisayarı yeniden başlatmayı üstlenmesi gerekir.|  
|**/chainingpackage** *PackageName*|Zincirlemeyi yapan paketin adını belirtir. Bu bilgiler kaydolup olanlar için diğer yükleme oturum bilgileri ile bildirilen [Microsoft Müşteri Deneyimi Geliştirme Programı (CEIP)](http://go.microsoft.com/fwlink/p/?LinkId=248244). Paket adı boşluk içeriyorsa, çift tırnak işaretleri sınırlayıcı olarak alın; Örneğin: **/chainingpackage "Ürün zincirleme"**.|  
  
 Bu adımlar, .NET Framework 4.5 adlı bir paket oluşturur. Program, .NET Framework 4.5'in sessiz bir kurulumunu dağıtır. Sessiz yükleme, kullanıcıların yükleme işlemi ile etkileşim değil ve dönüş kodu yakalamak ve yeniden işlemek zincirleme uygulama vardır; bkz: [ilerleme durumu bilgileri alınırken bir yükleme paketi](http://go.microsoft.com/fwlink/?LinkId=179606).  
 
<a name="select_dist_point"></a>   
### <a name="select-a-distribution-point"></a>Dağıtım noktası seçme  
 Paketi ve programı bir sunucudan istemci bilgisayarlara dağıtmak için, önce bir site sistemini dağıtım noktası olarak belirlemeniz ve sonra paketi dağıtım noktasına dağıtmanız gerekir.  
  
 Bir önceki bölümde oluşturulan .NET Framework 4.5 paketi için bir dağıtım noktası seçmek üzere aşağıdaki adımları kullanın:  
  
1.  Configuration Manager konsolunda seçin **yazılım Kitaplığı**.  
  
2.  İçinde **yazılım Kitaplığı** çalışma alanında, genişletin **Uygulama Yönetimi**ve ardından **paketleri**.  
  
3.  Paket paketler listesinden seçin **.NET Framework 4.5** önceki bölümde oluşturduğunuz.  
  
4.  Üzerinde **giriş** sekmesinde **dağıtım** grubunda, seçin **içeriği Dağıt**.  
  
5.  Üzerinde **genel** sekmesinde **içerik Dağıtma Sihirbazı**, seçin **sonraki**.  
  
6.  Üzerinde **içerik hedef** sayfasında sihirbazın seçin **Ekle**ve ardından **dağıtım noktası**.  
  
7.  İçinde **Ekle dağıtım noktaları** iletişim kutusunda, paket ve program barındırmak ve ardından seçin ve dağıtım noktalarının seçin **Tamam**.  
  
8.  Sihirbazı tamamlayın.  
  
 Paket şimdi, .NET Framework 4.5'i sessizce dağıtmak gereksinim duyduğunuz tüm bilgileri içerir. Paket ve program dağıtmadan önce dağıtım noktasına yüklendiğini doğrulayın; "İzleme içerik" bölümüne bakın [Configuration Manager'da içerik yönetimine yönelik işlemler ve Bakım](http://technet.microsoft.com/library/gg712694.aspx#BKMK_MonitorContent) Configuration Manager Belge Kitaplığı'nda.  
  
<a name="deploying_package"></a>   
### <a name="deploy-the-package"></a>Paketi dağıtma  
 .NET Framework 4.5 paketini ve programını dağıtmak için:  
  
1.  Configuration Manager konsolunda seçin **yazılım Kitaplığı**.  
  
2.  İçinde **yazılım Kitaplığı** çalışma alanında, genişletin **Uygulama Yönetimi**ve ardından **paketleri**.  
  
3.  Paketlerin adlandırılmış oluşturduğunuz paket listesinden **.NET Framework 4.5**.  
  
4.  Üzerinde **giriş** sekmesinde **dağıtım** grubunda, seçin **dağıtma**.  
  
5.  Üzerinde **genel** sayfasında **yazılım dağıtma Sihirbazı**, seçin **Gözat**ve ardından daha önce oluşturduğunuz koleksiyonu seçin. Seçin **sonraki**.  
  
6.  Üzerinde **içerik** sayfasında sihirbazın yazılım dağıtmak istediğiniz noktasını görüntülenir ve ardından doğrulamak **sonraki**.  
  
7.  Üzerinde **dağıtım ayarlarını** Sayfa Sihirbazı'nın onaylayın **eylem** ayarlanır **yükleme**, ve **amacı** içinayarlanmış**Gerekli**. Bu, yazılım paketinin hedeflenen bilgisayarlarda zorunlu bir yükleme olmasını sağlar. Seçin **sonraki**.  
  
8.  Üzerinde **zamanlama** Sayfa Sihirbazı'nın yüklenmesi için .NET Framework'ü istediğinizde belirtin. Seçebileceğiniz **yeni** yükleme süresini atama veya kullanıcı açık veya kapalı veya mümkün olan en kısa sürede açtığında yüklemek için yazılım isteyin. Seçin **sonraki**.  
  
9. Üzerinde **kullanıcı deneyimini** sihirbazın varsayılan değerlerini ve seçin sayfasında **sonraki**.  
  
    > [!WARNING]
    >  Üretim ortamınızın, dağıtım çizelgesi için farklı seçimler olmasını gerektiren ilkeleri olabilir. Bu seçenekler hakkında daha fazla bilgi için bkz: [tanıtım adı özellikleri: zamanlama sekmesi](http://technet.microsoft.com/library/bb694016.aspx) TechNet Kitaplığı'nda.  
  
10. Üzerinde **dağıtım noktaları** sihirbazın varsayılan değerlerini ve seçin sayfasında **sonraki**.  
  
11. Sihirbazı tamamlayın. Dağıtımının ilerlemesini izleyebilirsiniz **dağıtımları** düğümünün **izleme** çalışma.  
  
 Şimdi paket hedeflenen koleksiyona dağıtılır ve .NET Framework 4.5'in sessiz yüklemesi başlar. .NET Framework 4.5 yüklemesi hata kodları hakkında daha fazla bilgi için bkz: [dönüş kodları](#return_codes) bu konunun ilerleyen bölümlerinde.  
  
<a name="resources"></a>   
## <a name="resources"></a>Kaynaklar  
 Dağıtımı test etmek için altyapı hakkında daha fazla bilgi için [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] yeniden dağıtılabilir paketi, aşağıdaki kaynaklara bakın.  
  
 **Active Directory, DNS, DHCP:**  
  
-   [Windows Server 2008 için Active Directory etki alanı Hizmetleri](http://technet.microsoft.com/library/dd378891.aspx)  
  
-   [DNS sunucusu](http://technet.microsoft.com/library/cc732997.aspx)  
  
-   [DHCP sunucusu](http://technet.microsoft.com/library/cc896553.aspx)  
  
 **SQL Server 2008:**  
  
-   [SQL Server 2008 (SQL Server Video) yükleme](http://technet.microsoft.com/library/dd299415.aspx)  
  
-   [Veritabanı yöneticileri için SQL Server 2008 güvenlik genel bakış](http://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)  
  
 **System Center 2012 Configuration Manager (yönetim noktası, dağıtım noktası):**  
  
-   [System Center 2012 Configuration Manager için Site Yönetimi](http://technet.microsoft.com/library/gg681983.aspx)  
  
-   [Configuration Manager tek sitesi planlama ve dağıtım](http://technet.microsoft.com/library/bb680961.aspx)  
  
 **System Center 2012 Configuration Manager istemcisi Windows bilgisayarları için:**  
  
-   [System Center 2012 Configuration Manager için istemci dağıtma](http://technet.microsoft.com/library/gg699391.aspx)  
  
<a name="troubleshooting"></a>   
## <a name="troubleshooting"></a>Sorun giderme  
  
### <a name="log-file-locations"></a>Günlük dosyası konumları  
 Aşağıdaki günlük dosyalarına .NET Framework Kurulum sırasında oluşturulur:  
  
 .NET framework %Temp%\Microsoft *sürüm*\*.txt  
 .NET framework %Temp%\Microsoft *sürüm*\*.html  
  
 Burada *sürüm* 4.5 veya 4.7.2 gibi yüklüyorsanız .NET Framework sürümü.  
 
 Hangi günlük dosyaları yazılır kullanarak dizini de belirleyebilirsiniz `/log` komut satırı seçeneği, .NET Framework yükleme komutu. Daha fazla bilgi için bkz: [geliştiriciler için .NET Framework Dağıtım Kılavuzu](deployment-guide-for-developers.md#command-line-options). 
 
 Kullanabileceğiniz [günlük koleksiyonu aracı](https://www.microsoft.com/download/details.aspx?id=12493) .NET Framework günlük dosyaları toplamak için ve dosyaların boyutu azaltan Sıkıştırılmış dolap (.cab) dosya oluşturulamadı.  
  
<a name="return_codes"></a>   
### <a name="return-codes"></a>Dönüş kodları  
 Aşağıdaki tabloda en yaygın dönüş kodları [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] yeniden dağıtılabilir yükleme programı. Dönüş kodları yükleyicinin tüm sürümleri için aynıdır.  
  
 Ayrıntılı bilgi için bağlantılar görmek için bir sonraki bölüm [karşıdan hata kodları](#additional_error_codes).  
  
|Dönüş kodu|Açıklama|  
|-----------------|-----------------|  
|0|Yükleme başarıyla tamamlandı.|  
|1602|Kullanıcı yüklemeyi iptal etti.|  
|1603|Yükleme sırasında ciddi bir hata oluştu.|  
|1641|Yüklemenin tamamlanması için yeniden başlatma gereklidir. Bu ileti başarılı olduğunu gösterir.|  
|3010|Yüklemenin tamamlanması için yeniden başlatma gereklidir. Bu ileti başarılı olduğunu gösterir.|  
|5100|Kullanıcının bilgisayarı sistem gereksinimlerini karşılamıyor.|  
  
<a name="additional_error_codes"></a>   
### <a name="download-error-codes"></a>İndirme hatası kodları  
  
-   [Arka Plan Akıllı Aktarım Hizmeti (BITS) hata kodları](http://msdn.microsoft.com/library/aa362823.aspx)  
  
-   [URL ad hata kodları](http://msdn.microsoft.com/library/ms775145.aspx)  
  
-   [WinHttp hata kodları](http://msdn.microsoft.com/library/aa383770.aspx)  
  
 Diğer hata kodları:  
  
-   [Windows Installer hata kodları](http://msdn.microsoft.com/library/aa368542.aspx)  
  
-   [Windows Update Aracısı sonuç kodları](http://technet.microsoft.com/library/cc720442.aspx)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Geliştiriciler için Dağıtım Kılavuzu](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 [Sistem Gereksinimleri](../../../docs/framework/get-started/system-requirements.md)
