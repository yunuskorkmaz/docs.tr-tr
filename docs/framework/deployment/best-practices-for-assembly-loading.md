---
title: "Derleme Yükleme için En İyi Yöntemler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cb6671af34c22d824368de014362452ac9014279
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="best-practices-for-assembly-loading"></a>Derleme Yükleme için En İyi Yöntemler
Yol açabilir türü kimliğinin sorunları önlemek için bu makalede ele <xref:System.InvalidCastException>, <xref:System.MissingMethodException>ve diğer hataları. Makaleyi aşağıdaki öneriler ele alınmıştır:  
  
-   [Olumlu ve olumsuz yönlerini yükleme bağlamları anlama](#load_contexts)  
  
-   [Kısmi derleme adları bağlama kaçının](#avoid_partial_names)  
  
-   [Birden çok bağlamları bir derlemesi yüklenirken kaçının](#avoid_loading_into_multiple_contexts)  
  
-   [Derleme birden fazla sürümünü aynı bağlamına yüklenmesini önlemek](#avoid_loading_multiple_versions)  
  
-   [Varsayılan yükleme bağlamı geçmeniz önerilir](#switch_to_default)  
  
 İlk öneri [olumlu ve olumsuz yönlerini yükleme bağlamları anlamak](#load_contexts), hepsi bir yükleme bağlamları bilgi üzerinde bağımlı olduğu için diğer öneriler için arka plan bilgileri sağlar.  
  
<a name="load_contexts"></a>   
## <a name="understand-the-advantages-and-disadvantages-of-load-contexts"></a>Olumlu ve olumsuz yönlerini yükleme bağlamları anlama  
 Bir uygulama etki alanı içinde derlemeleri üç bağlamları birine yüklenebilir veya bir bağlam olmadan yüklenmiş olabilir:  
  
-   Derlemeleri genel derleme önbelleği, çalışma zamanı (örneğin, SQL Server), barındırılıyorsa, ana bilgisayar derleme deposu yoklama tarafından bulunan varsayılan yükleme bağlamı içerir ve <xref:System.AppDomainSetup.ApplicationBase%2A> ve <xref:System.AppDomainSetup.PrivateBinPath%2A> uygulama etki alanı. Çoğu aşırı <xref:System.Reflection.Assembly.Load%2A> yöntemi yük derlemelerine bu bağlamı.  
  
-   Bağlamdan yükleme yükleyicisi tarafından aranmaz konumlardan yüklenmiş derlemeleri içerir. Örneğin, eklentiler uygulama yolu altında olmayan bir dizin yüklenmemiş olabilir. <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>, <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType>, ve <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType> yoluyla yük yöntemler örnekleridir.  
  
-   Yalnızca yansıma bağlamına derlemeleri ile yüklenen içerir <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> ve <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> yöntemleri. Bunu burada ele alınmamıştır şekilde kodu bu bağlamda yürütülemiyor. Daha fazla bilgi için bkz: [nasıl yapılır: yük derlemelerine Reflection-Only bağlamı](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
-   Yansıma kullanarak geçici bir dinamik derleme oluşturulan yayma, derleme her bağlamda değildir. Ayrıca, kullanılarak yüklenen çoğu derlemeleri <xref:System.Reflection.Assembly.LoadFile%2A> yöntemi bağlamı olmadan yüklenir ve içinde bulundukları (ilke uygulandıktan sonra) kimliğini kurar sürece bayt dizileri yüklenen derlemeler bağlamı olmadan yüklü Genel Derleme Önbelleği.  
  
 Yürütme bağlamı olumlu ve olumsuz yönleri, aşağıdaki bölümlerde açıklandığı gibi sahip.  
  
### <a name="default-load-context"></a>Varsayılan yükleme bağlamı  
 Varsayılan yükleme bağlamına derlemeleri yüklenir, bağımlılıklarını otomatik olarak yüklenir. Varsayılan yükleme bağlamına yüklenen bağımlılıkları varsayılan yükleme bağlamı veya bağlamdan yükleme derlemeler için otomatik olarak bulunamadı. Derleme kimliğine göre yükleniyor derlemeleri bilinmeyen sürümleri kullanılmayan sağlayarak uygulamaları kararlılığını artırır (bkz [kaçının bağlama kısmi derleme adları](#avoid_partial_names) bölümü).  
  
 Varsayılan yükleme bağlamı kullanarak aşağıdaki dezavantajları bulunur:  
  
-   Diğer bağlamlarda yüklenen bağımlılıkları kullanılabilir değil.  
  
-   Varsayılan yükleme bağlamı içine algılama yolu dışında konumlardan derlemeler yüklenemiyor.  
  
### <a name="load-from-context"></a>Bağlamdan yükleme  
 Bağlamdan yükleme uygulama yolu altında değil ve bu nedenle yoklama içinde bulunmayan bir yoldan derleme yük olanak sağlar. Yol bilgileri bağlam tarafından korunduğundan bulunan ve bu yolundan yüklenen bağımlılıkları sağlar. Ayrıca, bu bağlamda derlemeleri varsayılan yük bağlamına yüklenen bağımlılıkları kullanabilirsiniz.  
  
 Kullanarak derlemeleri yükleme <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> yöntemi veya yoluyla yük diğer yöntemlerden birini aşağıdaki dezavantajları vardır:  
  
-   Aynı kimliğe sahip bir derleme zaten yüklü, ise <xref:System.Reflection.Assembly.LoadFrom%2A> farklı bir yol belirtilmiş olsa bile yüklenen derleme döndürür.  
  
-   Bir derlemeyi ile yüklenen ise <xref:System.Reflection.Assembly.LoadFrom%2A>, daha sonra aynı bütünleştirilmiş kodda görünen ada göre yüklemek bir varsayılan yükleme bağlamı derlemede çalışır, yükleme denemesi başarısız olur. Bir derlemeyi seri olduğunda bu durum oluşabilir.  
  
-   Bütünleştirilmiş ile yüklenmiş ise <xref:System.Reflection.Assembly.LoadFrom%2A>, ve aynı kimliğe sahip ancak farklı bir konumda bir derleme yoklama yolunu içeren bir <xref:System.InvalidCastException>, <xref:System.MissingMethodException>, veya diğer beklenmeyen davranışları ortaya çıkabilir.  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A>taleplerin <xref:System.Security.Permissions.FileIOPermissionAccess.Read?displayProperty=nameWithType> ve <xref:System.Security.Permissions.FileIOPermissionAccess.PathDiscovery?displayProperty=nameWithType>, veya <xref:System.Net.WebPermission>, belirtilen yol üzerinde.  
  
-   Yerel görüntü derleme için zaten varsa, kullanılmaz.  
  
-   Etki alanı bağımsız derlemesi yüklenemiyor.  
  
-   .NET Framework sürüm 1.0 ve 1.1, ilke uygulanmaz.  
  
### <a name="no-context"></a>Bağlam yok  
 Bağlam yükleme olduğu yansıma ile oluşturulan geçici derlemeler için tek seçenek yayma. Yükleme bağlamı olmadan, bir uygulama etki alanına aynı kimliğe sahip birden çok derleme yüklemek için tek yoludur. Yoklama maliyetini önlenmiş olur.  
  
 Bir derlemeyi genel derleme önbelleğinde kimliğini ilke uygulandığında kurulduğunda, derleme kimliğini eşleşen sürece bayt dizileri yüklenen derlemeler bağlamı olmadan yüklenir; Bu durumda genel derleme önbelleğinde derleme yüklenir.  
  
 Bağlam olmadan derlemeleri yükleme aşağıdaki dezavantajları bulunur:  
  
-   Tanıtıcı sürece diğer derlemelerden bağlamı olmadan yüklenen derlemeler bağlanılamıyor <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay.  
  
-   Bağımlılıklar otomatik olarak yüklenmez. Bir bağlam olmadan dağıtılacak, varsayılan yükleme bağlamına önceden veya işleyerek yük <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay.  
  
-   Bağlam olmadan aynı kimliğe sahip birden çok derlemeleri yükleme türü kimlik sorunları birden çok bağlamları aynı kimliğe sahip derlemeler yükleyerek neden benzer neden olabilir. Bkz: [bir derleme birden çok bağlamları yüklenmesini önlemek](#avoid_loading_into_multiple_contexts).  
  
-   Yerel görüntü derleme için zaten varsa, kullanılmaz.  
  
-   Etki alanı bağımsız derlemesi yüklenemiyor.  
  
-   .NET Framework sürüm 1.0 ve 1.1, ilke uygulanmaz.  
  
<a name="avoid_partial_names"></a>   
## <a name="avoid-binding-on-partial-assembly-names"></a>Kısmi derleme adları bağlama kaçının  
 Kısmi adı bağlama derleme görünen adı yalnızca parçası belirttiğinizde oluşur (<xref:System.Reflection.Assembly.FullName%2A>) bir derleme yükleme. Örneğin, çağırabilirsiniz <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> adıyla yalnızca basit derlemenin sürüm, kültür ve ortak anahtar belirteci atlama yöntemi. Veya deniyor olabilir <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> yöntemi, hangi ilk çağıran <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi ve derleme bulmak başarısız olursa, Genel Derleme Önbelleği arar ve derlemenin en son sürümünü yükler.  
  
 Kısmi ad bağlama, aşağıdakiler de dahil olmak üzere birçok sorunlara neden olabilir:  
  
-   <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> Yöntemi basit adında farklı bir derleme yük. Örneğin, iki uygulama hem basit adına sahip iki tamamen farklı derlemelerinin `GraphicsLibrary` genel derleme önbelleğine.  
  
-   Gerçekte yüklü olduğu derleme geriye dönük olarak uyumlu olmayabilir. Örneğin, sürüm belirtmeden programınızı ilk olarak kullanmak üzere yazılmış kadar sürümden daha sonraki bir sürümü yükleme de neden olabilir. Sonraki bir sürümünü değişiklikleri uygulamanızda hatalara neden olabilir.  
  
-   Gerçekte yüklü olduğu derleme İleri uyumlu olmayabilir. Örneğin, yerleşik ve bir derlemenin en son sürümü ile uygulamanızı test, ancak kısmi bağlama uygulamanızın kullandığı özellikler eksik daha önceki bir sürümünü yükleyebilirsiniz.  
  
-   Yeni uygulamaları yüklemek, var olan uygulamaları bozulabilir. Kullanan bir uygulamayı <xref:System.Reflection.Assembly.LoadWithPartialName%2A> yöntemi daha yeni bir uyumsuz bir paylaşılan derleme sürümü yükleyerek kilidi kırılmamış.  
  
-   Beklenmeyen bağımlılık yükleniyor ortaya çıkabilir. Bu iletiyi bileşenini kullanarak bir derlemede kısmi bağlama ile yüklenirken bir bağımlılık sonuçlanabilir paylaşan iki derleme yük yerleşik veya ile test.  
  
 Bu neden olabilir, sorunları nedeniyle <xref:System.Reflection.Assembly.LoadWithPartialName%2A> yöntemi olarak işaretlendi artık kullanılmıyor. Kullanmanızı öneririz <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi bunun yerine ve tam derleme görünen adları belirtin. Bkz: [olumlu ve olumsuz yönlerini yükleme bağlamları anlamak](#load_contexts) ve [için varsayılan yükleme bağlamı değiştirmeyi göz önünde bulundurun](#switch_to_default).  
  
 Kullanmak istiyorsanız, <xref:System.Reflection.Assembly.LoadWithPartialName%2A> yöntemi kolay, yükleme derleme yaptığından düşünün uygulamanızı eksik derleme tanımlayan bir hata iletisi ile başarısız olan'otomatik olarak kullanmaktan daha iyi bir kullanıcı deneyimi sağlamak büyük olasılıkla bir öngörülemeyen davranışı ve güvenlik açıklarını neden olabilecek derleme sürümü bilinmiyor.  
  
<a name="avoid_loading_into_multiple_contexts"></a>   
## <a name="avoid-loading-an-assembly-into-multiple-contexts"></a>Birden çok bağlamları bir derlemesi yüklenirken kaçının  
 Birden çok bağlamları bir derlemesi yüklenirken türü kimlik sorunlara neden olabilir. Aynı türde iki farklı bağlamdan içine aynı derlemeden yüklenir, aynı ada sahip iki farklı tür yüklenmiş gibi olur. Bir <xref:System.InvalidCastException> bir diğerini yazın kafa karıştırıcı iletiyle türe çalışırsanız durum `MyType` türüne yayınlanamıyor `MyType`.  
  
 Örneğin, varsayın `ICommunicate` arabirimi adlı bir derleme bildirilen `Utility`, programınızı ve ayrıca programınızı yükler diğer derlemelerden tarafından başvurulan. Bu diğer derlemeler uygulama türlerini içeren `ICommunicate` arabirimi, bunları kullanmak, program izin verme.  
  
 Şimdi, program çalıştırıldığında ne olacağını düşünün. Varsayılan yükleme bağlamına programınız tarafından başvurulan bir derleme yüklenir. Hedef derleme kimliğini tarafından yüklerseniz kullanarak <xref:System.Reflection.Assembly.Load%2A> yöntemi, varsayılan yükleme bağlamı olacaktır ve bu nedenle bağımlılıklarını olur. Programınız ve hedef derleme aynı kullanacağı `Utility` derleme.  
  
 Ancak, dosya yoluna göre hedef derleme yük varsayalım kullanarak <xref:System.Reflection.Assembly.LoadFile%2A> yöntemi. Derleme herhangi bir bağlam olmadan yüklü olduğundan bağımlılıklarını otomatik olarak yüklenmez. İçin bir işleyici olabilir <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> bağımlılık ve bunu sağlamak için olay yük `Utility` kullanarak bir bağlam yok derleme <xref:System.Reflection.Assembly.LoadFile%2A> yöntemi. Şimdi bir türünün bir örneği oluşturduğunuzda türü değişkenine atamak için deneyin ve hedef derleme bulunan `ICommunicate`, bir <xref:System.InvalidCastException> çalışma zamanı algıladığından durum `ICommunicate` iki kopyasını arabirimlerde `Utility` farklı tür derleme.  
  
 Bir derleme birden çok bağlamları yüklenen olabilir birçok senaryo vardır. Uygulama yolu hedef derlemesinde yerini değiştirme ve kullanarak çakışmaları önlemek için en iyi yaklaşımdır <xref:System.Reflection.Assembly.Load%2A> yöntemi tam görünen adı. Derleme sonra varsayılan yük bağlamına yüklenir ve her iki derlemeleri aynı kullanma `Utility` derleme.  
  
 Hedef derleme uygulama yolunuz dışında kalırsa, bu gerekir kullanabileceğiniz <xref:System.Reflection.Assembly.LoadFrom%2A> bağlamdan yükleme yüklemek için yöntem. Hedef derleme uygulamanızın başvuru derlenen varsa `Utility` derleme, bu kullanacağınız `Utility` uygulamanız varsayılan yük bağlamına yükledi derleme. Hedef derleme bir kopyası üzerinde bir bağımlılığa sahipse sorunlar oluşabilir Not `Utility` derleme dışında Uygulama yolu bulunur. Bu derleme bağlamdan yükleme, uygulama yükünü önce halinde yüklenmiş ise `Utility` derleme, uygulamanızın yükleme başarısız olur.  
  
 [Göz önünde bulundurun geçiş varsayılan yükleme bağlamı için](#switch_to_default) bölümde açıklanmıştır dosya yolu yükleri gibi kullanılarak alternatifleri <xref:System.Reflection.Assembly.LoadFile%2A> ve <xref:System.Reflection.Assembly.LoadFrom%2A>.  
  
<a name="avoid_loading_multiple_versions"></a>   
## <a name="avoid-loading-multiple-versions-of-an-assembly-into-the-same-context"></a>Derleme birden fazla sürümünü aynı bağlamına yüklenmesini önlemek  
 Bir yük bağlamına derleme birden fazla sürümünü yükleme türü kimlik sorunlara neden olabilir. Aynı türde iki aynı bütünleştirilmiş kodda sürümlerinden yüklenir, aynı ada sahip iki farklı tür yüklenmiş gibi olur. Bir <xref:System.InvalidCastException> bir diğerini yazın kafa karıştırıcı iletiyle türe çalışırsanız durum `MyType` türüne yayınlanamıyor `MyType`.  
  
 Örneğin, programınızı bir sürümünü yükleyebilirsiniz `Utility` derleme doğrudan ve daha sonra farklı bir sürümünü yükler başka bir derleme yükleyebilir `Utility` derleme. Veya bir kodlama hatası iki farklı kod yolları bir derlemenin farklı sürümleri yüklemek için uygulamanızda neden olabilir.  
  
 Varsayılan yükleme bağlamı kullandığınızda bu sorun oluşabilir <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi ve farklı sürüm numaralarını içeren tam derleme görünen adları belirtin. Bağlam olmadan yüklenen derlemeler için kullanarak sorunu kaynaklanabilir <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> aynı bütünleştirilmiş kodda farklı yolları yükleme yöntemi. Çalışma zamanı kimliklerini aynı olsa bile, farklı derlemeler olması için farklı yollar yüklenen iki derleme göz önünde bulundurur.  
  
 Tür kimliği ek olarak, bir derleme birden fazla sürümünü sorunlara yol açabilir bir <xref:System.MissingMethodException> farklı bir sürümü bu türden bekliyor koduna bir derleme sürümünden yüklenen bir türü aktarılırsa. Örneğin, kod daha yeni sürümüne eklenmiş olan bir yöntem bekleyebilirsiniz.  
  
 Sürümler arasında türünün davranışını değiştirdiyseniz, daha hafif hatalar oluşabilir. Örneğin, bir yöntem bir beklenmeyen bir özel durum oluşturduğunda veya beklenmeyen bir değer döndürür.  
  
 Yalnızca bir emin olmak için kodunuzu dikkatlice inceleyin derleme sürümü yüklenir. Kullanabileceğiniz <xref:System.AppDomain.GetAssemblies%2A?displayProperty=nameWithType> hangi derlemelerin herhangi bir zamanda yüklenen belirlemek amacıyla yöntemi.  
  
<a name="switch_to_default"></a>   
## <a name="consider-switching-to-the-default-load-context"></a>Varsayılan yükleme bağlamı geçmeniz önerilir  
 Uygulamanızın derleme yükleme ve dağıtım desenleri inceleyin. Bayt dizileri yüklenen derlemeler ortadan kaldırabilir? Yoklama yola derlemeleri taşıyabilir miyim? Derlemeleri genel derleme önbelleğinde veya uygulama etki alanında bulunuyorsa yol yoklama (diğer bir deyişle, kendi <xref:System.AppDomainSetup.ApplicationBase%2A> ve <xref:System.AppDomainSetup.PrivateBinPath%2A>), derleme kimliğini tarafından yükleyebilirsiniz.  
  
 Tüm derlemeleriniz algılama yolu yerleştirilecek mümkün değilse, eklenti .NET Framework modelini kullanarak, derlemeleri genel derleme önbelleğine yerleştirme veya uygulama etki alanları oluşturma gibi alternatifleri göz önünde bulundurun.  
  
### <a name="consider-using-the-net-framework-add-in-model"></a>Eklenti .NET Framework modeli kullanmayı düşünün  
 Genellikle uygulama Bankası'nda yüklü değil, eklentiler, uygulamak için bağlamdan yükleme kullanıyorsanız eklenti .NET Framework modelini kullanır. Bu model, uygulama etki alanları kendiniz yönetmeye gerek kalmadan uygulama düzeyinde etki alanı ya da işlem, yalıtım sağlar. Eklenti modeli hakkında daha fazla bilgi için bkz: [eklentiler ve genişletilebilirlik](../../../docs/framework/add-ins/index.md).  
  
### <a name="consider-using-the-global-assembly-cache"></a>Genel Derleme Önbelleği kullanmayı düşünün  
 Bir paylaşılan derleme yolu elde etmek için yer derlemeleri genel derleme önbelleğinde temel, uygulama dışında diğer bağlamlarda dezavantajları sürüyor veya varsayılan yükleme bağlamı avantajını kaybetmeden olmasıdır.  
  
### <a name="consider-using-application-domains"></a>Uygulama etki alanları kullanmayı düşünün  
 Bazı derlemeleriniz uygulamanın yoklama yolunda dağıtılamıyor karar verirseniz, bu derlemeler için yeni bir uygulama etki alanı oluşturmayı düşünün. Kullanan bir <xref:System.AppDomainSetup> yeni uygulama etki alanı oluşturma ve kullanma <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> özelliği yüklemek istediğiniz derlemeleri içeren yolu belirtin. Yoklama için birden fazla dizine sahipseniz, ayarlayabileceğiniz <xref:System.AppDomainSetup.ApplicationBase%2A> kök dizini ve kullanımına <xref:System.AppDomainSetup.PrivateBinPath%2A?displayProperty=nameWithType> araştırma için alt dizinler tanımlamak için özellik. Alternatif olarak, birden çok uygulama etki alanları oluşturun ve ayarlayın <xref:System.AppDomainSetup.ApplicationBase%2A> her uygulama etki alanı kendi derlemeler için uygun yolu.  
  
 Kullanabileceğiniz Not <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> yöntemi bu derlemeler yüklenemiyor. Şimdi algılama yolu olduklarından, bunlar bağlamdan yükleme yerine varsayılan yükleme bağlamı içine yüklenir. Ancak, için geçiş öneririz <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi ve doğru sürümlerini her zaman kullanılmasını sağlamak için derleme görünen adları tam sağlayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>  
 <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>  
 [Eklentiler ve Genişletilebilirlik](../../../docs/framework/add-ins/index.md)
