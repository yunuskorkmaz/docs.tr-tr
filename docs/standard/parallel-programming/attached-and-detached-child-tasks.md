---
title: Eklenen ve Ayrılan Alt Görevler
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, child tasks
ms.assetid: c95788bf-90a6-4e96-b7bc-58e36a228cc5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83451af25006e9da396a3e6618cbecee036e9fe2
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003769"
---
# <a name="attached-and-detached-child-tasks"></a>Eklenen ve Ayrılan Alt Görevler
A *alt görev* (veya *iç içe görev*) olan bir <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> olarak da bilinen başka bir görevin kullanıcı temsilcisinde oluşturulan örnek *üst görev*. Bir alt görev ya da iliştirilemez ya da. A *ayrılmış alt görev* üst bağımsız olarak yürütülen bir görevdir. Bir *iliştirilmiş alt görevi* ile oluşturulan iç içe bir görevdir <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> ana değil açıkça veya varsayılan olarak engelliyor, bağlı olmak seçeneği. Bir görev yalnızca sistem kaynakları tarafından sınırlanan, eklenen veya ilişkisi kesilen alt herhangi bir sayıda oluşturabilirsiniz.  
  
 Aşağıdaki tabloda, iki tür alt görev arasındaki temel farklar listelenmektedir.  
  
|Kategori|Ayrılmış alt görevler|Eklenen alt görevler|  
|--------------|--------------------------|--------------------------|  
|Üst, alt görevlerin tamamlanmasını bekler.|Hayır|Evet|  
|Üst, alt görevler tarafından atılan özel durumları yayar.|Hayır|Evet|  
|Üst durum alt bağlıdır.|Hayır|Evet|  
  
 Kendi diğer görevlerle ilişkileri daha az karmaşık olduğundan çoğu senaryoda, ayrılmış alt görevleri kullanmanızı öneririz. Diğer bir deyişle neden üst görevler içinde oluşturulan görevlerin varsayılan olarak ayrılmasının ve açıkça belirtmeniz gerekir <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> bir eklenmiş alt görev oluşturmak için seçeneği.  
  
## <a name="detached-child-tasks"></a>Ayrılmış alt görevler  
 Bir alt görev üst görev tarafından oluşturulmasına rağmen varsayılan olarak, ana görevden bağımsızdır. Aşağıdaki örnekte, bir üst görev basit bir alt görev oluşturur. Örnek kod, birden çok kez çalıştırırsanız, örneğin çıktısında çıktısının gösterilenden farklı ve ayrıca çıktının değişebilir olduğunu her zaman kod çalıştırmadan fark edebilirsiniz. Bu, üst görev ve alt görevleri birbirinden yürütmek için oluşur; alt ayrılmış bir görevdir. Örneği tamamlamak, yalnızca üst görevin tamamlanmasını bekler ve alt görev ise yürütülmeyebilir veya konsol uygulamasını önce tam sonlandırır.  
  
 [!code-csharp[TPL_ChildTasks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/nested1.cs#1)]
 [!code-vb[TPL_ChildTasks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/nested1.vb#1)]  
  
 Alt görev tarafından temsil edilen, bir <xref:System.Threading.Tasks.Task%601> nesne yerine <xref:System.Threading.Tasks.Task> nesnesi, üst görev alt erişerek tamamlanması için bekleyeceği sağlayabilirsiniz <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> ayrılmış alt görev olsa bile alt özellik. <xref:System.Threading.Tasks.Task%601.Result%2A> Özelliği, aşağıdaki örnekte gösterildiği gibi görevi tamamlanıncaya kadar engeller.  
  
 [!code-csharp[TPL_ChildTasks#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/childtasks.cs#4)]
 [!code-vb[TPL_ChildTasks#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/tpl_childtasks.vb#4)]  
  
## <a name="attached-child-tasks"></a>Eklenen alt görevler  
 Ayrılmış alt görevlerden farklı olarak, eklenen alt görevler yakından üst görevlerle eşitlenir. Kullanarak bir eklenmiş alt görev için önceki örnekte ayrılan alt görevi değiştirebilirsiniz <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> seçeneğini görev oluşturma deyiminde aşağıdaki örnekte gösterildiği gibi. Bu kodda ekli alt görev üstünden önce tamamlanır. Sonuç olarak örnekteki çıktı, kodu her çalıştırdığınızda aynıdır.  
  
 [!code-csharp[TPL_ChildTasks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/child1.cs#2)]
 [!code-vb[TPL_ChildTasks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/child1.vb#2)]  
  
 Eklenen alt görevler zaman uyumsuz işlemlerin sıkı eşitlenmiş grafiklerini oluşturmak için kullanabilirsiniz.  
  
 Ancak, yalnızca üst eklenen alt görevler yasaklamaz, bir alt görevin kendi üst öğesine ekleyebilirsiniz. Üst görevler açıkça engelleyebilir alt görevleri için bunları belirterek eklenmesini <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> üst görevin sınıfı oluşturucusu seçeneğini veya <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> yöntemi. Üst görev örtük olarak çağrılarak oluşturulan varsa bunları eklenmesini alt görevler önlemek <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> yöntemi. Aşağıdaki örnek bunu göstermektedir. Üst görevin çağrılarak oluşturulan dışında önceki örnekle aynı <xref:System.Threading.Tasks.Task.Run%28System.Action%29?displayProperty=nameWithType> yöntemi yerine <xref:System.Threading.Tasks.TaskFactory.StartNew%28System.Action%29?displayProperty=nameWithType> yöntemi. Alt görevin üst göreve iliştirme mümkün olmadığı için örnekteki çıktı, tahmin edilemez. Varsayılan görev oluşturma seçenekleri çünkü <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> yükleri içer <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>, bu örnekte "ayrılmış alt görevler" bölümündeki ilk örnek işlevsel olarak eşdeğerdir.  
  
 [!code-csharp[TPL_ChildTasks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/child1a.cs#3)]
 [!code-vb[TPL_ChildTasks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/child1a.vb#3)]  
  
## <a name="exceptions-in-child-tasks"></a>Alt görevlerdeki özel durumlar  
 Ayrılmış alt görev, bir özel durum oluşturursa, bu özel durum gözlemlenen veya doğrudan üst görevde olduğu gibi yuvalı olmayan görev işlenmiş. Bir eklenmiş alt görev, bir özel durum oluşturursa, özel durum otomatik olarak üst göreve ve bekler ya da görevin erişmeye çalıştığında geri iş parçacığına yayılır <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> özelliği. Bu nedenle, eklenen alt görevler kullanarak, tek bir noktada yapılan çağrıda tüm özel durumları işleyebilir <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> çağıran iş parçacığında. Daha fazla bilgi için [özel durum işleme](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
## <a name="cancellation-and-child-tasks"></a>İptal ve alt görevler  
 Görev iptali ortaktır. Diğer bir deyişle, iptal edilebilir olması için her ekli veya ayrılmış alt görev iptal belirtecini durumunu izlemeniz gerekir. Bir iptal isteği kullanarak üst öğe ve tüm alt öğelerini iptal etmek istiyorsanız, aynı belirteci için tüm görevler bağımsız değişken olarak geçirin ve her görevde her görevdeki isteğe yanıt mantığını girin. Daha fazla bilgi için [görev iptali](../../../docs/standard/parallel-programming/task-cancellation.md) ve [nasıl yapılır: bir görevi ve kendi alt öğelerini iptal etme](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
### <a name="when-the-parent-cancels"></a>Üst öğe iptal ettiğinde  
 Alt görevi başlatılmadan önce bir üst kendisini iptal ederse, alt hiçbir zaman başlamaz. Alt öğesi zaten başlatıldıktan sonra bir üst kendisini iptal ederse, alt öğe kendi iptal mantığına sahip değilse tamamlanana kadar çalışacaktır. Daha fazla bilgi için [görev iptali](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
### <a name="when-a-detached-child-task-cancels"></a>Ayrılmış alt görev iptal ettiğinde  
 Özel durum Benign kurum iptali değerlendirildiğinden ayrılmış alt görev üst göreve geçirilen aynı belirteci kullanarak kendisini iptal ve üst, alt görevin tamamlanmasını beklemez, hiçbir özel durum yayılır. Bu davranış, herhangi bir üst düzey görev aynıdır.  
  
### <a name="when-an-attached-child-task-cancels"></a>Bir eklenmiş alt görev iptal ettiğinde  
 Bir eklenmiş alt görev, üst göreve geçirilen aynı belirteci kullanarak kendini iptal ettiğinde bir <xref:System.Threading.Tasks.TaskCanceledException> katılan iş parçacığına yayılır bir <xref:System.AggregateException>. Eklenen alt görevlerin bir graph üzerinden yukarı yayılır tüm bereketli özel durumları özel durumların yanı sıra işleyebilmeniz üst görevin tamamlanmasını beklemeniz gerekir.  
  
 Daha fazla bilgi için [özel durum işleme](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
## <a name="preventing-a-child-task-from-attaching-to-its-parent"></a>Bir alt görevin üst göreve eklenmesini önleme  
 Bir alt görev tarafından oluşturulan işlenmeyen bir özel durum üst göreve yayılan. Bu davranışı, tüm alt görev özel durumlarını görevler ağacının tamamında dolaşmak yerine tek kök görevden gözlemek için kullanabilirsiniz. Ancak, bir üst göreve başka koddan ek beklemediğinden özel durum yayma sorunlu olabilir. Örneğin, bir üçüncü taraf kitaplık bileşenini çağıran bir uygulama düşünün bir <xref:System.Threading.Tasks.Task> nesne. Üçüncü taraf kitaplık bileşeni ayrıca oluşturursa bir <xref:System.Threading.Tasks.Task> belirtir ve nesne <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> üst göreve eklemek için üst, alt görevdeki işlenmemiş özel durumlar yayar. Bu ana uygulamada beklenmeyen davranışlara neden olabilir.  
  
 Bir alt görevin ana görevine eklenmesini engellemek için bu seçeneği belirtin <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> seçeneği üst oluşturduğunuzda <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> nesne. Ne zaman bir görevin kendi üst öğesine eklemek çalışır ve üst belirtir <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> seçeneği, alt görev üst öğeye Ekle & mümkün olmayacaktır ve yalnızca yürütme gibi <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> seçeneği belirtilmedi.  
  
 Bir alt görev alt görev zamanında tamamladığında kendi üst öğesine eklenmesini önleme isteyebilirsiniz. Tüm alt görevler tamamlanıncaya kadar bir üst görev sonlanmaz, uzun süre çalışan alt görev genel uygulamanın sonlanmayacağından neden olabilir. Bir görev ana görevine eklenmesini önleyerek uygulama performansını gösteren bir örnek için bkz [nasıl yapılır: alt görevin kendi üst öğesinden iliştirme önleme](../../../docs/standard/parallel-programming/how-to-prevent-a-child-task-from-attaching-to-its-parent.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)  
- [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
