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
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215842"
---
# <a name="securing-wrapper-code"></a>Sarmalayıcı Kodunun Güvenliğini Sağlama
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Sarmalayıcı kodu, özellikle sarmalayıcı tarafından kullanılan koddan daha yüksek güven olduğunda, benzersiz bir güvenlik zayıflığı kümesi açabilir. Çağıranın sınırlı izinlerinin uygun güvenlik denetiminde yer aldığı bir arayan adına yapılan her şey, yararlanılacak potansiyel bir zayıftır.  
  
 Çağıranın kendisi tarafından yapamayacağı sarmalayıcı aracılığıyla hiçbir şey etkinleştirmeyin. Bu, tam yığın yapma isteğine karşılık sınırlı bir güvenlik denetimi içeren bir şey yaparken özel bir tehlike olur. Tek düzeyli denetimler dahil edildiğinde, gerçek arayan ve API öğesi arasındaki sarmalayıcı kodu enterpolaşmek, bu durumda olmaması durumunda güvenlik denetiminin başarılı olmasına neden olur, böylece güvenlik weakening.  
  
## <a name="delegates"></a>Temsilciler  
 Temsilci güvenliği .NET Framework sürümleri arasında farklılık gösterir.  Bu bölümde, farklı temsilci davranışları ve ilişkili güvenlik konuları açıklanmaktadır.  
  
### <a name="in-version-10-and-11-of-the-net-framework"></a>.NET Framework sürüm 1,0 ve 1,1 ' de  
 Sürüm 1,0 ve 1,1 .NET Framework bir temsilci Oluşturucusu ve bir temsilci çağıranına karşı aşağıdaki güvenlik eylemlerini gerçekleştirin.  
  
- Bir temsilci oluşturulduğunda, temsilci hedef yönteminde güvenlik bağlantısı talepleri, Temsilci oluşturucunun izin kümesine göre gerçekleştirilir.  <xref:System.Security.SecurityException>güvenlik eylemi sonucu elde etmek için hata oluştu.  
  
- Temsilci çağrıldığında, çağıran temsilci üzerindeki tüm mevcut güvenlik talepleri gerçekleştirilir.  
  
 Kodunuz, çağırabilecek daha az güvenilir bir koddan <xref:System.Delegate> aldığında, izinlerini iletmek için daha az güvenilir kod etkinleştirdiğinizden emin olun. Bir temsilci alıp daha sonra kullanacaksanız, temsilciyi oluşturan kod çağrı yığınında değildir ve temsilci içindeki veya altındaki kod korumalı bir işlem denerse, izinleri test edilmez. Kodunuzun ve arayan kodunuzun oluşturucusunun daha yüksek bir ayrıcalıkları varsa Oluşturucu, çağrı yığınının parçası olmadan çağrı yolunu düzenleyebilir.  
  
### <a name="in-version-20-and-later-versions-of-the-net-framework"></a>Sürüm 2,0 ve sonraki sürümlerinde .NET Framework  
 Önceki sürümlerden farklı olarak, sürüm 2,0 ve sonraki .NET Framework sürümleri, temsilci oluşturulup çağrıldığında temsilci Oluşturucu için güvenlik eylemi gerçekleştirir.  
  
- Bir temsilci oluşturulduğunda, temsilci hedef yönteminde güvenlik bağlantısı talepleri, Temsilci oluşturucunun izin kümesine göre gerçekleştirilir.  <xref:System.Security.SecurityException>güvenlik eylemi sonucu elde etmek için hata oluştu.  
  
- Temsilci oluşturucunun izin kümesi, temsilci oluşturma sırasında da yakalanır ve temsilciyle birlikte depolanır.  
  
- Temsilci çağrıldığında, temsilci oluşturan ve çağıran farklı derlemelere ait olduğunda, Temsilci oluşturucunun yakalanan izin kümesi ilk olarak geçerli bağlamdaki tüm taleplere göre değerlendirilir.  Sonra, temsilci çağıranlarındaki tüm mevcut güvenlik talepleri gerçekleştirilir.  
  
## <a name="link-demands-and-wrappers"></a>Bağlantı taleplerini ve sarmalayıcıları  
 Bağlantı taleplerine sahip özel bir koruma durumu güvenlik altyapısında güçlenebilir, ancak kodunuzda olası bir zayıflığın kaynağı olmaya devam etmektedir.  
  
 Tam güvenilir kod bir [LinkDemand](link-demands.md)tarafından korunan bir özelliği, olayı veya yöntemi çağırırsa, çağıran Için **LinkDemand** izin denetimi karşılanıyorsa çağrı başarılı olur. Ayrıca, tam olarak güvenilir kod, bir özelliğin adını alan ve yansıma kullanarak **Get** erişimcisini çağıran bir sınıfı kullanıma sunarsa, Kullanıcı kodu bu özelliğe erişim hakkına sahip olmasa bile **Get** erişimcisine çağrı başarılı olur. Bunun nedeni, **LinkDemand** 'in yalnızca hemen güvenilen kod olan hemen çağrıyı denetlediğinde. Temelde, tam olarak güvenilen kod, kullanıcı kodunun bu çağrıyı yapma hakkına sahip olduğundan emin olmadan Kullanıcı kodu adına ayrıcalıklı bir çağrı yapıyor.  
  
 Bu tür güvenlik boşluklarını önlemeye yardımcı olmak için, ortak dil çalışma zamanı denetimi bir yönteme, oluşturucuya, özelliğe veya bir **LinkDemand**tarafından korunan olaya dolaylı çağrı üzerinde tam yığın yürüme talebine genişletir. Bu koruma, bazı performans maliyetleri doğurur ve güvenlik denetiminin semantiğini değiştirir; tam yığın ilerme isteği, daha hızlı, tek düzeyli bir denetim geçirildiğinde başarısız olabilir.  
  
## <a name="assembly-loading-wrappers"></a>Derleme yükleme sarmalayıcıları  
 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>de dahil olmak üzere yönetilen kodu yüklemek için kullanılan çeşitli yöntemler, arayanın kanıtını içeren derlemeleri yükler. Bu yöntemlerin herhangi birini sarmaladıysanız, güvenlik sistemi, derlemeleri yüklemek için çağıranın, sarmalayıcısına olan izinlerinin yerine kodunuzun izin iznini kullanabilir. Çağıranlarınızın sarmalayıcısına göre daha yüksek izinlerle daha fazla izin verilen kodu yüklemesine izin vermeniz gerekir.  
  
 Bir olası çağırandan (Internet izinleri düzeyi çağıran dahil) tam güvene veya önemli ölçüde daha yüksek güvene sahip olan tüm kodlar güvenliği bu şekilde zayıflatabilir. Kodunuzun, bir bayt dizisi alan ve bunu **Assembly. Load**öğesine ileten bir ortak yöntemi varsa, bunu çağıranın adına bir derleme oluşturarak güvenlik kesintiye uğramayabilir.  
  
 Bu sorun aşağıdaki API öğeleri için geçerlidir:  
  
- <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
  
- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
  
## <a name="demand-vs-linkdemand"></a>Talep ve  LinkDemand  
 Bildirime dayalı güvenlik, benzer ancak çok farklı denetimler gerçekleştiren iki tür güvenlik denetimi sunar. Yanlış seçim zayıf güvenlik veya performans kaybıyla sonuçlanabileceğinden, her iki formu anlamalısınız.  
  
 Bildirime dayalı güvenlik aşağıdaki güvenlik denetimlerini sunar:  
  
- <xref:System.Security.Permissions.SecurityAction.Demand> kod erişimi güvenlik yığını yürüi belirtir. Yığındaki tüm çağıranlar, geçirilecek belirtilen izne veya kimliğe sahip olmalıdır. Yığın farklı çağıranlar içerebileceğinden, her çağrıda **talep** oluşur. Bir yöntemi tekrar tekrar çağırırsanız, bu güvenlik denetimi her seferinde gerçekleşir. **Talep** , LTE saldırılarına karşı iyi bir koruma; üzerinden almaya çalışan yetkisiz kod algılanır.  
  
- [LinkDemand](link-demands.md) tam ZAMANıNDA (JIT) derleme zamanında gerçekleşir ve yalnızca anında çağrıyı denetler. Bu güvenlik denetimi çağıranın çağıranı denetlemez. Bu denetim başarılı olduktan sonra, çağıranın kaç kez arayanına bakılmaksızın ek bir güvenlik yükü yoktur. Ancak, LTE saldırılarına karşı koruma de yoktur. **LinkDemand**ile, testi geçen ve kodunuza başvuruda bulunan tüm kodlar, kötü amaçlı kodun yetkili kodu kullanarak çağrı yapmasına izin vererek güvenlik kesintiye uğramasına yol açabilir. Bu nedenle, tüm olası zayıf yanlar tamamen önlenemez olmadığı için **LinkDemand** kullanmayın.  
  
    > [!NOTE]
    > .NET Framework 4 ' te, bağlantı istekleri <xref:System.Security.SecurityRuleSet.Level2> derlemelerdeki <xref:System.Security.SecurityCriticalAttribute> özniteliğiyle değiştirilmiştir. <xref:System.Security.SecurityCriticalAttribute>, tam güven için bağlantı talebine eşdeğerdir; Ancak, devralma kurallarını da etkiler. Bu değişiklik hakkında daha fazla bilgi için bkz. [güvenlik-saydam kod, düzey 2](security-transparent-code-level-2.md).  
  
 **LinkDemand** kullanılırken gereken ek önlemler ayrı ayrı programlanabilir olmalıdır; güvenlik sistemi, zorlamada yardımcı olabilir. Herhangi bir hata, güvenlik zayıflılığını açar. Kodunuzu kullanan tüm yetkili kodların, aşağıdakileri yaparak ek güvenlik uygulamaktan sorumlu olması gerekir:  
  
- Çağıran kodun sınıf veya derlemeye erişimini kısıtlama.  
  
- Aynı güvenlik denetimlerinin Çağrılmakta olan kodda görünen çağrı kodu üzerinde yerleştirilmesi ve bunu yapmak için çağıranları obligating. Örneğin, belirtilen <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> bayrağıyla <xref:System.Security.Permissions.SecurityPermission> için **LinkDemand** ile korunan bir yöntemi çağıran kodu yazarsanız, yönteminiz bu izin Için bir **LinkDemand** (veya daha güçlü olan **istek**) de oluşturmanız gerekir. Kodunuz, kodunuzun **talep**korumalı yöntemini, kodunuzda güvenli olduğuna, diğer güvenlik koruması mekanizmalarına (talepler gibi) verilen bir şekilde kullanıyorsa, bu özel durumdur. Bu olağanüstü durumda, çağıran kodda güvenlik korumasını weakening konusunda bir sorumluluğu alır.  
  
- Kodunuzun çağıranlarının kendi adına korumalı kodu çağırmak için kodunuzu veremeyeceğinden emin olma. Diğer bir deyişle, arayanlar, yetkili kodun korunan koda belirli parametreleri geçmesini veya bundan sonra sonuç almasını zorunlu hale getirilemez.  
  
### <a name="interfaces-and-link-demands"></a>Arabirimler ve bağlantı talepleri  
 **LinkDemand** ile bir sanal yöntem, özellik veya olay bir temel sınıf yöntemini geçersiz kılıyorsa, temel sınıf yönteminin etkin olması için geçersiz kılınan yöntem Için aynı **LinkDemand** öğesine sahip olması gerekir. Kötü amaçlı kodun temel türe geri dönüştürülmesi ve temel sınıf yöntemini çağırması mümkündür. Ayrıca, bağlantı taleplerinin <xref:System.Security.AllowPartiallyTrustedCallersAttribute> derleme düzeyi özniteliğine sahip olmayan derlemelere örtülü olarak eklenebileceğini unutmayın.  
  
 Arabirim yöntemlerinin bağlantı taleplerine de sahip olduğu durumlarda yöntem uygulamalarını bağlantı taleplerine karşı korumak iyi bir uygulamadır. Arabirimler ile bağlantı taleplerini kullanma hakkında aşağıdakilere göz önünde edin:  
  
- Arabirim yöntemi uygulayan bir sınıfın genel yöntemine bir **LinkDemand** yerleştirirseniz, daha sonra arabirime ve yöntemini çağırdığınızda **LinkDemand** zorlanmaz. Bu durumda, arayüzle bağlantılı olduğunuzdan yalnızca arabirimdeki **LinkDemand** kabul edilir.  
  
 Güvenlik sorunları için aşağıdaki öğeleri gözden geçirin:  
  
- Arabirim yöntemlerinde açık bağlantı talepleri. Bu bağlantı taleplerinin beklenen korumayı sağlayıp sağlamadığından emin olun. Kötü amaçlı kodun, daha önce açıklandığı gibi bağlantı taleplerini aşmak için bir dönüştürme kullanıp kullanamayacağını belirleme.  
  
- Bağlantı taleplerine uygulanan sanal yöntemler.  
  
- Türleri ve uygulamadıkları arabirimler. Bunlar bağlantı taleplerini sürekli olarak kullanmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../standard/security/secure-coding-guidelines.md)
