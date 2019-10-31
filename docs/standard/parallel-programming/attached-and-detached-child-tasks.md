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
ms.openlocfilehash: 8f15ee4f136e3e2df1a4e1c7683467f2a4bc9bc0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123180"
---
# <a name="attached-and-detached-child-tasks"></a>Eklenen ve Ayrılan Alt Görevler
Bir *alt görev* (veya *iç içe görev*), *üst görev*olarak bilinen başka bir görevin Kullanıcı temsilcisinde oluşturulan bir <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> örneğidir. Bir alt görev ayrılabilir veya bağlı olabilir. *Ayrılmış bir alt görev* , üst öğesinden bağımsız olarak yürütülen bir görevdir. *Bağlı bir alt görev* , üst öğesi açıkça veya varsayılan olarak, eklenmesini engelleyecek <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> seçeneğiyle oluşturulan iç içe bir görevdir. Bir görev, yalnızca sistem kaynaklarıyla sınırlı sayıda eklenmiş ve ayrılmış alt görev oluşturabilir.  
  
 Aşağıdaki tabloda iki alt görev türü arasındaki temel farklılıklar listelenmiştir.  
  
|Kategori|Ayrılmış alt görevler|Bağlı alt görevler|  
|--------------|--------------------------|--------------------------|  
|Üst öğe, alt görevlerin tamamlanmasını bekler.|Hayır|Evet|  
|Üst öğe, alt görevler tarafından oluşturulan özel durumları yayar.|Hayır|Evet|  
|Üst öğenin durumu, alt öğenin durumuna bağlıdır.|Hayır|Evet|  
  
 Çoğu senaryoda, diğer görevlerle ilişkileri daha az karmaşık olduğundan, ayrılmış alt görevleri kullanmanızı öneririz. Bu, üst görevler içinde oluşturulan görevlerin varsayılan olarak ayrılmasının ve bağlı bir alt görev oluşturmak için <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> seçeneğini açıkça belirtmeniz gerekir.  
  
## <a name="detached-child-tasks"></a>Ayrılmış alt görevler  
 Bir alt görev bir üst görev tarafından oluşturulmuş olsa da, varsayılan olarak üst görevden bağımsızdır. Aşağıdaki örnekte, bir üst görev bir basit alt görev oluşturur. Örnek kodu birden çok kez çalıştırırsanız, örneğin çıkışının gösterilenden farklı olduğunu ve ayrıca kodu her çalıştırdığınızda çıkışın değişolabileceğini fark edebilirsiniz. Bu, üst görev ve alt görevler birbirinden bağımsız olarak yürütülemediğinden oluşur; alt öğe, ayrılmış bir görevdir. Örnek yalnızca üst görevin tamamlanmasını bekler ve konsol uygulaması sonlandırılmadan önce alt görev yürütülemeyebilir veya tamamlanmayabilir.  
  
 [!code-csharp[TPL_ChildTasks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/nested1.cs#1)]
 [!code-vb[TPL_ChildTasks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/nested1.vb#1)]  
  
 Alt görev bir <xref:System.Threading.Tasks.Task> nesnesi yerine <xref:System.Threading.Tasks.Task%601> nesne tarafından temsil ediliyorsa, üst görevin, ayrılmış bir alt görev olsa bile alt öğenin <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> özelliğine erişerek alt öğenin tamamlanmasını beklemesini sağlayabilirsiniz. <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği, aşağıdaki örnekte gösterildiği gibi, görevi tamamlanana kadar engeller.  
  
 [!code-csharp[TPL_ChildTasks#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/childtasks.cs#4)]
 [!code-vb[TPL_ChildTasks#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/tpl_childtasks.vb#4)]  
  
## <a name="attached-child-tasks"></a>Bağlı alt görevler  
 Ayrılmış alt görevlerin aksine, eklenen alt görevler üst öğeyle yakından eşitlenir. Aşağıdaki örnekte gösterildiği gibi, görev oluşturma deyimindeki <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> seçeneğini kullanarak önceki örnekteki ayrılmış alt görevi, eklenen bir alt görev olarak değiştirebilirsiniz. Bu kodda, ekli alt görev üst öğesinden önce tamamlanır. Sonuç olarak, örneğin çıktısı kodu her çalıştırdığınızda aynı olur.  
  
 [!code-csharp[TPL_ChildTasks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/child1.cs#2)]
 [!code-vb[TPL_ChildTasks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/child1.vb#2)]  
  
 Bağlı alt görevleri, zaman uyumsuz işlemlerin sıkı eşitlenmiş grafiklerini oluşturmak için kullanabilirsiniz.  
  
 Bununla birlikte, bir alt görev yalnızca üst öğesi bağlı alt görevleri yasaklamaz üst öğesine eklenebilir. Üst görev, ana görevin sınıf oluşturucusunda veya <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> yönteminde <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> seçeneğini belirterek, alt görevlerin bunlara iliştirmesini açıkça engelleyebilir. Üst görevler, <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> yöntemi çağırarak oluşturulmuş olmaları durumunda alt görevlerin bunlara eklenmesini dolaylı olarak önler. Aşağıdaki örnek bunu göstermektedir. Bu, üst görevin <xref:System.Threading.Tasks.TaskFactory.StartNew%28System.Action%29?displayProperty=nameWithType> yöntemi yerine <xref:System.Threading.Tasks.Task.Run%28System.Action%29?displayProperty=nameWithType> yöntemi çağırarak oluşturulması dışında, önceki örnekle aynıdır. Alt görev üst öğesine eklenemediği için, örneğin çıktısı tahmin edilemez. <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> aşırı yüklemeleri için varsayılan görev oluşturma seçenekleri <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>içerdiğinden Bu örnek, "ayrılmış alt görevler" bölümündeki ilk örneğe işlevsel olarak eşdeğerdir.  
  
 [!code-csharp[TPL_ChildTasks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/child1a.cs#3)]
 [!code-vb[TPL_ChildTasks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/child1a.vb#3)]  
  
## <a name="exceptions-in-child-tasks"></a>Alt görevlerdeki özel durumlar  
 Ayrılmış bir alt görev bir özel durum oluşturursa, bu özel durum doğrudan üst görevde, iç içe olmayan herhangi bir görevde olduğu gibi gözlemlenir veya işlenmelidir. Bağlı bir alt görev bir özel durum oluşturursa, özel durum otomatik olarak üst göreve yayılır ve görevin <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> özelliğine erişmeye çalışan veya bu öğeye erişmeye çalışan iş parçacığına geri gönderilir. Bu nedenle, ekli alt görevleri kullanarak, çağıran iş parçacığında <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> çağrısında yalnızca bir noktada tüm özel durumları işleyebilirsiniz. Daha fazla bilgi için bkz. [özel durum işleme](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
## <a name="cancellation-and-child-tasks"></a>İptal ve alt görevler  
 Görev iptali birlikte çalışır. Diğer bir deyişle, iptal edilebilir olması için, her ekli veya ayrılmış alt görev, iptal belirtecinin durumunu izmelidir. Bir üst ve tüm alt öğelerini tek bir iptal isteği kullanarak iptal etmek istiyorsanız, aynı belirteci tüm görevlere bir bağımsız değişken olarak geçirirsiniz ve her görevde her görevde isteğe yanıt veren mantığı sağlarsınız. Daha fazla bilgi için bkz. [Görev iptali](../../../docs/standard/parallel-programming/task-cancellation.md) ve [nasıl yapılır: bir görevi ve alt öğelerini iptal etme](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
### <a name="when-the-parent-cancels"></a>Üst öğe iptal edildiğinde  
 Bir üst öğe, alt görevi başlatılmadan önce iptal ederse, alt öğe hiçbir şekilde başlatılmaz. Alt görevi zaten başladıktan sonra bir üst öğe iptal ederse, alt öğesi kendi iptal mantığına sahip olmadığı takdirde tamamlanmayı çalışır. Daha fazla bilgi için bkz. [Görev iptali](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
### <a name="when-a-detached-child-task-cancels"></a>Ayrılmış bir alt görev iptal edildiğinde  
 Ayrılmış bir alt görev, üst öğeye iletilen aynı belirteci kullanarak kendisini iptal ederse ve üst öğe alt görevi beklemez, özel durum hiçbir özel durum yayılmaz çünkü özel durum zararsız iş birliği iptali olarak değerlendirilir. Bu davranış, herhangi bir üst düzey görevle aynıdır.  
  
### <a name="when-an-attached-child-task-cancels"></a>Bağlı bir alt görev iptal edildiğinde  
 Bağlı bir alt görev kendi üst görevine geçirilmiş aynı belirteci kullanarak kendisini iptal ettiğinde, bir <xref:System.Threading.Tasks.TaskCanceledException>, bir <xref:System.AggregateException>içindeki katılım iş parçacığına yayılır. Ana görevi beklemeniz gerekir, böylece tüm zararsız özel durumları, ekli alt görevlerin bir grafiğiyle yayılan tüm hatalı özel durumlara ek olarak işleyebilirsiniz.  
  
 Daha fazla bilgi için bkz. [özel durum işleme](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
## <a name="preventing-a-child-task-from-attaching-to-its-parent"></a>Alt görevin kendi üst öğesine iliştirmesini önlemek  
 Bir alt görev tarafından oluşturulan işlenmeyen bir özel durum üst göreve yayılır. Bu davranışı, bir görev ağacına geçiş yapmak yerine bir kök görevden tüm alt görev özel durumlarını gözlemlemek için kullanabilirsiniz. Ancak, bir üst görev diğer koddan ek beklemediğinde özel durum yayma soruna neden olabilir. Örneğin, bir <xref:System.Threading.Tasks.Task> nesnesinden üçüncü taraf kitaplık bileşeni çağıran bir uygulama düşünün. Üçüncü taraf kitaplık bileşeni aynı zamanda bir <xref:System.Threading.Tasks.Task> nesnesi oluşturup, üst göreve eklemek için <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> belirtiyorsa, alt görevde gerçekleşen işlenmemiş özel durumlar üst öğeye yayılır. Bu, ana uygulamada beklenmeyen davranışlara neden olabilir.  
  
 Bir alt görevin üst görevine iliştirmesini engellemek için üst <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> nesnesini oluştururken <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> seçeneğini belirtin. Bir görev, üst öğesine iliştirmeye çalıştığında ve üst öğe <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> seçeneğini belirttiğinde, alt görev bir üst öğeye bağlanamaz ve yalnızca <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> seçeneği belirtilmemişse gibi yürütülür.  
  
 Alt görev zamanında bitmediği zaman bir alt görevin kendi üst öğesine iliştirmesini de engellemek isteyebilirsiniz. Bir üst görev tüm alt görevler tamamlanana kadar bitmediğinden, uzun süreli bir alt görev genel uygulamanın kötü bir şekilde çalışmasına neden olabilir. Bir görevin üst görevine iliştirmesini önleyerek uygulama performansının nasıl iyileştirebileceğimizi gösteren bir örnek için, bkz. [nasıl yapılır: alt görevin üst öğesine iliştirmesini önleme](../../../docs/standard/parallel-programming/how-to-prevent-a-child-task-from-attaching-to-its-parent.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
- [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
