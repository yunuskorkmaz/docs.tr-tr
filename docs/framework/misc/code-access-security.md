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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775821"
---
# <a name="code-access-security"></a>Kod Erişimi Güvenliği
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Günümüzün son derece bağlı bilgisayar sistemleri çeşitli kaynaklanan kod sık sunulur büyük olasılıkla bilinmeyen kaynaklar. Kod, belgelerde yer alan veya Internet üzerinden indirilen e-posta adresine bağlı. Ne yazık ki, birçok bilgisayar kullanıcıları bölümünüzü virüsler ve solucanlar zarar verecek veya veri ve maliyet zamandan ve paradan tasarruf yok dahil olmak üzere mobil kötü amaçlı kod etkilerini karşılaşmıştır.  
  
 En sık kullanılan güvenlik mekanizmaları, oturum açma kimlik bilgilerini (genellikle parola) temel alarak kullanıcılara haklar ve kullanıcıya erişim izni kaynakları (genellikle dizinleri ve dosyaları). Ancak, bu yaklaşım bazı sorunları ele almak başarısız olur: kullanıcılar bazıları güvensiz olabilir; pek çok kaynaktan kod alın kod hataları veya kötü amaçlı kod tarafından kötüye sağlamak güvenlik açıkları içerebilir; ve kod bazen kullanıcının ne yapacağını bilmediği şeyler yapar. Sonuç olarak, bilgisayar sistemlerine bozuk ve kötü amaçlı ya da hata doldurulmuş yazılım dikkatli ve güvenilir kullanıcıların çalıştırdığınızda, özel veri sızmasına. Çoğu işletim sistemi güvenlik mekanizmaları her kod parçasını tamamen güvenilir olmasını zorunlu tutmak çalıştırmak için bir Web sayfasındaki betikleri için belki de hariç. Bu nedenle, yoktur hala ihtiyaç bile sistemler arasında bir güven ilişkisi olduğunda, başka bir sistem koruması ile yürütmek için tek bir bilgisayar sistemi kaynaklanan kod izin veren bir yaygın olarak geçerli güvenlik mekanizması.  
  
 .NET Framework, bilgisayar sistemlerine korumasıyla çalıştırın ve güvenilen koddan veya kazayla önlemeye yardımcı olmak için bilinmeyen kaynaklardan gelen koddan izin vermek için kötü amaçlı mobil kod korunmalarına yardımcı olmak amacıyla kod erişimi güvenliği adlı bir güvenlik mekanizması sağlar. güvenlikten ödün. Kod erişimi güvenliği, kodun diğer yönleri ve kod kaynaklandığı bağlı olarak değişen düzeylerde güvenilir kodun sağlar. Kod erişimi güvenliği, ayrıca çalıştırmak için tam olarak güvenilir olması gereken kod miktarını en aza indirir, kod güven düzeyleri uygulayan zorlar. Kod erişimi güvenliği kullanarak kodunuzu olacak olasılığını azaltabilirsiniz kötü amaçlı ya da hata doldurulan kod tarafından kötüye kullanılıyor. İşlemleri gerçekleştirmek için kodunuzu izin kümesini belirtebildiğinizden bunu, sorumluluk azaltabilir. Kod erişimi güvenliği, kodunuzdaki güvenlik açıklarına neden olabilir zararı en aza indirmek da yardımcı olabilir.  
  
> [!NOTE]
>  Kod erişimi güvenliği, için önemli değişiklikler yapıldı [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. En önemli bir değişiklik olmuştur [güvenlik saydamlık](../../../docs/framework/misc/security-transparent-code.md), vardır, ancak aynı zamanda kod erişim güvenliğini etkileyen diğer önemli değişiklikler. Bu değişiklikler hakkında daha fazla bilgi için bkz: [güvenlik değişiklikleri](../../../docs/framework/security/security-changes.md).  
  
 Kod erişimi güvenliği, kitaplık kodu ve kısmen güvenilir uygulamaların öncelikli olarak etkiler. Kitaplığı geliştiriciler kodlarını kısmen güvenilir uygulamaların yetkisiz erişimden korunmasına gerekir. Kısmen güvenilir uygulamaların Internet gibi dış kaynaklardan yüklenen uygulamalardır. Masaüstünde veya yerel intranet üzerindeki yüklü uygulamalarını tam güvende çalıştırın. Tam güven uygulamaları olarak işaretlenmediği sürece kod erişim güvenliği tarafından etkilenmez [güvenlik açısından saydam](../../../docs/framework/misc/security-transparent-code.md), tam olarak güvenilirdir. Tek sınırlama tam güven uygulamaları için olan ile işaretlenmiş uygulamaları <xref:System.Security.SecurityTransparentAttribute> özniteliği ile işaretlenmiş kod çağıramaz <xref:System.Security.SecurityCriticalAttribute> özniteliği. Böylece kod erişim güvenliği uygulanabilir kısmen güvenilir uygulamaların (örneğin, Internet Explorer'da) bir korumalı alan çalıştırmanız gerekir. Internet'ten bir uygulamayı indirmek ve masaüstünüzden çalıştırmak çalışırsanız, erişmenizi sağlayacak bir <xref:System.NotSupportedException> iletisi: "Derlemesi .NET Framework'ün önceki sürümlerinde korumalı olmasını neden bir ağ konumundan bir derlemeyi yüklemek için girişimde bulunuldu. Bu yük tehlikeli olabilir. .NET Framework'ün bu sürümü CAS ilkesini varsayılan olarak etkinleştirmez." Uygulama güvenilirliğinden emin olup, bunu kullanarak tam güven çalıştırılacak etkinleştirebilirsiniz [ \<loadFromRemoteSources > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md). Bir korumalı alan içinde bir uygulamayı çalıştırma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Korumalı alanda kısmen güvenilen kodu çalıştırma](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
 Bu kod, çağrı tek bir kod erişim güvenliği yapmaz bile tüm yönetilen hedefleyen ortak dil çalışma zamanı kod erişim güvenliği avantajlarından alır kod. Daha fazla bilgi için [kod erişimi güvenliği Temelleri](../../../docs/framework/misc/code-access-security-basics.md).  
  
<a name="key_functions"></a>   
## <a name="key-functions-of-code-access-security"></a>Kod erişim güvenliğini önemli işlevler  
 Kod erişimi güvenliği, kod korumalı kaynaklara ve işlemlere sahip olan erişimini sınırlamaya yardımcı olur. .NET Framework'te kod erişimi güvenliği, aşağıdaki işlevleri gerçekleştirir:  
  
- İzinler ve çeşitli sistem kaynaklarına erişim hakkı temsil eden izin kümeleri tanımlar.  
  
- İsteğe bağlı çağrıda bulunanların belirli izinlere sahip olduğunuzu kodu sağlar.  
  
- Böylece korunan kod çağırmak yalnızca belirli bir kuruluş veya sitesinde arayanlara izin vererek çağıranlarını bir dijital imza sahip isteğe bağlı kod sağlar.  
  
- Kod üzerindeki kısıtlamalar, verilen izinler, Arayanların olmalıdır izinlerle çağrı yığınında her arayanın karşılaştırarak, çalışma zamanında zorlar.  
  
<a name="walking_the_call_stack"></a>   
## <a name="walking-the-call-stack"></a>Çağrı yığınını walking  
 Kod bir kaynağa veya bir işlemi gerçekleştirmek için yetkili olup olmadığını belirlemek için çağrı yığını karşılaştırma her arayanın talep izin verilen izinler çalışma zamanının güvenlik sistemi size yol gösterir. Çağrı yığınındaki herhangi bir çağırıcı talep edilen iznine sahip değilse bir güvenlik özel durumu atılır ve erişim reddedildi. Yığın ilerlemesi önlemeye yardımcı olmak için tasarlanan saldırılar luring, hangi daha az kod yüksek derecede güvenilen bir kod ve yetkisiz eylemleri gerçekleştirmek için kullandığı güvenilir. Çalışma zamanında tüm çağıranların izinlerini zorlu performansı etkiler, ancak en az güvenilen kod tarafından saldırıları luring gelen kod korumaya yardımcı olmak için gereklidir. Performansı iyileştirmek için kodunuzu daha az yığın Yürüyüşü gerçekleştirmek olabilir; Ancak, bunu her bir güvenlik açığına gösterme emin olmanız gerekir.  
  
 Aşağıdaki çizimde derleme A4 bir yöntem çağrıda bulunanların P. izninizin olduğunu talep ettiğinde, yığın ilerlemesi  
  
 ![Kod erişimi güvenliği](../../../docs/framework/misc/media/slide-10a.gif "slide_10a")  
Güvenlik yığın ilerlemesi  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Kod erişimi güvenliği temelleri](../../../docs/framework/misc/code-access-security-basics.md)|Kod erişimi güvenliği ve en yaygın kullanımları açıklar.|  
|[Güvenliği saydam kod, Düzey 2](../../../docs/framework/misc/security-transparent-code-level-2.md)|Güvenlik saydamlık modeli açıklar [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].|  
|[Kısmen güvenilen koddan kitaplıkları kullanma](../../../docs/framework/misc/using-libraries-from-partially-trusted-code.md)|Yönetilmeyen kod ile kullanmak için kitaplıkları etkinleştirme ve yönetilmeyen koddan kitaplıkları kullanma açıklanmaktadır.|  
|[Temel Güvenlik Kavramları](../../../docs/standard/security/key-security-concepts.md)|Birçok içinde .NET Framework güvenlik sistemini kullanılan kavramları ve önemli terimlerin bir bakış sağlar.|  
|[Rol Tabanlı Güvenlik](../../../docs/standard/security/role-based-security.md)|Güvenlik rollerine göre edileceğini açıklar.|  
|[Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md)|Şifreleme uygulamalarınıza eklemenizi açıklar.|
