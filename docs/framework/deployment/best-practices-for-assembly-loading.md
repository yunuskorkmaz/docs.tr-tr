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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 53ad8f6187b4e9b1754094dae0ebfe6e05a1b78b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614137"
---
# <a name="best-practices-for-assembly-loading"></a>Derleme Yükleme için En İyi Yöntemler
Yol açabilir türü kimliği sorunları önlemek için bu makalede ele alınmaktadır <xref:System.InvalidCastException>, <xref:System.MissingMethodException>ve diğer hataları. Aşağıdaki öneriler anlatılmaktadır:  
  
- [Avantajlar ve dezavantajlar yük bağlamları anlama](#load_contexts)  
  
- [Kısmi derleme adları bağlama kaçının](#avoid_partial_names)  
  
- [Bir derlemeyi birden çok bağlamlarına yüklenmesini önlemek](#avoid_loading_into_multiple_contexts)  
  
- [Bir derlemenin birden çok sürümünü aynı bağlamına yüklenmesini önlemek](#avoid_loading_multiple_versions)  
  
- [Varsayılan yükleme bağlamı için göz önünde bulundurun](#switch_to_default)  
  
 İlk öneri [avantaj ve dezavantajlarını yük bağlamı anlamak](#load_contexts), tüm yükleme bağlamları hakkında bir bilgi bankasına bağlı olduğundan, arka plan bilgileri için diğer öneriler sağlar.  
  
<a name="load_contexts"></a>   
## <a name="understand-the-advantages-and-disadvantages-of-load-contexts"></a>Avantajlar ve Dezavantajlar yük bağlamları anlama  
 Bir uygulama etki alanı içinde derlemeler üç bağlamları birine yüklenebilir veya bunlar bağlamı olmadan yüklenebilir:  
  
- Varsayılan yükleme bağlamı'nı içeren derlemeler genel derleme önbelleği, çalışma zamanı (örneğin, SQL Server), barındırılıyorsa ana bilgisayar bütünleştirilmiş kod deposu yoklama işlemi tarafından bulunan ve <xref:System.AppDomainSetup.ApplicationBase%2A> ve <xref:System.AppDomainSetup.PrivateBinPath%2A> uygulama etki alanının. Çoğu aşırı yüklemeleri <xref:System.Reflection.Assembly.Load%2A> yöntemi bu bağlamına derlemeleri.  
  
- Load-from bağlamı yükleyicisi tarafından aranmaz konumlardan yüklenen derlemeleri içerir. Örneğin, uygulama yolu altında olmayan bir dizin eklentileri yüklenebilir. <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>, <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType>, ve <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType> yoluyla yükleme yöntemleri örnekleridir.  
  
- Yalnızca yansıma bağlamı ile yüklenen derlemeler içeren <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> ve <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> yöntemleri. Bunu burada ele alınmayan şekilde kodu bu bağlamda yürütülemez. Daha fazla bilgi için [nasıl yapılır: Salt yansıma bağlamına derlemeleri yükleme](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
- Geçici dinamik derleme yansıma kullanarak oluşturulan yayma, derleme herhangi bir bağlam içinde değil. Ayrıca, çoğu kullanılarak yüklenen derlemeler <xref:System.Reflection.Assembly.LoadFile%2A> yöntemi bağlamı olmadan yüklenir ve kimliklerini (İlkesi uygulandıktan sonra), içinde bulundukları kurar sürece bayt dizileri ' yüklenen derlemeler bağlamı olmadan yüklendi Genel Derleme Önbelleği.  
  
 Yürütme bağlamları aşağıdaki bölümlerde açıklandığı gibi avantajları ve sakıncaları vardır.  
  
### <a name="default-load-context"></a>Varsayılan yükleme bağlamı  
 Varsayılan yükleme bağlamı yüklenen derlemeler, bunların bağımlılıklarını otomatik olarak yüklenir. Varsayılan yükleme bağlamı yüklenen bağımlılıkları, varsayılan yükleme bağlamı'nı veya load-from bağlamı içindeki derlemeler için otomatik olarak bulunur. Derleme kimliği tarafından yüklenirken bilinmeyen derlemelerin sürümleri kullanılmamasını sağlayarak uygulamaları kararlılığını artırır (bkz [önlemek bağlama kısmi derleme adları](#avoid_partial_names) bölümü).  
  
 Varsayılan yükleme bağlamı'nı kullanarak, aşağıdaki dezavantajları bulunur:  
  
- Diğer bağlamı yüklenen bağımlılıklar kullanılamıyor.  
  
- Varsayılan yükleme bağlamı içine araştırma yolu dışındaki konumlardan derlemeler yüklenemiyor.  
  
### <a name="load-from-context"></a>Bağlamdan yükleme  
 Load-from bağlamı altında Uygulama yolu değil ve bu nedenle yoklama bulunmaz yoldan bütünleştirilmiş devredebilmenize olanak tanır. Yol bilgileri bağlam tarafından korunduğundan bu yolundan yüklendi ve yerleştirildi için bağımlılıkları sağlar. Ayrıca, bu bağlamda derlemeleri varsayılan yükleme bağlamı yüklenen bağımlılıkları kullanabilirsiniz.  
  
 Kullanarak derlemeleri yükleme <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> yöntemi veya yolu tarafından yüklenen diğer yöntemlerden birini aşağıdaki dezavantajları vardır:  
  
- Zaten aynı kimliğe sahip bir derleme yüklendiğinde, <xref:System.Reflection.Assembly.LoadFrom%2A> bile farklı bir yol belirtildi yüklü bütünleştirilmiş kodu döndürür.  
  
- Bir derleme ile yüklü ise <xref:System.Reflection.Assembly.LoadFrom%2A>, daha sonra varsayılan yükleme bağlamı'nı bir derlemede, aynı derlemenin görünen ada göre yükleme girişiminde, yükleme denemesi başarısız olur. Bir derlemeyi seri durumda olduğunda bu durum oluşabilir.  
  
- Bir derleme ile yüklü ise <xref:System.Reflection.Assembly.LoadFrom%2A>, ve bir derleme, aynı kimliğe sahip ancak farklı bir konumda yoklama yolunu içeren bir <xref:System.InvalidCastException>, <xref:System.MissingMethodException>, ya da diğer beklenmeyen davranışlar ortaya çıkabilir.  
  
- <xref:System.Reflection.Assembly.LoadFrom%2A> talepleri <xref:System.Security.Permissions.FileIOPermissionAccess.Read?displayProperty=nameWithType> ve <xref:System.Security.Permissions.FileIOPermissionAccess.PathDiscovery?displayProperty=nameWithType>, veya <xref:System.Net.WebPermission>, belirtilen yolda.  
  
- Derleme için bir yerel görüntü varsa kullanılmaz.  
  
- Derleme etki alanından bağımsız yüklenemez.  
  
- .NET Framework sürüm 1.0 ve 1.1, ilke uygulanmaz.  
  
### <a name="no-context"></a>İçerik yok  
 Yansıma ile oluşturulan geçici derlemeler için tek seçenek yayma olan bağlamı olmadan yükleniyor. Yükleme bağlamı olmadan, bir uygulama etki alanına aynı kimliğe sahip birden çok derleme yüklemek için tek yoludur. Yoklama maliyeti önlenmiş olur.  
  
 Genel derleme önbelleğindeki bir derleme kimliğini ilke uygulandığında kurulduğunda, derlemenin kimliğini eşleşen sürece bayt dizileri ' yüklenen derlemeler bağlamı olmadan yüklenir; Bu durumda, Genel Derleme Önbelleği'ndeki derleme yüklenir.  
  
 Bağlam olmayan derlemeler yüklenirken aşağıdaki dezavantajları bulunur:  
  
- Ele sürece diğer derlemeler bağlamı olmadan yüklenen derlemeler bağlanılamıyor <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay.  
  
- Bağımlılıkları otomatik olarak yüklenmez. Bunları bağlamı olmadan dağıtılacak, bunları varsayılan yük bağlamına dağıtılacak veya bunları işleyerek yük <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay.  
  
- Bağlam olmadan aynı kimliğe sahip birden çok derleme yükleniyor derlemeleri aynı kimliğe sahip birden çok bağlamlarına yükleyerek neden benzer türü kimlik sorunlarına yol açabilir. Bkz: [birden çok bağlamlarına bir derlemeye yüklenmesini engellemek](#avoid_loading_into_multiple_contexts).  
  
- Derleme için bir yerel görüntü varsa kullanılmaz.  
  
- Derleme etki alanından bağımsız yüklenemez.  
  
- .NET Framework sürüm 1.0 ve 1.1, ilke uygulanmaz.  
  
<a name="avoid_partial_names"></a>   
## <a name="avoid-binding-on-partial-assembly-names"></a>Kısmi derleme adları bağlama kaçının  
 Kısmi ad bağlaması, yalnızca derlemenin görünen ad parçası belirttiğiniz oluşur (<xref:System.Reflection.Assembly.FullName%2A>) bir bütünleştirilmiş kod yükleme. Örneğin, çağırabilirsiniz <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi derlemenin sürüm, kültür ve ortak anahtar belirteci atlama yalnızca basit ada sahip. Veya çağırabilirsiniz <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> hangi ilk çağrı, yöntem <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi ve derlemeyi bulmak başarısız olursa, Genel Derleme Önbelleği arar ve derlemenin en son sürümünü yükler.  
  
 Kısmi ad bağlaması, aşağıdakiler dahil olmak üzere birçok sorunlara neden olabilir:  
  
- <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> Yöntemi basit aynı ada sahip başka bir derleme yüklemek. Örneğin, iki uygulama hem de basit adına sahip iki tamamen farklı derlemeler yükleyebilirsiniz `GraphicsLibrary` genel bütünleştirilmiş kod önbelleğine.  
  
- Aslında yüklenen derleme geriye dönük olarak uyumlu olmayabilir. Örneğin, sürüm belirtmeden programınızı ilk olarak kullanmak üzere yazılmış daha sonraki bir sürümü sürümden yüklenmesini de neden olabilir. Sonraki sürümdeki değişiklikler, uygulamanızda hatalara neden olabilir.  
  
- Aslında yüklenen derleme ileriye dönük olarak uyumlu olmayabilir. Örneğin, oluşturulan ve uygulamanızı bir derlemenin en son sürümle test, ancak kısmi bağlama, uygulamanızın kullandığı özellikler eksik daha önceki bir sürümünü yükleyebilir.  
  
- Yeni uygulamaları yükleme, mevcut uygulamaları bozabilir. Kullanan bir uygulamayı <xref:System.Reflection.Assembly.LoadWithPartialName%2A> yöntemi bozulmuş paylaşılan bir derlemenin daha yeni ve uyumlu bir sürümünü yükleyerek.  
  
- Beklenmeyen bağımlılık yükleniyor ortaya çıkabilir. Bu kısmi bağlamayla yüklemeden, bir bağımlılık başarısız bir bileşen kullanma, bir derlemede sonuçlanabilir paylaşan iki derlemeler yüklemek veya sınandığı.  
  
 Bunu neden olabilir, sorunları nedeniyle <xref:System.Reflection.Assembly.LoadWithPartialName%2A> yöntemi olarak işaretlendi artık kullanılmıyor. Kullanmanızı öneririz <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi bunun yerine, tam bütünleştirilmiş kod görünen adlarını belirtin. Bkz: [avantaj ve dezavantajlarını yük bağlamı anlamak](#load_contexts) ve [varsayılan yükleme bağlamı için göz önünde bulundurun](#switch_to_default).  
  
 Kullanmak istiyorsanız <xref:System.Reflection.Assembly.LoadWithPartialName%2A> yöntemi kolay, yüklenirken derleme yaptığından düşünün uygulamanızı eksik derleme tanımlayan bir hata iletisi ile başarısız olan'otomatik olarak kullanarak daha iyi bir kullanıcı deneyimi sağlamak büyük olasılıkla bir beklenmeyen davranışlar ve güvenlik açıkları neden olabilecek derleme sürümü bilinmiyor.  
  
<a name="avoid_loading_into_multiple_contexts"></a>   
## <a name="avoid-loading-an-assembly-into-multiple-contexts"></a>Bir derlemeyi birden çok bağlamlarına yüklenmesini önlemek  
 Bir derlemeyi birden çok bağlamlarına yükleme türü kimlik sorunlara neden olabilir. Aynı türde iki farklı bağlamdan aynı derlemeye'ndan yüklenir, aynı ada sahip iki farklı tür yüklenmiş gibi olur. Bir <xref:System.InvalidCastException> diğer türü karmaşık bir iletiyle bir türe çalışırsanız durum `MyType` türüne yayınlanamıyor `MyType`.  
  
 Örneğin, varsayın `ICommunicate` arabirimi adlı bir derlemede bildirilmiş `Utility`, programınız ve ayrıca programınızı yükleyen diğer derlemeler tarafından başvurulan. Bu, diğer bütünleştirilmiş kodları, uygulayan türler bulunur. `ICommunicate` arabirimi, programınız onları kullanmak izin verme.  
  
 Şimdi, program çalıştığında ne olacağını düşünün. Programınız tarafından başvurulan bir derleme, varsayılan yükleme bağlamı yüklenir. Hedef derleme kimliğini tarafından yüklerseniz, kullanarak <xref:System.Reflection.Assembly.Load%2A> yöntemi, varsayılan yükleme bağlamı içinde olacaktır ve bu bağımlılıkları içerecektir. Programınızı hem de hedef derleme aynı kullanacağı `Utility` derleme.  
  
 Ancak, dosya yoluna göre hedef bütünleştirilmiş kod yükleme varsayalım kullanarak <xref:System.Reflection.Assembly.LoadFile%2A> yöntemi. Derleme herhangi bir bağlam olmadan yüklü olduğundan bağımlılıklarını otomatik olarak yüklenmez. İçin bir işleyici olabilir <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> ve bağımlılık sağlamak için olay yük `Utility` kullanarak bir bağlam yok derlemeyle <xref:System.Reflection.Assembly.LoadFile%2A> yöntemi. Artık bir türün örneğini oluşturduğunuzda deneyin türündeki bir değişkene atayın ve hedef derleme içinde bulunan `ICommunicate`e <xref:System.InvalidCastException> çalışma zamanı varsaydığı durum `ICommunicate` iki kopyasını arabirimlerde `Utility` farklı türleri için derleme.  
  
 Bir derlemeyi birden fazla bağlamı yüklenen olabilir birçok senaryo vardır. Uygulama yolunuz hedef derlemesinde yeniden konumlandırma ve kullanarak çakışmaları önlemek için en iyi yaklaşımdır <xref:System.Reflection.Assembly.Load%2A> yöntemi tam görünen adı. Derleme, ardından varsayılan yükleme bağlamı yüklenir ve iki derleme kullandığınızdan `Utility` derleme.  
  
 Hedef derleme dışında Uygulama yolu kalmalıdır, kullanabileceğiniz <xref:System.Reflection.Assembly.LoadFrom%2A> load-from bağlamı yüklemek için yöntemi. Hedef derleme, uygulamanızın bir başvuru ile derlendi ise `Utility` derlemesi, kullanacağınız `Utility` uygulamanızın varsayılan yükleme bağlamı yüklenen derleme. Hedef derleme bir kopyası üzerinde bir bağımlılık varsa sorunlar oluşabilir Not `Utility` derleme dışında Uygulama yolu bulunur. Bu derleme, uygulama yükleri önce load-from bağlamı içine yüklenen ise `Utility` derleme, uygulamanızın yükleme başarısız olur.  
  
 [Göz önünde bulundurun geçiş için varsayılan yükleme bağlamı](#switch_to_default) bölüm anlatır gibi dosya yolu yükleri kullanımına alternatifler <xref:System.Reflection.Assembly.LoadFile%2A> ve <xref:System.Reflection.Assembly.LoadFrom%2A>.  
  
<a name="avoid_loading_multiple_versions"></a>   
## <a name="avoid-loading-multiple-versions-of-an-assembly-into-the-same-context"></a>Bir derlemenin birden çok sürümünü aynı bağlamına yüklenmesini önlemek  
 Bir yük bağlamına birden çok derleme sürümünü yükleme türü kimlik sorunlara neden olabilir. Aynı türde, aynı derlemenin iki sürümlerinden yüklenir, aynı ada sahip iki farklı tür yüklenmiş gibi olur. Bir <xref:System.InvalidCastException> diğer türü karmaşık bir iletiyle bir türe çalışırsanız durum `MyType` türüne yayınlanamıyor `MyType`.  
  
 Örneğin, programınız bir sürümünü yükleyebilir `Utility` derleme doğrudan ve daha sonra farklı bir sürümü yükleyen başka bir derleme yükleyebilir `Utility` derleme. Veya bir kodlama hatası iki farklı kod yolları bir derlemenin farklı sürümleri yüklemek için uygulamanızda neden olabilir.  
  
 Varsayılan yük bağlamda kullanırken bu sorun oluşabilir <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi ve farklı sürüm numaralarını dahil tam derleme görünen adlarını belirtin. Bağlamı olmadan yüklenen derlemeler için kullanarak sorunu kaynaklanabilir <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> aynı derlemenin farklı yoldan yüklemek için yöntemi. Çalışma zamanı kimlikleri aynı olsa bile farklı derlemeler olarak farklı yoldan yüklenmiş iki derlemeleri göz önünde bulundurur.  
  
 Türü kimlik sorunlara ek olarak, birden çok derleme sürümünü neden olabilir bir <xref:System.MissingMethodException> derlemenin bir sürümünden yüklenen bir tür o türünden farklı bir sürüm kod geçirilmiş. Örneğin, kod daha yeni sürümüne eklenmiş olan bir yöntem bekleyebilirsiniz.  
  
 Sürümler arasında türü davranışını değiştirdiyseniz, daha ince hatalar oluşabilir. Örneğin, bir yöntem, beklenmeyen bir özel durum veya beklenmeyen bir değer döndürür.  
  
 Kodunuzun yalnızca bir emin olmak için dikkatle gözden geçirerek bir derlemenin sürümü yüklenir. Kullanabileceğiniz <xref:System.AppDomain.GetAssemblies%2A?displayProperty=nameWithType> herhangi bir zamanda hangi derlemelerin yüklü olduğundan belirlemek için yöntemi.  
  
<a name="switch_to_default"></a>   
## <a name="consider-switching-to-the-default-load-context"></a>Varsayılan yükleme bağlamı için göz önünde bulundurun  
 Uygulamanızın bütünleştirilmiş kod yükleme ve dağıtım desenleri inceleyin. Bayt dizileri yüklenen derlemeler ortadan kaldırabilir? Araştırma yolu derlemeleri taşıyabilir miyim? Derlemeleri genel derleme önbelleği veya uygulama etki alanında bulunuyorsa yolu yoklama (diğer bir deyişle, kendi <xref:System.AppDomainSetup.ApplicationBase%2A> ve <xref:System.AppDomainSetup.PrivateBinPath%2A>), derlemenin kimliğini tarafından yükleyebilirsiniz.  
  
 Yoklama yolu, tüm derlemelerin yerleştirileceği mümkün değilse, .NET Framework eklenti modeli kullanarak, derlemeleri genel bütünleştirilmiş kod önbelleğine yerleştirilmesi veya uygulama etki alanları oluşturma gibi alternatifleri düşünün.  
  
### <a name="consider-using-the-net-framework-add-in-model"></a>.NET Framework eklenti modeli kullanmayı düşünün  
 Genellikle Uygulama tabanı yüklü değil, eklentiler uygulamak için load-from bağlamı kullanıyorsanız, .NET Framework eklenti modeli kullanın. Bu model, uygulama etki alanları kendiniz yönetmeye gerek kalmadan uygulama düzeyinde etki alanı ya da işlem yalıtım sağlar. Eklenti modeli hakkında daha fazla bilgi için bkz. [eklentiler ve genişletilebilirlik](/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100)).  
  
### <a name="consider-using-the-global-assembly-cache"></a>Genel Derleme Önbelleği'ni kullanmayı düşünün  
 Paylaşılan derleme yolu eklentisinden yerde derlemeleri genel derleme önbelleğinde temel, uygulama dışında kaybetme varsayılan yükleme bağlamı avantajları veya dezavantajları diğer içerikler üzerinde alma olmadan olmasıdır.  
  
### <a name="consider-using-application-domains"></a>Uygulama etki alanları kullanmayı düşünün  
 Bazı bütünleştirilmiş kodlarınızı uygulamanın yoklama yolu dağıtılamıyor karar verirseniz, bu derlemeler için yeni bir uygulama etki alanı oluşturmayı göz önünde bulundurun. Kullanan bir <xref:System.AppDomainSetup> yeni uygulama etki alanı oluşturmak ve <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> özelliğini içeren derlemeler yüklemek istediğiniz yolu belirtin. Araştırma için birden fazla dizine sahipseniz, ayarlayabileceğiniz <xref:System.AppDomainSetup.ApplicationBase%2A> bir kök dizin ve <xref:System.AppDomainSetup.PrivateBinPath%2A?displayProperty=nameWithType> araştırma için alt dizinler tanımlamak için özellik. Alternatif olarak, birden çok uygulama etki alanları oluşturmak ve ayarlamak <xref:System.AppDomainSetup.ApplicationBase%2A> her uygulama etki alanı, derlemeler için uygun yolu.  
  
 Kullanabileceğiniz Not <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> bu derlemeleri yüklemek için yöntemi. Araştırma yolu artık oldukları için varsayılan yükleme bağlamı yerine load-from bağlamı içine yüklenen olacaktır. Ancak, için geçiş öneririz <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi ve doğru sürümleri her zaman kullanılmasını sağlamak için derleme görünen adları tam sağlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>
- <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>
