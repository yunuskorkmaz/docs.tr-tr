---
title: Sarmalayıcı Kodunun Güvenliğini Sağlama
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], wrapper code
- wrapper code, securing
- secure coding, wrapper code
- code security, wrapper code
ms.assetid: 1df6c516-5bba-48bd-b450-1070e04b7389
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d4adfa5d592514c9a91c93095e7199f4b425b712
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596645"
---
# <a name="securing-wrapper-code"></a>Sarmalayıcı Kodunun Güvenliğini Sağlama
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Sarmalayıcı kodu, özellikle sarmalayıcı, kullanan kodu daha yüksek güven bulunduğu bir dizi benzersiz güvenlik zayıf açabilirsiniz. Burada arayanın sınırlı izinlere uygun güvenlik iade etme bulunmayan, bir çağıranın adına yapılan herhangi bir şey kullanılmasına potansiyel zayıflığından olur.  
  
 Hiç bir şey kendisini çağıran yapamadı sarmalayıcı aracılığıyla etkinleştirin. Bir şey yapmak yerine tam yığın ilerlemesi isteğe bağlı bir sınırlı güvenlik denetimi içerir, bu özel bir tehlike olur. Tek düzey denetimleri söz konusu olduğunda, gerçek arayan ve söz konusu API öğesi arasında sarmalayıcı kodu interposing, değil, böylece zayıflatmanın zaman güvenlik başarılı olması güvenlik denetimi kolayca neden olabilir.  
  
## <a name="delegates"></a>Temsilciler  
 Temsilci güvenlik .NET Framework sürümleri arasında farklılık gösterir.  Bu bölümde, farklı bir temsilci davranışlar açıklanmıştır ve güvenlikle ilişkili.  
  
### <a name="in-version-10-and-11-of-the-net-framework"></a>Sürüm 1.0 ve 1.1 .NET Framework'ün  
 Sürüm 1.0 ve 1.1 .NET Framework'ün bir temsilci oluşturucu ve bir temsilci çağıran karşı aşağıdaki güvenlik eylemleri gerçekleştirin.  
  
- Bir temsilci oluşturduğunuzda, güvenlik bağlantı talepleri temsilci hedef yöntemi temsilci oluşturucusu izin kümesi karşı yapılır.  Güvenlik eylemi gerçekleştirmek için hata sonuçlanıyor bir <xref:System.Security.SecurityException>.  
  
- Temsilci çağrıldığında, var olan herhangi bir güvenlik talebi temsilci çağıran üzerinde gerçekleştirilir.  
  
 Kodunuzu zaman alan bir <xref:System.Delegate> deniyor olabilir ve en az güvenilen koddan, izinlerini ilerletmek en az güvenilen kod etkinleştirme değil emin olun. Bir temsilci alın ve daha sonra kullanmak, temsilci oluşturulan kod, çağrı yığınındaki değil ve kod ya da temsilci altında korunan bir işlem çalışırsa izinlerini test değil. Kodunuz ve çağıran kod Oluşturucusu daha yüksek ayrıcalıkları varsa, oluşturan çağrı yığınının parçası olmadan arama yolu düzenleyebilirsiniz.  
  
### <a name="in-version-20-and-later-versions-of-the-net-framework"></a>Sürüm 2.0 ve sonraki sürümlerinde .NET Framework'ün  
 Önceki sürümlerden farklı olarak sürüm 2.0 ve sonraki sürümlerinde .NET Framework'ün gerçekleştirir temsilci oluşturucusu karşı güvenlik eylemi temsilci oluşturduğunuzda ve çağrılır.  
  
- Bir temsilci oluşturduğunuzda, güvenlik bağlantı talepleri temsilci hedef yöntemi temsilci oluşturucusu izin kümesi karşı yapılır.  Güvenlik eylemi gerçekleştirmek için hata sonuçlanıyor bir <xref:System.Security.SecurityException>.  
  
- Temsilci oluşturan kişinin izin kümesi de temsilci oluşturma sırasında yakalanan ve temsilci ile depolanan.  
  
- Temsilci çağrıldığında, temsilci oluşturucusu ve çağıran farklı derlemelere ait temsilci oluşturan kişinin yakalanan izin kümesini karşı geçerli bağlam içinde tüm talepleri önce değerlendirilir.  Ardından, var olan herhangi bir güvenlik talebi temsilci çağıran üzerinde gerçekleştirilir.  
  
## <a name="link-demands-and-wrappers"></a>Bağlantı talepleri ve sarmalayıcılar  
 Bağlantı talepleri olan bir özel koruma çalışması güvenlik altyapısında güçlendirilmiş, ancak hala kodunuzdaki olası zayıflık kaynağı.  
  
 Tam olarak güvenilen kod bir özelliği, olay veya metodu tarafından korunan çağırırsa bir [LinkDemand](../../../docs/framework/misc/link-demands.md), varsa çağrının başarılı **LinkDemand** çağıranın izin denetleme karşılandığında. Ayrıca, tam olarak güvenilen kod bir sınıf sunarsa bir özelliğin adını ve çağrıları alan kendi **Al** erişimcisi için çağıran yansıma kullanarak **alma** erişimci başarılı olsa da kullanıcı kod mu Bu özellik erişim hakkına sahip değil. Bunun nedeni, **LinkDemand** tam olarak güvenilen kodu olan yalnızca şu anki çağırıcı, denetler. Esas olarak, tam olarak güvenilen kod, kullanıcı kodu bu çağrı yapma hakkı olduğundan emin yapmadan kullanıcı kodu adına ayrıcalıklı bir çağrı yapıyor.  
  
 Ortak dil çalışma zamanı gibi güvenlik açıklarını önlemeye yardımcı olmak için herhangi bir yöntemi, oluşturucu, özellik veya olay tarafından korunan dolaylı çağrı yığını walking tam isteğe bağlı olarak kontrolü genişletir bir **LinkDemand**. Bu koruma, bazı performans maliyetleri doğurur ve güvenlik denetimi semantiğini değiştirir; tam bir yığın ilerlemesi isteğe bağlı, burada daha hızlı ve tek düzey onay geçtiğinde başarısız olabilir.  
  
## <a name="assembly-loading-wrappers"></a>Derleme yükleme sarmalayıcıları  
 Yönetilen kod yüklemek için kullanılan çeşitli yöntemler de dahil olmak üzere <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>, çağırana kanıtı derlemeleri yükleme. Bu yöntemlerin herhangi biriyle sarma durumunda güvenlik sistemi kodunuzun izin verme, sarmalayıcı çağırana izinleri yerine derlemeleri yüklemek için kullanabilirsiniz. En az güvenilen kod, sarmalayıcı çağırana ait olanlardan daha yüksek izinler verilir kod yüklemeye izin.  
  
 Tam güven veya önemli ölçüde daha yüksek güven (Internet izin düzeyini arayan dahil) bir olası çağıran herhangi bir kodu bu şekilde güvenlik zayıflatabilir. Kodunuzu bir bayt dizisi alır ve buna ileten bir genel yöntem varsa **Assembly.Load**, böylece bir derleme, arayanın adınıza oluşturma, bu güvenlik bozulabilir.  
  
 Bu sorun aşağıdaki API öğeleri için geçerlidir:  
  
- <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
  
- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
  
## <a name="demand-vs-linkdemand"></a>İsteğe bağlı vs. LinkDemand  
 İki tür benzerdir, ancak çok farklı denetimleri gerçekleştirmek güvenlik denetimlerini bildirime dayalı güvenlik sunar. Yanlış bir seçim zayıf güvenliği veya performansı kaybına neden olabilir çünkü her iki biçimi anlamanız gerekir.  
  
 Aşağıdaki güvenlik denetimlerini bildirime dayalı güvenlik sunar:  
  
- <xref:System.Security.Permissions.SecurityAction.Demand> kod erişim güvenlik yığın ilerlemesi belirtir. Yığınındaki tüm çağıranlar, belirtilen izin veya kimlik geçirilecek sahip olmalıdır. **İsteğe bağlı** yığın farklı çağıranlar içerebilir. Her çağrıda oluşur. Yöntemini tekrar tekrar çağırmak, bu güvenlik denetimini her zaman oluşur. **İsteğe bağlı** saldırıları; luring karşı iyi korumadır üzerinden alınmaya çalışılırken yetkisiz kodu algıladı.  
  
- [LinkDemand](../../../docs/framework/misc/link-demands.md) just-ın-time (JIT) derleme zamanında olur ve yalnızca şu anki çağırıcı denetler. Bu güvenlik denetimi, arayanın arayan denetlemez. Bu denetimi başarılı olduğunda, ek güvenlik yükü kaç kez çağıran çağırabilirsiniz ne olursa olsun yoktur. Ancak, ayrıca gelen saldırıları luring koruması yoktur. İle **LinkDemand**, testin başarılı olması ve kodunuzu başvurabilirsiniz herhangi bir kod olası güvenlik yetkili kod kullanarak çağırmak kötü amaçlı kod vererek bozabilir. Bu nedenle, kullanmayın **LinkDemand** sürece tüm olası zayıflıkları kapsamlı önlenebilir.  
  
    > [!NOTE]
    >  İçinde [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], bağlantı talepleri tarafından değiştirildi <xref:System.Security.SecurityCriticalAttribute> özniteliğini <xref:System.Security.SecurityRuleSet.Level2> derlemeler. <xref:System.Security.SecurityCriticalAttribute> Tam güven için bağlantı talebi eşdeğerdir ancak, devralma kuralları da etkiler. Bu değişiklik hakkında daha fazla bilgi için bkz. [güvenliği saydam kod, 2. düzey](../../../docs/framework/misc/security-transparent-code-level-2.md).  
  
 Kullanırken gereken ek güvenlik önlemleri **LinkDemand** ayrı ayrı programlanmak gerekir; zorlamasıyla yardımcı güvenlik sistemi olabilir. Herhangi bir hata, bir güvenlik açığına açılır. Tüm yetkili kod kullandığından kodunuzu aşağıdakileri yaparak ek güvenlik uygulamak için sorumlu olması gerekir:  
  
- Belirli bir sınıfın veya derlemenin çağıran kodun erişimi sınırlandırma.  
  
- Aynı güvenlik yerleştirme çağrılan kod üzerinde görünen çağıran kod ve bunu yapmak için çağrıda bulunanların obligating denetler. Bir yöntemi çağıran kod yazın, örneğin, ile korunan bir **LinkDemand** için <xref:System.Security.Permissions.SecurityPermission> ile <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> bayrağı belirtilmiş, yönteminizi de olmalısınız bir **LinkDemand** (veya **İsteğe**, daha güçlü olan) Bu izin için. Kodunuzun kullandığı istisnadır **LinkDemand**-korumalı yöntem istediğinize karar sınırlı bir şekilde güvenli, başka bir güvenlik koruma mekanizması (örneğin, talepleri), kodu içinde verilen. Bu olağanüstü bir durumda, çağıranın arka plandaki kod güvenlik koruması zayıflatmanın içinde sorumluluğunu üstlenir.  
  
- Kendi adınıza korunan kod arama içine kodunuzu kodunuzun çağıranlar kandırmaya emin olamaz sağlama. Diğer bir deyişle, Arayanların korunan kod için özel parametreleri geçirmek için ya da sonuçları geri almak için yetkili kod tutamaz.  
  
### <a name="interfaces-and-link-demands"></a>Arabirimleri ve bağlantı talepleri  
 Sanal yöntem, özellik veya olay ile **LinkDemand** bir temel sınıf yöntemini geçersiz kılan bir temel sınıf yöntemi de aynı olmalıdır **LinkDemand** etkili olması için geçersiz kılınan yöntemi. Kötü amaçlı kod geri temel türüne ve temel sınıf yöntemini çağırmak mümkündür. Ayrıca bağlantı talepleri Not örtük olarak sahip olmayan derlemeler için eklenebilir <xref:System.Security.AllowPartiallyTrustedCallersAttribute> derleme düzeyi özniteliği.  
  
 Arabirim yöntemleri bağlantı talepleri olduğunda bağlantı talepleri olan yöntem uygulamaları korumak için iyi bir uygulamadır. Bağlantı talepleri olan arabirimler kullanma hakkında aşağıdakileri unutmayın:  
  
- Koyarsanız bir **LinkDemand** bir arabirimin yöntemini uygulayan bir sınıfın ortak yöntemi **LinkDemand** ardından cast arabirimi ve yöntem çağrısı uygulanmaz. Bu durumda, arabirim karşı yalnızca bağlantılı **LinkDemand** arabirimde ödenmiş olan.  
  
 Aşağıdaki öğeler için güvenlik sorunları gözden geçirin:  
  
- Arabirim yöntemleri üzerinde açık bağlantı talepleri. Bu bağlantı talepleri beklenen koruma teklif emin olun. Kötü amaçlı kod daha önce açıklandığı gibi bağlantı talepleri almak için bir yayın kullanıp kullanmadığını belirleyin.  
  
- Uygulanan bağlantı talepleri olan sanal yöntemleri.  
  
- Türler ve arabirimler uyguladıkları. Bunlar tutarlı bir şekilde bağlantı talepleri kullanmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
