---
title: Derleme Yükleme için En İyi Yöntemler
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies,binding
- LoadFrom method
- default load context
- TypeLoadException class,causes
- assembly loading errors
- load contexts
- assemblies,loading
- LoadWithPartialName method
- load-from context
ms.assetid: 68d1c539-6a47-4614-ab59-4b071c9d4b4c
ms.openlocfilehash: d1b6c2cd9f96a4acf48cbced48a86bc3e3409562
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716583"
---
# <a name="best-practices-for-assembly-loading"></a>Derleme Yükleme için En İyi Yöntemler
Bu makalede <xref:System.InvalidCastException>, <xref:System.MissingMethodException>ve diğer hatalara yol açabilecek kimlik tür sorunlarından kaçınmanın yolları anlatılmaktadır. Makalede aşağıdaki öneriler ele alınmaktadır:  
  
- [Yük bağlamlarının olumlu ve olumsuz yönlerini anlayın](#load_contexts)  
  
- [Kısmi derleme adlarında bağlamayı önleyin](#avoid_partial_names)  
  
- [Bir derlemeyi birden çok bağlama yüklemeden kaçının](#avoid_loading_into_multiple_contexts)  
  
- [Bir derlemenin birden çok sürümünü aynı içeriğe yüklemeden kaçının](#avoid_loading_multiple_versions)  
  
- [Varsayılan yükleme bağlamına geçmeyi düşünün](#switch_to_default)  
  
 İlk öneri, [Yük bağlamlarının olumlu ve olumsuz yönlerini anlamak](#load_contexts)için, bunların hepsi yük bağlamlarına bağlı olduğundan diğer önerilere yönelik arka plan bilgileri sağlar.  
  
<a name="load_contexts"></a>   
## <a name="understand-the-advantages-and-disadvantages-of-load-contexts"></a>Yük bağlamlarının olumlu ve olumsuz yönlerini anlayın  
 Bir uygulama etki alanı içinde, derlemeler üç bağlamdan birine yüklenebilir ya da bağlam olmadan yüklenebilirler:  
  
- Varsayılan yükleme bağlamı, genel derleme önbelleğini yoklaerek bulunan derlemeleri, çalışma zamanının barındırıldığı ana bilgisayar derleme deposunu (örneğin, SQL Server) ve uygulama etki alanının <xref:System.AppDomainSetup.ApplicationBase%2A> ve <xref:System.AppDomainSetup.PrivateBinPath%2A> içerir. <xref:System.Reflection.Assembly.Load%2A> yönteminin çoğu aşırı yüklemesi derlemeleri bu bağlamda yükler.  
  
- Yük-from bağlamı, yükleyici tarafından aranmayan konumlardan yüklenen derlemeleri içerir. Örneğin, eklentiler uygulama yolunda olmayan bir dizine yüklenmiş olabilir. <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>, <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType>ve <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType> yol tarafından yüklenen yöntemlerin örnekleridir.  
  
- Yalnızca yansıma bağlamı <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> ve <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> yöntemleriyle yüklenen derlemeleri içerir. Bu bağlamdaki kod yürütülemiyor, bu nedenle burada açıklanmıyor. Daha fazla bilgi için bkz. [nasıl yapılır: derlemeleri yalnızca yansıma bağlamına yükleme](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
- Yansıma yayma kullanarak geçici bir dinamik derleme oluşturduysanız, derleme hiçbir bağlamda değildir. Ek olarak, <xref:System.Reflection.Assembly.LoadFile%2A> yöntemi kullanılarak yüklenen çoğu derleme bağlam olmadan yüklenir ve kimlikleri (ilke uygulandıktan sonra), kendi genel derleme önbelleğinde olduğunu belirler ve bayt dizilerden yüklenen derlemeler bağlam olmadan yüklenir.  
  
 Yürütme bağlamlarının, aşağıdaki bölümlerde ele alındığı gibi avantajları ve dezavantajları vardır.  
  
### <a name="default-load-context"></a>Varsayılan yükleme bağlamı  
 Derlemeler varsayılan yükleme bağlamına yüklendiğinde, bağımlılıkları otomatik olarak yüklenir. Varsayılan yükleme bağlamına yüklenen bağımlılıklar, varsayılan yükleme bağlamındaki derlemeler veya yük-from bağlamı için otomatik olarak bulunur. Derleme kimliğine göre yükleme, derlemelerin bilinmeyen sürümlerinin kullanılmadığından emin olarak uygulamaların kararlılığını artırır ( [kısmi derleme adlarında bağlamaktan kaçının](#avoid_partial_names) bölümünde).  
  
 Varsayılan yükleme bağlamının kullanılması aşağıdaki dezavantajlara sahiptir:  
  
- Diğer bağlamlara yüklenen bağımlılıklar kullanılamaz.  
  
- Yoklama yolu dışındaki konumlardan derlemeleri varsayılan yükleme bağlamına yükleyemezsiniz.  
  
### <a name="load-from-context"></a>Yük-bağlam  
 Yük-from bağlamı, uygulama yolu altında olmayan bir yoldan bir derleme yüklemenize olanak sağlar ve bu nedenle, yoklama içine dahil değildir. Yol bilgileri bağlam tarafından korunduğundan, bağımlılıkların bu yoldan bulunmasını ve yüklenmesini sağlar. Ayrıca, bu bağlamdaki derlemeler varsayılan yükleme bağlamına yüklenen bağımlılıkları kullanabilir.  
  
 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> yöntemi veya yol tarafından yüklenen diğer yöntemlerden birini kullanarak derlemeleri yüklemek aşağıdaki dezavantajlara sahiptir:  
  
- Aynı kimliğe sahip bir derleme zaten yüklüyse <xref:System.Reflection.Assembly.LoadFrom%2A>, farklı bir yol belirtilmiş olsa bile yüklenen derlemeyi döndürür.  
  
- Bir derleme <xref:System.Reflection.Assembly.LoadFrom%2A>ile yüklenirse ve daha sonra varsayılan yükleme bağlamındaki bir derleme, görünen ad ile aynı derlemeyi yüklemeye çalışırsa, yükleme girişimi başarısız olur. Bu, bir derlemenin serisi kaldırıldığında ortaya çıkar.  
  
- Bir derleme <xref:System.Reflection.Assembly.LoadFrom%2A>ile yüklenmişse ve yoklama yolu aynı kimliğe sahip ancak farklı bir konumda bir derleme içeriyorsa, bir <xref:System.InvalidCastException>, <xref:System.MissingMethodException>ya da başka bir beklenmeyen davranış oluşabilir.  
  
- <xref:System.Reflection.Assembly.LoadFrom%2A> talepler <xref:System.Security.Permissions.FileIOPermissionAccess.Read?displayProperty=nameWithType> ve <xref:System.Security.Permissions.FileIOPermissionAccess.PathDiscovery?displayProperty=nameWithType>ya da <xref:System.Net.WebPermission>, belirtilen yolda.  
  
- Derleme için yerel bir görüntü varsa, bu kullanılmaz.  
  
- Derleme, etki alanı nötr olarak yüklenemez.  
  
- 1,0 ve 1,1 .NET Framework sürümlerinde, ilke uygulanmaz.  
  
### <a name="no-context"></a>Bağlam yok  
 Bağlam olmadan yükleme, yansıma yayma ile oluşturulan geçici derlemeler için tek seçenektir. Bağlam olmadan yükleme, aynı kimliğe sahip birden fazla derlemeyi tek bir uygulama etki alanında yüklemenin tek yoludur. Yoklama maliyeti kaçınılıyor.  
  
 Bayt dizilerinizden yüklenen derlemeler, ilke uygulandığında oluşturulan derleme kimliği, genel derleme önbelleğindeki bir derlemenin kimliğiyle eşleştiğinde bağlam olmadan yüklenir; Bu durumda, derleme genel derleme önbelleğinden yüklenir.  
  
 Derlemeleri bağlam olmadan yüklemek aşağıdaki dezavantajlara sahiptir:  
  
- Diğer derlemeler, <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olayını işlemediğiniz müddetçe, bağlamı olmadan yüklenen derlemelere bağlanamaz.  
  
- Bağımlılıklar otomatik olarak yüklenmez. Onları bağlam olmadan önyükleyebilir, varsayılan yükleme bağlamına önceden yükleyebilir veya <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olayını işleyerek yükleyebilirsiniz.  
  
- Aynı kimliğe sahip birden fazla derlemeyi bağlama olmadan yüklemek, aynı kimliğe sahip derlemeleri birden çok bağlamla yüklerken oluşan tür kimlik sorunlarına neden olabilir. Bkz. [bir derlemeyi birden çok bağlama yüklemeden kaçının](#avoid_loading_into_multiple_contexts).  
  
- Derleme için yerel bir görüntü varsa, bu kullanılmaz.  
  
- Derleme, etki alanı nötr olarak yüklenemez.  
  
- 1,0 ve 1,1 .NET Framework sürümlerinde, ilke uygulanmaz.  
  
<a name="avoid_partial_names"></a>   
## <a name="avoid-binding-on-partial-assembly-names"></a>Kısmi derleme adlarında bağlamayı önleyin  
 Bir derlemeyi yüklerken derleme görünen adının (<xref:System.Reflection.Assembly.FullName%2A>) yalnızca bir kısmını belirttiğinizde Kısmi ad bağlama gerçekleşir. Örneğin, sürüm, kültür ve ortak anahtar belirtecini atlayarak <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemini yalnızca derlemenin basit adıyla çağırabilirsiniz. Ya da öncelikle <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemini çağıran ve derlemeyi bulamıyorsa, genel derleme önbelleğinde arama yapan ve derlemenin en son kullanılabilir sürümünü yükleyen <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> yöntemini çağırabilirsiniz.  
  
 Kısmi ad bağlama, aşağıdakiler de dahil olmak üzere birçok soruna neden olabilir:  
  
- <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> yöntemi, aynı basit ada sahip farklı bir derleme yükleyebilir. Örneğin, iki uygulama, genel derleme önbelleğine `GraphicsLibrary` basit ada sahip olan iki tamamen farklı derleme yükleyebilirler.  
  
- Gerçekten yüklenen derleme geriye dönük olarak uyumlu olmayabilir. Örneğin, sürümü belirtmediğinde programınızın ilk olarak kullanılmak üzere yazıldığı sürümden daha sonraki bir sürümün yüklenmesine yol açabilir. Sonraki sürümdeki değişiklikler uygulamanızda hatalara neden olabilir.  
  
- Gerçekten yüklenen derleme ileri uyumlu olmayabilir. Örneğin, uygulamanızı derlemenin en son sürümüyle oluşturup test edebilir, ancak kısmi bağlama uygulamanızın kullandığı özellikleri olmayan daha önceki bir sürümü yükleyebilir.  
  
- Yeni uygulamaların yüklenmesi, mevcut uygulamaları bozabilir. <xref:System.Reflection.Assembly.LoadWithPartialName%2A> yöntemini kullanan bir uygulama, paylaşılan bir derlemenin daha yeni, uyumsuz bir sürümü yüklenerek bozulabilir.  
  
- Beklenmeyen bağımlılık yüklemesi meydana gelebilir. Bir bağımlılığı paylaşan iki derleme yüklersiniz, bunları kısmi bağlama ile yüklemek, derlenmiş veya test edilmemiş bir bileşeni kullanarak bir derlemenin oluşmasına neden olabilir.  
  
 Neden olabileceği sorunlar nedeniyle <xref:System.Reflection.Assembly.LoadWithPartialName%2A> yöntemi kullanılmıyor olarak işaretlendi. Bunun yerine <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemini kullanmanızı ve tam derleme görünen adlarını belirtmenizi öneririz. Bkz. [Yük bağlamlarının olumlu ve olumsuz yönlerini anlayın](#load_contexts) ve [varsayılan yükleme bağlamına geçmeyi düşünün](#switch_to_default).  
  
 Derlemeyi daha kolay hale getiren <xref:System.Reflection.Assembly.LoadWithPartialName%2A> yöntemini kullanmak istiyorsanız, uygulamanızın eksik derlemeyi tanımlayan bir hata iletisiyle başarısız olduğunu, derlemenin bilinmeyen bir sürümünü kullanarak otomatik olarak daha iyi bir kullanıcı deneyimi sağlayabileceğini göz önünde bulundurun. Bu, öngörülemeyen davranışlara ve güvenlik delikleri oluşmasına neden olabilir.  
  
<a name="avoid_loading_into_multiple_contexts"></a>   
## <a name="avoid-loading-an-assembly-into-multiple-contexts"></a>Bir derlemeyi birden çok bağlama yüklemeden kaçının  
 Bir derlemeyi birden çok bağlama yüklemek tür kimlik sorunlarına neden olabilir. Aynı türden iki farklı bağlamda aynı tür yüklüyse, aynı ada sahip iki farklı tür yüklenmiş olur. Bir türü diğerine dönüştürmeye çalışırsanız <xref:System.InvalidCastException>, `MyType` türündeki karmaşık iletiyle `MyType`türüne yayınlanamaz.  
  
 Örneğin, `ICommunicate` arabiriminin, programınız tarafından başvurulan `Utility`adlı bir derlemede bildirildiği ve ayrıca programınızın yüklediği diğer derlemelerin olduğunu varsayalım. Bu diğer derlemeler `ICommunicate` arabirimini uygulayan türler içerir ve programınızın bunları kullanmasına izin verir.  
  
 Artık programınız çalıştırıldığında ne olacağını düşünün. Programınızın başvurduğu derlemeler varsayılan yükleme bağlamına yüklenir. <xref:System.Reflection.Assembly.Load%2A> yöntemini kullanarak bir hedef derlemeyi kimliğine göre yüklerseniz, varsayılan yükleme bağlamında olur ve bu nedenle bağımlılıklarıdır. Hem programınızın hem de hedef derlemenin aynı `Utility` derlemesini kullanması gerekir.  
  
 Ancak, <xref:System.Reflection.Assembly.LoadFile%2A> yöntemini kullanarak hedef derlemeyi dosya yoluyla yüklediğinizi varsayalım. Derleme herhangi bir bağlam olmadan yüklenir, bu nedenle bağımlılıkları otomatik olarak yüklenmez. Bağımlılığı sağlamak için <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olayına yönelik bir işleyiciniz olabilir ve <xref:System.Reflection.Assembly.LoadFile%2A> yöntemini kullanarak hiçbir bağlam olmadan `Utility` derlemesini yükleyebilir. Artık hedef derlemede bulunan bir türün örneğini oluşturduğunuzda ve onu `ICommunicate`türünde bir değişkene atamayı denerseniz, çalışma zamanı `Utility` derlemesinin iki kopyasının `ICommunicate` arabirimlerini farklı türlerde olacak şekilde düşündüğü için bir <xref:System.InvalidCastException> oluşturulur.  
  
 Bir derlemenin birden çok bağlamına yüklenebileceği birçok farklı senaryo vardır. En iyi yaklaşım, hedef derlemenin uygulama yolunuzda yerini alarak ve <xref:System.Reflection.Assembly.Load%2A> yöntemini tam ekran adıyla kullanarak çakışmaları önlemelidir. Derleme daha sonra varsayılan yükleme bağlamına yüklenir ve her iki derleme de aynı `Utility` derlemesini kullanır.  
  
 Hedef derlemenin uygulama yolunun dışında kalması gerekiyorsa, yük-from bağlamına yüklemek için <xref:System.Reflection.Assembly.LoadFrom%2A> yöntemini kullanabilirsiniz. Hedef bütünleştirilmiş kod, uygulamanızın `Utility` derlemesine bir başvuru ile derlenmişse, uygulamanızın varsayılan yükleme bağlamına yüklediği `Utility` derlemesini kullanacaktır. Hedef derlemenin, uygulama yolunuz dışında bulunan `Utility` derlemesinin bir kopyasına bağımlılığı varsa, sorunların gerçekleşebileceğini unutmayın. Uygulamanız `Utility` derlemeyi yüklemeden önce bu derleme yük devretme bağlamına yüklenirse, uygulamanızın yükü başarısız olur.  
  
 [Varsayılan yükleme bağlamı bölümüne geçmeyi düşünün](#switch_to_default) <xref:System.Reflection.Assembly.LoadFile%2A> ve <xref:System.Reflection.Assembly.LoadFrom%2A>gibi dosya yolu yüklemelerinin kullanımına yönelik alternatifleri açıklar.  
  
<a name="avoid_loading_multiple_versions"></a>   
## <a name="avoid-loading-multiple-versions-of-an-assembly-into-the-same-context"></a>Bir derlemenin birden çok sürümünü aynı Içeriğe yüklemeden kaçının  
 Bir derlemenin birden çok sürümünü tek bir yük bağlamına yüklemek tür kimlik sorunlarına neden olabilir. Aynı tür aynı derlemenin iki sürümünden yüklüyse, aynı ada sahip iki farklı tür yüklenmiş olur. Bir türü diğerine dönüştürmeye çalışırsanız <xref:System.InvalidCastException>, `MyType` türündeki karmaşık iletiyle `MyType`türüne yayınlanamaz.  
  
 Örneğin, programınız `Utility` derlemesinin bir sürümünü doğrudan yükleyebilir ve daha sonra `Utility` derlemesinin farklı bir sürümünü yükleyen başka bir derlemeyi yükleyebilir. Ya da bir kodlama hatası, uygulamanızdaki iki farklı kod yolunun bir derlemenin farklı sürümlerini yüklemesine neden olabilir.  
  
 Varsayılan yükleme bağlamında, <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemini kullandığınızda ve farklı sürüm numaraları içeren tüm derleme görünen adlarını belirttiğinizde bu sorun oluşabilir. Bağlamı olmadan yüklenen derlemeler için, bu soruna farklı yollardan aynı derlemeyi yüklemek üzere <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> yöntemi kullanılarak neden olabilir. Çalışma zamanı, kimlikleri aynı olsa bile farklı yollardan yüklenen iki derlemeyi farklı derlemeler olacak şekilde değerlendirir.  
  
 Tür kimlik sorunlarına ek olarak, bir derlemenin birden çok sürümü, bir derlemenin bir sürümünden yüklenen bir tür, bu türü farklı bir sürümden bekleyen koda geçirilirse bir <xref:System.MissingMethodException> neden olabilir. Örneğin, kod sonraki sürüme eklenmiş bir yöntemi bekleyebilir.  
  
 Sürümler arasında tür davranışı değiştiyse daha hafif hatalar meydana gelebilir. Örneğin, bir yöntem beklenmeyen bir özel durum oluşturabilir veya beklenmeyen bir değer döndürebilir.  
  
 Yalnızca bir derlemenin yalnızca bir sürümünün yüklendiğinden emin olmak için kodunuzu dikkatle gözden geçirin. Belirli bir zamanda hangi derlemelerin yüklendiğini öğrenmek için <xref:System.AppDomain.GetAssemblies%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz.  
  
<a name="switch_to_default"></a>   
## <a name="consider-switching-to-the-default-load-context"></a>Varsayılan yükleme bağlamına geçmeyi düşünün  
 Uygulamanızın derleme yükleme ve dağıtım düzenlerini inceleyin. Bayt dizilerden yüklenen derlemeleri ortadan kaldırabilir misiniz? Derlemeleri yoklama yoluna taşıyabilir miyim? Derlemeler genel derleme önbelleğinde veya uygulama etki alanının yoklama yolunda bulunuyorsa (yani, <xref:System.AppDomainSetup.ApplicationBase%2A> ve <xref:System.AppDomainSetup.PrivateBinPath%2A>), derlemeyi kimliğine göre yükleyebilirsiniz.  
  
 Tüm derlemelerinizi yoklama yoluna koymak mümkün değilse, .NET Framework eklenti modelini kullanma, derlemeleri genel derleme önbelleğine yerleştirme veya uygulama etki alanları oluşturma gibi alternatifleri göz önünde bulundurun.  
  
### <a name="consider-using-the-net-framework-add-in-model"></a>.NET Framework eklentisi modelini kullanmayı düşünün  
 Genellikle uygulama tabanında yüklenmeyen eklentileri uygulamak için Load-from bağlamını kullanıyorsanız, .NET Framework eklenti modelini kullanın. Bu model uygulama etki alanı veya işlem düzeyinde yalıtım sağlar, böylece uygulama etki alanlarını kendiniz yönetmenizi zorunlu değildir. Eklenti modeli hakkında daha fazla bilgi için bkz. eklentiler [ve genişletilebilirlik](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).  
  
### <a name="consider-using-the-global-assembly-cache"></a>Genel derleme önbelleğini kullanmayı düşünün  
 Varsayılan Yük bağlamının avantajlarını kaybetmeden veya diğer bağlamların dezavantajlarını kaybetmeksizin, uygulama tabanının dışında paylaşılan bir derleme yolunun avantajlarından yararlanmak için bütünleştirilmiş kodları genel derleme önbelleğine yerleştirin.  
  
### <a name="consider-using-application-domains"></a>Uygulama etki alanlarını kullanmayı düşünün  
 Derlemelerin bazılarının uygulamanın yoklama yolunda dağıtılamadığını belirlerseniz, bu derlemeler için yeni bir uygulama etki alanı oluşturmayı düşünün. Yeni uygulama etki alanını oluşturmak için bir <xref:System.AppDomainSetup> kullanın ve yüklemek istediğiniz derlemeleri içeren yolu belirtmek için <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> özelliğini kullanın. Araştırmanız için birden çok dizininiz varsa, <xref:System.AppDomainSetup.ApplicationBase%2A> bir kök dizine ayarlayabilir ve <xref:System.AppDomainSetup.PrivateBinPath%2A?displayProperty=nameWithType> özelliğini kullanarak araştırmanın alt dizinlerini tanımlayabilirsiniz. Alternatif olarak, birden çok uygulama etki alanı oluşturabilir ve her bir uygulama etki alanının <xref:System.AppDomainSetup.ApplicationBase%2A> derlemeleri için uygun yola ayarlayabilirsiniz.  
  
 Bu derlemeleri yüklemek için <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metodunu kullanabileceğinizi unutmayın. Bunlar artık yoklama yolunda olduklarından, yük-from bağlamı yerine varsayılan yükleme bağlamına yüklenecektir. Ancak, <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemine geçmeniz ve doğru sürümlerin her zaman kullanıldığından emin olmak için tam derleme görünen adları sağlamanız önerilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>
- <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>
