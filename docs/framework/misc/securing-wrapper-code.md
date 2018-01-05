---
title: "Sarmalayıcı Kodunun Güvenliğini Sağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [.NET Framework], wrapper code
- wrapper code, securing
- secure coding, wrapper code
- code security, wrapper code
ms.assetid: 1df6c516-5bba-48bd-b450-1070e04b7389
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5e29a2bdd0bfa338d0266c0841e11aa2ac366529
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="securing-wrapper-code"></a>Sarmalayıcı Kodunun Güvenliğini Sağlama
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Sarmalayıcı kodu, özellikle sarmalayıcı, kullanan kodu daha yüksek güven olduğu güvenlik zayıf benzersiz birtakım açabilirsiniz. Burada arayanın sınırlı izinlere uygun güvenlik denetiminde dahil edilmeyen, çağıran adına yapılan herhangi bir şey yararlanılabilir için olası bir zayıflık olur.  
  
 Hiçbir şey çağıran kendisini yapamadı sarmalayıcı aracılığıyla etkinleştirin. Bir şey, bunu sınırlı güvenlik denetimi, bir tam yığın ilerlemesi talep aksine içerir, bu özel tehlike olur. Tek düzeyli denetimleri söz konusu olduğunda, gerçek çağıran ve söz konusu API öğesi arasında sarmalayıcı kodu interposing, değil, böylece zayıflatmanın zaman güvenlik başarılı olması güvenlik denetimi kolayca neden olabilir.  
  
## <a name="delegates"></a>Temsilciler  
 Temsilci güvenlik .NET Framework sürümleri arasında farklılık gösterir.  Bu bölümde farklı temsilci davranışları açıklar ve güvenlik konuları ilişkili.  
  
### <a name="in-version-10-and-11-of-the-net-framework"></a>Sürüm 1.0 ve .NET Framework 1.1  
 Sürüm 1.0 ve 1.1 .NET Framework'ün bir temsilci oluşturucusu ve temsilci çağıran karşı aşağıdaki güvenlik eylemleri gerçekleştirin.  
  
-   Bir temsilci oluşturulduğunda, güvenlik bağlantı talepleri temsilci hedef metot temsilci oluşturan verme kümesi karşı gerçekleştirilir.  Güvenlik eylemi karşılamak için hata sonuçlanıyor bir <xref:System.Security.SecurityException>.  
  
-   Temsilci çağrıldığında, var olan tüm güvenlik taleplerini temsilci çağıran üzerinde gerçekleştirilir.  
  
 Kodunuzun her alan bir <xref:System.Delegate> deniyor olabilir ve daha az güvenilen koddan, izinlerini ilerletmek daha az güvenilir kod etkinleştirme değil emin olun. Bir temsilci gerçekleştirin ve daha sonra kullanırsanız, temsilci oluşturulan kod çağrı yığınındaki değil ve kod ya da temsilci altında korumalı işlemi çalışırsa izinlerini test değil. Kodunuz ve çağıran kodu oluşturan daha yüksek ayrıcalıkları varsa, Oluşturucusu çağrı yığını parçası olmadan arama yolu düzenleyebilirsiniz.  
  
### <a name="in-version-20-and-later-versions-of-the-net-framework"></a>Sürüm 2.0 ve .NET Framework'ün sonraki sürümler  
 Önceki sürümlerden farklı olarak sürüm 2.0 ve .NET Framework'ün sonraki sürümlerinde gerçekleştirir temsilci Oluşturucu karşı güvenlik eylemi temsilci oluşturduğunuzda ve çağrılır.  
  
-   Bir temsilci oluşturulduğunda, güvenlik bağlantı talepleri temsilci hedef metot temsilci oluşturan verme kümesi karşı gerçekleştirilir.  Güvenlik eylemi karşılamak için hata sonuçlanıyor bir <xref:System.Security.SecurityException>.  
  
-   Temsilci oluşturucunun verme kümesi de temsilci oluşturma sırasında yakalanan ve temsilci ile depolanır.  
  
-   Temsilci çağrıldığında, temsilci oluşturucu ve çağıran için farklı derlemeler aitse Temsilci oluşturucunun yakalanan verme kümesi geçerli bağlamda hiçbir taleplerini karşı önce değerlendirilir.  Ardından, var olan tüm güvenlik taleplerini temsilci çağıran üzerinde gerçekleştirilir.  
  
## <a name="link-demands-and-wrappers"></a>Bağlantı talepleri ve sarmalayıcıları  
 Bağlantı talepleri özel koruma durumuyla güvenlik altyapısında güçlendirilmiş ancak hala kodunuzda olası zayıflık kaynağı değil.  
  
 Tam olarak güvenilen kod özelliği, olay veya tarafından korunan yöntemini çağırırsa bir [LinkDemand](../../../docs/framework/misc/link-demands.md), varsa çağrı başarılı **LinkDemand** çağıran için izni denetimi karşılandığında. Ayrıca, tam olarak güvenilen kod bir sınıfı gösterir, bir özelliğin adını ve çağrıları alan kendi **almak** erişimcisi için çağıran yansıma kullanarak **almak** erişimci başarılı kullanıcı kodu mu olsa bile Bu özelliğe erişmek için izniniz yok. Bunun nedeni, **LinkDemand** tam olarak güvenilen kod olan yalnızca anında arayanlar, denetler. Esas olarak, tam olarak güvenilen kod, kullanıcı kodu bu çağrı yapma hakkı sahip olduğundan emin yapmadan kullanıcı kodu adına ayrıcalıklı bir çağrı yapılmasıdır.  
  
 Ortak dil çalışma zamanı gibi güvenlik açıklarını önlemeye yardımcı olmak için tam yığını taramasını isteğe bağlı olarak onay yöntemi, oluşturucusu, özelliği veya olayı tarafından korunan tüm dolaylı çağrısında genişleten bir **LinkDemand**. Bu koruma, bazı performans maliyetler doğurur ve güvenlik denetimi semantiğini değiştirir; tam yığın ilerlemesi isteğe bağlı olduğu daha hızlı ve tek düzeyli onay geçtiğinde başarısız olabilir.  
  
## <a name="assembly-loading-wrappers"></a>Derleme yükleme sarmalayıcıları  
 Yönetilen kod yüklemek için kullanılan çeşitli yöntemler de dahil olmak üzere <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, çağıran kanıtı derlemeleri yükleme. Bu yöntemlerin herhangi biriyle sarmalama, güvenlik sistemi, kodun izin verme, sarmalayıcı çağırana izinleri yerine derlemelerini yüklemek için kullanabilirsiniz. Daha az güvenilir kod, sarmalayıcı çağırana olandan daha yüksek izinleri verilir kod yüklemeye izin vermemelisiniz.  
  
 Tam güven ya da (bir Internet izin düzeyini çağıran dahil) olası çağıran daha önemli ölçüde daha yüksek güven sahip herhangi bir kodu bu şekilde güvenlik zayıflatabilir. Kodunuzu bir bayt dizisi alır ve buna ileten bir ortak yöntemi varsa **Assembly.Load**, böylece derlemenin arayanın adınıza oluşturma, bu güvenlik kesintiye uğrayabilir.  
  
 Bu sorun aşağıdaki API öğeleri için geçerlidir:  
  
-   <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
  
-   <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
  
## <a name="demand-vs-linkdemand"></a>İsteğe bağlı vs. LinkDemand  
 Bildirim temelli güvenlik benzer, ancak çok farklı denetimlerini gerçekleştiren güvenlik denetimleri iki tür sunar. Yanlış bir seçim zayıf güvenlik veya performans kaybına neden olabilir çünkü her iki forms anlamanız gerekir.  
  
 Bildirimsel güvenliği aşağıdaki güvenlik denetimlerini sunar:  
  
-   <xref:System.Security.Permissions.SecurityAction.Demand>kod erişim güvenliği yığın ilerlemesi belirtir. Yığında tüm arayanlar belirtilen izni veya kimlik geçirmek için olması gerekir. **İsteğe bağlı** yığın farklı arayanlar içerebileceğinden her çağrıda oluşur. Sürekli bir yöntemini çağırırsanız, bu güvenlik denetimi her zaman oluşur. **İsteğe bağlı** saldırıları; luring karşı iyi korumadır üzerinden alınmaya çalışılırken yetkisiz kod algılandı.  
  
-   [LinkDemand](../../../docs/framework/misc/link-demands.md) tam zamanında (JIT) derleme zamanında olur ve yalnızca ilk çağıran denetler. Bu güvenlik denetimini arayanın çağıran denetlemez. Bu onay geçirmeden sonra ek güvenlik yükü çağıran çağırabilirsiniz kaç kez olsun yoktur. Ancak, aynı zamanda saldırıları luring gelen koruması yoktur. İle **LinkDemand**, test geçirir ve kodunuzu başvurabilir herhangi bir kod olası güvenlik yetkili kod kullanarak çağırmak kötü amaçlı kod vererek bölünebilir. Bu nedenle, kullanmayın **LinkDemand** sürece tüm olası zayıf baştan sona önlenebilir.  
  
    > [!NOTE]
    >  İçinde [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], bağlantı talepleri değiştirilir tarafından <xref:System.Security.SecurityCriticalAttribute> özniteliğini <xref:System.Security.SecurityRuleSet.Level2> derlemeler. <xref:System.Security.SecurityCriticalAttribute> Tam güven için; bir bağlantı isteği eşdeğerdir ancak devralma kuralları de etkiler. Bu değişiklik hakkında daha fazla bilgi için bkz: [güvenliği saydam kod, Düzey 2](../../../docs/framework/misc/security-transparent-code-level-2.md).  
  
 Kullanırken gerekli ek güvenlik önlemleri **LinkDemand** ayrı ayrı programlanmış gerekir; zorlamasıyla Yardım güvenlik sistemi olabilir. Tüm hata güvenlik zayıflık açar. Tüm yetkili kod kullandığından kodunuzu aşağıdakileri yaparak ek güvenlik uygulamak için sorumlu olması gerekir:  
  
-   Sınıf veya derleme arama kodun erişimi kısıtlama.  
  
-   Aynı güvenlik yerleştirme çağrılan kod görünür çağıran kodu ve bunu yapmak için kendi arayanlar obligating denetler. Bir yöntemi çağırır kod yazma, örneğin, ile korunduğunu bir **LinkDemand** için <xref:System.Security.Permissions.SecurityPermission> ile <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> bayrağı belirtilmiş, yönteminizi de olmalısınız bir **LinkDemand** (veya **İsteğe bağlı**, daha güçlü olan) bu izni. Kodunuzu kullanıp kullanmadığını istisnadır **LinkDemand**-korumalı karar sınırlı bir şekilde yöntemdir güvenli, kodunuzda (örneğin, taleplerin) başka bir güvenlik koruma mekanizması verilen. Bu olağanüstü durumda arayan güvenlik Koruması arka plandaki kod zayıflatmanın içinde sorumluluk alır.  
  
-   Korumalı kod onların adına çağırma içine kodunuzu kodunuzu 's arayanlar kandırarak olduğunu olamaz sağlama. Diğer bir deyişle, arayanlar belirli parametreleri korumalı kod geçirmek için veya sonuçlar buradan geri almak için yetkili kodu zorlayamaz.  
  
### <a name="interfaces-and-link-demands"></a>Arabirimleri ve bağlantı talepleri  
 Sanal yöntemi, özelliği veya olay ile **LinkDemand** bir temel sınıf yöntemini geçersiz kılar temel sınıf yöntemi de aynı olmalıdır **LinkDemand** etkili olması için geçersiz kılınan yöntemi. Kötü amaçlı kod geri temel türe ve temel sınıf yöntemi çağırmak mümkündür. Ayrıca taleplerini bağlantı Not örtük olarak olmayan derlemeler eklenebilir <xref:System.Security.AllowPartiallyTrustedCallersAttribute> derleme düzeyinde bir öznitelik.  
  
 Arabirim yöntemleri ayrıca bağlantı talepleri olduğunda yöntemi uygulamaları bağlantı talepleri ile korumak için iyi bir uygulamadır. Bağlantı talepleri olan arabirimler kullanma hakkında aşağıdakileri unutmayın:  
  
-   Yerleştirdiğiniz varsa bir **LinkDemand** genel yöntemini bir arabirim yöntemini kullanan bir sınıfın **LinkDemand** sonra cast arabirimine ve yöntemi çağırma uygulanmaz. Bu durumda, arabirim karşı yalnızca bağlantılı olduğundan **LinkDemand** üzerinde ayardaki arabirimidir.  
  
 Güvenlik sorunları için aşağıdaki öğeleri inceleyin:  
  
-   Açık bağlantı talepleri arabirim yöntemleri. Bu bağlantı talepleri beklenen koruması sunar emin olun. Kötü amaçlı kod daha önce açıklandığı şekilde bağlantı talepleri almak için bir cast kullanıp kullanmadığını belirleyin.  
  
-   Bağlantı talepleri uygulanmış olan sanal yöntemleri.  
  
-   Türleri ve uyguladıkları arabirimler. Bu bağlantı talepleri tutarlı bir şekilde kullanmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenli Kodlama Yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
