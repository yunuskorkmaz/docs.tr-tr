---
title: Kod Erişimi Güvenliği
description: .NET 'teki kod erişimi güvenlik mekanizması hakkında bilgi edinin ve bilgisayar sistemlerinin kötü amaçlı mobil koddan korunmasını sağlar.
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
ms.openlocfilehash: 6fa7983d0355a9e11728f8dbd0f4e06bbb0f8e5b
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281647"
---
# <a name="code-access-security"></a>Kod Erişimi Güvenliği
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Günümüzün yüksek oranda bağlı bilgisayar sistemleri, büyük olasılıkla bilinmeyen kaynaklardan kaynaklanan koda sıklıkla açıktır. Kod, belgelerde bulunan veya Internet üzerinden indirilen e-postaya bağlanabilir. Ne yazık ki, birçok bilgisayar kullanıcısı virüsler ve solucanlar de dahil olmak üzere kötü amaçlı mobil kodun etkilerini Ağızdan yaşadı ve bu da verileri ve maliyet zamanını ve paradan zarar verebilir veya yok edebilir.  
  
 En yaygın güvenlik mekanizmaları, kullanıcılar için oturum açma kimlik bilgilerini (genellikle bir parola) temel alan haklar verir ve kullanıcının erişmesine izin verilen kaynakları (genellikle dizinler ve dosyalar) kısıtlar. Ancak, bu yaklaşım çeşitli sorunları ele alamıyor: kullanıcılar çok sayıda kaynaktan kod edinerek, bazıları güvenilir olmayabilir; kod, kötü amaçlı kod tarafından yararlanılmasını sağlayan hatalar veya güvenlik açıkları içerebilir; ve kod bazen Kullanıcı tarafından bunu bilmez. Sonuç olarak, bilgisayar sistemleri zarar görmüş olabilir ve güvenilir kullanıcılar kötü amaçlı veya hata doldurulmuş yazılımlar çalıştırmazsa, özel veriler sızmış olabilir. Çoğu işletim sistemi güvenlik mekanizması, bir Web sayfasındaki betikler hariç olmak üzere her kod parçasının çalışması için tamamen güvenilir olmasını gerektirir. Bu nedenle, sistemler arasında güven ilişkisi olmasa bile, bir bilgisayar sisteminden kaynaklanan kodun başka bir sistem üzerinde koruma ile yürütülmesine izin veren, yaygın olarak uygulanabilir bir güvenlik mekanizması olması gerekir.  
  
 .NET Framework, bilgisayar sistemlerinin kötü amaçlı mobil koddan korunmasına yardımcı olmak için kod erişim güvenliği adlı bir güvenlik mekanizması sağlar, bilinmeyen kaynaklardan gelen kodun koruma ile çalışmasına izin vermek ve güvenilen kodun kasıtlı veya yanlışlıkla güvenliği tehlikeye atmasını önlemeye yardımcı olur. Kod erişim güvenliği, kodun kaynaklandığı ve kodun kimliğinin diğer yönlerine bağlı olarak kodun farklı derecelerde güvenilir olmasını sağlar. Kod erişimi güvenliği, kod üzerinde farklı güven düzeyleri de uygular ve bu da çalışması için tam güvenilir olması gereken kod miktarını en aza indirir. Kod erişim güvenliğini kullanmak, kodunuzun kötü amaçlı veya hata doldurulmuş kod ile kötüye kullanılması olasılığını azaltabilir. Kodunuzun gerçekleştirmesine izin verilmesi gereken işlem kümesini belirtebileceğiniz için yükümlülük azalmasına olanak sağlayabilir. Kod erişimi güvenliği, kodunuzda güvenlik açıklarına neden olabilecek hasarı en aza indirmenize de yardımcı olabilir.  
  
> [!NOTE]
> Kod erişim güvenliği için .NET Framework 4 ' te önemli değişiklikler yapılmıştır. En önemli değişiklik [güvenlik saydamlığına](security-transparent-code.md)sahiptir, ancak kod erişim güvenliğini etkileyen diğer önemli değişiklikler de vardır. Bu değişiklikler hakkında daha fazla bilgi için bkz. [güvenlik değişiklikleri](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).  
  
 Kod erişimi güvenliği birincil olarak kitaplık kodunu ve kısmen güvenilen uygulamaları etkiler. Kitaplık geliştiricileri, kısmen güvenilen uygulamalardan kendi kodlarını yetkisiz erişimlerden korumalıdır. Kısmen güvenilen uygulamalar, Internet gibi dış kaynaklardan yüklenen uygulamalardır. Masaüstünüzde veya yerel intranette yüklü olan uygulamalar tam güvende çalışır. Tam güven uygulamaları, tamamen güvenilir olduklarından, [güvenlik açısından saydam](security-transparent-code.md)olarak işaretlenmedikçe, kod erişim güvenliği tarafından etkilenmez. Tam güvenle uygulamalara yönelik tek sınırlama, özniteliğiyle işaretlenen uygulamaların <xref:System.Security.SecurityTransparentAttribute> özniteliğiyle işaretlenen kodu çağıramasıdır <xref:System.Security.SecurityCriticalAttribute> . Kısmen güvenilen uygulamalar, kod erişimi güvenliğinin uygulanabilmesi için bir korumalı alanda (örneğin, Internet Explorer 'da) çalıştırılmalıdır. Bir uygulamayı Internet 'ten indirip masaüstünüzden çalıştırmayı denerseniz, <xref:System.NotSupportedException> "bir ağ konumundan bir derlemeyi yükleme girişiminde bulunuldu. bu durum, derlemenin önceki .NET Framework korumalı olmasını sağlayan bir ağ konumundan bir derlemeyi yüklemeye çalışır. .NET Framework bu sürümü, varsayılan olarak CAS ilkesini etkinleştirmez, bu nedenle bu yük tehlikeli olabilir. " Uygulamanın güvenilir olduğundan eminseniz, [ \<loadFromRemoteSources> öğesini](../configure-apps/file-schema/runtime/loadfromremotesources-element.md)kullanarak tam güven olarak çalışmasını sağlayabilirsiniz. Bir uygulamayı bir korumalı alanda çalıştırma hakkında bilgi için bkz. [nasıl yapılır: bir korumalı olarak kısmen güvenilen kodu çalıştırma](how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
 Ortak dil çalışma zamanını hedefleyen tüm yönetilen kodlar, bu kod tek bir kod erişim güvenliği çağrısı yapmasa bile, kod erişim güvenliği avantajlarından yararlanır. Daha fazla bilgi için bkz. [kod erişimi güvenlik temelleri](code-access-security-basics.md).  
  
<a name="key_functions"></a>
## <a name="key-functions-of-code-access-security"></a>Kod erişim güvenliği 'nin önemli Işlevleri  
 Kod erişim güvenliği, kodda korunan kaynaklara ve işlemlere erişimi sınırlamaya yardımcı olur. .NET Framework, kod erişim güvenliği aşağıdaki işlevleri gerçekleştirir:  
  
- Çeşitli sistem kaynaklarına erişme hakkını temsil eden izinleri ve izin kümelerini tanımlar.  
  
- Kodun çağıranlarının belirli izinlere sahip olduğunu talep etmesini sağlar.  
  
- Kod çağıranlarının dijital imzaya sahip olmasını talep etmesini sağlar ve böylece yalnızca belirli bir kuruluştan veya siteden gelen çağıranların korunan kodu aramasını sağlar.  
  
- Çağrı yığınında her çağıranın verilen izinlerini çağıranların sahip olması gereken izinlerle karşılaştırarak çalışma zamanında kod kısıtlamalarını zorlar.  
  
<a name="walking_the_call_stack"></a>
## <a name="walking-the-call-stack"></a>Çağrı yığını yürüme  
 Kodun bir kaynağa erişmek veya bir işlemi gerçekleştirmek için yetkilendirilip yetkilendirilmediğini anlamak için, çalışma zamanının güvenlik sistemi çağrı yığınına kılavuzluk eder ve her çağıranın verilen izinlerini talep edilen izinlerle karşılaştırır. Çağrı yığınındaki herhangi bir çağıran, istenen izne sahip değilse, bir güvenlik özel durumu oluşturulur ve erişim reddedilir. Yığın ilerlemesi, daha az güvenilen kodun yüksek güvenilir kodu çağırdığı ve yetkisiz eylemler gerçekleştirmek için kullandığı, düğüm saldırılarını önlemeye yardımcı olmak için tasarlanmıştır. Çalışma zamanında tüm çağıranların yoğun izinleri performansı etkiler, ancak kodun daha az güvenilir bir kod ile kodsuz saldırılardan korunmasını sağlamak önemlidir. Performansı iyileştirmek için, kodunuzun daha az yığın gerçekleştirmesini sağlayabilirsiniz; Ancak, bunu yaptığınızda güvenlik zayıflığından emin olmanız gerekir.  
  
 Aşağıdaki çizimde, bir derleme a4 içindeki bir yöntem çağıranların izin P 'ye sahip olduğu durumlarda oluşan yığın izlenecek sonuç gösterilmektedir.  
  
 ![Kod erişim güvenliği](media/slide-10a.gif "slide_10a")  
Güvenlik yığını ilerleme  
  
<a name="related_topics"></a>
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Kod Erişim Güvenliği Temelleri](code-access-security-basics.md)|Kod erişim güvenliğini ve en yaygın kullanımları açıklar.|  
|[Güvenliği Saydam Kod, 2. Düzey](security-transparent-code-level-2.md)|.NET Framework 4 ' teki güvenlik saydamlığı modelini açıklar.|  
|[Kısmen Güvenilen Koddan Kitaplıkları Kullanma](using-libraries-from-partially-trusted-code.md)|Yönetilmeyen kod ile kullanım için kitaplıkların nasıl etkinleştirileceğini ve yönetilmeyen koddan kitaplıkların nasıl kullanılacağını açıklar.|  
|[Temel Güvenlik Kavramları](../../standard/security/key-security-concepts.md)|.NET Framework güvenlik sisteminde kullanılan önemli koşulların ve kavramların çoğuna genel bir bakış sağlar.|  
|[Rol Tabanlı Güvenlik](../../standard/security/role-based-security.md)|Rollere göre güvenliğin nasıl ekleneceğini açıklar.|  
|[Şifreleme Hizmetleri](../../standard/security/cryptographic-services.md)|Uygulamalarınızın nasıl şifreleneceğini açıklar.|
