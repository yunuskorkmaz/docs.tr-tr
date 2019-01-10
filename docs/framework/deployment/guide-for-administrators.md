---
title: Yöneticiler için .NET Framework Dağıtım Kılavuzu
ms.date: 04/10/2018
helpviewer_keywords:
- administrator's guide, deploying .NET Framework
- deployment [.NET Framework], administrator's guide
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a94f9c650927aee0f120ee3c0b1199b6c977ef0e
ms.sourcegitcommit: 0888d7b24f475c346a3f444de8d83ec1ca7cd234
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2018
ms.locfileid: "53776740"
---
# <a name="net-framework-deployment-guide-for-administrators"></a>Yöneticiler için .NET Framework Dağıtım Kılavuzu
Bu makalede bir sistem yöneticisi nasıl dağıtacağınız açıklanmıştır [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ve Microsoft System Center Configuration Manager'ı kullanarak bir ağ üzerindeki sistem gereksinimlerini. Bu makalede tüm istemci bilgisayarların .NET Framework için gerekli olan minimum sistem gereksinimlerini karşıladığı varsayılmıştır. Yüklemeye yönelik yazılım ve donanım gereksinimleri listesi için [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], bkz: [sistem gereksinimleri](../../../docs/framework/get-started/system-requirements.md).  
  
> [!NOTE]
>  Ancak bunlarla sınırlı olmaksızın bu dokümanda bahsedilen yazılımlar [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], System Center Configuration Manager ve Active Directory olduğunuz her lisans ve koşullarına tabidir. Bu yönergeler, bu tür lisans koşullarını ve koşulları gözden geçirilmiş yazılımların sahipleri tarafından kabul edildiği varsaymaktadır. Bu yönergeler, bu tür lisans anlaşmalarının koşullarından feragat etmiş sayılmaz.  
>   
>  .NET Framework desteği hakkında daha fazla bilgi için bkz: [Microsoft .NET Framework desteği yaşam döngüsü ilkesi](https://go.microsoft.com/fwlink/?LinkId=196607) Microsoft Support Web sitesi.  
  
 Bu konu aşağıdaki bölümleri içermektedir:  
  
 [Dağıtım işlemi](#the_deployment_process)  
 [.NET Framework'ü dağıtma](#deploying_in_a_test_environment)  
 [Koleksiyon oluşturma](#creating_a_collection)  
 [Bir paket ve program oluşturma](#creating_a_package)  
 [Bir dağıtım noktası seçin](#select_dist_point)  
 [Paketi dağıtma](#deploying_package)  
[Kaynaklar](#resources)  
[Sorun giderme](#troubleshooting)  
  
<a name="the_deployment_process"></a>   
## <a name="the-deployment-process"></a>Dağıtım işlemi  
 Yerinde destek altyapısı varsa, ağ üzerinden .NET Framework dağıtılabilir paketini bilgisayarlara dağıtmak için Sistem Merkezi 2012 Yapılandırma Yöneticisi'ni kullanın. Altyapının oluşturulması, beş birincil alanın oluşturulmasını ve tanımlanmasını gerektirir: koleksiyonlar, yazılım için bir paket ve program, dağıtım noktaları ve dağıtımlar.  
  
-   **Koleksiyonları** kullanıcılar, kullanıcı grupları veya bilgisayarlar, .NET Framework dağıtıldığı gibi Configuration Manager kaynaklarına gruplarıdır. Daha fazla bilgi için [System Center Configuration Manager'da koleksiyonlara giriş](https://docs.microsoft.com/sccm/core/clients/manage/collections/introduction-to-collections) Yapılandırma Yöneticisi belge kitaplığı.  
  
-   **Paketler ve programlar** genellikle bir istemci bilgisayara yüklenecek yazılım uygulamalarını gösterir, ancak bunlar tek tek dosyaları, güncelleştirmeleri veya hatta ayrı ayrı komutları da içerebilir. Daha fazla bilgi için [paketler ve programlar System Center Configuration Manager'da](https://docs.microsoft.com/sccm/apps/deploy-use/packages-and-programs) Yapılandırma Yöneticisi belge kitaplığı.  
  
-   **Dağıtım noktaları** Configuration Manager sitesi, yazılımın istemci bilgisayarlarda çalışması gereken dosyaları depolayan sistem rolleridir. Yapılandırma Yöneticisi istemcisi bir yazılım dağıtımı alıp işlediğinde, yazılımla ilişkili içeriği indirmek ve kurulum işlemini başlatmak için bir dağıtım noktasıyla temasa geçer. Daha fazla bilgi için [Configuration Manager'da içerik yönetimi için temel kavramlar](https://docs.microsoft.com/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management) Yapılandırma Yöneticisi belge kitaplığı.  
  
-   **Dağıtımları** belirtilen hedef koleksiyonun ilgili üyelerinden yazılım paketini yüklemek için isteyin. 
  
> [!IMPORTANT]
>  Bu konudaki yordamlar, bir paket ve program oluşturmak ve dağıtmak için normal ayarları içerir ve tüm olası ayarları kapsamayabilir. Diğer Configuration Manager dağıtım seçenekleri için bkz. [Yapılandırma Yöneticisi belge kitaplığı](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg682041%28v=technet.10%29).  
  
<a name="deploying_in_a_test_environment"></a>   
## <a name="deploying-the-net-framework"></a>.NET Framework'ü dağıtma  
 System Center 2012 Configuration Manager sessiz yüklemesini dağıtmak için kullanabileceğiniz [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], burada kullanıcılar yükleme işlemiyle etkileşimde bulunmazlar. Aşağıdaki adımları uygulayın:  
  
1.  [Koleksiyon oluşturma](#creating_a_collection).  
  
2.  [Bir paket ve program için .NET Framework yeniden dağıtılabilir oluşturma](#creating_a_package).  
  
3.  [Dağıtım noktası seçme](#select_dist_point).  
  
4.  [Paketi dağıtma](#deploying_package).  
  
<a name="creating_a_collection"></a>   
### <a name="create-a-collection"></a>Koleksiyon oluşturma  
 Bu adımda, paket ve program dağıtacağınız bilgisayarları seçersiniz ve onları bir aygıt koleksiyonunda gruplandırırsınız. Yapılandırma Yöneticisi'nde bir koleksiyon oluşturmak için, doğrudan üyelik kurallarını (koleksiyon üyelerini el ile belirtirsiniz) veya sorgu kurallarını (koleksiyon üyelerini sizin belirttiğiniz ölçütlere göre Yapılandırma Yöneticisi belirler) kullanabilirsiniz. Sorgular ve doğrudan kurallar dahil, üyelik kuralları hakkında daha fazla bilgi için bkz. [System Center Configuration Manager'da koleksiyonlara giriş](https://docs.microsoft.com/sccm/core/clients/manage/collections/introduction-to-collections) Yapılandırma Yöneticisi belge kitaplığı.  
  
 Bir koleksiyon oluşturmak için:  
  
1.  Configuration Manager Konsolu'nda **varlıklar ve Uyumluluk**.  
  
2.  İçinde **varlıklar ve Uyumluluk** çalışma alanı seçin **cihaz koleksiyonları**.  
  
3.  Üzerinde **giriş** sekmesinde **Oluştur** Grup öğesini **cihaz Koleksiyonu Oluştur**.  
  
4.  Üzerinde **genel** sayfasının **cihaz koleksiyonu Oluşturma Sihirbazı**, koleksiyon için bir ad girin.  
  
5.  Seçin **Gözat** bir sınırlama koleksiyonu belirtmek için.  
  
6.  Üzerinde **Üyelik kuralları** sayfasında **Kuralı Ekle**ve ardından **doğrudan kural** açmak için **doğrudan üyelik kuralı oluşturma Sihirbazı**. Seçin **sonraki**.  
  
7.  Üzerinde **kaynak Ara** sayfasında **kaynak sınıfı** listesinde **sistem kaynağı**. İçinde **öznitelik adı** listesinde **adı**. İçinde **değer** alanına `%`ve ardından **sonraki**.  
  
8.  Üzerinde **kaynak** sayfasında, .NET Framework'ü dağıtmak istediğiniz her bilgisayar için onay kutusunu seçin. Seçin **sonraki**ve ardından Sihirbazı tamamlayın.  
  
9. Üzerinde **Üyelik kuralları** sayfasının **cihaz koleksiyonu Oluşturma Sihirbazı**, seçin **sonraki**ve ardından Sihirbazı tamamlayın.  
  
<a name="creating_a_package"></a>   
### <a name="create-a-package-and-program-for-the-net-framework-redistributable-package"></a>.NET Framework yeniden dağıtılabilir paketi için paket ve program oluşturma  
 Aşağıdaki adımlar, .NET Framework yeniden dağıtılabilir için el ile bir paket oluşturur. Paket, .NET Framework'ün kurulumu için belirtilen parametreleri ve paketin hedef bilgisayarlara nereden dağıtılacağını içerir.  
  
 Bir paket oluşturmak için:  
  
1.  Configuration Manager Konsolu'nda **yazılım Kitaplığı**.  
  
2.  İçinde **yazılım Kitaplığı** çalışma alanında, genişletme **Uygulama Yönetimi**ve ardından **paketleri**.  
  
3.  Üzerinde **giriş** sekmesinde **Oluştur** Grup öğesini **Paket Oluştur**.  
  
4.  Üzerinde **paket** sayfasının **paket ve Program Sihirbazı Oluştur**, aşağıdaki bilgileri girin:  
  
    -   Adı: `.NET Framework 4.5`  
  
    -   Üretici: `Microsoft`  
  
    -   Dil. `English (US)`  
  
5.  Seçin **bu paket kaynak dosyaları içerir**ve ardından **Gözat** yerel seçin veya ağ .NET Framework yükleme dosyalarını içeren klasörü. Klasör seçtiğinizde, seçin **Tamam**ve ardından **sonraki**.  
  
6.  Üzerinde **Program türü** sayfasında sihirbazın seçin **standart Program**ve ardından **sonraki**.  
  
7.  Üzerinde **Program** sayfasının **paket ve Program Sihirbazı Oluştur**, aşağıdaki bilgileri girin:  
  
    1.  **Adı:** `.NET Framework 4.5`  
  
    2.  **Komut satırı:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (komut satırı seçenekleri açıklanmıştır tabloda Bu adımlardan sonra)  
  
    3.  **Çalıştırın:** Seçin **gizli**.  
  
    4.  **Program çalışabilir:** Program, kullanıcının oturum açmış bağımsız olarak çalışabileceğini belirten seçeneği seçin.  
  
8.  Üzerinde **gereksinimleri** sayfasında **sonraki** varsayılan değerleri kabul edin ve ardından Sihirbazı tamamlayın.  
  
 Aşağıdaki tablo, 7. adımda belirtilen komut satırı seçeneklerini açıklar.  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/q**|Sessiz modu ayarlar. Hiçbir kullanıcı girişine gerek yoktur ve hiçbir çıktı gösterilmez.|  
|**/ norestart**|Kurulum programının otomatik olarak yeniden başlatılmasını önler. Bu seçeneği kullanırsanız, Yapılandırma Yöneticisi'nin bilgisayarı yeniden başlatmayı üstlenmesi gerekir.|  
|**/chainingpackage** *PackageName*|Zincirlemeyi yapan paketin adını belirtir. Bu bilgiler kaydolup kişilerin diğer yükleme oturum bilgileriyle birlikte raporlanır [Microsoft Müşteri Deneyimini Geliştirme Programı (CEIP)](https://go.microsoft.com/fwlink/p/?LinkId=248244). Paket adı boşluk içeriyorsa, sınırlayıcı olarak çift tırnak işareti kullanın. Örneğin: **/chainingpackage "Chaining Product"**.|  
  
 Bu adımlar, .NET Framework 4.5 adlı bir paket oluşturur. Program, .NET Framework 4.5'in sessiz bir kurulumunu dağıtır. Sessiz yüklemede, kullanıcılar yükleme işlemiyle etkileşimde bulunmazlar ve zincirleme uygulama döndürülen kodu yakalamak ve yeniden işlemek zorundadır; bkz: [yükleme paketinden ilerleme bilgisi alma](https://go.microsoft.com/fwlink/?LinkId=179606).  
 
<a name="select_dist_point"></a>   
### <a name="select-a-distribution-point"></a>Dağıtım noktası seçme  
 Paketi ve programı bir sunucudan istemci bilgisayarlara dağıtmak için, önce bir site sistemini dağıtım noktası olarak belirlemeniz ve sonra paketi dağıtım noktasına dağıtmanız gerekir.  
  
 Bir önceki bölümde oluşturulan .NET Framework 4.5 paketi için bir dağıtım noktası seçmek üzere aşağıdaki adımları kullanın:  
  
1.  Configuration Manager Konsolu'nda **yazılım Kitaplığı**.  
  
2.  İçinde **yazılım Kitaplığı** çalışma alanında, genişletme **Uygulama Yönetimi**ve ardından **paketleri**.  
  
3.  Paketler listesinden, paketi seçin **.NET Framework 4.5** , önceki bölümde oluşturduğunuz.  
  
4.  Üzerinde **giriş** sekmesinde **dağıtım** Grup öğesini **içeriği Dağıt**.  
  
5.  Üzerinde **genel** sekmesinde **içerik Dağıtma Sihirbazı**, seçin **sonraki**.  
  
6.  Üzerinde **içerik hedefi** sayfasında sihirbazın seçin **Ekle**ve ardından **dağıtım noktası**.  
  
7.  İçinde **dağıtım noktaları Ekle** iletişim kutusunda, paket ve programı barındıracak ve ardından dağıtım noktaları seçin **Tamam**.  
  
8.  Sihirbazı tamamlayın.  
  
 Paket şimdi, .NET Framework 4.5'i sessizce dağıtmak gereksinim duyduğunuz tüm bilgileri içerir. Paket ve programı dağıtmadan önce dağıtım noktasında yüklendiğini doğrulayın; "İçeriği izleme" bölümüne bakın [System Center Configuration Manager ile dağıttığınız içeriği izleme](https://docs.microsoft.com/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed) Yapılandırma Yöneticisi belge kitaplığı.  
  
<a name="deploying_package"></a>   
### <a name="deploy-the-package"></a>Paketi dağıtma  
 .NET Framework 4.5 paketini ve programını dağıtmak için:  
  
1.  Configuration Manager Konsolu'nda **yazılım Kitaplığı**.  
  
2.  İçinde **yazılım Kitaplığı** çalışma alanında, genişletme **Uygulama Yönetimi**ve ardından **paketleri**.  
  
3.  Paketler listesinden, oluşturduğunuz adlı paketi seçin **.NET Framework 4.5**.  
  
4.  Üzerinde **giriş** sekmesinde **dağıtım** Grup öğesini **Dağıt**.  
  
5.  Üzerinde **genel** sayfasının **yazılım dağıtma Sihirbazı**, seçin **Gözat**ve ardından daha önce oluşturduğunuz koleksiyonu seçin. Seçin **sonraki**.  
  
6.  Üzerinde **içerik** sayfasında sihirbazın yazılımı dağıtmak istediğiniz noktanın görüntülendiğini ve ardından doğrulamak **sonraki**.  
  
7.  Üzerinde **dağıtım ayarları** Sayfası Sihirbazı'nın onaylayın **eylem** ayarlanır **yükleme**, ve **amaçlı** içinayarlanmış**Gerekli**. Bu, yazılım paketinin hedeflenen bilgisayarlarda zorunlu bir yükleme olmasını sağlar. Seçin **sonraki**.  
  
8.  Üzerinde **zamanlama** sayfasında sihirbazın yüklenmesi için .NET Framework'ü istediğinizde belirtin. Seçebileceğiniz **yeni** bir yükleme zamanı atamak ya da yazılım üzerinde veya kapattığında veya mümkün olan en kısa sürede kullanıcı oturum açtığında isteyin. Seçin **sonraki**.  
  
9. Üzerinde **kullanıcı deneyimi** sayfasında, varsayılan değerleri seçin kullanın ve **sonraki**.  
  
> [!WARNING]
> Üretim ortamınızın, dağıtım çizelgesi için farklı seçimler olmasını gerektiren ilkeleri olabilir. Bu seçenekler hakkında daha fazla bilgi için bkz: [reklam adı özellikleri: Zamanla sekmesinde](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb694016%28v=technet.10%29).
  
10. Üzerinde **dağıtım noktaları** sayfasında, varsayılan değerleri seçin kullanın ve **sonraki**.  
  
11. Sihirbazı tamamlayın. Dağıtım ilerlemesini izleyebilirsiniz **dağıtımları** düğümünün **izleme** çalışma.  
  
 Şimdi paket hedeflenen koleksiyona dağıtılır ve .NET Framework 4.5'in sessiz yüklemesi başlar. .NET Framework 4.5 yükleme hatası kodları hakkında daha fazla bilgi için bkz: [dönüş kodları](#return_codes) bu konunun ilerleyen bölümlerinde.  
  
<a name="resources"></a>   
## <a name="resources"></a>Kaynaklar  
 Dağıtımı test etmek için altyapısı hakkında daha fazla bilgi için [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] yeniden dağıtılabilir paket, aşağıdaki kaynaklara bakın.  
  
 **Active Directory, DNS, DHCP:**  
  
-   [Active Directory etki alanı Hizmetleri](/windows/desktop/ad/active-directory-domain-services)  
  
-   [Etki alanı adı sistemi (DNS)](/windows-server/networking/dns/dns-top)  
  
-   [Dinamik konak Yapılandırma Protokolü (DHCP)](/windows-server/networking/technologies/dhcp/dhcp-top)  
  
 **SQL Server 2008:**  
  
-   [SQL Server 2008 (SQL Server Video) yükleme](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/dd299415%28v=sql.100%29)  
  
-   [Veritabanı yöneticileri için SQL Server 2008 Güvenliğe genel bakış](https://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)  
  
 **System Center 2012 Configuration Manager (yönetim noktası, dağıtım noktası):**  
  
-   [System Center 2012 Configuration Manager için Site Yönetimi](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg681983%28v=technet.10%29)  
  
-   [Yapılandırma Yöneticisi tek Site planlama ve dağıtım](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb680961%28v=technet.10%29)  
  
 **Windows bilgisayarlar için System Center 2012 Configuration Manager istemcisi:**  
  
-   [System Center 2012 Configuration Manager için İstemci Dağıtma](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg699391%28v=technet.10%29)  
  
<a name="troubleshooting"></a>   
## <a name="troubleshooting"></a>Sorun giderme  
  
### <a name="log-file-locations"></a>Günlük dosyası konumları  
 Aşağıdaki günlük dosyalarını, .NET Framework Kurulum sırasında üretilir:  
  
 .NET framework %Temp%\Microsoft *sürüm*\*.txt  
 .NET framework %Temp%\Microsoft *sürüm*\*.html  
  
 Burada *sürüm* .NET Framework 4.5 veya 4.7.2 gibi güvenilirliğinden sürümüdür.  
 
 İçin hangi günlük dosyaları yazılır kullanarak dizini belirtebilirsiniz `/log` komut satırı seçeneği, .NET Framework yükleme komutu. Daha fazla bilgi için [geliştiriciler için .NET Framework Dağıtım Kılavuzu](deployment-guide-for-developers.md#command-line-options). 
 
 Kullanabileceğiniz [günlük toplama aracı](https://www.microsoft.com/download/details.aspx?id=12493) .NET Framework günlük dosyaları toplamak ve dosyaların boyutunu azaltır bir sıkıştırılmış kabin (.cab) dosyası oluşturun.  
  
<a name="return_codes"></a>   
### <a name="return-codes"></a>Dönüş kodları  
 Aşağıdaki tabloda en yaygın dönüş kodlarını listelemektedir [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] yeniden dağıtılabilir yükleme programındaki. Dönüş kodları yükleyicinin tüm sürümleri için aynıdır.  
  
 Ayrıntılı bilgilerin bağlantılarını görmek için bir sonraki bölüm [indirme hatası kodları](#additional_error_codes).  
  
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
  
-   [Arka Plan Akıllı Aktarım Hizmeti (BITS) hata kodları](/windows/desktop/Bits/bits-return-values)  
  
-   [URL adı hata kodları](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775145%28v=vs.85%29)  
  
-   [WinHttp hata kodları](/windows/desktop/WinHttp/error-messages)  
  
 Diğer hata kodları:  
  
-   [Windows Installer hata kodları](/windows/desktop/msi/error-codes)  
  
-   [Windows Update Aracısı sonuç kodları](/security-updates/WindowsUpdateServices/18127055)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
- [Geliştiriciler için Dağıtım Kılavuzu](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
- [Sistem Gereksinimleri](../../../docs/framework/get-started/system-requirements.md)
