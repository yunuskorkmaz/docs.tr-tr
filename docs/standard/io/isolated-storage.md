---
title: Yalıtılmış Depolama
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- data storage using isolated storage
- stores
- storing data using isolated storage
- isolated storage
- location of isolated storage in file system
- standardizing storage systems
- storing data using isolated storage, when not to use
- code, isolated storage
- isolated storage, options
- data storage using isolated storage, when not to use
- storing data using isolated storage, options
- isolated storage, when not to use
- data storage using isolated storage, options
- isolation
ms.assetid: aff939d7-9e49-46f2-a8cd-938d3020e94e
ms.openlocfilehash: ed784bafda2aed829f2e97d7e7e8b2716c48c7ba
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706588"
---
# <a name="isolated-storage"></a>Yalıtılmış Depolama
<a name="top"></a>Masaüstü uygulamaları için yalıtılmış depolama, kodu kaydedilen verilerle ilişkilendirmenin standartlaştırılmış yollarını tanımlayarak yalıtım ve güvenlik sağlayan bir veri depolama mekanizmasıdır. Standart hale getirme başka yararlar da sağlar. Yöneticiler yalıtılmış depolamayı değiştirecek araçları kullanarak dosya depolama alanını yapılandırabilir, güvenlik ilkelerini ayarlayabilir ve kullanılmayan verileri silebilir. Yalıtılmış depolama ile kodunuz dosya sistemindeki güvenli konumları belirtmek için benzersiz yollara ihtiyaç duymaz ve veriniz yalnızca yalıtılmış depolama erişimi olan diğer uygulamalardan korunur. Bir uygulamanın depo alanının nerede olduğunu belirten sabit kodlu bilgi gerekli değildir.

> [!IMPORTANT]
> Yalıtılmış depolama, Windows 8. x Mağazası uygulamaları için kullanılamaz. Bunun yerine, yerel verileri ve dosyaları depolamak için Windows Çalışma Zamanı API 'sinde bulunan `Windows.Storage` ad alanlarında uygulama veri sınıflarını kullanın. Daha fazla bilgi için bkz. Windows Geliştirme Merkezi 'nde [uygulama verileri](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) .

Bu konu aşağıdaki bölümleri içermektedir:

- [Veri bölmeleri ve depolar](#data_compartments_and_stores)

- [Yalıtılmış depolama için kotalar](#quotas)

- [Güvenli erişim](#secure_access)

- [İzin verilen kullanım ve güvenlik riskleri](#allowed_usage)

- [Yalıtılmış depolama konumları](#isolated_storage_locations)

- [Yalıtılmış depolamayı oluşturma, numaralandırma ve silme](#isolated_storage_tasks)

- [Yalıtılmış depolama için senaryolar](#scenarios_for_isolated_storage)

- [İlgili konular](#related_topics)

- [Başvuru](#reference)

<a name="data_compartments_and_stores"></a>

## <a name="data-compartments-and-stores"></a>Veri Bölmeleri ve Depoları

Bir uygulama bir dosya içinde veri depoladığında, depolama konumunun başka bir uygulama tarafından öğrenilme ve bu nedenle bozulma olasılığını en aza indirmek için dosya adı ve depolama konumu dikkatle seçilmelidir. Bu sorunları yönetecek standart bir sistem olmadığında, depolama çakışmalarını en aza indiren geçici teknikler karmaşık olabilir ve sonuçları güvenilir olmayabilir.

Yalıtılmış depolama ile veri her zaman kullanıcıya ve derlemeye göre yalıtılır. Derlemenin başlangıç noktası veya tanımlayıcı adı gibi kimlik bilgileri derlemenin kimliğini belirler. Veri ayrıca benzer kimlik bilgileri kullanarak uygulama etki alanına göre de yalıtılabilir.

Yalıtılmış depolama kullandığınızda, uygulamanız veriyi kodun yayımcısı veya imzası gibi bir bilgi ile ilişkili benzersiz bir veri bölmesine kaydeder. Veri bölmesi belirli bir depolama konumu değildir, bir soyutlamadır, ve depo denen verinin tutulduğu gerçek dizin konumlarını içeren bir veya daha fazla yalıtılmış depolama dosyasından oluşur. Örneğin, bir uygulamanın kendisiyle ilişkili bir veri bölmesi olabilir, ve dosya sistemindeki bir dizin o uygulama için veriyi tutan gerçek depoyu uygulayabilir. Depoya kaydedilen veri kullanıcı tercih bilgisinden uygulama durumuna kadar herhangi türde bir veri olabilir. Geliştirici için, veri bölmesinin konumu saydamdır. Depolar genellikle istemcide bulunur, ancak bir sunucu uygulaması yalıtılmış depoları kullanarak belirli bir kullanıcı için veri depolayabilir. Yalıtılmış depolama ayrıca bir kullanıcının gezici profili ile bir sunucu üzerinde bilgi tutarak o bilginin gezici kullanıcıyla birlikte hareket etmesini sağlayabilir.

<a name="quotas"></a>

## <a name="quotas-for-isolated-storage"></a>Ayrık Depolama Kotaları

Bir kota, kullanılabilen yalıtılmış depolama miktarındaki bir sınırdır. Kota dosya alanı baytlarının yanı sıra depodaki dizin ve diğer bilgilerle ilgili ek yükü de içerir. Yalıtılmış depolama, <xref:System.Security.Permissions.IsolatedStoragePermission> nesneleri kullanılarak ayarlanan depolama sınırları olan izin kotalarını kullanır. Kotayı aşan verileri yazmaya çalışırsanız bir <xref:System.IO.IsolatedStorage.IsolatedStorageException> özel durumu oluşturulur.  .NET Framework Yapılandırma Aracı (Mscorcfg.msc) kullanarak değiştirilebilen güvenlik ilkesi koda hangi izinlerin verildiğini belirler. <xref:System.Security.Permissions.IsolatedStoragePermission> verilen kod, <xref:System.Security.Permissions.IsolatedStoragePermission.UserQuota%2A> özelliğinin izin verdiğinden daha fazla depolama alanı kullanılmasıyla kısıtlıdır. Ancak, kod farklı kullanıcı kimlikleri sunarak izin kotalarını atlayabileceği için, izin kotaları kod davranışı için kesin bir sınır yerine daha çok kodun nasıl davranacağı üzerine bir kılavuz olarak görev görür.

Kotalar gezici depolarda uygulanmaz. Bu nedenle kodun bunu kullanabilmesi için biraz daha yüksek bir izin düzeyi gerekir. Numaralandırma değerleri <xref:System.Security.Permissions.IsolatedStorageContainment.AssemblyIsolationByRoamingUser> ve <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByRoamingUser> bir gezici kullanıcı için yalıtılmış depolamayı kullanma izni belirtir.

<a name="secure_access"></a>

## <a name="secure-access"></a>Güvenli Erişim

Yalıtılmış depolama kullanımı kısmen güvenilir uygulamaların bilgisayarın güvenlik ilkesi tarafından kontrol edilerek veri depolamasını sağlar. Bu özellikle bir kullanıcının dikkatli olarak çalıştırmak isteyeceği indirilen bileşenler için kullanışlıdır. Güvenlik ilkesi, standart I/O mekanizmalarını kullanarak dosya sistemine eriştiğinizde bu tür kod iznini nadiren verir. Ancak varsayılan olarak; yerel bilgisayardan, yerel bir ağdan veya Internet üzerinden çalıştırılan koda yalıtılmış depolama hakkı verilir.

Yöneticiler uygun olan güven düzeyine göre bir uygulamanın veya kullanıcının ne kadar yalıtılmış depolama alanına sahip olacağını sınırlayabilir. Ek olarak, yöneticiler bir kullanıcının kalıcı verilerini tamamen kaldırabilir. Yalıtılmış depolama oluşturmak veya erişim sağlamak için, koda uygun <xref:System.Security.Permissions.IsolatedStorageFilePermission> izni verilmelidir.

Yalıtılmış depolamaya erişmek için, kod tüm gerekli yerel platform işletim sistemi haklarına sahip olmalıdır. Hangi kullanıcıların dosya sistemini kullanmaya hakkı olduğunu kontrol eden erişim denetim listeleri (ACL) sağlanmalıdır. .NET Framework uygulamaları, platforma özel kimliğe bürünme işlemi gerçekleştirmedikleri sürece yalıtılmış depolamaya erişmek için işletim sistemi haklarına sahiptir. Bu durumda, uygulama kimliğine bürünülen kullanıcının yalıtılmış depolamaya erişmek için gerekli uygun işletim sistemi haklarına sahip olduğundan emin olmakta sorumludur. Bu erişim, internetten çalıştırılan veya indirilen kodun belirli bir kullanıcı ile ilgili depolama alanında okuma ve yazma işlemleri yapabilmesi için kullanışlı bir yol sağlar.

Yalıtılmış depolamaya erişimi denetlemek için ortak dil çalışma zamanı <xref:System.Security.Permissions.IsolatedStorageFilePermission> nesneleri kullanır. Her nesne aşağıdaki değerleri belirten özelliklere sahiptir:

- İzin verilen kullanım, izin verilen erişim türünü belirtir. Değerler <xref:System.Security.Permissions.IsolatedStorageContainment> numaralandırmanın üyeleridir. Bu değerler hakkında daha fazla bilgi için, sonraki bölümdeki tabloya bakın.

- Depo kotası, önceki bölümde anlatıldığı gibidir.

Çalışma zamanı, kod ilk olarak bir depoyu açmaya çalıştığında izin <xref:System.Security.Permissions.IsolatedStorageFilePermission>. Kodun ne kadar güvenilir olduğuna bağlı olarak, bu izni verip vermeyeceğine karar verir. İzin verildiğinde, izin verilen kullanım ve depolama kotası değerleri güvenlik ilkesi ve kodun <xref:System.Security.Permissions.IsolatedStorageFilePermission>isteği tarafından belirlenir. Güvenlik ilkesi .Net Framework Yapılandırma Aracı (Mscorcfg.msc) kullanılarak ayarlanır. Çağrı yığınındaki tüm çağıranlar, her çağıranın en azından uygun izin verilen kullanıma sahip olduğundan emin olmak için kontrol edilir. Çalışma zamanı ayrıca dosyanın kaydedileceği depoyu açan veya oluşturan koda uygulanan kotayı da kontrol eder. Eğer bu koşullar sağlanırsa, izin verilir. Kota, depoya yazılan her dosyada tekrar denetlenir.

Ortak dil çalışma zamanı, güvenlik ilkesine göre uygun olan <xref:System.Security.Permissions.IsolatedStorageFilePermission> olarak izin vereceğinden, uygulama kodu izin istemek için gerekli değildir. Ancak, <xref:System.Security.Permissions.IsolatedStorageFilePermission>dahil olmak üzere, uygulamanız için gereken belirli izinleri istemeniz iyi bir neden vardır.

<a name="allowed_usage"></a>

## <a name="allowed-usage-and-security-risks"></a>İzin Verilen Kullanım ve Güvenlik Riskleri

<xref:System.Security.Permissions.IsolatedStorageFilePermission> tarafından belirtilen izin verilen kullanım, yalıtılmış depolamayı oluşturma ve kullanma ile hangi kodun izin verileceğini belirler. Aşağıdaki tablo izinde belirtilen izin verilen kullanımın hangi yalıtım türlerine karşılık geldiğini gösterir ve her izin verilen kullanım ile ilişkili güvenlik risklerini özetler.

|İzin verilen kullanım|Yalıtım türleri|Güvenlik etkisi|
|-------------------|---------------------|---------------------|
|<xref:System.Security.Permissions.IsolatedStorageContainment.None>|Hiçbir yalıtılmış depolama kullanımına izin verilmez.|Güvenlik etkisi yoktur.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser>|Kullanıcı, etki alanı ve derlemeye göre yalıtım Her derlemenin etki alanı içinde ayrı bir alt deposu bulunur. Bu izni kullanan depolar örtülü olarak bilgisayara göre de yalıtılır.|Bu izin düzeyi kaynakları yetkisiz aşırı kullanıma açık bırakır, ancak uygulanan kotalar bunu zorlaştırır. Buna hizmet reddi saldırısı denir.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByRoamingUser>|`DomainIsolationByUser`ile aynıdır, ancak mağaza, dolaşım Kullanıcı profilleri etkinse ve Kotalar zorlanmadığında dolaşımını yapan bir konuma kaydedilir.|Kotaların devre dışı bırakılması gerektiği için, depo kaynakları bir hizmet reddi saldırısına karşı daha savunmasızdır.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.AssemblyIsolationByUser>|Kullanıcı ve derlemeye göre yalıtım Bu izni kullanan depolar örtülü olarak bilgisayara göre de yalıtılır.|Kotalar hizmet reddi saldırısını önlemeye yardımcı olmak için bu düzeyde uygulanır. Başka bir etki alanındaki aynı derleme bu depoya erişebilir ve bu nedenle uygulamalar arasında bilgi sızma olasılığı bulunur.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.AssemblyIsolationByRoamingUser>|`AssemblyIsolationByUser`ile aynıdır, ancak mağaza, dolaşım Kullanıcı profilleri etkinse ve Kotalar zorlanmadığında dolaşımını yapan bir konuma kaydedilir.|`AssemblyIsolationByUser`ile aynıdır, ancak kotalar olmadan hizmet reddi saldırısı riski artar.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser>|Kullanıcıya göre yalıtım. Genellikle yalnızca yönetici veya hata ayıklama araçları bu izin düzeyini kullanır.|Bu izinle olan erişim, kodun bir kullanıcının yalıtılmış depolama dosyalarını ve dizinlerini görüntülemesine ve silmesine olanak verir (derleme yalıtımına bakmaksızın). Riskler, bilgi sızması ve veri kaybını içerir ancak bunlarla sınırlı değildir.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.UnrestrictedIsolatedStorage>|Tüm kullanıcılar, etki alanları ve derlemelere göre yalıtım. Genellikle yalnızca yönetici veya hata ayıklama araçları bu izin düzeyini kullanır.|Bu izin tüm kullanıcılar için tüm yalıtılmış depoların açığa çıkma olasılığını oluşturur.|

<a name="isolated_storage_locations"></a>

## <a name="isolated-storage-locations"></a>Ayrık Depolama Konumları

Bazen yalıtılmış depolamaya yapılan bir değişikliği işletim sisteminin dosya sistemini kullanarak doğrulamak yararlıdır. Ayrıca yalıtılmış depolama dosyalarının konumunu da bilmek isteyebilirsiniz. Bu konum işletim sistemine göre değişir. Aşağıdaki tablo bazı yaygın işletim sistemleri için yalıtılmış depolamanın bulunduğu kök konumlarını gösterir. Bu kök konumu altında Microsoft\IsolatedStorage dizinlerine bakın. Dosya sisteminde yalıtılmış depolamayı görmek için klasör ayarlarını değiştirerek gizli dosyaları ve klasörleri görünür yapmanız gerekir.

|İşletim sistemi|Dosya sistemindeki konumu|
|----------------------|-----------------------------|
|Windows 2000, Windows XP, Windows Server 2003 (Windows NT 4.0'dan yükseltme)|Gezinme etkinleştirilmiş depolar =<br /><br /> \<SYSTEMROOT > \Profiles\\< User\>\Application Data<br /><br /> Gezici olmayan depolar =<br /><br /> \<SYSTEMROOT > \Profiles\\< User\>\Local Settings\Application Data|
|Windows 2000 - temiz yükleme (ve Windows 98 ve Windows NT 3.51'den yükseltme)|Gezinme etkinleştirilmiş depolar =<br /><br /> \<SYSTEMDRIVE > \Documents ve Settings\\< User\>\Application Data<br /><br /> Gezici olmayan depolar =<br /><br /> \<SYSTEMDRIVE > \Documents ve Settings\\< User\>\Local Settings\Application Data|
|Windows XP, Windows Server 2003 - temiz yükleme (Windows 2000 ve Windows 98'den yükseltme)|Gezinme etkinleştirilmiş depolar =<br /><br /> \<SYSTEMDRIVE > \Documents ve Settings\\< User\>\Application Data<br /><br /> Gezici olmayan depolar =<br /><br /> \<SYSTEMDRIVE > \Documents ve Settings\\< User\>\Local Settings\Application Data|
|Windows 8, Windows 7, Windows Server 2008, Windows Vista|Gezinme etkinleştirilmiş depolar =<br /><br /> \<SYSTEMDRIVE > \Users\\< Kullanıcı\>\AppData\Roaming<br /><br /> Gezici olmayan depolar =<br /><br /> \<SYSTEMDRIVE > \Users\\< Kullanıcı\>\AppData\Local|

<a name="isolated_storage_tasks"></a>

## <a name="creating-enumerating-and-deleting-isolated-storage"></a>Ayrık Depolama Birimi Oluşturma, Numaralandırma ve Silme

.NET Framework yalıtılmış depolamayı içeren görevleri gerçekleştirmenize yardımcı olması için <xref:System.IO.IsolatedStorage> ad alanında üç sınıf sağlar:

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>, <xref:System.IO.IsolatedStorage.IsolatedStorage?displayProperty=nameWithType> türetilir ve depolanan derleme ve uygulama dosyalarının temel yönetimini sağlar. <xref:System.IO.IsolatedStorage.IsolatedStorageFile> sınıfının bir örneği dosya sisteminde bulunan tek bir depoyu temsil eder.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> <xref:System.IO.FileStream?displayProperty=nameWithType> türetilir ve bir depodaki dosyalara erişim sağlar.

- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>, uygun yalıtım türüyle bir mağaza oluşturmanıza ve seçmenize olanak tanıyan bir numaralandırmadır.

Yalıtılmış depolama sınıfları, yalıtılmış depoları oluşturmanızı, numaralandırmanızı ve silmenizi sağlar. Bu görevleri gerçekleştirmeye yönelik yöntemlere <xref:System.IO.IsolatedStorage.IsolatedStorageFile> nesnesi aracılığıyla ulaşılabilir. Bazı işlemler yalıtılmış depolamayı yönetme hakkını temsil eden <xref:System.Security.Permissions.IsolatedStorageFilePermission> iznine sahip olmanızı gerektirir; Ayrıca, dosya veya dizine erişmek için işletim sistemi haklarına sahip olmanız gerekebilir.

Ortak yalıtılmış depolama görevlerini gösteren bir dizi örnek için, [Ilgili konularda](#related_topics)listelenen nasıl yapılır konularına bakın.

<a name="scenarios_for_isolated_storage"></a>

## <a name="scenarios-for-isolated-storage"></a>Ayrık Depolama Birimi Senaryoları

Yalıtılmış depolama, aşağıdaki dört senaryo da dahil olmak üzere pek çok durumda kullanışlıdır:

- İndirilen denetimler. İnternetten indirilen yönetilen kod denetimlerinin normal I/O sınıflarıyla hard diske yazmasına izin verilmez, ancak yalıtılmış depolama kullanarak kullanıcıların ayarlarını ve uygulama durumlarını kalıcı olarak tutabilirler.

- Paylaşılan bileşen depolama. Uygulamalar arasında paylaşılan denetimler, veri depolarına kontrollü erişim sağlamak için yalıtılmış depolama kullanabilir.

- Sunucu depolama alanı. Sunucu uygulamaları yalıtılmış depolamayı kullanarak uygulamaya istekte bulunan büyük sayıdaki kullanıcılar için tek tek depo sağlayabilir. Yalıtılmış depolama her zaman kullanıcıya göre tutulduğu için, sunucu isteği yapan kullanıcının kimliğine bürünmelidir. Bu durumda, veriler, uygulamanın kullanıcıları arasında ayrım yapmak için kullandığı kimliğin aynısı olan sorumlunun kimliğine göre yalıtılmıştır.

- Dolaşım. Uygulamalar gezici kullanıcı profilleriyle de yalıtılmış depolama kullanabilir. Bu, bir kullanıcının yalıtılmış depolarının profil ile birlikte gezinmesini sağlar.

Yalıtılmış depolamayı aşağıdaki durumlarda kullanmamalısınız:

- Şifrelenmemiş anahtarlar veya şifreler gibi yüksek değerli veriler için, çünkü yalıtılmış depolama yüksek derecede güvenilen koddan, yönetilmeyen koddan veya bilgisayarın güvenilen kullanıcılarından korunmaz.

- Kod saklamak için.

- Yöneticilerin kontrol ettiği yapılandırma ve dağıtım ayarları için. (Kullanıcı tercihleri yapılandırma ayarı sayılmaz, çünkü yöneticiler onları kontrol etmez.)

Çoğu uygulama veri depolamak ve yalıtmak için bir veri tabanı kullanır ve bu durumda bir veritabanındaki bir veya daha fazla satır belirli bir kullanıcı için depolamayı temsil edebilir. Kullanıcı sayısı az olduğunda, bir veritabanı kullanmanın getirdiği ek yük fazla olduğunda veya veritabanı olanağı olmadığında bir veritabanı yerine yalıtılmış depolamayı kullanabilirsiniz. Ayrıca, uygulama bir veritabanı satırının sağladığından daha esnek ve karmaşık depo gerektirdiğinde, yalıtılmış depolama uygun bir alternatif olabilir.

<a name="related_topics"></a>

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Yalıtım Türleri](../../../docs/standard/io/types-of-isolation.md)|Farklı yalıtım türlerini açıklar.|
|[Nasıl yapılır: Yalıtılmış Depolama için Depoları Alma](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)|Kullanıcı ve derlemeye göre yalıtılmış bir mağaza elde etmek için <xref:System.IO.IsolatedStorage.IsolatedStorageFile> sınıfının kullanılmasına bir örnek sağlar.|
|[Nasıl yapılır: Yalıtılmış Depolama için Depoları Numaralandırma](../../../docs/standard/io/how-to-enumerate-stores-for-isolated-storage.md)|Kullanıcı için yalıtılmış depolamanın boyutunu hesaplamak üzere <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> yönteminin nasıl kullanılacağını gösterir.|
|[Nasıl yapılır: Yalıtılmış Depolamadaki Depoları Silme](../../../docs/standard/io/how-to-delete-stores-in-isolated-storage.md)|Yalıtılmış depoları silmek için <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A?displayProperty=nameWithType> yönteminin iki farklı şekilde nasıl kullanılacağını gösterir.|
|[Nasıl yapılır: Yalıtılmış Depolama ile Alan Dolu Koşullarını Öngörme](../../../docs/standard/io/how-to-anticipate-out-of-space-conditions-with-isolated-storage.md)|Bir yalıtılmış depodaki kalan alanın nasıl ölçüldüğünü gösterir.|
|[Nasıl yapılır: Yalıtılmış Depolamada Dosya ve Dizinler Oluşturma](../../../docs/standard/io/how-to-create-files-and-directories-in-isolated-storage.md)|Bir yalıtılmış depoda dosyalar ve dizinler oluşturma ile ilgili bazı örnekler sağlar.|
|[Nasıl yapılır: Yalıtılmış Depolamada Mevcut Dosya ve Dizinleri Bulma](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md)|Yalıtılmış depolamada dizin yapısının ve dosyaların nasıl okunduğunu gösterir.|
|[Nasıl yapılır: Yalıtılmış Depolamadaki Dosyaları Okuma ve Yazma](../../../docs/standard/io/how-to-read-and-write-to-files-in-isolated-storage.md)|Bir yalıtılmış depolama dosyasına dize yazmak ve ardından geri okumak ile ilgili bir örnek sağlar.|
|[Nasıl yapılır: Yalıtılmış Depolamadaki Dosya ve Dizinleri Silme](../../../docs/standard/io/how-to-delete-files-and-directories-in-isolated-storage.md)|Yalıtılmış depolama dosyalarının ve dizinlerinin nasıl silindiğini gösterir.|
|[Dosya ve Akış G/Ç'si](../../../docs/standard/io/index.md)|Zaman uyumlu ve zaman uyumsuz dosya ve veri akışı erişimini nasıl gerçekleştireceğinizi açıklar.|

<a name="reference"></a>

## <a name="reference"></a>Başvuru

- <xref:System.IO.IsolatedStorage.IsolatedStorage?displayProperty=nameWithType>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream?displayProperty=nameWithType>

- <xref:System.IO.IsolatedStorage.IsolatedStorageScope?displayProperty=nameWithType>
