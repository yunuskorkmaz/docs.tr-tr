---
title: Kod Erişimi Güvenliği
ms.date: 03/30/2017
helpviewer_keywords:
- named permission sets, code access security
- call stacks
- malicious code
- stack walk
- security [.NET Framework], code access security
- permissions [.NET Framework], code access security
- trusted code
- mobile code security
- unmanaged code, code access security
- granting permissions, code access security
- user authentication, code access security
- code access security
ms.assetid: 859af632-c80d-4736-8d6f-1e01b09ce127
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e01d3ecf3367baed6673a66015918337105eecb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392739"
---
# <a name="code-access-security"></a>Kod Erişimi Güvenliği
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Günümüzün yüksek oranda bağlı bilgisayar sistemleri çeşitli kaynaklanan kod açığa sık büyük olasılıkla bilinmeyen kaynaklar. Kod e-posta bağlı, belgelerde yer alan veya Internet üzerinden indirilir. Ne yazık ki, çok sayıda bilgisayar kullanıcıları bölümünüzü virüsler ve zarar veya veri ve maliyet zaman ve para destroy solucanlar da dahil olmak üzere kötü amaçlı mobil kod etkilerini karşılaşmıştır.  
  
 En yaygın güvenlik mekanizmaları kullanıcıların oturum açma kimlik bilgilerini (genellikle parola) temel alarak kullanıcılara hakları verin ve kullanıcı erişim izni kaynakları (genellikle dizin ve dosyaların) kısıtlayın. Ancak, bazı sorunları gidermek bu yaklaşım başarısız: kullanıcıların bazıları olabilir güvenilmez; birçok kaynaktan kod alın kod hataları veya kötü amaçlı kod tarafından kullanılmasına etkinleştirmek güvenlik açıkları içerebilir; ve kod bazen kullanıcı ne yapacağını bilmez işlemi yapar. Sonuç olarak, bilgisayar sistemleri bozuk ve kötü amaçlı veya hata doldurulmuş yazılım dikkatli ve güvenilir kullanıcıları çalıştırdığınızda, özel veri sızabileceği. Çoğu işletim sistemi güvenlik mekanizmaları her kod parçası, tamamen güvenilir gerektiren çalıştırmak için bir Web sayfasında betikler için belki de hariç. Bu nedenle, gerçek hala bir gereksinimi sistemler arasında bir güven ilişkisi olduğunda, başka bir sistem koruması ile yürütmek için tek bir bilgisayar sistemi kaynaklanan kodu izin veren bir yaygın olarak geçerli güvenlik mekanizması.  
  
 .NET Framework ile koruma çalıştıracak ve güvenilen koddan kasıtlı olarak veya kazayla önlemeye yardımcı olmak için bilinmeyen kaynaklardan gelen koddan izin vermek için kötü amaçlı mobil kod bilgisayar sistemleri korunmalarına yardımcı olmak amacıyla kod erişimi güvenliği adlı bir güvenlik mekanizması sağlar güvenliği tehlikeye. Kod erişim güvenliği değişen derecelerde diğer yönlerini kodun kimlik ve kod kaynaklandığı bağlı olarak güvenilir olması için kod sağlar. Kod erişim güvenliği ayrıca farklı çalıştırmak için tam olarak güvenilir olması gerekir kod miktarını kodu güven düzeyleri zorlar. Kod erişim güvenliği kullanarak kodunuzu olacaktır olasılığını azaltabilir kötü amaçlı veya hata doldurulmuş kodla kullandı. İşlemleri gerçekleştirmek için kodunuzu izin kümesi belirttiğinden, pasif azaltabilir. Kod erişimi güvenliği, ayrıca güvenlik açıklarından kodunuzda kaynaklanan sonuçlanabilir hasarı en aza yardımcı olur.  
  
> [!NOTE]
>  Kod erişim güvenliği için önemli değişiklikler yapılmıştır [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. En önemli değişiklik yapıldı [güvenlik saydamlık](../../../docs/framework/misc/security-transparent-code.md), ancak ayrıca kod erişim güvenliği etkileyen diğer önemli değişiklikler. Bu değişiklikler hakkında daha fazla bilgi için bkz: [güvenlik değişiklikleri](../../../docs/framework/security/security-changes.md).  
  
 Kod erişim güvenliği öncelikle kitaplık kodu ve kısmen güvenilir uygulamalar etkiler. Kitaplık geliştiricileri kendi kodlarını kısmen güvenilir uygulamalar yetkisiz erişimden korumanız gerekir. Kısmen güvenilir uygulamalar Internet gibi dış kaynaklardan yüklenen uygulamalardır. Masaüstünde veya yerel intranet üzerindeki yüklü uygulamaların tam güvende çalıştırın. Tam güven uygulamaları olarak işaretlenmiş sürece kod erişim güvenliği tarafından etkilenmez [güvenliği saydam](../../../docs/framework/misc/security-transparent-code.md)tam güvenilir olduğundan. Tam güven uygulamaları için yalnızca sınırlaması olan ile işaretlenen uygulamalar <xref:System.Security.SecurityTransparentAttribute> özniteliği ile işaretlenmiş kod çağıramaz <xref:System.Security.SecurityCriticalAttribute> özniteliği. Kod erişim güvenliği uygulanabilir böylece kısmen güvenilir uygulamalar (örneğin, Internet Explorer'da) bir korumalı alan çalıştırmanız gerekir. Internet'ten bir uygulama indirin ve masaüstünüzden çalıştırmak çalışırsanız, alırsınız bir <xref:System.NotSupportedException> ileti: "önceki sürümlerde korumalı olmasını derleme neden bir ağ konumundan bir derlemeyi yüklemek için girişimde bulunuldu .NET Framework. Bu yük tehlikeli olabilir .NET Framework'ün bu sürüm CAS ilkesini varsayılan olarak etkinleştirmez." Uygulama güvenilirliğinden eminseniz, tam güven olarak kullanarak çalışacak şekilde etkinleştirebilirsiniz [ \<loadFromRemoteSources > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md). Uygulamanın korumalı alanda çalıştırma hakkında daha fazla bilgi için bkz: [nasıl yapılır: çalıştırma kısmen güvenilen kod içinde bir korumalı alan](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
 Bu kodu çağrı tek bir kod erişim güvenliği yapmaz olsa bile tüm yönetilen kod erişim güvenliği yararları ortak dil çalışma zamanı alır hedefleyen kod. Daha fazla bilgi için bkz: [kod erişim güvenliği Temelleri](../../../docs/framework/misc/code-access-security-basics.md).  
  
<a name="key_functions"></a>   
## <a name="key-functions-of-code-access-security"></a>Kod erişimi güvenliği, önemli işlevleri  
 Kod erişimi güvenliği korumalı kaynaklara ve işlemlere koduna sahip erişimini sınırlamanıza yardımcı olur. .NET Framework'te kod erişimi güvenliği aşağıdaki işlevleri gerçekleştirir:  
  
-   İzinler ve çeşitli sistem kaynaklarına erişim hakkı temsil izin kümeleri tanımlar.  
  
-   İsteğe bağlı kendi arayanlar belirli izinlere sahip olduğunuzu kodu sağlar.  
  
-   Kod talep böylece korunan kod çağırmak yalnızca belirli bir kuruluş veya sitesinden arayanlara izin verme kendi arayanlar dijital bir imza sahip olmasını sağlar.  
  
-   Kod kısıtlamalar çalışma zamanında her çağıran arayanlar olmalıdır izinlerine çağrı yığınında verilen izinleri karşılaştırarak zorlar.  
  
<a name="walking_the_call_stack"></a>   
## <a name="walking-the-call-stack"></a>Çağrı yığını taramasını  
 Kod bir kaynağa erişmek veya bir işlem gerçekleştirmek için yetkili olup olmadığını belirlemek için her çağıran talep izin verilen izinleri karşılaştırma çağrı yığını zamanının güvenlik sistemi anlatılmaktadır. Çağrı yığınında herhangi bir çağırıcı talep edilen izne sahip değil, bir güvenlik özel durum oluşur ve erişim reddedildi. Yığın ilerlemesi önlemeye yardımcı olmak için tasarlanmış saldırılara luring, hangi daha az kod yüksek derecede güvenilen kod çağırır ve izinsiz eylemler gerçekleştirmek için kullandığı güvenilir. Çalışma zamanında tüm arayanlar izinleriyle yoğun performansı etkiler, ancak daha az güvenilen kod tarafından saldırıları luring kod korunmasına yardımcı olmak için gereklidir. Performansı iyileştirmek için daha az yığın yetenekte gerçekleştirmek kodunuzu olabilir; Ancak, bunu her bir güvenlik zayıflık gösterme emin olmanız gerekir.  
  
 Aşağıdaki çizimde, arayanlar P. izninizin olduğunu derleme A4 yönteminde talep ettiğinde, sonuçları yığın ilerlemesi gösterir  
  
 ![Kod erişimi güvenliği](../../../docs/framework/misc/media/slide-10a.gif "slide_10a")  
Güvenlik yığın ilerlemesi  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Kod erişim güvenliği temelleri](../../../docs/framework/misc/code-access-security-basics.md)|Kod erişimi güvenliği ve en yaygın kullanımları açıklar.|  
|[Güvenliği saydam kod, Düzey 2](../../../docs/framework/misc/security-transparent-code-level-2.md)|Güvenlik saydamlık modelinde açıklar [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].|  
|[Kısmen güvenilen koddan kitaplıkları kullanma](../../../docs/framework/misc/using-libraries-from-partially-trusted-code.md)|Yönetilmeyen kod ile kullanmak için kitaplıkları etkinleştirmek ve yönetilmeyen koddan kitaplıkları kullanma açıklar.|  
|[Temel Güvenlik Kavramları](../../../docs/standard/security/key-security-concepts.md)|Anahtar terimleri ve kavramları .NET Framework güvenlik sisteminde kullanılan çoğu bir bakış sağlar.|  
|[Rol Tabanlı Güvenlik](../../../docs/standard/security/role-based-security.md)|Güvenlik rollerine göre içerecek şekilde açıklar.|  
|[Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md)|Şifreleme uygulamalarınıza içerecek şekilde açıklar.|
