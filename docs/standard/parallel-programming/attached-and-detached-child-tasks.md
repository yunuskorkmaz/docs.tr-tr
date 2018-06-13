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
ms.openlocfilehash: 53f31402e78a15289bb996c63e1e8e3cd98e6aac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590780"
---
# <a name="attached-and-detached-child-tasks"></a>Eklenen ve Ayrılan Alt Görevler
A *alt görev* (veya *iç içe geçmiş görev*) olan bir <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> kullanıcı temsilci olarak bilinen başka bir görev oluşturulan örnek *üst görev*. Bir alt görev ya da iliştirilemez ya da. A *ayrılmış alt görev* üst bağımsız olarak yürüten bir görevdir. Bir *alt görev bağlı* ile oluşturulan iç içe geçmiş bir görevi <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> , üst değil açıkça veya varsayılan olarak engelliyor, bağlı olmak seçeneği. Bir görev herhangi bir sayıda eklenen ve ayrılan alt görevler, yalnızca sistem kaynaklarının yetersizliği sınırlı oluşturabilir.  
  
 Aşağıdaki tabloda iki tür alt görevleri arasındaki temel farklar listelenmektedir.  
  
|Kategori|Ayrılan alt görevler|Ekli alt görevler|  
|--------------|--------------------------|--------------------------|  
|Üst alt görevin tamamlanmasını bekler.|Hayır|Evet|  
|Üst alt görevler tarafından oluşturulan özel durumları yayar.|Hayır|Evet|  
|Üst durumunu alt durumuna bağlıdır.|Hayır|Evet|  
  
 Diğer görevler ile bunların ilişkileri daha az karmaşık olduğundan çoğu senaryoda, ayrılan alt görevler kullanmanızı öneririz. Diğer bir deyişle neden üst görevleri içinde oluşturulan görevler, varsayılan olarak ayrılır ve açıkça belirtmelisiniz <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> ekli alt görev oluşturmak için seçeneği.  
  
## <a name="detached-child-tasks"></a>Ayrılan alt görevler  
 Alt görevin üst göreve göre oluşturulur, ancak varsayılan olarak, üst görevini bağımsızdır. Aşağıdaki örnekte, bir basit alt görevin üst göreve oluşturur. Kod örneği birden çok kez çalıştırırsanız, örneğin çıktısını gösterilen farklı ve ayrıca çıktı değişebilir, her zaman kod çalıştırmadan fark edebilirsiniz. Bu durum, üst görev ve alt görevler diğer bağımsız olarak execute kaynaklanır; alt ayrılmış bir görevdir. Örnek tamamlamak, yalnızca üst görevin tamamlanmasını bekler ve alt görev değil yürütür veya tam konsol uygulaması önce sona erer.  
  
 [!code-csharp[TPL_ChildTasks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/nested1.cs#1)]
 [!code-vb[TPL_ChildTasks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/nested1.vb#1)]  
  
 Alt görev tarafından temsil edilen varsa bir <xref:System.Threading.Tasks.Task%601> nesne yerine bir <xref:System.Threading.Tasks.Task> nesne olun üst görev erişerek tamamlamak alt için bekleyeceği <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> ayrılmış alt görevin olsa bile alt özelliği. <xref:System.Threading.Tasks.Task%601.Result%2A> Özelliği, aşağıdaki örnekte gösterildiği gibi görevi tamamlanana kadar engeller.  
  
 [!code-csharp[TPL_ChildTasks#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/childtasks.cs#4)]
 [!code-vb[TPL_ChildTasks#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/tpl_childtasks.vb#4)]  
  
## <a name="attached-child-tasks"></a>Ekli alt görevler  
 Ayrılan alt görevler, bağlı alt görevler yakından üst öğesi ile eşitlenir. Kullanarak bir ekli alt görevi için önceki örnekte ayrılmış alt görev değiştirebilirsiniz <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> aşağıdaki örnekte gösterildiği gibi görev oluşturma deyiminde seçeneği. Bu kodda ekli alt görevin üst önce tamamlanır. Sonuç olarak, örneğin çıktısını kodu çalıştırmak her zaman aynıdır.  
  
 [!code-csharp[TPL_ChildTasks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/child1.cs#2)]
 [!code-vb[TPL_ChildTasks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/child1.vb#2)]  
  
 Ekli alt görevler sıkı bir şekilde eşitlenmiş grafiklerini zaman uyumsuz işlemler oluşturmak için kullanabilirsiniz.  
  
 Ancak, yalnızca üst ekli alt görevler yasaklamaz varsa alt görevin üst göreve ekleyebilirsiniz. Üst görevleri açıkça engelleyebilir alt görevler için belirterek eklenmesini <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> üst görevin sınıfı oluşturucusu seçeneğinde veya <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> yöntemi. Üst görevleri örtük olarak çağrılarak oluşturulan varsa bunları eklenmesini alt görevler engellemek <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> yöntemi. Aşağıdaki örnek bunu göstermektedir. Üst görev çağırarak oluşturulur ancak bu önceki örneğe benzer <xref:System.Threading.Tasks.Task.Run%28System.Action%29?displayProperty=nameWithType> yöntemi yerine <xref:System.Threading.Tasks.TaskFactory.StartNew%28System.Action%29?displayProperty=nameWithType> yöntemi. Alt görevin üst göreve eklemek mümkün olmadığı için örneğin çıktısını tahmin edilemez. Varsayılan görev oluşturma seçenekleri çünkü <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> aşırı dahil <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>, bu örnekte, "alt görevler ayrılmış" bölümündeki ilk örnek işlevsel olarak eşdeğerdir.  
  
 [!code-csharp[TPL_ChildTasks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/child1a.cs#3)]
 [!code-vb[TPL_ChildTasks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/child1a.vb#3)]  
  
## <a name="exceptions-in-child-tasks"></a>Alt görevler özel durumları  
 Ayrılmış alt görevin bir özel durum oluşturursa, bu özel durum gözlenen veya doğrudan üst görevinde olduğu gibi iç içe olmayan görev işlenmiş. Ekli alt görev bir özel durum oluşturursa, özel durum otomatik olarak üst göreve ve geri bekler veya görevin erişmeye çalışan iş parçacığı yayılır <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> özelliği. Bu nedenle, bağlı alt görevler kullanarak, tüm özel durumları çağrısında yalnızca bir noktada işleyebilir <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> çağıran iş parçacığı üzerinde. Daha fazla bilgi için bkz: [özel durum işleme](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
## <a name="cancellation-and-child-tasks"></a>İptal etme ve alt görevler  
 Görev iptali işbirlikçi ' dir. Diğer bir deyişle, iptal edilebilen olması için her bağlı veya ayrılmış alt görev iptal belirteci durumunu izlemeniz gerekir. Bir iptal isteğini kullanarak bir üst ve tüm alt öğelerini iptal etmek istiyorsanız, aynı belirteci tüm görevler bağımsız değişken olarak geçirmek ve her görev her görev isteğine yanıt mantığını sağlayın. Daha fazla bilgi için bkz: [görev iptali](../../../docs/standard/parallel-programming/task-cancellation.md) ve [nasıl yapılır: bir görevi ve ait alt öğelerini iptal etme](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
### <a name="when-the-parent-cancels"></a>Ne zaman üst iptal eder  
 Alt görevini başlatmadan önce bir üst kendisini iptal ederse alt hiçbir zaman başlatır. Bir üst kendisi, alt görevini zaten başladıktan sonra iptal ederse, kendi iptal mantığı olmadıkça alt tamamlanıncaya kadar çalışır. Daha fazla bilgi için bkz: [görev iptali](../../../docs/standard/parallel-programming/task-cancellation.md).  
  
### <a name="when-a-detached-child-task-cancels"></a>Ayrılmış alt görevin ne zaman iptal eder  
 Özel durum zararsız iş Birliği iptal değerlendirildiğinden ayrılmış alt görevin kendisi üst geçildi aynı belirteci kullanarak iptal eder ve üst alt görevin tamamlanmasını bekle değil, hiçbir özel durum yayılır. Bu davranış, herhangi bir üst düzey görev aynıdır.  
  
### <a name="when-an-attached-child-task-cancels"></a>Ne zaman bir ekli alt görev iptal eder  
 Ekli alt görevin kendisi onun üst görevine geçirildi aynı belirteci kullanarak iptal ettiğinde bir <xref:System.Threading.Tasks.TaskCanceledException> katılma iş parçacığı içinde yayılır bir <xref:System.AggregateException>. Böylece yukarı ekli alt görevler bir grafik yayılır tüm hataya neden olan özel durumları yanı sıra tüm zararsız özel durumları işlemek için üst görev beklemeniz gerekir.  
  
 Daha fazla bilgi için bkz: [özel durum işleme](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md).  
  
## <a name="preventing-a-child-task-from-attaching-to-its-parent"></a>Alt görevin üst göreve eklenmesini önleme  
 Bir alt görevi tarafından oluşturulan işlenmeyen bir özel durum üst göreve yayılır. Bu davranış, görevleri ağacının çapraz geçiş yapan yerine bir kök görevden tüm alt görev özel durumlarını izlemek için kullanabilirsiniz. Ancak, bir üst görev diğer kodundan ek beklemiyor olduğunda özel durum yayma sorunlu olabilir. Örneğin, bir üçüncü taraf kitaplığı bileşenden çağıran uygulamasının göz önünde bulundurun bir <xref:System.Threading.Tasks.Task> nesnesi. Üçüncü taraf kitaplık bileşeni de oluşturursa bir <xref:System.Threading.Tasks.Task> nesne ve belirten <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> üst göreve eklemek için üst alt görevde meydana gelen işlenmeyen özel durumlar yayılması. Bu ana uygulama beklenmeyen davranışlara neden olabilir.  
  
 Bir alt görev kendi üst göreve eklenmesini önlemek için şunu belirtin <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> seçeneği üst oluşturduğunuzda <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> nesnesi. Ne zaman kendi üst eklemek bir görev çalışır ve üst belirtir <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> seçeneği, alt görevin üst öğeye eklemeniz mümkün olmaz ve yalnızca yürütecek gibi <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> seçeneği belirtilmedi.  
  
 Alt görevin alt görev zamanında bitirdiğinizde değil, üst göreve eklenmesini önlemek isteyebilirsiniz. Tüm alt görevler tamamlanana kadar üst göreve tamamlanmıyor olduğundan, uzun süre çalışan alt görevin kötü gerçekleştirmek genel uygulama neden olabilir. Bir görev kendi üst göreve eklenmesini engelleyerek uygulama performansını gösteren örnek için bkz: [nasıl yapılır: alt görevin üst göreve Attaching gelen önleme](../../../docs/standard/parallel-programming/how-to-prevent-a-child-task-from-attaching-to-its-parent.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)  
 [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
