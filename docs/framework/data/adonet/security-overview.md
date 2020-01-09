---
title: Güvenliğe genel bakış
ms.date: 03/30/2017
ms.assetid: 33e09965-61d5-48cc-9e8c-3b047cc4f194
ms.openlocfilehash: 8a036a40d2b1728f39037018c3672551b8b67bd9
ms.sourcegitcommit: 8c99457955fc31785b36b3330c4ab6ce7984a7ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/29/2019
ms.locfileid: "75545028"
---
# <a name="security-overview"></a>Güvenliğe genel bakış

Uygulamanın güvenliğini sağlamak, devam eden bir işlemdir. Bir geliştiricinin bir uygulamanın tüm saldırılardan güvenli olduğunu garanti edebildiği bir nokta olmaz. Bu, yeni teknolojilerin ne tür gelecekte yeni teknolojiler sunabileceğini tahmin etmek olanaksızdır. Bunun tersine, bir sistemde hiç kimse henüz keşfedilmiş (veya yayımlanmadığı) güvenlik kusuru yok veya var olmadığı anlamına gelmez. Projenin tasarım aşamasında güvenlik planlaması yapmanız ve güvenliğin uygulamanın kullanım ömrü boyunca nasıl bakımının planlanacağını planlamanız gerekir.

## <a name="design-for-security"></a>Güvenlik için tasarım
 Güvenli uygulamalar geliştirmenin en büyük sorunlarından biri, güvenlik genellikle bir proje kod tamamlandıktan sonra uygulamaya yönelik bir şeydir. Bir uygulamayı güvenli hale getirmeye yönelik olarak düşündüler verilmediği için, bilinemeyebilir 'teki bir uygulamaya güvenlik, güvenli olmayan uygulamalara yönelik olarak oluşturulmamalıdır.

 Son dakikalık güvenlik uygulamaları, yeni kısıtlamalar kapsamında yazılım kesildiği veya beklenmeyen işlevlere uyum sağlamak için yeniden yazılması gerektiği için daha fazla hataya yol açar. Düzeltilen kodun her satırı, yeni bir hata tanıtma olasılığını içerir. Bu nedenle, yeni özelliklerin geliştirilmesinde ilerlemeniz için geliştirme sürecinin başlarında güvenliği göz önünde bulundurmanız gerekir.

### <a name="threat-modeling"></a>Tehdit Modelleme
 Kullanıma sunulan tüm olası saldırıları anlamadığınız takdirde bir sistemi saldırılara karşı koruyamazsınız. *Tehdit modelleme*olarak adlandırılan güvenlik tehditlerini değerlendirme işlemi, ADO.net uygulamanızda güvenlik ihlallerinin oluşma olasılığını ve kollerini belirlemede gereklidir.

 Tehdit modelleme üç üst düzey adımdan oluşur: duyuru görünümünü anlama, sistemin güvenliğini belirleme ve tehditleri belirleme.

 Tehdit modellemesi, en önemli verileri kullanıma sunduklarında, uygulamanızdaki güvenlik açıklarını en çok tehlikeli olanları bulmaya yönelik yinelemeli bir yaklaşımdır. Güvenlik açıklarını tanımladıktan sonra, bunları önem derecesine göre derecelendirdikten sonra tehditleri sayaca yönelik öncelikli bir karşı önlem kümesi oluşturursunuz.

Daha fazla bilgi için aşağıdaki kaynaklara bakın:

|Kaynak|Açıklama|
|--------------|-----------------|
|Güvenlik Mühendisliği portalındaki [tehdit modelleme](https://www.microsoft.com/securityengineering/sdl/threatmodeling) sitesi|Bu sayfadaki kaynaklar, tehdit modelleme sürecini anlamanıza yardımcı olur ve kendi uygulamalarınızı güvenli hale getirmek için kullanabileceğiniz tehdit modellerini derleyebilirsiniz|

## <a name="the-principle-of-least-privilege"></a>En az ayrıcalık Ilkesi
 Uygulamanızı tasarladığınızda, yapılandırdığınızda ve dağıttığınızda, uygulamanızın saldırıya uğradığını varsaymalısınız. Bu saldırılar genellikle kodu çalıştıran kullanıcının izinleriyle yürütülen kötü amaçlı koddan gelir. Diğerleri, bir saldırgan tarafından yararlanılabilen iyi şekilde kod içerebilir. Güvenliği planlarken, her zaman en kötü durum senaryosunun gerçekleşeceğini kabul eder.

 Kullanabileceğiniz bir sayaç ölçüsü, en az ayrıcalıkla çalışırken kodunuzun etrafında çok sayıda duvarı kullanmayı denemenize olanak tanır. En az ayrıcalık ilkesi, verilen ayrıcalıkların, işin tamamlanması için gereken en kısa süre için gerekli olan en az kod miktarına verilmesi gerektiğini belirtir.

 Güvenli uygulamalar oluşturmak için en iyi yöntem, hiçbir izin olmadan ve sonra gerçekleştirilen belirli bir görev için en dar izinleri ekleyecek şekilde başlatılır. Buna karşılık, tüm izinlerle başlayıp, her birinin reddedilmesi, güvenli olmayan uygulamalara, gerekenden daha fazla izin verilmesinin istenmeden daha fazla izin verilmesinin mevcut olmasından kaynaklanır.

Uygulamalarınızın güvenliğini sağlama hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın:

|Kaynak|Açıklama|
|--------------|-----------------|
|[Uygulamalarının Güvenliğini Sağlama](/visualstudio/ide/securing-applications)|Genel güvenlik konularına bağlantılar içerir. Ayrıca dağıtılmış uygulamalar, Web uygulamaları, mobil uygulamalar ve masaüstü uygulamalarının güvenliğini sağlamaya yönelik konulara bağlantılar içerir.|

## <a name="code-access-security-cas"></a>Kod Erişimi Güvenliği (CAS)

Kod erişim güvenliği (CAS), kodun korumalı kaynaklara ve işlemlere erişimi sınırlamaya yardımcı olan bir mekanizmadır. .NET Framework, CAS aşağıdaki işlevleri gerçekleştirir:

- Çeşitli sistem kaynaklarına erişme hakkını temsil eden izinleri ve izin kümelerini tanımlar.

- Yöneticilerin, izin kümelerini kod gruplarıyla (kod grupları) ilişkilendirerek güvenlik ilkesini yapılandırmasına olanak sağlar.

- Kodun çalışması için gereken izinleri ve olması gereken izinleri ve kodun hiçbir şekilde sahip olması gereken izinleri belirtmesini sağlar.

- Kod tarafından istenen izinlere ve güvenlik ilkesi tarafından izin verilen işlemlere göre yüklenen her derleme için izin verir.

- Kodun çağıranlarının belirli izinlere sahip olduğunu talep etmesini sağlar.

- Kod çağıranlarının dijital imzaya sahip olmasını talep etmesini sağlar ve böylece yalnızca belirli bir kuruluştan veya siteden gelen çağıranların korunan kodu aramasını sağlar.

- Çağrı yığınında her çağıranın verilen izinlerini çağıranların sahip olması gereken izinlerle karşılaştırarak çalışma zamanında kod kısıtlamalarını zorlar.

Bir saldırının başarılı olması durumunda oluşabilecek hasar miktarını en aza indirmek için, kodunuz için yalnızca işlerini yapmak için ihtiyaç duymakta olan kaynaklara erişim veren bir güvenlik bağlamı seçin ve daha fazla bilgi edinebilirsiniz.

Daha fazla bilgi için aşağıdaki kaynaklara bakın:

|Kaynak|Açıklama|
|--------------|-----------------|
|[Kod Erişimi Güvenliği ve ADO.NET](code-access-security.md)|Bir ADO.NET uygulamasının perspektifinden kod erişimi güvenliği, rol tabanlı güvenlik ve kısmen güvenilen ortamlar arasındaki etkileşimleri açıklar.|
|[Kod erişim güvenliği](../../misc/code-access-security.md)|.NET Framework CA 'ları açıklayan ek konuların bağlantılarını içerir.|

## <a name="database-security"></a>Veritabanı Güvenliği

En az ayrıcalık ilkesi de veri kaynağınız için geçerlidir. Veritabanı güvenliği için bazı genel yönergeler şunları içerir:

- Olası en düşük ayrıcalıklara sahip hesaplar oluşturun.

- Kullanıcıların yalnızca kod çalışmasını sağlamak için yönetim hesaplarına erişmesine izin vermeyin.

- İstemci uygulamalarına sunucu tarafı hata iletileri döndürme.

- Hem istemcide hem de sunucuda tüm girişleri doğrulayın.

- Parametreli komutları kullanın ve dinamik SQL deyimlerden kaçının.

- Herhangi bir güvenlik ihlallerine uyarı almak için kullandığınız veritabanı için güvenlik denetimini ve günlük kaydını etkinleştirin.

Daha fazla bilgi için aşağıdaki kaynaklara bakın:

|Kaynak|Açıklama|
|--------------|-----------------|
|[SQL Server Güvenliği](./sql/sql-server-security.md)|SQL Server hedef alan güvenli ADO.NET uygulamaları oluşturmaya yönelik rehberlik sağlayan uygulama senaryolarında SQL Server güvenliğe genel bir bakış sağlar.|
|[Veri erişimi stratejileri için öneriler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))|Verilere erişmek ve veritabanı işlemlerini gerçekleştirmek için öneriler sağlar.|

## <a name="security-policy-and-administration"></a>Güvenlik Ilkesi ve yönetimi

Kod erişimi güvenliği (CAS) ilkesini yanlış yönetmek, güvenlik zayıflığı oluşturabilir. Bir uygulama dağıtıldıktan sonra güvenlik izleme teknikleri kullanılmalıdır ve yeni tehditler ortaya çıktı olarak değerlendirilir.

Daha fazla bilgi için aşağıdaki kaynaklara bakın:

|Kaynak|Açıklama|
|--------------|-----------------|
|[Güvenlik Ilkesi yönetimi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100))|Güvenlik ilkesi oluşturma ve yönetme hakkında bilgi sağlar.|
|[En Iyi Güvenlik Ilkesi uygulamaları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sa4se9bc(v=vs.100))|Güvenlik ilkesini yönetmeyi açıklayan bağlantılar sağlar.|

## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](securing-ado-net-applications.md)
- [.NET 'te güvenlik](../../../standard/security/index.md)
- [SQL Server Güvenliği](./sql/sql-server-security.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
