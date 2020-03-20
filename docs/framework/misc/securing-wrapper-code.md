---
title: Sarmalayıcı Kodunun Güvenliğini Sağlama
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], wrapper code
- wrapper code, securing
- secure coding, wrapper code
- code security, wrapper code
ms.assetid: 1df6c516-5bba-48bd-b450-1070e04b7389
ms.openlocfilehash: 3d38a4d4fd33798cf5987f5ce67305725ad9daec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399912"
---
# <a name="securing-wrapper-code"></a>Sarmalayıcı Kodunun Güvenliğini Sağlama
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Sarıcı kodu, özellikle sarıcının onu kullanan koddan daha yüksek güvene sahip olduğu durumlarda, benzersiz bir güvenlik zayıflık kümesi açabilir. Arayan adına yapılan ve arayanın sınırlı izinlerinin uygun güvenlik denetimine dahil olmadığı her şey, yararlanılacak olası bir zayıflıktır.  
  
 Arayanın kendi kendine yapamayacağı bir şeyi sarmalayıcı aracılığıyla asla etkinleştirin. Bu, tam bir yığın yürüyüş talebinin aksine, sınırlı bir güvenlik denetimi içeren bir şey yaparken özel bir tehlikedir. Tek düzeyli denetimler söz konusu olduğunda, gerçek arayan ile söz konusu API öğesi arasında paketkodu biraraya getirmek, güvenlik denetiminin olması gerektiği zaman kolayca başarılı olmasına ve böylelikle güvenliği zayıflatmasına neden olabilir.  
  
## <a name="delegates"></a>Temsilciler  
 Temsilci güvenliği .NET Framework sürümleri arasında farklılık gösterir.  Bu bölümde farklı temsilci davranışları ve ilişkili güvenlik hususları açıklanmaktadır.  
  
### <a name="in-version-10-and-11-of-the-net-framework"></a>.NET Framework'ün 1.0 ve 1.1 sürümünde  
 .NET Framework sürümü 1.0 ve 1.1, bir temsilci oluşturucuve bir temsilci arayana karşı aşağıdaki güvenlik eylemlerini gerçekleştirir.  
  
- Bir temsilci oluşturulduğunda, temsilci hedef yöntemindeki güvenlik bağlantısı talepleri, temsilci oluşturucunun hibe kümesine karşı gerçekleştirilir.  Güvenlik eyleminin karşılamaması, <xref:System.Security.SecurityException>bir .  
  
- Temsilci çağrıldığında, temsilci arayan daki varolan güvenlik talepleri gerçekleştirilir.  
  
 Kodunuz, daha <xref:System.Delegate> az güvenilen bir koddan bu kodu çağırabilen bir kod aldığında, daha az güvenilen kodun izinlerini yükseltmesini etkinleştirmediğinizden emin olun. Bir temsilci alır ve daha sonra kullanırsanız, temsilciyi oluşturan kod çağrı yığınında değildir ve temsilcinin içinde veya altında kod korumalı bir işlem deneseydi izinleri sınanmaz. Kodunuz ve arayan kodunuz oluşturucudan daha yüksek ayrıcalıklara sahipse, oluşturucu arama yığınının bir parçası olmadan çağrı yolunu düzenleyebilir.  
  
### <a name="in-version-20-and-later-versions-of-the-net-framework"></a>.NET Framework sürüm 2.0 ve sonraki sürümlerinde  
 Önceki sürümlerin aksine, .NET Framework sürüm 2.0 ve sonraki sürümleri, temsilci oluşturulduğunda ve çağrıldığında temsilci oluşturucuya karşı güvenlik eylemi gerçekleştirir.  
  
- Bir temsilci oluşturulduğunda, temsilci hedef yöntemindeki güvenlik bağlantısı talepleri, temsilci oluşturucunun hibe kümesine karşı gerçekleştirilir.  Güvenlik eyleminin karşılamaması, <xref:System.Security.SecurityException>bir .  
  
- Temsilci oluşturucunun hibe kümesi de temsilci oluşturma sırasında yakalanır ve temsilci ile birlikte depolanır.  
  
- Temsilci çağrıldığında, temsilci oluşturucu ve arayan farklı derlemelere aitse, ilk olarak geçerli bağlamdaki taleplere göre delege oluşturucunun yakalanan hibe kümesi değerlendirilir.  Ardından, temsilci arayan üzerinde varolan tüm güvenlik talepleri gerçekleştirilir.  
  
## <a name="link-demands-and-wrappers"></a>Bağlantı talepleri ve sarmalayıcılar  
 Güvenlik altyapısında bağlantı talepleri olan özel bir koruma durumu güçlendirilmiştir, ancak yine de kodunuzda olası bir zayıflık kaynağıdır.  
  
 Tam olarak güvenilen kod, [Bir LinkDemand](link-demands.md)tarafından korunan bir özelliği, olayı veya yöntemi çağırırsa, arayan için **LinkDemand** izin denetimi karşılanırsa arama başarılı olur. Ayrıca, tam olarak güvenilen kod, bir özelliğin adını alan ve yansımayı kullanarak erişimini **alan** bir sınıfı ortaya çıkarırsa, kullanıcı kodu bu özelliğe erişme hakkına sahip olmasa **bile,** erişime erişim sağlayanı arar. Bunun **nedeni, LinkDemand'ın** yalnızca tam olarak güvenilen kod olan hemen arayanı denetler. Özünde, tam olarak güvenilen kod, kullanıcı kodunun bu aramayı yapma hakkına sahip olduğundan emin olmadan kullanıcı kodu adına ayrıcalıklı bir arama yapar.  
  
 Bu tür güvenlik açıklarını önlemeye yardımcı olmak için, ortak dil çalışma süresi, bir **Bağlantı Talebi**tarafından korunan bir yönteme, oluşturucuya, özelliğine veya olayına dolaylı çağrıda çeki tam bir yığın yürüyüş talebine genişletir. Bu koruma bazı performans maliyetlerine neden olursa ve güvenlik denetiminin anlambilimini değiştirir; tam yığın yürüyüşü talebi, daha hızlı, tek düzeyli denetimin geçtiği yerde başarısız olabilir.  
  
## <a name="assembly-loading-wrappers"></a>Montaj yükleme sarmalayıcıları  
 Yönetilen kodu yüklemek için kullanılan <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>çeşitli yöntemler, arayanın kanıtıyla derlemeleri yükleyin. Bu yöntemlerden herhangi birini sararsanız, güvenlik sistemi derlemeleri yüklemek için arayanın paketleyicinize verdiği izinler yerine kodunuzu izin verme yöntemini kullanabilir. Daha az güvenilen kodun, arayanın sarıcınıza verdiğinden daha yüksek izinler verilen kodu yüklemesine izin vermemelisiniz.  
  
 Tam güvene sahip veya potansiyel bir arayandan önemli ölçüde daha yüksek güvene sahip herhangi bir kod (Internet izinleri düzeyinde arayan dahil) bu şekilde güvenliği zayıflatabilir. Kodunuzda bir bayt dizisini alan ve **Assembly.Load'a**geçen ortak bir yöntem varsa, bu nedenle arayanın adına bir derleme oluşturmak, güvenliği bozabilir.  
  
 Bu sorun aşağıdaki API öğeleri için geçerlidir:  
  
- <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
  
- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
  
## <a name="demand-vs-linkdemand"></a>Talep ve  LinkDemand  
 Bildirimsel güvenlik, benzer ancak çok farklı denetimler gerçekleştiren iki tür güvenlik denetimi sunar. Yanlış seçim zayıf güvenlik veya performans kaybına neden olabileceğinden, her iki formu da anlamalısınız.  
  
 Bildirimsel güvenlik aşağıdaki güvenlik denetimlerini sunar:  
  
- <xref:System.Security.Permissions.SecurityAction.Demand>kod erişim güvenlik yığını yürüyüş belirtir. Yığındaki tüm arayanların geçmek için belirtilen izin veya kimliğe sahip olması gerekir. Yığın farklı arayanlar içerebilir, çünkü **talep** her aramada oluşur. Bir yöntemi tekrar tekrar çağırırsanız, bu güvenlik denetimi her seferinde gerçekleşir. **Talep,** luring saldırılarına karşı iyi bir korumadır; geçmeye çalışan yetkisiz kod algılanacaktır.  
  
- [LinkDemand](link-demands.md) tam zamanında (JIT) derleme zamanında gerçekleşir ve yalnızca hemen arayanı denetler. Bu güvenlik denetimi arayanın arayan denetlemesi değildir. Bu denetim geçtikten sonra, arayan kaç kez arayabilir olursa olsun ek güvenlik yükü yoktur. Ancak, luring saldırılarına karşı hiçbir koruma da yoktur. **LinkDemand**ile, testi geçen ve kodunuzu referans alabilecek herhangi bir kod, kötü amaçlı kodun yetkili kodu kullanarak aramasına izin vererek güvenliği bozabilir. Bu nedenle, tüm olası zayıflıkları iyice önlenebilir sürece **LinkDemand** kullanmayın.  
  
    > [!NOTE]
    > .NET Framework 4'te bağlantı talepleri derlemelerde <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecurityRuleSet.Level2> öznitelik ile değiştirilmiştir. Tam <xref:System.Security.SecurityCriticalAttribute> güven için bir bağlantı talebi eşdeğerdir; ancak, aynı zamanda kalıtım kurallarını etkiler. Bu değişiklik hakkında daha fazla bilgi için Bkz. [Güvenlik Saydam Kodu, Düzey 2.](security-transparent-code-level-2.md)  
  
 **LinkDemand** kullanırken gerekli ekstra önlemler ayrı ayrı programlanmalıdır; güvenlik sistemi uygulama ile yardımcı olabilir. Herhangi bir hata bir güvenlik zafiyesi açar. Kodunuzu kullanan tüm yetkili kodlar aşağıdakileri yaparak ek güvenlik uygulamaktan sorumlu olmalıdır:  
  
- Arama kodunun sınıfa veya derlemeye erişimini kısıtlama.  
  
- Çağrılan kodda görünen arama koduna aynı güvenlik denetimlerini yerleştirmek ve arayanların bunu yapması zorunlu hale getirmek. Örneğin, belirtilen <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> bayrak için Bir **LinkDemand** ile korunan bir <xref:System.Security.Permissions.SecurityPermission> yöntem çağıran bir kod yazarsanız, yönteminiz de bu izin için bir **LinkDemand** (veya **Talep**, daha güçlü) yapmalıdır. Bunun istisnası, kodunuzdaki diğer güvenlik koruma mekanizmaları (talepler gibi) göz önüne alındığında, kodunuzun Güvenli olduğuna karar verdiğiniz sınırlı bir şekilde **LinkDemand**korumalı yöntemi kullanmasıdır. Bu istisnai durumda, arayan temel koddaki güvenlik korumasını zayıflatma sorumluluğunu üstleniyor.  
  
- Kodunuzu arayanların, kodunuzu kendi adlarına korumalı kodu araması için kandıramamasını sağlamak. Başka bir deyişle, arayanlar yetkili kodu korumalı koda belirli parametreleri geçirmeye veya ondan sonuçları geri almaya zorlayamaz.  
  
### <a name="interfaces-and-link-demands"></a>Arayüzler ve Bağlantı Talepleri  
 **LinkDemand'li** sanal bir yöntem, özellik veya olay bir taban sınıf yöntemini geçersiz kılıyorsa, etkili olabilmesi **için** taban sınıf yönteminin de geçersiz kılınması gerekir. Kötü amaçlı kodun temel türe geri dökümü ve taban sınıf yöntemini çağırması mümkündür. Ayrıca, bağlantı taleplerinin <xref:System.Security.AllowPartiallyTrustedCallersAttribute> derleme düzeyinde özniteliği olmayan derlemelere dolaylı olarak eklenebilir.  
  
 Arayüz yöntemleri de bağlantı talepleri olduğunda bağlantı talepleri ile yöntem uygulamalarını korumak için iyi bir uygulamadır. Arayüzlerle bağlantı taleplerini kullanma hakkında aşağıdakilere dikkat edin:  
  
- Bir Bağlantı **İsteği'ni** arabirim yöntemini uygulayan bir sınıfın ortak yöntemine yerletirseniz, arabirime döküm yapıp yöntemi çağırırsanız, **LinkDemand** zorlanmaz. Bu durumda, arabirime karşı bağlantı nız olduğundan, yalnızca arabirimdeki **LinkDemand** onurlandırılır.  
  
 Güvenlik sorunları için aşağıdaki öğeleri gözden geçirin:  
  
- Arabirim yöntemleriyle ilgili açık bağlantı talepleri. Bu bağlantı taleplerinin beklenen korumayı sunduğundan emin olun. Kötü amaçlı kod daha önce açıklandığı gibi bağlantı taleplerini aşmak için bir döküm kullanıp kullanamayacağını belirleyin.  
  
- Bağlantı talepleri ile sanal yöntemler uygulanır.  
  
- Uyguladıkları türler ve arabirimler. Bunlar bağlantı taleplerini tutarlı bir şekilde kullanmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../standard/security/secure-coding-guidelines.md)
