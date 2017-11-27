---
title: "Dinamik dil çalışma zamanına genel bakış | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dynamic language runtime
- IronPython
- DLR
- IronRuby
ms.assetid: f769a271-8aff-4bea-bfab-6160217ce23d
caps.latest.revision: "26"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b62a737a5106c64d08a342365867c460075011b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="dynamic-language-runtime-overview"></a>Dinamik Dil Çalışma Zamanına Genel Bakış
*Dinamik dil çalışma zamanı* (DLR) olan hizmetleri dinamik diller için bir dizi ortak dil çalışma zamanı (CLR) ekler bir çalışma zamanı ortamı. DLR, .NET Framework üzerinde çalıştırmak için ve statik olarak yazılan diller için dinamik özellik eklemek için dinamik dilleri geliştirmek kolaylaştırır.  
  
 Dinamik Dil belirleyebilir bir nesne türünü çalışma zamanında statik olarak yazılmış ancak C# ve Visual Basic gibi dilleri (kullandığınızda `Option Explicit On`) tasarım zamanında nesne türlerini belirtmeniz gerekir. Dinamik Dil Lisp, Smalltalk, JavaScript, PHP, Ruby, Python, ColdFusion, Lua, Cobra ve Groovy gösterilebilir.  
  
 Çoğu dinamik dilleri geliştiriciler için aşağıdaki avantajları sağlar:  
  
-   Bir hızlı geri döngü (REPL veya okuma değerlendirmek Yazdır, döngü) kullanma olanağı. Bu, birkaç deyimleri girin ve hemen bunları sonuçları görmek için Yürüt sağlar.  
  
-   Yukarıdan aşağıya geliştirme ve daha geleneksel aşağıdan yukarıya geliştirme desteği. Örneğin, yukarıdan aşağıya yaklaşımı kullandığınızda, henüz uygulanmadı işlevleri çağırmak ve bunları gerektiğinde temel alınan uygulamaları ekleyin.  
  
-   Daha kolay yeniden düzenleme ve statik tür bildirimleri kod genelindeki değiştirmek olmadığı için değişiklik kod.  
  
 Dinamik Dil mükemmel komut dosyası dili olun. Müşterilerin kolayca yeni komutları ve işlevsellik ile dinamik diller kullanılarak oluşturulan uygulamaların genişletebilirsiniz. Dinamik dilleri de sık Web siteleri oluşturmak için kullanılır ve sunucu grupları bakımı, çeşitli yardımcı programlarını geliştirme ve veri dönüşümleri gerçekleştirme harnesses sınayın.  
  
 DLR amacı, .NET Framework üzerinde çalıştırmak ve .NET birlikte çalışabilirliği sağlamak için dinamik diller sistem sağlamaktır. DLR C# ve Visual Studio 2010 Visual Basic'te bu dillerde dinamik davranışını desteklemez ve çalışabilmeleri dinamik dilleri ile etkinleştirmek için dinamik nesneler tanıtır.  
  
 DLR, ayrıca, dinamik işlemler destekleyen kitaplıkları oluşturmanıza yardımcı olur. Örneğin, XML veya JavaScript nesne gösterimi (JSON) nesnelerini kullanan bir kitaplığınız varsa nesnelerinizi DLR kullanan diller için dinamik nesneler olarak yer alabilir. Bu nesneler ile çalışan ve nesnenin üyelerine erişme sözdizimsel olarak daha basit ve daha doğal kod yazma kitaplığı kullanıcıları sağlar.  
  
 Örneğin, C# XML sayacında artırmak için aşağıdaki kodu kullanabilirsiniz.  
  
 `Scriptobj.SetProperty("Count", ((int)GetProperty("Count")) + 1);`  
  
 DLR kullanarak, aşağıdaki kodu aynı işlem için bunun yerine kullanabilirsiniz.  
  
 `scriptobj.Count += 1;`  
  
 CLR gibi DLR .NET Framework'ün bir parçası ve .NET Framework ve Visual Studio yükleme paketleri sağlanır. DLR açık kaynak sürümü indirmek için de kullanılabilir [CodePlex](http://go.microsoft.com/fwlink/?LinkId=141028) Web sitesi.  
  
> [!NOTE]
>  DLR açık kaynak sürümü Visual Studio ve .NET Framework dahil DLR tüm özelliklerini sahiptir. Dil uygulayıcılar için ek destek de sağlar. Daha fazla bilgi için belgelere bakın [CodePlex](http://go.microsoft.com/fwlink/?LinkId=141028) Web sitesi.  
  
 DLR kullanılarak geliştirilmiş dilleri örnekleri şunlardır:  
  
-   IronPython. Kullanılabilir açık kaynaklı yazılımları olarak [GitHub](https://github.com/IronLanguages/ironpython2) Web sitesi.  
  
-   IronRuby. Kullanılabilir açık kaynaklı yazılımları olarak [RubyForge](http://go.microsoft.com/fwlink/?LinkId=141044) Web sitesi.  
  
## <a name="primary-dlr-advantages"></a>Birincil DLR avantajları  
 DLR aşağıdaki avantajları sağlar.  
  
### <a name="simplifies-porting-dynamic-languages-to-the-net-framework"></a>.NET Framework dinamik dilleri taşıma basitleştirir  
 DLR sözcük çözümleyiciler, ayrıştırıcıları, semantik çözümleyiciler, kod oluşturucuları ve geleneksel kendilerini oluşturmak için sahip oldukları diğer araçları oluşturmamak dil Implementers sağlar. DLR kullanmak için bir dil üretmek gerek duyduğu *ifade ağaçları*, çalışma zamanı yardımcı yordamları, bir ağaç şeklinde yapısı dil düzeyi kodda temsil eder ve isteğe bağlı dinamik nesneleri uygulamak <xref:System.Dynamic.IDynamicMetaObjectProvider> arabirimi. DLR ve .NET Framework çok fazla kod analizi ve kod oluşturma görevleri otomatik hale getirme. Bu dil Implementers benzersiz dil özellikleri odaklanmasına olanak sağlar.  
  
### <a name="enables-dynamic-features-in-statically-typed-languages"></a>Statik olarak yazılan dillerde dinamik özelliklerini etkinleştirir  
 C# ve Visual Basic gibi var olan .NET Framework dilleri dinamik nesneler oluşturma ve statik olarak yazılan nesnelerin ile birlikte kullanın. Örneğin, C# ve Visual Basic dinamik nesneler için HTML, belge nesne modeli (DOM) ve .NET yansıması kullanabilirsiniz.  
  
### <a name="provides-future-benefits-of-the-dlr-and-net-framework"></a>DLR ve .NET Framework gelecekteki avantajları sağlar  
 DLR kullanarak uygulanan dilleri gelecekteki DLR ve .NET Framework geliştirmelerden faydalanabilmeniz yararlı olabilir. Örneğin, bir geliştirilmiş atık toplayıcı veya yükleme süresi daha hızlı derleme sahip yeni bir sürümü .NET Framework sürümü, DLR hemen kullanarak uygulanan dilleri aynı avantajı alırsınız. DLR daha iyi derleme gibi iyileştirmeler eklerse, performans DLR kullanarak uygulanan tüm diller için de geliştirir.  
  
### <a name="enables-sharing-of-libraries-and-objects"></a>Kitaplıklar ve nesnelerin etkinleştirir paylaşımı  
 Nesneleri ve bir dilde uygulanan kitaplıkları diğer dilleri tarafından kullanılabilir. DLR de statik olarak yazılan ve dinamik dilleri arasında birlikte çalışabilirlik sağlar. Örneğin, C# dinamik bir dilinde yazılmış bir kitaplık kullanan bir dinamik Nesne bildirebilirsiniz. Aynı anda .NET Framework kitaplıklarından dinamik dilleri kullanabilirsiniz.  
  
### <a name="provides-fast-dynamic-dispatch-and-invocation"></a>Hızlı dinamik gönderme ve çağırma sağlar  
 DLR Gelişmiş çok biçimli önbelleğe almayı destekleyerek dinamik işlemler hızlı yürütülmesini sağlar. DLR gerekli çalışma zamanı uygulamaları nesnelere kullanan işlemler bağlama için kurallar oluşturur ve bu kurallar aynı nesne türlerini aynı kod birbirini izleyen yürütmeleri sırasında Kaynak Tükenme bağlama hesaplamalar önlemek için önbelleğe alır.  
  
## <a name="dlr-architecture"></a>DLR mimarisi  
 Aşağıdaki çizimde, dinamik dil çalışma zamanı mimarisini gösterir.  
  
 ![Dinamik dil çalışma zamanı mimarisine genel bakış](../../../docs/framework/reflection-and-codedom/media/dlr-archoverview.png "DLR_ArchOverview")  
DLR mimarisi  
  
 DLR daha iyi CLR bir hizmetler kümesini ekleyen dinamik dili destekleyen. Bu hizmetler şunlardır:  
  
-   İfade ağaçları. DLR dil semantiği göstermek için ifade ağaçları kullanır. Bu amaç için denetim akışı, atama ve diğer dili modelleme düğümleri içerecek şekilde genişletilmiş LINQ ifade ağaçları DLR sahiptir. Daha fazla bilgi için bkz: [ifade ağaçları](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b).  
  
-   Site önbelleğe almayı çağırın. A *dinamik çağrısı site* gibi bir işlem gerçekleştirdiğiniz kod yürürlükte olan `a + b` veya `a.b()` dinamik nesneler üzerinde. DLR özelliklerini önbelleğe `a` ve `b` (genellikle bu nesne türleri) ve işlemi hakkında bilgi. Böyle bir işlem daha önce gerçekleştirildiyse DLR önbelleği hızlı dağıtım için gerekli tüm bilgileri alır.  
  
-   Dinamik Nesne birlikte çalışabilirlik. DLR sınıfları ve dinamik nesneleri ve işlemleri temsil eder ve dil Implementers ve dinamik kitaplıkların yazarlar tarafından kullanılan arabirimleri kümesi sağlar. Bu sınıflar ve arabirimler içerir <xref:System.Dynamic.IDynamicMetaObjectProvider>, <xref:System.Dynamic.DynamicMetaObject>, <xref:System.Dynamic.DynamicObject>, ve <xref:System.Dynamic.ExpandoObject>.  
  
 Yalnızca .NET Framework ile ancak diğer altyapılar ve Silverlight ve com gibi hizmetler ile iletişim kurmak için çağrı siteler DLR bağlayıcıları kullanır Bağlayıcıları bir dil semantiği şifreleyebilir ve ifade ağaçları kullanarak bir çağrı sitede işlemlerini gerçekleştirmek nasıl belirtin. Bu dinamik sağlar ve statik olarak DLR kitaplıkları paylaşma ve DLR destekleyen tüm teknolojileri erişmek için kullandığınız dilleri belirtilmiş.  
  
## <a name="dlr-documentation"></a>DLR belgeleri  
 DLR açık kaynak sürümü dinamik davranışı için bir dil eklemek için nasıl kullanılacağı hakkında ya da .NET Framework ile dinamik dil kullanımını etkinleştirme hakkında daha fazla bilgi için belgelere bakın [CodePlex](http://go.microsoft.com/fwlink/?LinkId=141028) Web sitesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Dynamic.ExpandoObject>  
 <xref:System.Dynamic.DynamicObject>  
 [Ortak dil çalışma zamanı](../../../docs/standard/clr.md)  
 [İfade ağaçları](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)  
 [İzlenecek yol: Oluşturma ve dinamik nesneler kullanma](~/docs/csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)