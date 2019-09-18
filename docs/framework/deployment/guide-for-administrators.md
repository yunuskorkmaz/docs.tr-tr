---
title: Yöneticiler için .NET Framework Dağıtım Kılavuzu
ms.date: 04/10/2018
helpviewer_keywords:
- administrator's guide, deploying .NET Framework
- deployment [.NET Framework], administrator's guide
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 91099b9b4d230839bc14c5fe4d5eafd05ac95541
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052152"
---
# <a name="net-framework-deployment-guide-for-administrators"></a>Yöneticiler için .NET Framework Dağıtım Kılavuzu

Bu adım adım makalede, bir sistem yöneticisinin Microsoft System Center Configuration Manager kullanarak bir ağ üzerinde .NET Framework 4,5 ve sistem bağımlılıklarını nasıl dağıtabileceğiniz açıklanır. Bu makalede tüm istemci bilgisayarların .NET Framework için gerekli olan minimum sistem gereksinimlerini karşıladığı varsayılmıştır. 4,5 .NET Framework yüklemeye yönelik yazılım ve donanım gereksinimlerinin bir listesi için bkz. [sistem gereksinimleri](../get-started/system-requirements.md).

> [!NOTE]
> Bu belgede başvurulan yazılım, sınırlama olmadan, .NET Framework 4,5, System Center Configuration Manager ve Active Directory, her biri lisans hüküm ve koşullarına tabidir. Bu yönergeler, bu tür lisans koşullarını ve koşulları gözden geçirilmiş yazılımların sahipleri tarafından kabul edildiği varsaymaktadır. Bu yönergeler, bu tür lisans anlaşmalarının koşullarından feragat etmiş sayılmaz.
>
> .NET Framework için destek hakkında daha fazla bilgi için Microsoft Desteği Web sitesindeki [Microsoft .NET Framework destek yaşam döngüsü ilkesi](https://go.microsoft.com/fwlink/?LinkId=196607) ' ne bakın.

Bu konu aşağıdaki bölümleri içermektedir:

- [Dağıtım işlemi](#the_deployment_process)
- [.NET Framework'ü dağıtma](#deploying_in_a_test_environment)
- [Koleksiyon oluşturma](#creating_a_collection)
- [Paket ve program oluşturma](#creating_a_package)
- [Bir dağıtım noktası seçin](#select_dist_point)
- [Paketi dağıtma](#deploying_package)
- [Kaynaklar](#resources)
- [Sorun giderme](#troubleshooting)

<a name="the_deployment_process"></a>

## <a name="the-deployment-process"></a>Dağıtım işlemi

Yerinde destek altyapısı varsa, ağ üzerinden .NET Framework dağıtılabilir paketini bilgisayarlara dağıtmak için Sistem Merkezi 2012 Yapılandırma Yöneticisi'ni kullanın. Altyapının oluşturulması, beş birincil alanın oluşturulmasını ve tanımlanmasını gerektirir: koleksiyonlar, yazılım için bir paket ve program, dağıtım noktaları ve dağıtımlar.

- **Koleksiyonlar** , .NET Framework dağıtıldığı kullanıcılar, Kullanıcı grupları veya bilgisayarlar gibi Configuration Manager kaynak gruplarıdır. Daha fazla bilgi için, Configuration Manager belge kitaplığındaki [System Center Configuration Manager koleksiyonlara giriş](https://docs.microsoft.com/sccm/core/clients/manage/collections/introduction-to-collections) bölümüne bakın.

- **Paketler ve programlar** , genellikle bir istemci bilgisayara yüklenecek yazılım uygulamalarını temsil eder, ancak tek tek dosyalar, güncelleştirmeler ve hatta ayrı komutlar da içerebilir. Daha fazla bilgi için Configuration Manager belge kitaplığındaki [System Center Configuration Manager Içindeki paketler ve programlar](https://docs.microsoft.com/sccm/apps/deploy-use/packages-and-programs) bölümüne bakın.

- **Dağıtım noktaları** , yazılımın istemci bilgisayarlarda çalışması için gereken dosyaları depolayan site sistem rolleridir Configuration Manager. Yapılandırma Yöneticisi istemcisi bir yazılım dağıtımı alıp işlediğinde, yazılımla ilişkili içeriği indirmek ve kurulum işlemini başlatmak için bir dağıtım noktasıyla temasa geçer. Daha fazla bilgi için bkz. Configuration Manager belge kitaplığındaki [Configuration Manager içerik yönetimi Için temel kavramlar](https://docs.microsoft.com/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management) .

- **Dağıtımlar** , yazılım paketini yüklemek için belirtilen hedef koleksiyonun geçerli üyelerine yönlendirir.

> [!IMPORTANT]
> Bu konudaki yordamlar, bir paket ve program oluşturmak ve dağıtmak için normal ayarları içerir ve tüm olası ayarları kapsamayabilir. Diğer Configuration Manager dağıtım seçenekleri için, [Configuration Manager belge kitaplığı](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg682041%28v=technet.10%29)' na bakın.

<a name="deploying_in_a_test_environment"></a>

## <a name="deploying-the-net-framework"></a>.NET Framework'ü dağıtma

.NET Framework 4,5 ' nin sessiz yüklemesini dağıtmak için System Center 2012 Configuration Manager kullanabilirsiniz. Bu, kullanıcıların yükleme işlemiyle etkileşimde bulunmazlar. Aşağıdaki adımları uygulayın:

1. [Koleksiyon oluşturun](#creating_a_collection).

2. [Yeniden dağıtılabilir .NET Framework için bir paket ve program oluşturun](#creating_a_package).

3. [Bir dağıtım noktası seçin](#select_dist_point).

4. [Paketi dağıtın](#deploying_package).

<a name="creating_a_collection"></a>

### <a name="create-a-collection"></a>Koleksiyon oluşturma

Bu adımda, paket ve program dağıtacağınız bilgisayarları seçersiniz ve onları bir aygıt koleksiyonunda gruplandırırsınız. Yapılandırma Yöneticisi'nde bir koleksiyon oluşturmak için, doğrudan üyelik kurallarını (koleksiyon üyelerini el ile belirtirsiniz) veya sorgu kurallarını (koleksiyon üyelerini sizin belirttiğiniz ölçütlere göre Yapılandırma Yöneticisi belirler) kullanabilirsiniz. Sorgular ve doğrudan kurallar dahil Üyelik kuralları hakkında daha fazla bilgi için, Configuration Manager belge kitaplığındaki [System Center Configuration Manager koleksiyonlara giriş](https://docs.microsoft.com/sccm/core/clients/manage/collections/introduction-to-collections) bölümüne bakın.

Bir koleksiyon oluşturmak için:

1. Configuration Manager konsolunda, **varlıklar ve uyumluluk**' i seçin.

2. **Varlıklar ve uyum** çalışma alanında, **Cihaz Koleksiyonları**' nı seçin.

3. **Oluştur** grubunun **giriş** sekmesinde, **cihaz koleksiyonu oluştur**' u seçin.

4. **Cihaz koleksiyonu oluşturma Sihirbazı**' nın **genel** sayfasında, koleksiyon için bir ad girin.

5. Sınırlama koleksiyonu belirtmek için **Gözden** geçirme ' yi seçin.

6. **Üyelik kuralları** sayfasında **Kural Ekle**' yi ve ardından **doğrudan kural** ' ı seçerek **doğrudan üyelik kuralı oluşturma Sihirbazı**' nı açın. Seçin **sonraki**.

7. Kaynak **Ara** sayfasında, **kaynak sınıfı** listesinde **sistem kaynağı**' nı seçin. **Öznitelik adı** listesinde **ad**' ı seçin. **Değer** alanında, girin `%`ve ardından **İleri**' yi seçin.

8. **Kaynak Seç** sayfasında, .NET Framework dağıtmak istediğiniz her bilgisayar için onay kutusunu seçin. **İleri**' yi seçin ve ardından Sihirbazı doldurun.

9. **Cihaz koleksiyonu oluşturma Sihirbazı**' nın **Üyelik kuralları** sayfasında, **İleri**' yi seçin ve ardından Sihirbazı doldurun.

<a name="creating_a_package"></a>

### <a name="create-a-package-and-program-for-the-net-framework-redistributable-package"></a>.NET Framework yeniden dağıtılabilir paketi için paket ve program oluşturma

Aşağıdaki adımlar, .NET Framework yeniden dağıtılabilir için el ile bir paket oluşturur. Paket, .NET Framework'ün kurulumu için belirtilen parametreleri ve paketin hedef bilgisayarlara nereden dağıtılacağını içerir.

Bir paket oluşturmak için:

1. Configuration Manager konsolunda **yazılım kitaplığı**' nı seçin.

2. **Yazılım kitaplığı** çalışma alanında **uygulama yönetimi**' ni genişletin ve **paketler**' i seçin.

3. **Giriş** sekmesinde, **Oluştur** grubunda, **paket oluştur**' u seçin.

4. **Paket ve program oluşturma Sihirbazı**' nın **paket** sayfasında, aşağıdaki bilgileri girin:

    - Ada`.NET Framework 4.5`

    - Üreticisini`Microsoft`

    - Dil. `English (US)`

5. **Bu paket kaynak dosyaları içerir**' i seçin ve ardından .NET Framework yükleme dosyalarını içeren yerel veya ağ klasörünü seçmek için **Araştır** ' ı seçin. Klasörü seçtikten sonra **Tamam**' ı seçin ve ardından **İleri**' yi seçin.

6. Sihirbazın **program türü** sayfasında, **standart program**' ı seçin ve ardından **İleri**' yi seçin.

7. **Paket ve program oluşturma Sihirbazı**' nın **Program** sayfasında, aşağıdaki bilgileri girin:

    1. **Ad:** `.NET Framework 4.5`

    2. **Komut satırı:** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (komut satırı seçenekleri, bu adımların ardından tabloda açıklanmıştır)

    3. **Çalışmaz** **Gizli**öğesini seçin.

    4. **Program çalışabilir:** Kullanıcının oturum açmış olmasından bağımsız olarak programın çalıştıracağınızı belirten seçeneği belirleyin.

8. **Gereksinimler** sayfasında, varsayılan değerleri kabul etmek için **İleri** ' yi seçin ve ardından Sihirbazı doldurun.

Aşağıdaki tablo, 7. adımda belirtilen komut satırı seçeneklerini açıklar.

|Seçenek|Açıklama|
|------------|-----------------|
|**/q**|Sessiz modu ayarlar. Hiçbir kullanıcı girişine gerek yoktur ve hiçbir çıktı gösterilmez.|
|**/ norestart**|Kurulum programının otomatik olarak yeniden başlatılmasını önler. Bu seçeneği kullanırsanız, Yapılandırma Yöneticisi'nin bilgisayarı yeniden başlatmayı üstlenmesi gerekir.|
|**/ChainingPackage** *PackageName*|Zincirlemeyi yapan paketin adını belirtir. Bu bilgiler, [Microsoft müşteri deneyimini geliştirme programı (CEIP)](https://go.microsoft.com/fwlink/p/?LinkId=248244)için kaydolup diğer yükleme oturum bilgileriyle birlikte raporlanır. Paket adı boşluk içeriyorsa, çift tırnak işaretlerini sınırlayıcılar olarak kullanın; Örneğin: **/chainingpackage "zincirleme ürün"** .|

Bu adımlar, .NET Framework 4.5 adlı bir paket oluşturur. Program, .NET Framework 4.5'in sessiz bir kurulumunu dağıtır. Sessiz yüklemede, kullanıcılar yükleme işlemiyle etkileşime girmez ve zincirleme uygulama, dönüş kodunu yakalayıp yeniden başlatmayı işleymelidir; bkz. [bir yükleme paketinden Ilerleme bilgileri alma](https://go.microsoft.com/fwlink/?LinkId=179606).

<a name="select_dist_point"></a>

### <a name="select-a-distribution-point"></a>Dağıtım noktası seçme

Paketi ve programı bir sunucudan istemci bilgisayarlara dağıtmak için, önce bir site sistemini dağıtım noktası olarak belirlemeniz ve sonra paketi dağıtım noktasına dağıtmanız gerekir.

Bir önceki bölümde oluşturulan .NET Framework 4.5 paketi için bir dağıtım noktası seçmek üzere aşağıdaki adımları kullanın:

1. Configuration Manager konsolunda **yazılım kitaplığı**' nı seçin.

2. **Yazılım kitaplığı** çalışma alanında **uygulama yönetimi**' ni genişletin ve **paketler**' i seçin.

3. Paket listesinden, önceki bölümde oluşturduğunuz **4,5 .NET Framework** paketini seçin.

4. **Giriş** sekmesinde, **dağıtım** grubunda, **içeriği dağıt**' ı seçin.

5. **Içerik Dağıtma Sihirbazı**' nın **genel** sekmesinde, **İleri**' yi seçin.

6. Sihirbazın **Içerik hedefi** sayfasında **Ekle**' yi ve ardından **dağıtım noktası**' nı seçin.

7. **Dağıtım noktaları Ekle** iletişim kutusunda, paketi ve programı barındıracak dağıtım noktalarını seçin ve ardından **Tamam**' ı seçin.

8. Sihirbazı tamamlayın.

Paket şimdi, .NET Framework 4.5'i sessizce dağıtmak gereksinim duyduğunuz tüm bilgileri içerir. Paketi ve programı dağıtmadan önce, dağıtım noktasında yüklü olduğunu doğrulayın; Configuration Manager belge kitaplığındaki [System Center Configuration Manager ile dağıttığınız Içeriği izlemek](https://docs.microsoft.com/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed) Için "içeriği izleme" bölümüne bakın.

<a name="deploying_package"></a>

### <a name="deploy-the-package"></a>Paketi dağıtma

.NET Framework 4.5 paketini ve programını dağıtmak için:

1. Configuration Manager konsolunda **yazılım kitaplığı**' nı seçin.

2. **Yazılım kitaplığı** çalışma alanında **uygulama yönetimi**' ni genişletin ve **paketler**' i seçin.

3. Paket listesinden **.NET Framework 4,5**adlı oluşturduğunuz paketi seçin.

4. **Giriş** sekmesinde, **dağıtım** grubunda, **Dağıt**' ı seçin.

5. **Yazılım Dağıtma Sihirbazı**'nın **genel** sayfasında, **Araştır**' ı seçin ve daha önce oluşturduğunuz koleksiyonu seçin. Seçin **sonraki**.

6. Sihirbazın **içerik** sayfasında, yazılımı dağıtmak istediğiniz noktanın görüntülendiğini doğrulayın ve ardından **İleri**' yi seçin.

7. Sihirbazın **dağıtım ayarları** sayfasında, **eylemin** **yüklenmek**üzere ayarlandığını ve **amacın** **gerekli**olarak ayarlandığını onaylayın. Bu, yazılım paketinin hedeflenen bilgisayarlarda zorunlu bir yükleme olmasını sağlar. Seçin **sonraki**.

8. Sihirbazın **zamanlama** sayfasında, .NET Framework yüklenmesini istediğiniz tarihi belirtin. Bir yükleme süresi atamak için **Yeni** ' yi seçebilir veya yazılımın kullanıcı oturum açtığında ya da kapalıyken veya mümkün olan en kısa sürede yüklenmesine izin verebilirsiniz. Seçin **sonraki**.

9. Sihirbazın **Kullanıcı deneyimi** sayfasında varsayılan değerleri kullanın ve **İleri**' yi seçin.

    > [!WARNING]
    > Üretim ortamınızın, dağıtım çizelgesi için farklı seçimler olmasını gerektiren ilkeleri olabilir. Bu seçenekler hakkında daha fazla bilgi için [bkz. tanıtım adı özellikleri: Zamanlama sekmesi](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb694016%28v=technet.10%29).

10. Sihirbazın **dağıtım noktaları** sayfasında, varsayılan değerleri kullanın ve **İleri**' yi seçin.

11. Sihirbazı tamamlayın. Dağıtım ilerlemesini **izleme** çalışma alanının **dağıtımlar** düğümünde izleyebilirsiniz.

Şimdi paket hedeflenen koleksiyona dağıtılır ve .NET Framework 4.5'in sessiz yüklemesi başlar. .NET Framework 4,5 yükleme hata kodları hakkında daha fazla bilgi için bu konunun devamındaki [Return Codes](#return_codes) bölümüne bakın.

<a name="resources"></a>

## <a name="resources"></a>Kaynaklar

.NET Framework 4,5 yeniden dağıtılabilir paketi dağıtımını test eden altyapı hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.

**Active Directory, DNS, DHCP:**

- [Active Directory Domain Services](/windows/desktop/ad/active-directory-domain-services)

- [Etki alanı adı sistemi (DNS)](/windows-server/networking/dns/dns-top)

- [Dinamik ana bilgisayar Yapılandırma Protokolü (DHCP)](/windows-server/networking/technologies/dhcp/dhcp-top)

**SQL Server 2008:**

- [SQL Server 2008 (SQL Server video) yükleniyor](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/dd299415(v=sql.100))

- [SQL Server 2008 güvenliğe genel bakış veritabanı yöneticileri](https://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)

**System Center 2012 Configuration Manager (yönetim noktası, dağıtım noktası):**

- [System Center 2012 Configuration Manager için Site Yönetimi](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg681983%28v=technet.10%29)

- [Tek site planlama ve dağıtım Configuration Manager](https://docs.microsoft.com/previous-versions/system-center/configuration-manager-2007/bb680961%28v=technet.10%29)

**Windows bilgisayarlar için System Center 2012 Configuration Manager istemcisi:**

- [System Center 2012 Configuration Manager için İstemci Dağıtma](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/gg699391%28v=technet.10%29)

<a name="troubleshooting"></a>

## <a name="troubleshooting"></a>Sorun giderme

### <a name="log-file-locations"></a>Günlük dosyası konumları

Aşağıdaki günlük dosyaları .NET Framework kurulum sırasında oluşturulur:

- %Temp%\Microsoft .NET Framework *Version*\*. txt
- %Temp%\Microsoft .NET Framework *Version*\*. html

Burada *Sürüm* , yüklemekte olduğunuz .NET Framework sürümü (4,5 veya 4.7.2 gibi).

Ayrıca, .NET Framework yükleme komutunda `/log` komut satırı seçeneğini kullanarak, günlük dosyalarının yazıldığı dizini de belirtebilirsiniz. Daha fazla bilgi için bkz. [geliştiriciler için .NET Framework dağıtım kılavuzu](deployment-guide-for-developers.md#command-line-options).

[Günlük toplama aracını](https://www.microsoft.com/download/details.aspx?id=12493) , .NET Framework günlük dosyalarını toplamak ve dosyaların boyutunu azaltan sıkıştırılmış dolap (. cab) dosyası oluşturmak için kullanabilirsiniz.

<a name="return_codes"></a>

### <a name="return-codes"></a>Dönüş kodları

Aşağıdaki tabloda, .NET Framework 4,5 yeniden dağıtılabilir yükleme programından en sık kullanılan dönüş kodları listelenmektedir. Dönüş kodları yükleyicinin tüm sürümleri için aynıdır.

Ayrıntılı bilgilerin bağlantıları için bkz. sonraki bölüm, [indirme hata kodları](#additional_error_codes).

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

- [URL bilinen adı hata kodları](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775145%28v=vs.85%29)

- [WinHttp hata kodları](/windows/desktop/WinHttp/error-messages)

Diğer hata kodları:

- [Windows Installer hata kodları](/windows/desktop/msi/error-codes)

- [Windows Update Aracısı sonuç kodları](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc720442(v=ws.10))

## <a name="see-also"></a>Ayrıca bkz.

- [Geliştiriciler için Dağıtım Kılavuzu](deployment-guide-for-developers.md)
- [Sistem Gereksinimleri](../get-started/system-requirements.md)
