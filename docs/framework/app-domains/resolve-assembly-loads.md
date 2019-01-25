---
title: Derleme Yüklerini Çözme
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a93052cba4693e63b3cb702a5ab8f6e15a8d8dec
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684495"
---
# <a name="resolving-assembly-loads"></a>Derleme Yüklerini Çözme
.NET Framework sağlar <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> olay yüklenirken derleme üzerinde daha fazla denetim gerektiren uygulamalar için. Bu olayını işleyerek, uygulamanız hangisinin birkaç derleme sürümlerini yüklemek için dinamik bir derleme yayılamıyor ve döndürün. yük bağlamdan normal algılama yolları, select dışındaki bir derlemeyi yüklemek vb. Bu konuda işleme yönelik yönergeler sağlanmaktadır <xref:System.AppDomain.AssemblyResolve> olay.  
  
> [!NOTE]
>  Derleme yüklerini salt yansıma bağlamında çözümlemek için <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> olay yerine.  
  
## <a name="how-the-assemblyresolve-event-works"></a>AssemblyResolve olay nasıl çalışır?  
 İçin bir işleyici kaydettiğinizde <xref:System.AppDomain.AssemblyResolve> olay işleyicisi adına göre çalışma zamanının bir derlemeye bağlanacak başarısız olduğunda çağrılır. Örneğin, aşağıdaki yöntemleri çağırarak kullanıcı kodundan neden <xref:System.AppDomain.AssemblyResolve> tetiklenecek olayı:  
  
-   Bir <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> yöntemi aşırı yüklemesini veya <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi aşırı yüklemesi, ilk bağımsız değişken olan yüklenecek derlemenin görünen adını temsil eden bir dize (yani tarafından döndürülen dize <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> özelliği).  
  
-   Bir <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> yöntemi aşırı yüklemesini veya <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi aşırı yüklemesi, ilk bağımsız değişken bir <xref:System.Reflection.AssemblyName> yüklenecek derlemenin tanımlayan nesne.  
  
-   Bir <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> yöntemi aşırı yüklemesi.  
  
-   Bir <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> veya <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> başka bir uygulama etki alanındaki bir nesnesini başlatan bir yöntemi aşırı yüklemesi.  
  
### <a name="what-the-event-handler-does"></a>Olay işleyicisi yapar  
 İşleyici için <xref:System.AppDomain.AssemblyResolve> olayı içinde yüklenen derlemenin görünen adı alır <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> özelliği. İşleyicinin derleme adı tanımazsa, null değeri döndürür (`Nothing` Visual Basic'te `nullptr` Visual C++'ta).  
  
 İşleyicinin derleme adı tanıyorsa Bu yük ve istek karşılayan bir derleme döndürür. Aşağıdaki liste bazı örnek senaryolar açıklanmaktadır.  
  
-   İşleyicinin bir derlemenin sürümünü konumunu biliyorsa kullanarak derleme yükleyebileceği <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> veya <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> yöntemi ve yüklenen derleme başarılıysa döndürebilir.  
  
-   İşleyici derlemeleri bayt dizileri depolanan bir veritabanına erişimi varsa, aşağıdakilerden birini kullanarak bir bayt dizisi yükleyebileceği <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> bir bayt dizisi ele yöntemi aşırı yüklemeleri.  
  
-   İşleyici, dinamik bir derleme oluşturmak ve onu döndürür.  
  
> [!NOTE]
>  İşleyicinin derleme load-from bağlamı, yükleme bağlamı veya bağlam olmadan içine yüklemeniz gerekir. İşleyicinin derleme salt yansıma bağlamına kullanarak yükler, <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> veya <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> yöntemi, yükleme denemesi başlatan <xref:System.AppDomain.AssemblyResolve> event başarısız olur.  
  
 Uygun bir derleme döndürmek için olay işleyicisinin sorumluluğundadır. İşleyicinin istenen derlemenin görünen adını geçirerek ayrıştırabilirsiniz <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> özellik değerini <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> Oluşturucusu. İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], işleyici kullanabilirsiniz <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> geçerli istek başka bir derlemenin bir bağımlılık olup olmadığını belirlemek için özellik. Bu bilgiler bağımlılığını yerine getirecek bir derleme belirlemenize yardımcı olabilir.  
  
 Olay işleyicisi, istenen sürümden derlemenin farklı bir sürümünü geri dönebilirsiniz.  
  
 Çoğu durumda, işleyici tarafından döndürülen derleme yükleme bağlamı işleyicisi içine yükler bağlamı bağımsız olarak görünür. Örneğin, işleyicinin kullanıyorsa <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> load-from bağlamı içine derleme bir derlemeyi yüklemek için yöntemi işleyici döndürdüğünde yükleme bağlamı içinde görünür. Ancak, aşağıdaki örnekte işleyici döndürdüğünde bağlamı olmadan derleme görünür:  
  
-   İşleyici bağlamı olmadan bir derleme yükler.  
  
-   <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> Özelliği null değil.  
  
-   İstenen derleme (diğer bir deyişle, tarafından döndürülen derleme <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> özelliği) bağlamı olmadan yüklendi.  
  
 Bağlamları hakkında daha fazla bilgi için bkz. <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> yöntemi aşırı yüklemesi.  
  
 Aynı uygulama etki alanına aynı derlemenin birden çok sürümü yüklenebilir. Atama sorunları türüne neden olabileceği için bu uygulama önerilmez. Bkz: [en iyi uygulamalar için derleme yükleme](../../../docs/framework/deployment/best-practices-for-assembly-loading.md).  
  
### <a name="what-the-event-handler-should-not-do"></a>Hangi olay işleyicisi yapmanız gerekir  
 İşleme için birincil kuralı <xref:System.AppDomain.AssemblyResolve> olaydır tarafından tanınmayan bir derleme döndürülecek denememelisiniz. İşleyici yazdığınızda, hangi derlemelerin olay verilmesine neden olabilecek bilmeniz gerekir. İşleyicinizi diğer derlemeler için null değeri döndürmelidir.  
  
> [!IMPORTANT]
>  İle başlayarak [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], <xref:System.AppDomain.AssemblyResolve> olayı için uydu derlemeleri oluşturulur. Tüm derleme yük istekleri çözmek işleyici çalışırsa, bu değişiklik .NET Framework'ün önceki bir sürümü için yazılmış bir olay işleyicisi etkiler. Tarafından tanınmayan bütünleştirilmiş kodları yoksay olay işleyicileri, bu değişiklikten etkilenmez: Bunlar, null döndürür ve normal bir geri dönüş mekanizması izlenir.  
  
 Bir derleme yüklenirken, olay işleyicisi herhangi birini kullanmak zorunda değilsiniz <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> veya <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> neden olabilecek bir yöntem aşırı yüklemeleri <xref:System.AppDomain.AssemblyResolve> bu için yığın taşmasına neden olabileceği için yükseltilmiş yinelemeli olarak olay. (Bu konunun önceki kısımlarında sağlanan listesine bakın.) Bu, özel durum işleme yükleme isteği için sağladığınız tüm olay işleyicileri dönene kadar hiçbir özel durum nedeniyle olsa bile gerçekleşir. Bu nedenle, aşağıdaki kod, bir yığın taşması sonuçları `MyAssembly` bulunamadı:  
  
 [!code-cpp[AssemblyResolveRecursive#1](../../../samples/snippets/cpp/VS_Snippets_CLR/assemblyresolverecursive/cpp/example.cpp#1)]
 [!code-csharp[AssemblyResolveRecursive#1](../../../samples/snippets/csharp/VS_Snippets_CLR/assemblyresolverecursive/cs/example.cs#1)]
 [!code-vb[AssemblyResolveRecursive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/assemblyresolverecursive/vb/example.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Bütünleştirilmiş Kod Yükleme için En İyi Yöntemler](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)
- [Uygulama Etki Alanlarını Kullanma](../../../docs/framework/app-domains/use.md)
