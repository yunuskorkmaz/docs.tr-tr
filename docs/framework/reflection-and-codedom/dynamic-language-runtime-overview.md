---
title: Dinamik dil çalışma zamanına genel bakış | Microsoft Docs
ms.date: 03/30/2017
helpviewer_keywords:
- dynamic language runtime
- IronPython
- DLR
- IronRuby
ms.assetid: f769a271-8aff-4bea-bfab-6160217ce23d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a4645efc9276429cbdb0812f1ca501c89ea5dbb
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45743235"
---
# <a name="dynamic-language-runtime-overview"></a>Dinamik Dil Çalışma Zamanına Genel Bakış
*Dinamik dil çalışma zamanı* (DLR) olan bir çalışma zamanı ortamı Hizmetleri dinamik dilleri için bir dizi ortak dil çalışma zamanı (CLR) ekler. DLR dinamik dilleri .NET Framework üzerinde çalışan ve statik olarak yazılan diller için dinamik özellik eklemek için geliştirmeyi daha kolay hale getirir.  
  
 Dinamik dilleri belirleyebilir bir nesne türünü çalışma zamanında, statik olarak yazdığınız ancak C# ve Visual Basic gibi dilleri (kullandığınızda `Option Explicit On`) nesne türlerini çalışma zamanında belirtmeniz gerekir. Lisp, Smalltalk, JavaScript, PHP, Ruby, Python, ColdFusion, Lua, Cobra ve Groovy dinamik dilleri örnekleridir.  
  
 Çoğu dinamik diller, geliştiriciler için aşağıdaki avantajları sağlar:  
  
-   Bir hızlı geri bildirim döngüsü (REPL veya okuma değerlendirmek yazdırma döngü) kullanma olanağı. Bu, birkaç ifadelerini girin ve sonuçları görmek için bunları hemen yürütme sağlar.  
  
-   Hem üst alt geliştirme hem de daha geleneksel aşağıdan yukarıya geliştirme desteği. Örneğin, yukarıdan aşağıya yaklaşımı kullandığınızda, henüz uygulanmadı işlevlerini ve ihtiyaç duyduğunuzda ardından temel uygulamaları ekleyin.  
  
-   Yeniden düzenleme ve kod genelindeki statik tür bildirimleri değiştirmek olmadığı için kod değişiklikleri, daha kolay.  
  
 Dinamik dilleri mükemmel komut dosyası dilleri olun. Müşterilerin yeni komutlar ve işlevler ile dinamik dilleri kullanılarak oluşturulmuş uygulamaları kolayca genişletebilirsiniz. Dinamik dilleri, Web siteleri oluşturmak için de sık kullanılan ve sunucu grupları bakımı, çeşitli yardımcı programlarını geliştirme ve veri dönüşümleri gerçekleştirme harnesses test edin.  
  
 .NET Framework üzerinde çalışan ve bunları ve.NET birlikte çalışabilirliği sağlamak için dinamik dilleri bir sistemin DLR amacı etkinleştirmektir. C# ve Visual Studio 2010 Visual Basic'te bu dillerde dinamik davranışı destekleyen ve dinamik dilleri ile çalışabilmeleri etkinleştirmek için dinamik nesneler DLR tanıtır.  
  
 DLR ayrıca dinamik işlemleri destekleyen kitaplıkları oluşturmanıza yardımcı olur. Örneğin, XML veya JavaScript nesne gösterimi (JSON) nesneleri kullanan kitaplığı varsa, nesnelerinizi DLR kullanan diller için dinamik nesneler olarak görünebilir. Bu nesneler ile çalışan ve nesnenin üyelerine erişme sözdizimi kurallarına göre daha basit ve daha doğal kod yazma kitaplığı kullanıcıları sağlar.  
  
 Örneğin, C# dilinde XML sayacında artırmak için aşağıdaki kodu kullanabilirsiniz.  
  
 `Scriptobj.SetProperty("Count", ((int)GetProperty("Count")) + 1);`  
  
 DLR kullanarak, aşağıdaki kod aynı işlem için bunun yerine kullanabilirsiniz.  
  
 `scriptobj.Count += 1;`  
  
 CLR gibi DLR .NET Framework'ün bir parçasıdır ve .NET Framework ve Visual Studio yükleme paketleri sağlanır. DLR açık kaynak sürümü ücretsiz olarak da kullanılabilir [IronLanguages/dlr](https://github.com/IronLanguages/dlr) github deposu.  
  
> [!NOTE]
>  Visual Studio ve .NET Framework dahil DLR özelliklerinin tümünü DLR açık kaynak sürümü vardır. Ayrıca dil uygulayanlar için ek destek sağlar. Daha fazla bilgi için şirket belgelerine bakın. [IronLanguages/dlr](https://github.com/IronLanguages/dlr) github deposu. 
  
 DLR kullanılarak geliştirilen diller örnekleri şunları içerir:  
  
-   IronPython. Açık kaynak yazılımlardan olarak [GitHub](https://github.com/IronLanguages/ironpython2) Web sitesi.  
  
-   Ironruby. Açık kaynak yazılımlardan olarak [RubyForge](https://go.microsoft.com/fwlink/?LinkId=141044) Web sitesi.  
  
## <a name="primary-dlr-advantages"></a>Birincil DLR avantajları  
 DLR aşağıdaki avantajları sağlar.  
  
### <a name="simplifies-porting-dynamic-languages-to-the-net-framework"></a>.NET Framework için dinamik dilleri taşıma basitleştirir  
 Sözcük temelli çözümleyiciler, Çözümleyicileri, anlam Çözümleyicileri, kod oluşturucuları ve geleneksel olarak kendilerini oluşturmak için sahip oldukları diğer araçları oluşturmaktan kaçınmak dil uygulayıcılar DLR sağlar. DLR kullanmak için bir dil üretmesi gerekir *ifade ağaçları*isteğe bağlı dinamik nesneleri ve çalışma zamanı Yardımcısı rutinleri için bir ağaç şeklinde yapısına dil düzeyi kod temsil eden uygulamak <xref:System.Dynamic.IDynamicMetaObjectProvider> arabirimi. DLR ve .NET Framework çok fazla kod analizi ve kod oluşturma görevleri otomatikleştirin. Bu benzersiz dil özellikleri hakkında yoğunlaşabilirsiniz dil uygulayıcılar sağlar.  
  
### <a name="enables-dynamic-features-in-statically-typed-languages"></a>Statik olarak belirlenmiş dillerde dinamik özelliklerini etkinleştirir  
 C# ve Visual Basic gibi var olan .NET Framework dillerinde, dinamik nesneler oluşturma ve bunları statik olarak yazılan nesnelerin ile birlikte kullanın. Örneğin, C# ve Visual Basic dinamik nesneler için HTML belge nesne modeli (DOM) ve .NET yansıma kullanabilirsiniz.  
  
### <a name="provides-future-benefits-of-the-dlr-and-net-framework"></a>.NET Framework ve DLR gelecekteki avantajlarını sağlar  
 DLR kullanılarak diller, gelecekteki DLR ve .NET Framework iyileştirmeleri yararlı olabilir. Örneğin, bir Gelişmiş çöp Toplayıcıya veya yükleme süresi daha hızlı derleme sahip yeni bir sürümü .NET Framework sürümleri, DLR hemen kullanılarak uygulanan dil aynı avantajı alın. Daha iyi derleme gibi iyileştirmeler DLR ekler, DLR kullanılarak uygulanan tüm diller için performansı da artırır.  
  
### <a name="enables-sharing-of-libraries-and-objects"></a>Kitaplıklar ve nesnelerin etkinleştirir paylaşma  
 Nesneleri ve kitaplıkları tek bir dilde uygulanan diğer dilleri tarafından kullanılabilir. DLR ayrıca statik olarak yazılmış ve dinamik diller arasında birlikte çalışabilirlik sağlar. Örneğin, C# dinamik bir dilde yazılmış bir kitaplık kullanan bir dinamik Nesne bildirebilirsiniz. Dinamik dilleri, aynı zamanda, .NET Framework kitaplıkları kullanabilirsiniz.  
  
### <a name="provides-fast-dynamic-dispatch-and-invocation"></a>Hızlı dinamik dağıtma ve çağırma sağlar  
 DLR Gelişmiş çok biçimli önbelleğe alma destekleyerek dinamik işlemler hızlı olarak yürütülmesini sağlar. DLR gerekli çalışma zamanı uygulamaları için nesneleri kullanan işlemleri bağlama için kuralları oluşturur ve ardından bu kurallar aynı nesne türlerini aynı kodunu birbirini izleyen yürütmeleri sırasında kaynak tüketme bağlama hesaplamalar önlemek için önbelleğe alır.  
  
## <a name="dlr-architecture"></a>DLR mimarisi  
 Aşağıdaki çizim, dinamik dil çalışma zamanı mimarisini gösterir.  
  
 ![Dinamik dil çalışma zamanı mimarisine genel bakış](../../../docs/framework/reflection-and-codedom/media/dlr-archoverview.png "DLR_ArchOverview")  
DLR mimarisi  
  
 Bir hizmet kümesi için daha iyi CLR DLR ekler dinamik dili destekleyen. Bu hizmetler şunları içerir:  
  
-   İfade ağaçları. DLR dil semantiği temsil etmek için ifade ağaçları kullanır. Bu amaç için denetim akışı, atama ve diğer dil modelleme düğümleri içerecek şekilde genişletilmiş LINQ ifade ağaçları DLR sahiptir. Daha fazla bilgi için [ifade ağaçları](https://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b).  
  
-   Site önbelleğe alma çağırın. A *dinamik çağrı sitesini* gerçekleştirmek olduğu gibi bir işlem kodu bir yerinde olduğundan `a + b` veya `a.b()` dinamik nesneler üzerinde. DLR özelliklerini önbelleğe `a` ve `b` (genellikle bu nesne türleri) ve işlemi hakkında bilgi. Bu tür bir işlem daha önce gerçekleştirilen varsa DLR önbellekten hızlı dağıtım için gerekli tüm bilgileri alır.  
  
-   Dinamik Nesne birlikte çalışabilirlik. Sınıfları ve arabirimleri dinamik nesneleri ve işlemleri temsil eder ve dil uygulayıcılar ve dinamik kitaplıklar yazarları tarafından kullanılan bir dizi DLR sağlar. Bu sınıflar ve arabirimler dahil <xref:System.Dynamic.IDynamicMetaObjectProvider>, <xref:System.Dynamic.DynamicMetaObject>, <xref:System.Dynamic.DynamicObject>, ve <xref:System.Dynamic.ExpandoObject>.  
  
 Yalnızca .NET Framework ile ancak diğer altyapıları ve Silverlight ve com gibi hizmetler ile iletişim kurmak için çağrı siteleri DLR bağlayıcıları kullanır Bağlayıcıları, bir dil semantiği şifreleyebilir ve ifade ağaçları kullanarak bir çağrı sitesine işlemleri gerçekleştirmek nasıl belirtin. Bu, dinamik olarak sağlar ve DLR kitaplıkları paylaşma ve DLR destekleyen teknoloji erişmek için kullandığınız diller statik olarak belirlenmiş.  
  
## <a name="dlr-documentation"></a>DLR belgeleri  
 .NET Framework ile dinamik bir dil kullanımını etkinleştirme veya DLR açık kaynak sürümü için dil dinamik davranış eklemek için kullanma hakkında daha fazla bilgi için şirket belgelerine bakın. [IronLanguages/dlr](https://github.com/IronLanguages/dlr/tree/master/Docs) GitHub Git tarafından oluşturulur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Dynamic.ExpandoObject>  
 <xref:System.Dynamic.DynamicObject>  
 [Ortak dil çalışma zamanı](../../../docs/standard/clr.md)  
 [İfade Ağaçları](https://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)  
 [İzlenecek yol: Nesneler oluşturma ve dinamik kullanma](~/docs/csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
