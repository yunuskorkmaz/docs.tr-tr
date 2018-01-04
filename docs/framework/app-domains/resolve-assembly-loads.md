---
title: "Derleme Yüklerini Çözme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], resolving loads
- application domains, loading assemblies
- resolving assembly loads
- assemblies [.NET Framework], loading
- application domains, resolving assembly loads
ms.assetid: 5099e549-f4fd-49fb-a290-549edd456c6a
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3eb975b7ee8fdbba8435937fcb6f976d464db932
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="resolving-assembly-loads"></a>Derleme Yüklerini Çözme
.NET Framework sağlar <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay yüklenirken derleme üzerinde daha fazla denetim gerektiren uygulamalar için. Bu olay işleyerek uygulamanız hangi birkaç derleme sürümlerini yüklemek için bir dinamik derleme yayma ve geri yükleme bağlamdan normal yoklama yolları, select dışındaki bir derlemeyi yüklemek vb. Bu konuda işleme yönelik yönergeler sağlanmaktadır <xref:System.AppDomain.AssemblyResolve> olay.  
  
> [!NOTE]
>  Derleme yüklerini salt yansıma bağlamında çözümlemek için <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> olay bunun yerine.  
  
## <a name="how-the-assemblyresolve-event-works"></a>AssemblyResolve olay nasıl çalışır?  
 İçin bir işleyici kaydettiğinizde <xref:System.AppDomain.AssemblyResolve> olay işleyicisi adı tarafından çağrılan bir derlemeye bağlamak Çalışma Zamanı Modülü başarısız olduğunda. Örneğin, kullanıcı kodundan aşağıdaki yöntemleri çağırma neden <xref:System.AppDomain.AssemblyResolve> çıkarılmasına olay:  
  
-   Bir <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> yöntemi aşırı yüklemesini veya <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi aşırı yüklemesini, ilk bağımsız değişkeni olan yüklemek için derleme görünen adını temsil eden bir dize (diğer bir deyişle, tarafından döndürülen dize <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> özelliği).  
  
-   Bir <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> yöntemi aşırı yüklemesini veya <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi aşırı yüklemesini, ilk bağımsız değişkeni bir <xref:System.Reflection.AssemblyName> yüklemek için derleme tanımlayan nesne.  
  
-   Bir <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> yöntemi aşırı yüklemesini.  
  
-   Bir <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> veya <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> başka bir uygulama etki alanındaki bir nesneyi başlatır yöntemi aşırı yüklemesini.  
  
### <a name="what-the-event-handler-does"></a>Olay işleyiciyi içermiyor  
 İşleyicisi <xref:System.AppDomain.AssemblyResolve> olayı olarak yüklenmesi için derleme görünen adını alır <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> özelliği. İşleyicinin derleme adı tanımazsa, null döndürür (`Nothing` Visual Basic'te `nullptr` Visual C++'ta).  
  
 İşleyicinin derleme adı tanısa da yük ve istek karşılayan bir derlemeyi döndürür. Aşağıdaki listede bazı örnek senaryolar açıklanmaktadır.  
  
-   İşleyicinin derleme sürümünün konumunu biliyorsa kullanarak derleme yükleyebileceği <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> veya <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> yöntemi ve yüklenen derleme başarılı olursa geri dönebilirsiniz.  
  
-   İşleyici bayt dizileri depolanan derlemelerinin bir veritabanına erişimi varsa, aşağıdakilerden birini kullanarak bir bayt dizisi yükleyebileceği <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> bir bayt dizisi ele yöntemi aşırı.  
  
-   İşleyici, bir dinamik derleme oluşturur ve onu döndürür.  
  
> [!NOTE]
>  İşleyicinin derleme bağlamdan yükleme, yük bağlam içine veya bağlam olmadan içine yüklemeniz gerekir. İşleyicinin derleme salt yansıma bağlamına kullanarak yükler, <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> veya <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> yöntemi, yükleme denemesi, geçirilen <xref:System.AppDomain.AssemblyResolve> olay başarısız olur.  
  
 Uygun bir derleme döndürmek için olay işleyicisini sorumluluğundadır. İşleyici istenen derlemeyi görünen adını geçirerek ayrıştıramıyor <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> özellik değerine <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> Oluşturucusu. İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], işleyici kullanabilirsiniz <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> geçerli isteğin bir bağımlılık başka bir derlemenin olup olmadığını belirlemek için özellik. Bu bilgiler bağımlılığını yerine getirecek bir derlemeyi tanımlamaya yardımcı olabilir.  
  
 Olay işleyicisinin derleme istenen sürümden farklı bir sürümünü geri dönebilirsiniz.  
  
 Çoğu durumda, işleyici tarafından döndürülen derleme işleyicisi içine yükler bağlam bağımsız olarak yük bağlamında görüntülenir. Örneğin, işleyicinin kullanıyorsa <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> bağlamdan yükleme, derleme bir derlemeyi yüklemeye yöntemi işleyici döndürdüğünde yük bağlamında görüntülenir. Ancak, aşağıdaki durumda işleyici döndürdüğünde bağlamı olmadan derleme görünür:  
  
-   İşleyici bağlamı olmadan bir derleme yükler.  
  
-   <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> Özelliği null değil.  
  
-   İstekte bulunan derleme (diğer bir deyişle, tarafından döndürülen derleme <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> özelliği) bağlamı olmadan yüklendi.  
  
 İçerikleri hakkında daha fazla bilgi için bkz: <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> yöntemi aşırı yüklemesini.  
  
 Aynı uygulama etki alanına aynı bütünleştirilmiş kodda birden fazla sürümünü yüklenebilir. Atama sorunları yazmak için neden olabilir çünkü bu yöntem önerilmez. Bkz: [en iyi uygulamalar için derleme yükleme](../../../docs/framework/deployment/best-practices-for-assembly-loading.md).  
  
### <a name="what-the-event-handler-should-not-do"></a>Hangi olay işleyicisi yapmanız gerekir  
 İşleme için birincil kuralı <xref:System.AppDomain.AssemblyResolve> olaydır, tarafından tanınmayan bir derlemeyi döndürülecek çalışmanız gerektiğidir değil. İşleyici yazarken, hangi derlemelerin olay çıkarılmasına neden olabilecek bilmeniz gerekir. İşleyicinizi diğer derlemeler için null değerini döndürmelidir.  
  
> [!IMPORTANT]
>  İle başlayarak [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], <xref:System.AppDomain.AssemblyResolve> olayı için uydu derlemelerini oluşturulur. Tüm derleme yük istekleri çözmek işleyici çalışırsa, bu değişiklik .NET Framework'ün önceki bir sürümü için yazılmış bir olay işleyicisi etkiler. Bunlar tarafından tanınmayan derlemeleri yoksay olay işleyicileri bu değişiklikten etkilenmez: boş döndürmeleri ve normal geri dönüş mekanizması gelmelidir.  
  
 Bir derlemeyi yüklenirken, olay işleyicisi herhangi birini kullanmamalısınız <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> veya <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> neden olabilir yöntemi aşırı <xref:System.AppDomain.AssemblyResolve> yükseltilmiş yinelemeli olarak, çünkü bu bir yığın taşması neden olacak şekilde olay. (Bu konuda daha önce sağlanan listesine bakın.) Tüm olay işleyicileri döndürmüş kadar hiçbir özel durum nedeniyle özel durum işleme yükü talebi sağlayan olsa bile bu gerçekleşir. Bu nedenle, aşağıdaki kod, bir yığın taşması sonuçları `MyAssembly` bulunamadı:  
  
 [!code-cpp[AssemblyResolveRecursive#1](../../../samples/snippets/cpp/VS_Snippets_CLR/assemblyresolverecursive/cpp/example.cpp#1)]
 [!code-csharp[AssemblyResolveRecursive#1](../../../samples/snippets/csharp/VS_Snippets_CLR/assemblyresolverecursive/cs/example.cs#1)]
 [!code-vb[AssemblyResolveRecursive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/assemblyresolverecursive/vb/example.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bütünleştirilmiş Kod Yükleme için En İyi Yöntemler](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)  
 [Uygulama Etki Alanlarını Kullanma](../../../docs/framework/app-domains/use.md)
