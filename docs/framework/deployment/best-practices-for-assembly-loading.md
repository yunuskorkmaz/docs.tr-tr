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
ms.openlocfilehash: 7575c40edf47e977335bcc34fcd9e49debab0980
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181696"
---
# <a name="best-practices-for-assembly-loading"></a>Derleme Yükleme için En İyi Yöntemler
Bu makalede, tür kimliği, ,, <xref:System.InvalidCastException> <xref:System.MissingMethodException>ve diğer hatalara yol açabilir sorunları önlemek için yollar tartışır. Makalede aşağıdaki öneriler anlatılmaktadır:  
  
- [Yük bağlamlarının avantaj ve dezavantajlarını anlama](#load_contexts)  
  
- [Kısmi montaj adlarını bağlamaktan kaçının](#avoid_partial_names)  
  
- [Derlemeyi birden çok içeriğe yüklemekten kaçının](#avoid_loading_into_multiple_contexts)  
  
- [Bir derlemenin birden çok sürümüne aynı içeriğe yüklemekten kaçının](#avoid_loading_multiple_versions)  
  
- [Varsayılan yük bağlamına geçmeyi düşünün](#switch_to_default)  
  
 İlk öneri, [yük bağlamlarının avantaj larını ve dezavantajlarını anlamak,](#load_contexts)diğer öneriler için arka plan bilgileri sağlar, çünkü hepsi yük bağlamları bilgisine bağlıdır.  
  
<a name="load_contexts"></a>
## <a name="understand-the-advantages-and-disadvantages-of-load-contexts"></a>Yük Bağlamlarının Avantaj ve Dezavantajlarını Anlama  
 Bir uygulama etki alanı içinde, derlemeler üç bağlamdan birine yüklenebilir veya bağlam olmadan yüklenebilir:  
  
- Varsayılan yük bağlamı, genel montaj önbelleğini, çalışma zamanı barındırılan (örneğin SQL Server'da) ana <xref:System.AppDomainSetup.ApplicationBase%2A> bilgisayar <xref:System.AppDomainSetup.PrivateBinPath%2A> montaj deposunu ve uygulama etki alanını ve uygulama etki alanını sondalayarak bulunan derlemeleri içerir. <xref:System.Reflection.Assembly.Load%2A> Yöntemin çoğu bu bağlamda derlemeleri yükler.  
  
- Yükten gelen bağlam, yükleyici tarafından aranmayan konumlardan yüklenen derlemeler içerir. Örneğin, eklentiler uygulama yolu altında olmayan bir dizine yüklenmiş olabilir. <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>, <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType>, <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType> ve yol ile yük yöntemleriörnekleridir.  
  
- Yalnızca yansıma bağlamı, metotlar <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> ve <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> yöntemlerle yüklenen derlemeleri içerir. Bu bağlamda kod yürütülemez, bu nedenle burada tartışılamaz. Daha fazla bilgi için [bkz: Derlemeleri Yalnızca Yansıma Bağlamına Yükleyin.](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)  
  
- Yansıma yontma kullanarak geçici bir dinamik derleme oluşturduysanız, derleme herhangi bir bağlamda değildir. Buna ek olarak, <xref:System.Reflection.Assembly.LoadFile%2A> yöntem kullanılarak yüklenen derlemelerin çoğu bağlam olmadan yüklenir ve kimlikleri (ilke uygulandıktan sonra) genel derleme önbelleğinde olduklarını belirlemedikçe, bayt dizilerinden yüklenen derlemeler bağlam olmadan yüklenir.  
  
 Yürütme bağlamları, aşağıdaki bölümlerde ele alındığı gibi avantajları ve dezavantajları vardır.  
  
### <a name="default-load-context"></a>Varsayılan Yük Bağlamı  
 Derlemeler varsayılan yük bağlamına yüklendiğinde, bunların bağımlılıkları otomatik olarak yüklenir. Varsayılan yük bağlamına yüklenen bağımlılıklar, varsayılan yük bağlamındaki derlemeler veya yükten gelen bağlamdaki derlemeler için otomatik olarak bulunur. Derleme kimliğine göre yüklenmesi, derlemelerin bilinmeyen sürümlerinin kullanılmamasını sağlayarak uygulamaların kararlılığını artırır [(Bkz. Kısmi Montaj Adlarına Bağlanmayı Kaçın](#avoid_partial_names) bölümüne bakınız).  
  
 Varsayılan yük bağlamını kullanmak aşağıdaki dezavantajlara sahiptir:  
  
- Diğer bağlamlara yüklenen bağımlılıklar kullanılamaz.  
  
- Sondalama yolunun dışındaki konumlardan derlemeleri varsayılan yük bağlamına yükleyemezsiniz.  
  
### <a name="load-from-context"></a>Yük-Bağlamdan  
 Yükten gelen bağlam, bir derlemeyi uygulama yolu altında olmayan bir yoldan yüklemenize olanak tanır ve bu nedenle sondalamaya dahil edilmez. Yol bilgilerinin bağlam tarafından korunduğundan, bağımlılıkların bu yoldan bulunmasını ve yüklenmesini sağlar. Ayrıca, bu bağlamdaki derlemeler varsayılan yük bağlamına yüklenen bağımlılıkları kullanabilir.  
  
 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> Yöntemi kullanarak derlemeleri yükleme veya yol ile yüklenen diğer yöntemlerden biri aşağıdaki dezavantajlara sahiptir:  
  
- Aynı kimliğe sahip bir derleme <xref:System.Reflection.Assembly.LoadFrom%2A> zaten yüklenmişse, farklı bir yol belirtilmiş olsa bile yüklenen derlemeyi döndürür.  
  
- Bir derleme ile <xref:System.Reflection.Assembly.LoadFrom%2A>yüklenir ve daha sonra varsayılan yük bağlamında bir derleme görüntü adına göre aynı derleme yüklemeye çalışır, yük girişimi başarısız olur. Bu, bir derleme deserialized oluşabilir.  
  
- Bir derleme yüklüyse <xref:System.Reflection.Assembly.LoadFrom%2A>ve sondalama yolu aynı kimliğe sahip bir derleme <xref:System.InvalidCastException>içeriyorsa, ancak farklı bir konumda, bir , , <xref:System.MissingMethodException>veya başka beklenmeyen davranışlar oluşabilir.  
  
- <xref:System.Reflection.Assembly.LoadFrom%2A>talep <xref:System.Security.Permissions.FileIOPermissionAccess.Read?displayProperty=nameWithType> <xref:System.Security.Permissions.FileIOPermissionAccess.PathDiscovery?displayProperty=nameWithType>ve <xref:System.Net.WebPermission>, veya , belirtilen yolda.  
  
- Derleme için yerel bir görüntü varsa, kullanılmaz.  
  
- Derleme etki alanı nötr olarak yüklenemez.  
  
- .NET Framework 1.0 ve 1.1 sürümlerinde ilke uygulanmaz.  
  
### <a name="no-context"></a>İçerik Yok  
 Bağlamsız yükleme, yansıma yayan geçici derlemeler için tek seçenektir. Bağlam olmadan yükleme, aynı kimliğe sahip birden çok derlemeyi tek bir uygulama etki alanına yüklemenin tek yoludur. Sondalamanın maliyetinden kaçınılır.  
  
 İlke uygulandığında kurulan derlemenin kimliği, genel derleme önbelleğindeki bir derlemenin kimliğiyle eşleşmedikçe, bayt dizilerinden yüklenen derlemeler bağlam sızdırılır; bu durumda, derleme genel montaj önbelleğinden yüklenir.  
  
 Bağlam olmadan derlemeler yükleme aşağıdaki dezavantajları vardır:  
  
- Diğer derlemeler, <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> siz olayı işlemediğiniz sürece bağlam olmadan yüklenen derlemelere bağlanamaz.  
  
- Bağımlılıklar otomatik olarak yüklenmez. Bunları bağlam olmadan önceden yükleyebilir, varsayılan yük bağlamına önceden yükleyebilir veya olayı işleyerek yükleyebilirsiniz. <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>  
  
- Bağlam olmadan aynı kimliğe sahip birden çok derlemenin yüklenmesi, aynı kimliğe sahip derlemelerin birden çok içeriğe yüklenmesinden kaynaklanan tür kimlik sorunlarına neden olabilir. Bkz. [Derlemeyi Birden Çok İçerir'e Yüklemekten Kaçının.](#avoid_loading_into_multiple_contexts)  
  
- Derleme için yerel bir görüntü varsa, kullanılmaz.  
  
- Derleme etki alanı nötr olarak yüklenemez.  
  
- .NET Framework 1.0 ve 1.1 sürümlerinde ilke uygulanmaz.  
  
<a name="avoid_partial_names"></a>
## <a name="avoid-binding-on-partial-assembly-names"></a>Kısmi Montaj Adlarını Bağlamaktan Kaçının  
 Kısmi ad bağlama, bir derleme yüklediğinizde montaj<xref:System.Reflection.Assembly.FullName%2A>göstergesi adının yalnızca bir kısmını ( ) belirttiğiniz zaman oluşur. Örneğin, <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi yalnızca basit bir derleme adı olan, sürüm, kültür ve ortak anahtar belirteci atlayarak çağırabilirsiniz. Veya <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> önce yöntemi <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> çağıran ve derlemeyi bulamıyorsa, genel derleme önbelleğini arayan ve derlemenin kullanılabilir en son sürümünü yükleyen yöntemi arayabilirsiniz.  
  
 Kısmi ad bağlama, aşağıdakiler de dahil olmak üzere birçok soruna neden olabilir:  
  
- Yöntem, <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> aynı basit ada sahip farklı bir derleme yükleyebilir. Örneğin, iki uygulama, her ikisi de basit bir ada `GraphicsLibrary` sahip iki tamamen farklı derlemeleri genel derleme önbelleğine yükleyebilir.  
  
- Gerçekte yüklenen derleme geriye dönük uyumlu olmayabilir. Örneğin, sürümü belirtmemek, programınızın kullanmak üzere yazıldığı sürümden çok daha geç bir sürümün yüklenmesiyle sonuçlanabilir. Sonraki sürümdeki değişiklikler uygulamanızda hatalara neden olabilir.  
  
- Gerçekte yüklenen montaj ileri uyumlu olmayabilir. Örneğin, uygulamanızı bir derlemenin en son sürümüyle oluşturup test etmiş olabilirsiniz, ancak kısmi bağlama, uygulamanızın kullandığı özelliklerden yoksun çok daha önceki bir sürümü yükleyebilir.  
  
- Yeni uygulamalar yüklemek varolan uygulamaları bozabilir. <xref:System.Reflection.Assembly.LoadWithPartialName%2A> Yöntemi kullanan bir uygulama paylaşılan bir derlemenin daha yeni, uyumsuz bir sürümünü yükleyerek kırılabilir.  
  
- Beklenmeyen bağımlılık yüklemesi oluşabilir. Bir bağımlılığı paylaşan iki derleme yüklerseniz, bunları kısmi bağlamayla yüklemek, yapılamayan veya test edilmemiş bir bileşeni kullanarak bir derlemeye neden olabilir.  
  
 Neden olabileceği sorunlar nedeniyle, <xref:System.Reflection.Assembly.LoadWithPartialName%2A> yöntem geçersiz olarak işaretlenmiştir. Bunun yerine <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi kullanmanızı ve tam montaj görüntü adlarını belirtmenizi öneririz. Bkz. [Yük Bağlamlarının Avantaj ve Dezavantajlarını Anlayın](#load_contexts) ve [Varsayılan Yük Bağlamına Geçmeyi Düşünün.](#switch_to_default)  
  
 Derleme yüklemeyi <xref:System.Reflection.Assembly.LoadWithPartialName%2A> kolaylaştırdığı için yöntemi kullanmak istiyorsanız, uygulamanızın eksik derlemeyi tanımlayan bir hata iletisiyle başarısız olmasının, derlemenin bilinmeyen bir sürümünü otomatik olarak kullanmaktan daha iyi bir kullanıcı deneyimi sağlama olasılığının yüksek olduğunu ve bunun öngörülemeyen davranış ve güvenlik açıklarına neden olabileceğini düşünün.  
  
<a name="avoid_loading_into_multiple_contexts"></a>
## <a name="avoid-loading-an-assembly-into-multiple-contexts"></a>Derlemeyi Birden Çok İçerir'e Yüklemekten Kaçının  
 Derlemeyi birden çok içeriğe yüklemek tür kimliği sorunlarına neden olabilir. Aynı tür aynı derlemeden iki farklı içeriğe yüklenirse, aynı ada sahip iki farklı tür yüklenmiş gibi olur. Bir <xref:System.InvalidCastException> türü diğerine atmaya çalışırsanız, bu tür `MyType` ekibe `MyType`atılamaz kafa karıştırıcı ileti ile bir atılır.  
  
 Örneğin, `ICommunicate` `Utility`arabirimin, programınız ve ayrıca programınızın yüklediği diğer derlemeler tarafından başvurulan adlı bir derlemede bildirilmiş olduğunu varsayalım. Bu diğer derlemeler, `ICommunicate` arabirimi uygulayan ve programınızın bunları kullanmasına izin veren türler içerir.  
  
 Şimdi programınız çalıştırıldığında ne olacağını düşünün. Programınız tarafından başvurulan derlemeler varsayılan yük bağlamına yüklenir. Bir hedef derlemeyi, <xref:System.Reflection.Assembly.Load%2A> yöntemi kullanarak kimliğine göre yüklerseniz, varsayılan yük bağlamında olur ve bağımlılıkları da yüklenir. Hem programınız hem de hedef `Utility` derleme aynı derlemeyi kullanır.  
  
 Ancak, yöntemi kullanarak hedef derlemeyi dosya yoluna <xref:System.Reflection.Assembly.LoadFile%2A> yüklediğinizi varsayalım. Derleme herhangi bir bağlam olmadan yüklenir, bu nedenle bağımlılıkları otomatik olarak yüklenmez. <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> Olayın bağımlılık sağlaması için bir işleyiciniz olabilir ve <xref:System.Reflection.Assembly.LoadFile%2A> yöntemi kullanarak `Utility` derlemeyi bağlam olmadan yükleyebilir. Şimdi, hedef derlemede bulunan bir tür örneği oluşturduğunuzda ve bunu bir tür `ICommunicate`değişkenine atamaya çalıştığınızda, `ICommunicate` çalışma zamanı `Utility` derlemenin iki kopyasındaki arabirimleri farklı türler olarak değerlendirdiği için bir <xref:System.InvalidCastException> atılmıştır.  
  
 Derlemenin birden çok içeriğe yüklenebileceği başka senaryolar da vardır. En iyi yaklaşım, uygulama yolunuzdaki hedef derlemeyi değiştirerek ve <xref:System.Reflection.Assembly.Load%2A> yöntemi tam ekran adı ile kullanarak çakışmaları önlemektir. Derleme daha sonra varsayılan yük bağlamına yüklenir ve `Utility` her iki derleme de aynı derlemeyi kullanır.  
  
 Hedef derlemenin uygulama yolunuzuzun dışında kalması <xref:System.Reflection.Assembly.LoadFrom%2A> gerekiyorsa, bu yöntemi yük bağlamına yüklemek için kullanabilirsiniz. Hedef derleme, uygulamanızın `Utility` derlemesine bir başvuruyla derlenmişse, `Utility` uygulamanızın varsayılan yük bağlamına yüklediği derlemeyi kullanır. Hedef derlemenin uygulama yolunuzuzun dışında bulunan `Utility` derlemenin bir kopyasına bağımlı olması durumunda sorunların oluşabileceğini unutmayın. Bu derleme, uygulamanız `Utility` montajı yüklemeden önce yük ten içeriğe yüklenirse, uygulamanızın yükü başarısız olur.  
  
 [Varsayılan Yük Bağlamına Geçmeyi Düşün](#switch_to_default) bölümü, dosya yolu <xref:System.Reflection.Assembly.LoadFile%2A> yüklerini kullanma nın alternatiflerini tartışır ve. <xref:System.Reflection.Assembly.LoadFrom%2A>  
  
<a name="avoid_loading_multiple_versions"></a>
## <a name="avoid-loading-multiple-versions-of-an-assembly-into-the-same-context"></a>Bir Derlemenin Birden Çok Sürümüne Aynı İçerime Yüklemekten Kaçının  
 Bir derlemenin birden çok sürümüne tek bir yük bağlamına yüklenmesi tür kimliği sorunlarına neden olabilir. Aynı tür, aynı derlemenin iki sürümünden yüklenmişse, aynı ada sahip iki farklı tür yüklenmiş gibi olur. Bir <xref:System.InvalidCastException> türü diğerine atmaya çalışırsanız, bu tür `MyType` ekibe `MyType`atılamaz kafa karıştırıcı ileti ile bir atılır.  
  
 Örneğin, programınız `Utility` derlemenin bir sürümünü doğrudan yükleyebilir ve daha sonra `Utility` derlemenin farklı bir sürümünü yükleyen başka bir derleme yükleyebilir. Veya bir kodlama hatası, uygulamanızda bir derlemenin farklı sürümlerini yüklemek için iki farklı kod yolunun yüklenmesine neden olabilir.  
  
 Varsayılan yük bağlamında, <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi kullandığınızda ve farklı sürüm numaralarını içeren tam montaj görüntü adlarını belirttiğiniz zaman bu sorun oluşabilir. Bağlam olmadan yüklenen derlemeler için sorun, aynı derlemeyi farklı yollardan yüklemek için <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> yöntem kullanılarak neden olabilir. Çalışma zamanı, kimlikleri aynı olsa bile, farklı yollardan yüklenen iki derlemeyi farklı derlemeler olarak kabul eder.  
  
 Tür kimlik sorunlarına ek olarak, derlemenin <xref:System.MissingMethodException> birden çok sürümü, derlemenin bir sürümünden yüklenen bir tür, bu türü farklı bir sürümden bekleyen koda geçirilirse neden olabilir. Örneğin, kod sonraki sürüme eklenen bir yöntem bekleyebilirsiniz.  
  
 Tür davranışı sürümler arasında değiştiyse daha ince hatalar oluşabilir. Örneğin, bir yöntem beklenmeyen bir özel durum atabilir veya beklenmeyen bir değer döndürebilir.  
  
 Derlemenin yalnızca bir sürümünün yüklendiğinden emin olmak için kodunuzu dikkatle inceleyin. Herhangi bir <xref:System.AppDomain.GetAssemblies%2A?displayProperty=nameWithType> zamanda hangi derlemelerin yüklendiğini belirlemek için yöntemi kullanabilirsiniz.  
  
<a name="switch_to_default"></a>
## <a name="consider-switching-to-the-default-load-context"></a>Varsayılan Yük Bağlamına Geçmeyi Düşünün  
 Uygulamanızın montaj yükleme ve dağıtım desenlerini inceleyin. Bayt dizilerinden yüklenen derlemeleri ortadan kaldırabilir misiniz? Meclisleri sondaj yoluna taşıyabilir misin? Derlemeler genel derleme önbelleğinde veya uygulama etki alanının sondalama yolunda bulunuyorsa (diğer bir deyişle, onun <xref:System.AppDomainSetup.ApplicationBase%2A> ve <xref:System.AppDomainSetup.PrivateBinPath%2A>), derlemeyi kimliğine göre yükleyebilirsiniz.  
  
 Tüm derlemelerinizi sondalama yoluna koymak mümkün değilse, .NET Framework eklentimodelini kullanma, derlemeleri genel derleme önbelleğine yerleştirme veya uygulama etki alanları oluşturma gibi alternatifleri göz önünde bulundurun.  
  
### <a name="consider-using-the-net-framework-add-in-model"></a>.NET Framework Add-In Modelini Kullanmayı Düşünün  
 Genellikle uygulama tabanında yüklü olmayan eklentileri uygulamak için yükten gelen bağlamı kullanıyorsanız, .NET Framework eklentisi modelini kullanın. Bu model, uygulama etki alanlarını kendiniz yönetmenize gerek kalmadan uygulama etki alanında veya işlem düzeyinde yalıtım sağlar. Eklenti modeli hakkında daha fazla bilgi için [Eklentiler ve Genişletilebilirlik'e](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb384200(v%3dvs.100))bakın.  
  
### <a name="consider-using-the-global-assembly-cache"></a>Genel Montaj Önbelleğini Kullanmayı Düşünün  
 Varsayılan yük bağlamının avantajlarını kaybetmeden veya diğer bağlamların dezavantajlarını üstlenmeden, uygulama tabanının dışında paylaşılan bir derleme yolundan yararlanmak için derlemeleri genel derleme önbelleğine yerleştirin.  
  
### <a name="consider-using-application-domains"></a>Uygulama Etki Alanlarını Kullanmayı Düşünün  
 Bazı derlemelerinizin uygulamanın sondalama yolunda dağıtılamayacağını belirlerseniz, bu derlemeler için yeni bir uygulama alanı oluşturmayı düşünün. Yeni <xref:System.AppDomainSetup> uygulama etki alanı oluşturmak için <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> bir kullanın ve yüklemek istediğiniz derlemeleri içeren yolu belirtmek için özelliği kullanın. Sondalamak için birden çok dizin <xref:System.AppDomainSetup.ApplicationBase%2A> varsa, bir kök dizini ayarlayabilir ve sondaiçin alt dizinleri tanımlamak için <xref:System.AppDomainSetup.PrivateBinPath%2A?displayProperty=nameWithType> özelliği kullanabilirsiniz. Alternatif olarak, birden çok uygulama etki <xref:System.AppDomainSetup.ApplicationBase%2A> alanı oluşturabilir ve her uygulama etki alanının derlemeleri için uygun şekilde ayarlayabilirsiniz.  
  
 Bu derlemeleri <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> yüklemek için yöntemi kullanabileceğinizi unutmayın. Artık sondalama yolunda olduklarından, yük bağlamı yerine varsayılan yük bağlamına yüklenirler. Ancak, <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> doğru sürümlerin her zaman kullanıldığından emin olmak için yönteme geçmenizi ve tam montaj ekran adları sağlamanızı öneririz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>
- <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>
