---
title: Güvenlik Overview2
ms.date: 03/30/2017
ms.assetid: 33e09965-61d5-48cc-9e8c-3b047cc4f194
ms.openlocfilehash: 0b5b86aad2365c76351ff748228826ba703223dc
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56091805"
---
# <a name="security-overview"></a>Güvenlik Genel Bakış
Bir uygulamanın güvenliğini sağlama, devam eden bir işlem bulunmaktadır. Hiçbir zaman bir geliştirici gelecekteki saldırıları yeni teknolojileri tür zekadan yararlanabilmesini tahmin etmek mümkün olduğundan, uygulamanın tüm saldırılara karşı güvenli olduğu garanti edebilir bir noktası olacaktır. Buna karşılık, hiç kimse sahip olduğu bir sistemde henüz bulunan (veya yayımlanmış) güvenlik açıkları gelmez hiçbiri mevcut veya var olabilir. Yanı sıra proje tasarım aşaması sırasında güvenlik için planlama, uygulama ömrü boyunca güvenlik nasıl korunur planlamak gerekir.  
  
## <a name="design-for-security"></a>Güvenlik için tasarlama  
 Güvenli uygulamalar geliştirme üzerine en büyük sorunlardan biri güvenlik genellikle akla, bir proje kodu tamamlandıktan sonra uygulamak için bir şey olmasıdır. Uygulama güvenli kılan için küçük bir düşünce verilmiş olduğundan güvenlik uygulamaya gizliliğe oluşturma değil, güvenli olmayan uygulamaları yol açar.  
  
 Son dakika güvenlik uygulama, daha fazla hata için yeni kısıtlamalar altında yazılım sonu olarak müşteri adayları veya beklenmeyen işlevselliği uyum sağlayacak şekilde yazılması gerekir. Her değiştirilen kod satırı, yeni bir hata ile tanışın olasılığını içerir. Böylece dağıtımınızla birlikte yeni özellikler geliştirmeye devam edebilirsiniz, bu nedenle başlarında geliştirme süreci güvenlik düşünmelisiniz.  
  
### <a name="threat-modeling"></a>Tehdit modelleme  
 İçin sunulan tüm olası saldırıları anlamadan bir sistem saldırılara karşı koruyamaz. Güvenlik tehditlerini değerlendirme işleminin adlı *tehdit modelleme*, olasılığını ve güvenlik ihlallerini ADO.NET uygulamanızdaki etkilerini belirlemek gereklidir.  
  
 Tehdit modelleme, üst düzey üç adımdan oluşur: anlama saldırganın görünümü, sistem güvenliğini characterizing ve tehditleri belirleme.  
  
 Tehdit modelleme, çünkü bunlar en hassas verileri ortaya çıkaran, en tehlikeli bulmak için uygulamanızın güvenlik açıkları değerlendirmek için yinelemeli bir yaklaşımdır. Güvenlik açıklarını tanımlamak sonra bunları önem sırasına göre derecelendirmek ve sayacı ile tehditlere karşı önlemler öncelikli bir dizi oluşturun.  
  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Tehdit modelleme](https://go.microsoft.com/fwlink/?LinkId=98353) MSDN güvenlik Geliştirici merkezinde site|Bu sayfadaki kaynaklardan işlem modelleme tehdit anlama ve kendi uygulamalarınızı güvenli hale getirmek için kullanabileceğiniz tehdit modelleri oluşturmanıza yardımcı olur|  
  
## <a name="the-principle-of-least-privilege"></a>En düşük öncelik ilkesini  
 Tasarlamasına, hazırlamasına ve uygulamanızı dağıtmak, uygulamanız saldırıya olduğunu varsaymalısınız. Genellikle bu saldırıları kodu çalıştıran kullanıcı izinleriyle yürüten kötü amaçlı kod gelir. Diğerleri, saldırgan tarafından kötü amaçlı iyi niyetli kod ile gönderilebilir. Güvenlik planlarken, her zaman iki katına senaryo meydana gelir varsayılır.  
  
 En az ayrıcalık ile çalıştırarak mümkün olduğunca çok duvarlarının kodunuzu etrafında erect, uygulamalarını bir tamamlayıcı ölçü denemektir. En düşük öncelik ilkesini herhangi bir ayrıcalık kod kısa süre işin tamamlanması için gerekli olan için gerekli az miktarda verilmesi gerektiğini söyler.  
  
 Güvenli uygulamalar oluşturmak için en iyi hiçbir izinlerle hiç başlatmak ve sonra gerçekleştirilen belirli görev için en düşük izinleri eklemektir. Bunun aksine, tüm izinleri ile başlayan ve ardından tek olanları reddetme müşteri adayları test edin ve daha fazla izne gerekli kasıtsız olarak verme güvenlik açıkları olabilir çünkü korumak zor olan güvenli uygulamalar için.  
  
 Uygulamalarınızın güvenliğini sağlama konusunda daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Uygulamalarının Güvenliğini Sağlama](/visualstudio/ide/securing-applications)|Genel güvenlik konulara bağlantılar içerir. Ayrıca, dağıtılmış uygulamalar, Web uygulamaları, mobil uygulamalar ve masaüstü uygulamalarının güvenliğini sağlamak için konulara bağlantılar içerir.|  
  
## <a name="code-access-security-cas"></a>Kod Erişimi Güvenliği (CAS)  
 Kod erişimi güvenliği (CAS) kod korumalı kaynaklara ve işlemlere sahip olan erişimini sınırlamaya yardımcı olan bir mekanizmadır. .NET Framework, CA'ları aşağıdaki işlevleri gerçekleştirir:  
  
-   İzinler ve çeşitli sistem kaynaklarına erişim hakkı temsil eden izin kümeleri tanımlar.  
  
-   İzin kümeleri grupları (kod gruplarını) kod ile ilişkilendirerek güvenlik ilkesini yapılandırmak yöneticilerin sağlar.  
  
-   Sahip olmak yararlı olabilecek izinleri yanı sıra gerektirir çalıştırmak için izinleri istemek kod sağlar ve kodu asla olmalıdır hangi izinleri belirtir.  
  
-   Kod tarafından istenen izinleri ve güvenlik ilkesi tarafından izin verilen işlemler temel yüklendiğinde, her derleme için izinleri verir.  
  
-   İsteğe bağlı çağrıda bulunanların belirli izinlere sahip olduğunuzu kodu sağlar.  
  
-   Böylece korunan kod çağırmak yalnızca belirli bir kuruluş veya sitesinde arayanlara izin vererek çağıranlarını bir dijital imza sahip isteğe bağlı kod sağlar.  
  
-   Kod üzerindeki kısıtlamalar, verilen izinler, Arayanların olmalıdır izinlerle çağrı yığınında her arayanın karşılaştırarak, çalışma zamanında zorlar.  
  
 Saldırının başarılı olursa oluşabilecek zarar miktarını en aza indirmek için yalnızca kendi işlerinizi tamamlandı ve artık gerekli kaynaklara erişim veren kodunuz için bir güvenlik bağlamı'nı seçin.  
  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Kod Erişimi Güvenliği ve ADO.NET](../../../../docs/framework/data/adonet/code-access-security.md)|Kod erişimi güvenliği, rol tabanlı güvenlik ve ADO.NET uygulamanın perspektifinden kısmen güvenilir ortamlar arasındaki etkileşimler açıklanmaktadır.|  
|[Kod erişimi güvenliği](../../../../docs/framework/misc/code-access-security.md)|.NET Framework'teki CAS açıklayan ek konulara bağlantılar içerir.|  
  
## <a name="database-security"></a>Veritabanı güvenliği  
 En düşük öncelik ilkesini veri kaynağınız için de geçerlidir. Veritabanı güvenliği için bazı genel yönergeleri içerir:  
  
-   Olası en düşük ayrıcalıkları olan hesapları oluşturun.  
  
-   Kullanıcılar yalnızca kod çalışma elde etmek için yönetim hesaplarına erişim izin vermez.  
  
-   İstemci uygulamaları için sunucu tarafı hata iletileri gitmez.  
  
-   Hem istemci hem de sunucu tüm girişleri doğrulayın.  
  
-   Parametreli komutların kullanın ve dinamik SQL deyimleri kaçının.  
  
-   Denetim ve günlük uyarı almanız için herhangi bir güvenlik ihlallerini kullanmakta olduğunuz veritabanı için güvenlik sağlar.  
  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[SQL Server Güvenliği](../../../../docs/framework/data/adonet/sql/sql-server-security.md)|SQL Server'ı hedefleyen güvenli ADO.NET uygulamalar oluşturmaya yönelik rehberlik uygulama senaryoları ile SQL Server güvenliğine genel bakış sağlar.|  
|[Veri erişim stratejileri için öneriler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))|Veri erişimi ve veritabanı işlemleri gerçekleştirmek için öneriler sağlar.|  
  
## <a name="security-policy-and-administration"></a>Güvenlik İlkesi ve yönetim  
 Yanlış kod erişimi güvenliği (CAS) ilkesi yönetme, olası güvenlik zayıf oluşturabilirsiniz. Bir uygulama dağıtıldıktan sonra teknikleri, güvenlik izleme için kullanılmalıdır ve yeni tehditleri değerlendirilen riskleri ortaya çıkmaya başladı.  
  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Güvenlik İlkesi Yönetimi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100))|Oluşturma ve Güvenlik İlkesi'ni yönetme hakkında bilgi sağlar.|  
|[Güvenlik İlkesi en iyi uygulamalar](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sa4se9bc(v=vs.100))|Güvenlik ilkesini yönetmek nasıl açıklayan bağlantılar sağlar.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [.NET içinde güvenlik](../../../standard/security/index.md)
- [SQL Server Güvenliği](../../../../docs/framework/data/adonet/sql/sql-server-security.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
