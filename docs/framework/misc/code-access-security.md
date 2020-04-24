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
ms.openlocfilehash: a7dce1efedfb652096e6b583eca08e5b80d282a5
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645786"
---
# <a name="code-access-security"></a>Kod Erişimi Güvenliği
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Günümüzün yüksek oranda bağlı bilgisayar sistemleri sık sık çeşitli, muhtemelen bilinmeyen kaynaklardan kaynaklanan kodlara maruz kalmaktadır. Kod e-postaya eklenebilir, belgelerde bulunabilir veya Internet üzerinden indirilebilir. Ne yazık ki, birçok bilgisayar kullanıcısı, verilere zarar veren veya yok eden ve zaman ve paraya mal olabilecek virüsler ve solucanlar da dahil olmak üzere kötü amaçlı mobil kodun etkilerini ilk elden deneyimlemiş.  
  
 En yaygın güvenlik mekanizmaları, kullanıcılara oturum açma kimlik bilgilerine (genellikle parola) dayalı haklar verir ve kullanıcının erişmesine izin verilen kaynakları (genellikle dizinler ve dosyalar) kısıtlar. Ancak, bu yaklaşım çeşitli sorunları gidermek için başarısız olur: kullanıcılar birçok kaynaktan kod almak, bazıları güvenilmez olabilir; kod, kötü amaçlı kod tarafından kullanılmasını sağlayan hatalar veya güvenlik açıkları içerebilir; ve kod bazen kullanıcı yapacağını bilmiyor şeyler yapar. Sonuç olarak, bilgisayar sistemleri zarar görebilir ve dikkatli ve güvenilir kullanıcılar kötü amaçlı veya hata dolu yazılımçalıştırdığında özel veriler sızdırılabilir. Çoğu işletim sistemi güvenlik mekanizması, bir Web sayfasındaki komut dosyaları dışında, çalıştırmak için her kod parçasına tamamen güvenilmesi ni gerektirir. Bu nedenle, sistemler arasında güven ilişkisi olmasa bile, bir bilgisayar sisteminden kaynaklanan kodun başka bir sistemde korumayla yürütülmesine olanak tanıyan yaygın olarak uygulanabilir bir güvenlik mekanizmasına hala ihtiyaç vardır.  
  
 .NET Framework, bilgisayar sistemlerinin kötü amaçlı mobil kodlardan korunmasına, bilinmeyen kökenlerden gelen kodların korumayla çalışmasına izin vermek ve güvenilen kodun kasıtlı veya yanlışlıkla güvenliği tehlikeye atmasını önlemeye yardımcı olmak için kod erişim güvenliği adı verilen bir güvenlik mekanizması sağlar. Kod erişim güvenliği, kodun kaynağına ve kodun kimliğinin diğer yönlerine bağlı olarak kodun farklı derecelerde güvenilir olmasını sağlar. Kod erişim güvenliği, çalıştırmak için tam olarak güvenilmesi gereken kod miktarını en aza indiren, kodüzerinde değişen güven düzeylerini de zorlar. Kod erişim güvenliğini kullanmak, kodunuzu kötü amaçlı veya hata dolu kod tarafından kötüye kullanılma olasılığını azaltabilir. Kodunuzu gerçekleştirmesine izin verilmesi gereken işlem kümesini belirtebildiğiniz için, yükümlülüğünüzü azaltabilir. Kod erişim güvenliği, kodunuzda güvenlik açıklarından kaynaklanınabilecek zararı en aza indirmeye de yardımcı olabilir.  
  
> [!NOTE]
> .NET Framework 4'teki kod erişim güvenliğinde önemli değişiklikler yapılmıştır. En önemli değişiklik [güvenlik saydamlığı](security-transparent-code.md)olmuştur, ancak kod erişim güvenliğini etkileyen diğer önemli değişiklikler de vardır. Bu değişiklikler hakkında bilgi için [Güvenlik Değişiklikleri'ne](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)bakın.  
  
 Kod erişim güvenliği öncelikle kitaplık kodunu ve kısmen güvenilen uygulamaları etkiler. Kitaplık geliştiricileri, kodlarını kısmen güvenilen uygulamalara karşı yetkisiz erişime karşı korumalıdır. Kısmen güvenilen uygulamalar, Internet gibi dış kaynaklardan yüklenen uygulamalardır. Masaüstünüze veya yerel intranet'e yüklenen uygulamalar tam güven içinde çalışır. Tam güven uygulamaları, tam olarak güvenildikleri için [güvenlik saydam](security-transparent-code.md)olarak işaretlenmedikçe kod erişim güvenliğinden etkilenmez. Tam güven uygulamaları için tek sınırlama, öznitelik ile <xref:System.Security.SecurityTransparentAttribute> işaretlenmiş uygulamalar öznitelik ile <xref:System.Security.SecurityCriticalAttribute> işaretlenmiş kodu arayamaz olmasıdır. Kod erişim güvenliğinin uygulanabilmesi için kısmen güvenilen uygulamaların bir kum alanında (örneğin, Internet Explorer'da) çalıştırılması gerekir. Bir uygulamayı Internet'ten indirip masaüstünüzden çalıştırmayı denerseniz, şu <xref:System.NotSupportedException> mesajla birlikte bir ileti alırsınız: "Bir derlemeyi ağ konumundan yükleme girişiminde bulunuldu ve bu da derlemenin .NET Framework'ün önceki sürümlerinde kuma alınmasına neden oldu. .NET Framework'ün bu sürümü varsayılan olarak CAS ilkesini etkinleştirmez, bu nedenle bu yük tehlikeli olabilir." Uygulamanın güvenilir olduğundan eminseniz, [ \<loadFromRemoteSources> öğesini](../configure-apps/file-schema/runtime/loadfromremotesources-element.md)kullanarak uygulamanın tam güven olarak çalıştırılmasını etkinleştirebilirsiniz. Bir uygulamayı bir sandbox'ta çalıştırma hakkında bilgi için [bkz.](how-to-run-partially-trusted-code-in-a-sandbox.md)  
  
 Ortak dil çalışma süresini hedefleyen tüm yönetilen kod, bu kod tek bir kod erişim güvenlik çağrısı yapmasa bile kod erişim güvenliğiavantajlarından yararlanır. Daha fazla bilgi için [Kod Erişim Güvenlik Temelleri'ne](code-access-security-basics.md)bakın.  
  
<a name="key_functions"></a>
## <a name="key-functions-of-code-access-security"></a>Kod Erişim Güvenliğinin Temel İşlevleri  
 Kod erişim güvenliği, kodun korumalı kaynaklara ve işlemlere erişimini sınırlamaya yardımcı olur. .NET Framework'de kod erişim güvenliği aşağıdaki işlevleri gerçekleştirir:  
  
- Çeşitli sistem kaynaklarına erişme hakkını temsil eden izinleri ve izin kümelerini tanımlar.  
  
- Kodun arayanların belirli izinlere sahip olmasını talep etmesini sağlar.  
  
- Kodun, arayanların dijital imzaya sahip olmasını talep etmesini sağlayarak belirli bir kuruluşveya siteden yalnızca arayanların korumalı kodu aramasını sağlar.  
  
- Arama yığınındaki her arayanın verilen izinlerini, arayanların sahip olması gereken izinlerle karşılaştırarak, çalışma zamanında kod üzerindeki kısıtlamaları zorlar.  
  
<a name="walking_the_call_stack"></a>
## <a name="walking-the-call-stack"></a>Çağrı Yığınını Yürümek  
 Kodun kaynağa erişmeye veya bir işlem gerçekleştirmeye yetkili olup olmadığını belirlemek için, çalışma zamanının güvenlik sistemi arama yığınını yürütür ve her arayanın verilen izinlerini istenen izinle karşılaştırır. Arama yığınındaki herhangi bir arayan istenen izne sahip değilse, bir güvenlik özel durumu atılır ve erişim reddedilir. Yığın yürüyüşü, daha az güvenilen kodun son derece güvenilir kodu aradığı ve yetkisiz eylemler gerçekleştirmek için kullandığı çekme saldırılarını önlemeye yardımcı olmak için tasarlanmıştır. Çalışma zamanında tüm arayanların izinlerini istemek performansı etkiler, ancak kodun daha az güvenilen kodla saldırıları cezbetmeye karşı korunmasına yardımcı olmak önemlidir. Performansı en iyi duruma getirmek için, kodunuzu daha az yığın yürüyüşleri gerçekleştirebilirsiniz; ancak, bunu her yaptığınızda bir güvenlik zayıflığı ortaya çıkarmadığınızdan emin olmalısınız.  
  
 Aşağıdaki resimde, Derleme A4'teki bir yöntem arayanların p iznine sahip olması gerektiğinde ortaya çıkan yığın yürüyüşünü gösterir.  
  
 ![Kod erişim güvenliği](media/slide-10a.gif "slide_10a")  
Güvenlik yığını yürüyüşü  
  
<a name="related_topics"></a>
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Kod Erişim Güvenliği Temelleri](code-access-security-basics.md)|Kod erişim güvenliğini ve en yaygın kullanımlarını açıklar.|  
|[Güvenliği Saydam Kod, 2. Düzey](security-transparent-code-level-2.md)|.NET Framework 4'teki güvenlik saydamlık modelini açıklar.|  
|[Kısmen Güvenilen Koddan Kitaplıkları Kullanma](using-libraries-from-partially-trusted-code.md)|Kitaplıkların yönetilmeyen kodla nasıl kullanılacağını ve yönetilmeyen koddan kitaplıkların nasıl kullanılacağını açıklar.|  
|[Temel Güvenlik Kavramları](../../standard/security/key-security-concepts.md)|.NET Framework güvenlik sisteminde kullanılan anahtar terimler ve kavramlara genel bir bakış sağlar.|  
|[Rol Tabanlı Güvenlik](../../standard/security/role-based-security.md)|Rollere dayalı güvenliğin nasıl birleştirilen açıklar.|  
|[Şifreleme Hizmetleri](../../standard/security/cryptographic-services.md)|Uygulamalarınıza şifrelemenin nasıl dahil edilebildiğini açıklar.|
