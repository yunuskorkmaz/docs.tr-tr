---
title: Yöneticiler için .NET Framework Dağıtım Kılavuzu
ms.date: 04/10/2018
helpviewer_keywords:
- administrator's guide, deploying .NET Framework
- deployment [.NET Framework], administrator's guide
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
ms.openlocfilehash: be15ce0b0bed37da6fe400e98bfdd118c48f7ba0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75716533"
---
# <a name="net-framework-deployment-guide-for-administrators"></a>Yöneticiler için .NET Framework Dağıtım Kılavuzu

Bu adım adım makale, bir sistem yöneticisinin Microsoft Endpoint Configuration Manager'ı kullanarak .NET Framework 4.5 ve sistem bağımlılıklarını ağ da nasıl dağıtabileceğini açıklar. Bu makalede tüm istemci bilgisayarların .NET Framework için gerekli olan minimum sistem gereksinimlerini karşıladığı varsayılmıştır. .NET Framework 4.5'i yüklemek için yazılım ve donanım gereksinimlerinin listesi için [Bkz. Sistem Gereksinimleri.](../get-started/system-requirements.md)

> [!NOTE]
> .NET Framework 4.5, Configuration Manager ve Active Directory dahil ancak bunlarla sınırlı olmamak üzere bu belgede başvurulan yazılımın her biri lisans hüküm ve koşullarına tabidir. Bu yönergeler, bu tür lisans koşullarını ve koşulları gözden geçirilmiş yazılımların sahipleri tarafından kabul edildiği varsaymaktadır. Bu yönergeler, bu tür lisans anlaşmalarının koşullarından feragat etmiş sayılmaz.
>
> .NET Framework desteği hakkında daha fazla bilgi için Microsoft Destek web [sitesindeki .NET Framework resmi destek politikasına](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework) bakın.

Bu konu aşağıdaki bölümleri içermektedir:

- [Dağıtım işlemi](#the_deployment_process)
- [.NET Framework'ü dağıtma](#deploying_in_a_test_environment)
- [Koleksiyon oluşturma](#creating_a_collection)
- [Paket ve program oluşturma](#creating_a_package)
- [Dağıtım noktası seçme](#select_dist_point)
- [Paketi dağıtma](#deploying_package)
- [Kaynaklar](#resources)
- [Sorun giderme](#troubleshooting)

<a name="the_deployment_process"></a>

## <a name="the-deployment-process"></a>Dağıtım işlemi

Destekleyici altyapıyı yerleştirdiğinizde, .NET Framework yeniden dağıtılabilir paketini ağdaki bilgisayarlara dağıtmak için Configuration Manager'ı kullanırsınız. Altyapının oluşturulması, beş birincil alanın oluşturulmasını ve tanımlanmasını gerektirir: koleksiyonlar, yazılım için bir paket ve program, dağıtım noktaları ve dağıtımlar.

- **Koleksiyonlar,** .NET Framework'ün dağıtıldığı kullanıcılar, kullanıcı grupları veya bilgisayarlar gibi Configuration Manager kaynaklarıgruplarıdır. Daha fazla bilgi için Configuration Manager dokümantasyon kitaplığında [Configuration Manager'daki koleksiyonlara giriş'e](https://docs.microsoft.com/configmgr/core/clients/manage/collections/introduction-to-collections) bakın.

- **Paketler ve programlar** genellikle istemci bilgisayara yüklenecek yazılım uygulamalarını temsil eder, ancak tek tek dosyalar, güncelleştirmeler ve hatta tek tek komutlar da içerebilir. Daha fazla bilgi için Configuration Manager belgeleri kitaplığında [Configuration Manager'daki Paketler ve programlara](https://docs.microsoft.com/configmgr/apps/deploy-use/packages-and-programs) bakın.

- **Dağıtım noktaları,** yazılımın istemci bilgisayarlarda çalışması için gerekli dosyaları depolayan Configuration Manager site sistem rolleridir. Yapılandırma Yöneticisi istemcisi bir yazılım dağıtımı alıp işlediğinde, yazılımla ilişkili içeriği indirmek ve kurulum işlemini başlatmak için bir dağıtım noktasıyla temasa geçer. Daha fazla bilgi için Configuration Manager dokümantasyon [kitaplığında Configuration Manager'da içerik yönetimi için temel kavramlara](https://docs.microsoft.com/configmgr/core/plan-design/hierarchy/fundamental-concepts-for-content-management) bakın.

- **Dağıtımlar,** yazılım paketini yüklemeleri için belirtilen hedef koleksiyonun ilgili üyelerine talimat verir.

> [!IMPORTANT]
> Bu konudaki yordamlar, bir paket ve program oluşturmak ve dağıtmak için normal ayarları içerir ve tüm olası ayarları kapsamayabilir. Diğer Configuration Manager dağıtım seçenekleri için [Configuration Manager Documentation Library'ye](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg682041%28v=technet.10%29)bakın.

<a name="deploying_in_a_test_environment"></a>

## <a name="deploying-the-net-framework"></a>.NET Framework'ü dağıtma

.NET Framework 4.5'in sessiz bir yüklemesini dağıtmak için Configuration Manager'ı kullanabilirsiniz, burada kullanıcılar yükleme işlemiyle etkileşimde değildir. Şu adımları uygulayın:

1. [Bir koleksiyon oluşturun.](#creating_a_collection)

2. [.NET Framework yeniden dağıtılabilir için bir paket ve program oluşturun.](#creating_a_package)

3. [Bir dağıtım noktası seçin.](#select_dist_point)

4. [Paketi dağıtın.](#deploying_package)

<a name="creating_a_collection"></a>

### <a name="create-a-collection"></a>Koleksiyon oluşturma

Bu adımda, paket ve program dağıtacağınız bilgisayarları seçersiniz ve onları bir aygıt koleksiyonunda gruplandırırsınız. Yapılandırma Yöneticisi'nde bir koleksiyon oluşturmak için, doğrudan üyelik kurallarını (koleksiyon üyelerini el ile belirtirsiniz) veya sorgu kurallarını (koleksiyon üyelerini sizin belirttiğiniz ölçütlere göre Yapılandırma Yöneticisi belirler) kullanabilirsiniz. Sorgular ve doğrudan kurallar da dahil olmak üzere üyelik kuralları hakkında daha fazla bilgi için Configuration Manager Documentation [Library'deki Configuration Manager'daki koleksiyonlara giriş](https://docs.microsoft.com/configmgr/core/clients/manage/collections/introduction-to-collections) bilgisine bakın.

Bir koleksiyon oluşturmak için:

1. Configuration Manager konsolunda **Varlıklar ve Uyumluluk'u**seçin.

2. Varlıklar **ve Uyumluluk** çalışma alanında **Aygıt Koleksiyonları'nı**seçin.

3. **Oluştur** **grubundaKi Giriş** sekmesinde **Aygıt Koleksiyonu Oluştur'u**seçin.

4. Aygıt Koleksiyonu Oluşturma **Sihirbazı'nın** **Genel** sayfasında, koleksiyon için bir ad girin.

5. Sınırlayıcı bir koleksiyon belirtmek için **Gözat'ı** seçin.

6. Üyelik **Kuralları** sayfasında Kural **Ekle'yi**seçin ve ardından **Doğrudan Üyelik Kuralı Oluştur Sihirbazı'nı**açmak için **Doğrudan Kural'ı** seçin. **İleri**’yi seçin.

7. Kaynak **Ara** sayfasında, Kaynak **sınıf** listesinde **Sistem Kaynağı'nı**seçin. **Öznitelik ad** listesinde **Ad'ı**seçin. **Değer** alanına girin `%`ve sonra **İleri'yi**seçin.

8. Kaynakları **Seç** sayfasında, .NET Framework'e dağıtmak istediğiniz her bilgisayar için onay kutusunu seçin. **İleri'yi**seçin ve sihirbazı tamamlayın.

9. **Aygıt Toplama Sihirbazı Oluştur'un**Üyelik **Kuralları** sayfasında **İleri'yi**seçin ve ardından sihirbazı tamamlayın.

<a name="creating_a_package"></a>

### <a name="create-a-package-and-program-for-the-net-framework-redistributable-package"></a>.NET Framework yeniden dağıtılabilir paketi için paket ve program oluşturma

Aşağıdaki adımlar, .NET Framework yeniden dağıtılabilir için el ile bir paket oluşturur. Paket, .NET Framework'ün kurulumu için belirtilen parametreleri ve paketin hedef bilgisayarlara nereden dağıtılacağını içerir.

Bir paket oluşturmak için:

1. Configuration Manager konsolunda **Yazılım Kitaplığı'nı**seçin.

2. Yazılım **Kitaplığı** çalışma alanında, **Uygulama Yönetimi'ni**genişletin ve ardından **Paketleri**seçin.

3. **Giriş** sekmesinde, **Oluştur** grubunda **Paket Oluştur'u**seçin.

4. Paket Oluştur ve **Program Sihirbazı'nın** **Paket** sayfasında aşağıdaki bilgileri girin:

    - Adı:`.NET Framework 4.5`

    - Üretici:`Microsoft`

    - Dil. `English (US)`

5. Bu paketi seçin **kaynak dosyaları içerir**ve sonra .NET Framework yükleme dosyalarını içeren yerel veya ağ klasörünü seçmek için **Gözat'ı** seçin. Klasörü seçtiğinizde **Tamam'ı**ve **sonra İleri'yi**seçin.

6. Sihirbazın **Program Türü** sayfasında Standart **Program'ı**seçin ve sonra **İleri'yi**seçin.

7. Paket Oluştur ve **Program Sihirbazı'nın** **Program** sayfasında aşağıdaki bilgileri girin:

    1. **Adı:**`.NET Framework 4.5`

    2. **Komut satırı:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (bu adımlardan sonra tabloda komut satırı seçenekleri açıklanmıştır)

    3. **Çalıştır:** **Gizli'yi**seçin.

    4. **Program çalıştırabilirsiniz:** Bir kullanıcının oturum açıp açmadığına bakılmaksızın programın çalıştırılayacağını belirten seçeneği seçin.

8. **Gereksinimler** sayfasında, varsayılan değerleri kabul etmek için **İleri'yi** seçin ve ardından sihirbazı tamamlayın.

Aşağıdaki tablo, 7. adımda belirtilen komut satırı seçeneklerini açıklar.

|Seçenek|Açıklama|
|------------|-----------------|
|**/q**|Sessiz modu ayarlar. Hiçbir kullanıcı girişine gerek yoktur ve hiçbir çıktı gösterilmez.|
|**/norestart**|Kurulum programının otomatik olarak yeniden başlatılmasını önler. Bu seçeneği kullanırsanız, Yapılandırma Yöneticisi'nin bilgisayarı yeniden başlatmayı üstlenmesi gerekir.|
|**/zincirleme paket** *PaketAdı*|Zincirlemeyi yapan paketin adını belirtir. Bu bilgiler, Microsoft Müşteri Deneyimi Geliştirme Programı'na (CEIP) kaydolmuş olanlar için diğer yükleme oturumu bilgileriyle birlikte bildirilir. Paket adı boşluklar içeriyorsa, sınırlayıcı olarak çift tırnak işaretleri kullanın; örneğin: **/zincirleme paket "Zincirleme Ürün"**.|

Bu adımlar, .NET Framework 4.5 adlı bir paket oluşturur. Program, .NET Framework 4.5'in sessiz bir kurulumunu dağıtır. Sessiz bir yüklemede, kullanıcılar yükleme işlemiyle etkileşime girmez ve zincirleme uygulaması iade kodunu yakalamak ve yeniden başlatmaişlemini işlemek zorundadır; bkz. [Yükleme Paketinden İlerleme Bilgileri Alma.](https://docs.microsoft.com/previous-versions/cc825975(v=vs.100))

<a name="select_dist_point"></a>

### <a name="select-a-distribution-point"></a>Dağıtım noktası seçme

Paketi ve programı bir sunucudan istemci bilgisayarlara dağıtmak için, önce bir site sistemini dağıtım noktası olarak belirlemeniz ve sonra paketi dağıtım noktasına dağıtmanız gerekir.

Bir önceki bölümde oluşturulan .NET Framework 4.5 paketi için bir dağıtım noktası seçmek üzere aşağıdaki adımları kullanın:

1. Configuration Manager konsolunda **Yazılım Kitaplığı'nı**seçin.

2. Yazılım **Kitaplığı** çalışma alanında, **Uygulama Yönetimi'ni**genişletin ve ardından **Paketleri**seçin.

3. Paket listesinden, önceki bölümde oluşturduğunuz **.NET Framework 4.5** paketini seçin.

4. **Giriş** sekmesinde, **Dağıtım** grubunda **İçeriği Dağıt'ı**seçin.

5. **İçeriği Dağıt sihirbazının** **Genel** sekmesinde, **İleri'yi**seçin.

6. Sihirbazın **İçerik Hedef** sayfasında **Ekle'yi**ve ardından Dağıtım **Noktası'nı**seçin.

7. Dağıtım **Noktaları Ekle** iletişim kutusunda, paketi ve programı barındıracak dağıtım noktası(lar)'ı seçin ve ardından **Tamam'ı**seçin.

8. Sihirbazı tamamlayın.

Paket şimdi, .NET Framework 4.5'i sessizce dağıtmak gereksinim duyduğunuz tüm bilgileri içerir. Paketi ve programı dağıtmadan önce, dağıtım noktasına yüklenmiş olduğundan doğrulayın; Configuration Manager Documentation Library'de [Configuration Manager ile dağıttığınız Monitor içeriğinin](https://docs.microsoft.com/configmgr/core/servers/deploy/configure/monitor-content-you-have-distributed) "İçerik durumu izleme" bölümüne bakın.

<a name="deploying_package"></a>

### <a name="deploy-the-package"></a>Paketi dağıtma

.NET Framework 4.5 paketini ve programını dağıtmak için:

1. Configuration Manager konsolunda **Yazılım Kitaplığı'nı**seçin.

2. Yazılım **Kitaplığı** çalışma alanında, **Uygulama Yönetimi'ni**genişletin ve ardından **Paketleri**seçin.

3. Paket listesinden **,.NET Framework 4.5**adlı paketi seçin.

4. **Giriş** sekmesinde, **Dağıtım** grubunda **Dağıt'ı**seçin.

5. **Yazılım Dağıt**sihirbazının **Genel** sayfasında **Gözat'ı**seçin ve daha önce oluşturduğunuz koleksiyonu seçin. **İleri**’yi seçin.

6. Sihirbazın **İçerik** sayfasında, yazılımı dağıtmak istediğiniz noktanın görüntülendiğini doğrulayın ve **sonra İleri'yi**seçin.

7. Sihirbazın **Dağıtım Ayarları** sayfasında, **Eylemin** **Yükleme**olarak ayarlı olduğunu ve **Amaç'ın Gerekli**olarak ayarlı olduğunu onaylayın. **Purpose** Bu, yazılım paketinin hedeflenen bilgisayarlarda zorunlu bir yükleme olmasını sağlar. **İleri**’yi seçin.

8. Sihirbazın **Zamanlama** sayfasında ,.NET Çerçevesi'nin ne zaman yüklenmesini istediğinizi belirtin. Yükleme zamanı atamak için **Yeni'yi** seçebilir veya kullanıcı oturum açıp kapattığında veya mümkün olan en kısa sürede yazılımı yüklemesini emredebilir. **İleri**’yi seçin.

9. Sihirbazın **Kullanıcı Deneyimi** sayfasında varsayılan değerleri kullanın ve **İleri'yi**seçin.

    > [!WARNING]
    > Üretim ortamınızın, dağıtım çizelgesi için farklı seçimler olmasını gerektiren ilkeleri olabilir. Bu seçenekler hakkında bilgi [için, Bkz. Reklam Adı Özellikleri: Zamanlama Sekmesi](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb694016%28v=technet.10%29).

10. Sihirbazın **Dağıtım Noktaları** sayfasında varsayılan değerleri kullanın ve **İleri'yi**seçin.

11. Sihirbazı tamamlayın. **İzleme** çalışma alanının **Dağıtımlar** düğümünde dağıtımın ilerlemesini izleyebilirsiniz.

Şimdi paket hedeflenen koleksiyona dağıtılır ve .NET Framework 4.5'in sessiz yüklemesi başlar. .NET Framework 4.5 yükleme hata kodları hakkında daha fazla bilgi için bu konunun ilerleyen bölümlerinde [İade Kodları](#return_codes) bölümüne bakın.

<a name="resources"></a>

## <a name="resources"></a>Kaynaklar

.NET Framework 4.5 yeniden dağıtılabilir paketinin dağıtımını sınayabilir altyapı hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.

**Etkin Dizin, DNS, DHCP:**

- [Active Directory Domain Services](/windows/desktop/ad/active-directory-domain-services)

- [Etki Alanı Adı Sistemi (DNS)](/windows-server/networking/dns/dns-top)

- [Dinamik Ana Bilgisayar Yapılandırma Protokolü (DHCP)](/windows-server/networking/technologies/dhcp/dhcp-top)

**SQL Server 2008:**

- [SQL Server 2008 Kurulumu (SQL Server Video)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/dd299415(v=sql.100))

- [SQL Server 2008 Veritabanı Yöneticileri için Güvenlik Genel Bakış](https://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)

**Sistem Merkezi 2012 Konfigürasyon Yöneticisi (Yönetim Noktası, Dağıtım Noktası):**

- [System Center 2012 Configuration Manager için Site Yönetimi](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg681983%28v=technet.10%29)

- [Configuration Manager Tek Site Planlama ve Dağıtım](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb680961%28v=technet.10%29)

**Windows bilgisayarlar için System Center 2012 Configuration Manager istemcisi:**

- [System Center 2012 Configuration Manager için İstemci Dağıtma](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg699391%28v=technet.10%29)

<a name="troubleshooting"></a>

## <a name="troubleshooting"></a>Sorun giderme

### <a name="log-file-locations"></a>Günlük dosyası konumları

.NET Framework kurulumu sırasında aşağıdaki günlük dosyaları oluşturulur:

- %temp%\Microsoft .NET Framework *sürümü*\*.txt
- %temp%\Microsoft .NET Framework *sürümü*\*.html

*sürüm,* 4.5 veya 4.7.2 gibi .NET Framework'ün yüklediğiniz sürümüdür.

.NET Framework yükleme komutundaki `/log` komut satırı seçeneğini kullanarak günlük dosyalarının yazıldığı dizini de belirtebilirsiniz. Daha fazla bilgi için [geliştiriciler için .NET Framework dağıtım kılavuzuna](deployment-guide-for-developers.md#command-line-options)bakın.

.NET Framework günlük dosyalarını toplamak ve dosyaların boyutunu küçülten sıkıştırılmış bir dolap (.cab) dosyası oluşturmak için [günlük toplama aracını](https://www.microsoft.com/download/details.aspx?id=12493) kullanabilirsiniz.

<a name="return_codes"></a>

### <a name="return-codes"></a>Dönüş kodları

Aşağıdaki tabloda .NET Framework 4.5 yeniden dağıtılabilir yükleme programındaki en yaygın iade kodları listelenilmiştir. Dönüş kodları yükleyicinin tüm sürümleri için aynıdır.

Ayrıntılı bilgi için bağlantılar için, sonraki bölüme bakın, [Hata kodları indirin.](#additional_error_codes)

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

- [Arka Plan Akıllı Aktarım Hizmeti (BITS) hata kodları](/windows/desktop/Bits/bits-return-values)

- [URL takma hata kodları](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775145%28v=vs.85%29)

- [WinHttp hata kodları](/windows/desktop/WinHttp/error-messages)

Diğer hata kodları:

- [Windows Installer hata kodları](/windows/desktop/msi/error-codes)

- [Windows Update Aracısı sonuç kodları](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc720442(v=ws.10))

## <a name="see-also"></a>Ayrıca bkz.

- [Geliştiriciler için Dağıtım Kılavuzu](deployment-guide-for-developers.md)
- [Sistem Gereksinimleri](../get-started/system-requirements.md)
