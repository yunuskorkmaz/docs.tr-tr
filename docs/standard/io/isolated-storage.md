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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: df5601fb0dbf088bd28da91f7279a330f2bb3494
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170693"
---
# <a name="isolated-storage"></a>Yalıtılmış Depolama
<a name="top"></a> Masaüstü uygulamaları için yalıtılmış depolama, kaydedilmiş verilerle bir birlikte ilişkili bir kodun standartlaştırılmış yolları tanımlayarak yalıtım ve güvenlik sağlayan bir veri depolama mekanizmasıdır. Standart hale getirme başka yararlar da sağlar. Yöneticiler yalıtılmış depolamayı değiştirecek araçları kullanarak dosya depolama alanını yapılandırabilir, güvenlik ilkelerini ayarlayabilir ve kullanılmayan verileri silebilir. Yalıtılmış depolama ile kodunuz dosya sistemindeki güvenli konumları belirtmek için benzersiz yollara ihtiyaç duymaz ve veriniz yalnızca yalıtılmış depolama erişimi olan diğer uygulamalardan korunur. Bir uygulamanın depo alanının nerede olduğunu belirten sabit kodlu bilgi gerekli değildir.

> [!IMPORTANT]
> Yalıtılmış depolama için uygun değildir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar. Bunun yerine, uygulama verisi sınıflarını kullanın `Windows.Storage` yerel verileri ve dosyaları depolamak için Windows çalışma zamanı API içinde bulunan ad alanları. Daha fazla bilgi için [uygulama verileri](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) Windows geliştirme Merkezi'nde.

Bu konu aşağıdaki bölümleri içermektedir:

- [Veri bölmeleri ve depoları](#data_compartments_and_stores)

- [Ayrık depolama kotaları](#quotas)

- [Güvenli erişim](#secure_access)

- [İzin verilen kullanım ve güvenlik riskleri](#allowed_usage)

- [Ayrık depolama konumları](#isolated_storage_locations)

- [Oluşturma, numaralandırma ve yalıtılmış depolama siliniyor](#isolated_storage_tasks)

- [Ayrık depolama birimi senaryoları](#scenarios_for_isolated_storage)

- [İlgili Konular](#related_topics)

- [Başvuru](#reference)

<a name="data_compartments_and_stores"></a>

## <a name="data-compartments-and-stores"></a>Veri Bölmeleri ve Depoları

Bir uygulama bir dosya içinde veri depoladığında, depolama konumunun başka bir uygulama tarafından öğrenilme ve bu nedenle bozulma olasılığını en aza indirmek için dosya adı ve depolama konumu dikkatle seçilmelidir. Bu sorunları yönetecek standart bir sistem olmadığında, depolama çakışmalarını en aza indiren geçici teknikler karmaşık olabilir ve sonuçları güvenilir olmayabilir.

Yalıtılmış depolama ile veri her zaman kullanıcıya ve derlemeye göre yalıtılır. Derlemenin başlangıç noktası veya tanımlayıcı adı gibi kimlik bilgileri derlemenin kimliğini belirler. Veri ayrıca benzer kimlik bilgileri kullanarak uygulama etki alanına göre de yalıtılabilir.

Yalıtılmış depolama kullandığınızda, uygulamanız veriyi kodun yayımcısı veya imzası gibi bir bilgi ile ilişkili benzersiz bir veri bölmesine kaydeder. Veri bölmesi belirli bir depolama konumu değildir, bir soyutlamadır, ve depo denen verinin tutulduğu gerçek dizin konumlarını içeren bir veya daha fazla yalıtılmış depolama dosyasından oluşur. Örneğin, bir uygulamanın kendisiyle ilişkili bir veri bölmesi olabilir, ve dosya sistemindeki bir dizin o uygulama için veriyi tutan gerçek depoyu uygulayabilir. Depoya kaydedilen veri kullanıcı tercih bilgisinden uygulama durumuna kadar herhangi türde bir veri olabilir. Geliştirici için, veri bölmesinin konumu saydamdır. Depolar genellikle istemcide bulunur, ancak bir sunucu uygulaması yalıtılmış depoları kullanarak belirli bir kullanıcı için veri depolayabilir. Yalıtılmış depolama ayrıca bir kullanıcının gezici profili ile bir sunucu üzerinde bilgi tutarak o bilginin gezici kullanıcıyla birlikte hareket etmesini sağlayabilir.

<a name="quotas"></a>

## <a name="quotas-for-isolated-storage"></a>Ayrık Depolama Kotaları

Bir kota, kullanılabilen yalıtılmış depolama miktarındaki bir sınırdır. Kota dosya alanı baytlarının yanı sıra depodaki dizin ve diğer bilgilerle ilgili ek yükü de içerir. Yalıtılmış depolama birimi kullanılarak ayarlanan depolama sınırları olan izin kotalarını kullanır <xref:System.Security.Permissions.IsolatedStoragePermission> nesneleri. Eğer kotayı aşan veri yazma denerseniz bir <xref:System.IO.IsolatedStorage.IsolatedStorageException> özel durumu oluşturulur.  .NET Framework Yapılandırma Aracı (Mscorcfg.msc) kullanarak değiştirilebilen güvenlik ilkesi koda hangi izinlerin verildiğini belirler. Verilmiş kod <xref:System.Security.Permissions.IsolatedStoragePermission> hiçbir daha fazla depolama alanı kullanımıyla kısıtlıdır <xref:System.Security.Permissions.IsolatedStoragePermission.UserQuota%2A> özelliği sağlar. Ancak, kod farklı kullanıcı kimlikleri sunarak izin kotalarını atlayabileceği için, izin kotaları kod davranışı için kesin bir sınır yerine daha çok kodun nasıl davranacağı üzerine bir kılavuz olarak görev görür.

Kotalar gezici depolarda uygulanmaz. Bu nedenle kodun bunu kullanabilmesi için biraz daha yüksek bir izin düzeyi gerekir. Numaralandırma değerlerinin <xref:System.Security.Permissions.IsolatedStorageContainment.AssemblyIsolationByRoamingUser> ve <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByRoamingUser> gezici bir kullanıcı için yalıtılmış depolama kullanımı iznini belirtin.

<a name="secure_access"></a>

## <a name="secure-access"></a>Güvenli Erişim

Yalıtılmış depolama kullanımı kısmen güvenilir uygulamaların bilgisayarın güvenlik ilkesi tarafından kontrol edilerek veri depolamasını sağlar. Bu özellikle bir kullanıcının dikkatli olarak çalıştırmak isteyeceği indirilen bileşenler için kullanışlıdır. Güvenlik ilkesi, standart I/O mekanizmalarını kullanarak dosya sistemine eriştiğinizde bu tür kod iznini nadiren verir. Ancak varsayılan olarak; yerel bilgisayardan, yerel bir ağdan veya Internet üzerinden çalıştırılan koda yalıtılmış depolama hakkı verilir.

Yöneticiler uygun olan güven düzeyine göre bir uygulamanın veya kullanıcının ne kadar yalıtılmış depolama alanına sahip olacağını sınırlayabilir. Ek olarak, yöneticiler bir kullanıcının kalıcı verilerini tamamen kaldırabilir. Oluşturma veya yalıtılmış depolamaya erişmek için kod uygun verilmelidir <xref:System.Security.Permissions.IsolatedStorageFilePermission> izni.

Yalıtılmış depolamaya erişmek için, kod tüm gerekli yerel platform işletim sistemi haklarına sahip olmalıdır. Hangi kullanıcıların dosya sistemini kullanmaya hakkı olduğunu kontrol eden erişim denetim listeleri (ACL) sağlanmalıdır. .NET Framework uygulamaları, platforma özel kimliğe bürünme işlemi gerçekleştirmedikleri sürece yalıtılmış depolamaya erişmek için işletim sistemi haklarına sahiptir. Bu durumda, uygulama kimliğine bürünülen kullanıcının yalıtılmış depolamaya erişmek için gerekli uygun işletim sistemi haklarına sahip olduğundan emin olmakta sorumludur. Bu erişim, internetten çalıştırılan veya indirilen kodun belirli bir kullanıcı ile ilgili depolama alanında okuma ve yazma işlemleri yapabilmesi için kullanışlı bir yol sağlar.

Yalıtılmış Depolama erişimi denetlemek için ortak dil çalışma zamanı kullanan <xref:System.Security.Permissions.IsolatedStorageFilePermission> nesneleri. Her nesne aşağıdaki değerleri belirten özelliklere sahiptir:

- İzin verilen kullanım, izin verilen erişim türünü belirtir. Üyeleri değerler <xref:System.Security.Permissions.IsolatedStorageContainment> sabit listesi. Bu değerler hakkında daha fazla bilgi için, sonraki bölümdeki tabloya bakın.

- Depo kotası, önceki bölümde anlatıldığı gibidir.

Çalışma zamanı <xref:System.Security.Permissions.IsolatedStorageFilePermission> kod önce bir depoyu açmayı denediğinde izni. Ne kadar kodun güvenilir olduğuna göre bu izni vermek etkinleştirilip etkinleştirilmeyeceğini belirler. İzin verilirse, izin verilen kullanım ve depo kotası değerleri güvenlik ilkesi ve kodun isteği tarafından belirlenir <xref:System.Security.Permissions.IsolatedStorageFilePermission>. Güvenlik ilkesi .Net Framework Yapılandırma Aracı (Mscorcfg.msc) kullanılarak ayarlanır. Çağrı yığınındaki tüm çağıranlar, her çağıranın en azından uygun izin verilen kullanıma sahip olduğundan emin olmak için kontrol edilir. Çalışma zamanı ayrıca dosyanın kaydedileceği depoyu açan veya oluşturan koda uygulanan kotayı da kontrol eder. Eğer bu koşullar sağlanırsa, izin verilir. Kota, depoya yazılan her dosyada tekrar denetlenir.

Uygulama kodunun izin istemesi, ortak dil çalışma zamanı çünkü gerekli değildir <xref:System.Security.Permissions.IsolatedStorageFilePermission> güvenlik ilkesini temel alarak uygundur. Ancak, uygulamanız gereken belirli izinleri istemek için iyi nedenler vardır <xref:System.Security.Permissions.IsolatedStorageFilePermission>.

<a name="allowed_usage"></a>

## <a name="allowed-usage-and-security-risks"></a>İzin Verilen Kullanım ve Güvenlik Riskleri

Tarafından belirtilen izin verilen kullanım <xref:System.Security.Permissions.IsolatedStorageFilePermission> olduğu kod izin oluşturma ve yalıtılmış depolama kullanma derecesini belirler. Aşağıdaki tablo izinde belirtilen izin verilen kullanımın hangi yalıtım türlerine karşılık geldiğini gösterir ve her izin verilen kullanım ile ilişkili güvenlik risklerini özetler.

|İzin verilen kullanım|Yalıtım türleri|Güvenlik etkisi|
|-------------------|---------------------|---------------------|
|<xref:System.Security.Permissions.IsolatedStorageContainment.None>|Hiçbir yalıtılmış depolama kullanımına izin verilmez.|Güvenlik etkisi yoktur.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser>|Kullanıcı, etki alanı ve derlemeye göre yalıtım Her derlemenin etki alanı içinde ayrı bir alt deposu bulunur. Bu izni kullanan depolar örtülü olarak bilgisayara göre de yalıtılır.|Bu izin düzeyi kaynakları yetkisiz aşırı kullanıma açık bırakır, ancak uygulanan kotalar bunu zorlaştırır. Buna hizmet reddi saldırısı denir.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByRoamingUser>|Aynı `DomainIsolationByUser`, ancak depolama, gezici kullanıcı profilleri etkinleştirildiyse ve kotalar uygulanmıyorsa gezecek olan bir konuma kaydedilir.|Kotaların devre dışı bırakılması gerektiği için, depo kaynakları bir hizmet reddi saldırısına karşı daha savunmasızdır.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.AssemblyIsolationByUser>|Kullanıcı ve derlemeye göre yalıtım Bu izni kullanan depolar örtülü olarak bilgisayara göre de yalıtılır.|Kotalar hizmet reddi saldırısını önlemeye yardımcı olmak için bu düzeyde uygulanır. Başka bir etki alanındaki aynı derleme bu depoya erişebilir ve bu nedenle uygulamalar arasında bilgi sızma olasılığı bulunur.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.AssemblyIsolationByRoamingUser>|Aynı `AssemblyIsolationByUser`, ancak depolama, gezici kullanıcı profilleri etkinleştirildiyse ve kotalar uygulanmıyorsa gezecek olan bir konuma kaydedilir.|Olarak aynı `AssemblyIsolationByUser`, ancak kotalar olmadığı bir hizmet reddi saldırısı riskini artırır.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser>|Kullanıcıya göre yalıtım. Genellikle yalnızca yönetici veya hata ayıklama araçları bu izin düzeyini kullanır.|Bu izinle olan erişim, kodun bir kullanıcının yalıtılmış depolama dosyalarını ve dizinlerini görüntülemesine ve silmesine olanak verir (derleme yalıtımına bakmaksızın). Riskler, bilgi sızması ve veri kaybını içerir ancak bunlarla sınırlı değildir.|
|<xref:System.Security.Permissions.IsolatedStorageContainment.UnrestrictedIsolatedStorage>|Tüm kullanıcılar, etki alanları ve derlemelere göre yalıtım. Genellikle yalnızca yönetici veya hata ayıklama araçları bu izin düzeyini kullanır.|Bu izin tüm kullanıcılar için tüm yalıtılmış depoların açığa çıkma olasılığını oluşturur.|

<a name="isolated_storage_locations"></a>

## <a name="isolated-storage-locations"></a>Ayrık Depolama Konumları

Bazen yalıtılmış depolamaya yapılan bir değişikliği işletim sisteminin dosya sistemini kullanarak doğrulamak yararlıdır. Ayrıca yalıtılmış depolama dosyalarının konumunu da bilmek isteyebilirsiniz. Bu konum işletim sistemine göre değişir. Aşağıdaki tablo bazı yaygın işletim sistemleri için yalıtılmış depolamanın bulunduğu kök konumlarını gösterir. Bu kök konumu altında Microsoft\IsolatedStorage dizinlerine bakın. Dosya sisteminde yalıtılmış depolamayı görmek için klasör ayarlarını değiştirerek gizli dosyaları ve klasörleri görünür yapmanız gerekir.

|İşletim sistemi|Dosya sistemindeki konumu|
|----------------------|-----------------------------|
|Windows 2000, Windows XP, Windows Server 2003 (Windows NT 4.0'dan yükseltme)|Gezinme etkinleştirilmiş depolar =<br /><br /> \<SYSTEMROOT > \Profiles\\< kullanıcı\>\Application veri<br /><br /> Gezici olmayan depolar =<br /><br /> \<SYSTEMROOT > \Profiles\\< kullanıcı\>\Local veri|
|Windows 2000 - temiz yükleme (ve Windows 98 ve Windows NT 3.51'den yükseltme)|Gezinme etkinleştirilmiş depolar =<br /><br /> \<SYSTEMDRIVE > \Documents ve ayarları\\< kullanıcı\>\Application veri<br /><br /> Gezici olmayan depolar =<br /><br /> \<SYSTEMDRIVE > \Documents ve ayarları\\< kullanıcı\>\Local veri|
|Windows XP, Windows Server 2003 - temiz yükleme (Windows 2000 ve Windows 98'den yükseltme)|Gezinme etkinleştirilmiş depolar =<br /><br /> \<SYSTEMDRIVE > \Documents ve ayarları\\< kullanıcı\>\Application veri<br /><br /> Gezici olmayan depolar =<br /><br /> \<SYSTEMDRIVE > \Documents ve ayarları\\< kullanıcı\>\Local veri|
|[!INCLUDE[win8](../../../includes/win8-md.md)], Windows 7, Windows Server 2008, Windows Vista|Gezinme etkinleştirilmiş depolar =<br /><br /> \<SYSTEMDRIVE > \Users\\< kullanıcı\>\AppData\Roaming<br /><br /> Gezici olmayan depolar =<br /><br /> \<SYSTEMDRIVE > \Users\\< kullanıcı\>\AppData\Local|

<a name="isolated_storage_tasks"></a>

## <a name="creating-enumerating-and-deleting-isolated-storage"></a>Ayrık Depolama Birimi Oluşturma, Numaralandırma ve Silme

.NET Framework üç sınıf sağlar <xref:System.IO.IsolatedStorage> yalıtılmış depolamayı içeren görevleri gerçekleştirmenize yardımcı olması için ad alanı:

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>, öğesinden türetilen <xref:System.IO.IsolatedStorage.IsolatedStorage?displayProperty=nameWithType> ve depolanan derleme ve uygulama dosyalarının temel yönetimini sağlar. Örneği <xref:System.IO.IsolatedStorage.IsolatedStorageFile> sınıfı, dosya sisteminde bulunan tek bir depoyu temsil eder.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> öğesinden türetilen <xref:System.IO.FileStream?displayProperty=nameWithType> ve bir depodaki dosyalara erişim sağlar.

- <xref:System.IO.IsolatedStorage.IsolatedStorageScope> oluşturun ve uygun yalıtım türüyle bir depo seçin olanak sağlayan bir sabit listesidir.

Yalıtılmış depolama sınıfları, yalıtılmış depoları oluşturmanızı, numaralandırmanızı ve silmenizi sağlar. Bu görevleri gerçekleştirmek için yöntemleri aracılığıyla sunulur <xref:System.IO.IsolatedStorage.IsolatedStorageFile> nesne. Bazı işlemler olmasını gerektiren <xref:System.Security.Permissions.IsolatedStorageFilePermission> izni yalıtılmış depolamayı yönetme hakkını temsil eder; dosya veya dizine erişmek için işletim sistemi haklarına sahip olmanız gerekebilir.

Yaygın yalıtılmış depolama görevlerini gösteren örnekler dizi için listelenen nasıl yapılır konularına bakın [ilgili konular](#related_topics).

<a name="scenarios_for_isolated_storage"></a>

## <a name="scenarios-for-isolated-storage"></a>Ayrık Depolama Birimi Senaryoları

Yalıtılmış depolama, aşağıdaki dört senaryo da dahil olmak üzere pek çok durumda kullanışlıdır:

- İndirilen denetimler. İnternetten indirilen yönetilen kod denetimlerinin normal I/O sınıflarıyla hard diske yazmasına izin verilmez, ancak yalıtılmış depolama kullanarak kullanıcıların ayarlarını ve uygulama durumlarını kalıcı olarak tutabilirler.

- Paylaşılan bileşen depolama. Uygulamalar arasında paylaşılan denetimler, veri depolarına kontrollü erişim sağlamak için yalıtılmış depolama kullanabilir.

- Sunucu depolama alanı. Sunucu uygulamaları yalıtılmış depolamayı kullanarak uygulamaya istekte bulunan büyük sayıdaki kullanıcılar için tek tek depo sağlayabilir. Yalıtılmış depolama her zaman kullanıcıya göre tutulduğu için, sunucu isteği yapan kullanıcının kimliğine bürünmelidir. Bu durumda, veriler uygulamanın kullanıcıları arasında ayrım yapmak için uygulamanın kullandığı aynı kimlik sorumlu kimliğine göre yalıtılır.

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
|[Nasıl yapılır: Yalıtılmış depolama için depoları alma](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)|Kullanarak bir örnek sağlar <xref:System.IO.IsolatedStorage.IsolatedStorageFile> kullanıcı ve derlemeye göre yalıtılan bir depo almak için sınıf.|
|[Nasıl yapılır: Yalıtılmış depolama için depoları numaralandırma](../../../docs/standard/io/how-to-enumerate-stores-for-isolated-storage.md)|Nasıl kullanılacağını gösterir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> kullanıcının tüm yalıtılmış deposunun boyutunu hesaplamak için yöntemi.|
|[Nasıl yapılır: Yalıtılmış depolamadaki depoları silme](../../../docs/standard/io/how-to-delete-stores-in-isolated-storage.md)|Nasıl kullanılacağını gösterir <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A?displayProperty=nameWithType> yalıtılmış depoları silmek için iki farklı yolla yöntemi.|
|[Nasıl yapılır: Dolu yalıtılmış depolama ile alan çıkış koşullarını öngörme](../../../docs/standard/io/how-to-anticipate-out-of-space-conditions-with-isolated-storage.md)|Bir yalıtılmış depodaki kalan alanın nasıl ölçüldüğünü gösterir.|
|[Nasıl yapılır: Yalıtılmış depolamada dosya ve dizinler oluşturma](../../../docs/standard/io/how-to-create-files-and-directories-in-isolated-storage.md)|Bir yalıtılmış depoda dosyalar ve dizinler oluşturma ile ilgili bazı örnekler sağlar.|
|[Nasıl yapılır: Yalıtılmış depolamada mevcut dosya ve dizinleri bulma](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md)|Yalıtılmış depolamada dizin yapısının ve dosyaların nasıl okunduğunu gösterir.|
|[Nasıl yapılır: Okuma ve yalıtılmış depolamadaki dosyaları yazma](../../../docs/standard/io/how-to-read-and-write-to-files-in-isolated-storage.md)|Bir yalıtılmış depolama dosyasına dize yazmak ve ardından geri okumak ile ilgili bir örnek sağlar.|
|[Nasıl yapılır: Dosya ve dizinleri yalıtılmış depolamadaki Sil](../../../docs/standard/io/how-to-delete-files-and-directories-in-isolated-storage.md)|Yalıtılmış depolama dosyalarının ve dizinlerinin nasıl silindiğini gösterir.|
|[Dosya ve Akış G/Ç'si](../../../docs/standard/io/index.md)|Zaman uyumlu ve zaman uyumsuz dosya ve veri akışı erişimini nasıl gerçekleştireceğinizi açıklar.|

<a name="reference"></a>

## <a name="reference"></a>Başvuru

- <xref:System.IO.IsolatedStorage.IsolatedStorage?displayProperty=nameWithType>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream?displayProperty=nameWithType>

- <xref:System.IO.IsolatedStorage.IsolatedStorageScope?displayProperty=nameWithType>
