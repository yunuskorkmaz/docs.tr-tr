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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73123180"
---
# <a name="attached-and-detached-child-tasks"></a>Eklenen ve Ayrılan Alt Görevler
Alt *görev* (veya iç içe <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> *görev)* üst *görev*olarak bilinen başka bir görevin kullanıcı temsilcisinde oluşturulan bir örnektir. Bir alt görev ayrılabilir veya eklenebilir. *Ayrılmış alt görev,* üst öğesinden bağımsız olarak yürüten bir görevdir. *Ekli alt görev,* üst öğesi açıkça veya <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> varsayılan olarak eklenmesini yasaklayan seçenekle oluşturulan iç içe yönelik bir görevdir. Bir görev, yalnızca sistem kaynaklarıyla sınırlı olan, herhangi bir sayıda eklenmiş ve ayrılmış alt görev oluşturabilir.  
  
 Aşağıdaki tabloda, iki tür alt görev arasındaki temel farklar listelenir.  
  
|Kategori|Ayrılmış alt görevler|Ekli alt görevler|  
|--------------|--------------------------|--------------------------|  
|Üst öğe alt görevlerin tamamlanmasını bekler.|Hayır|Evet|  
|Üst öğe, alt görevler tarafından atılan özel durumları yayır.|Hayır|Evet|  
|Ebeveynin durumu çocuğun durumuna bağlıdır.|Hayır|Evet|  
  
 Çoğu senaryoda, diğer görevlerle ilişkileri daha az karmaşık olduğundan, ayrılmış alt görevleri kullanmanızı öneririz. Bu nedenle, üst görevler içinde oluşturulan görevler varsayılan olarak ayrılmıştır ve ekli bir alt görev oluşturma <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> seçeneğini açıkça belirtmeniz gerekir.  
  
## <a name="detached-child-tasks"></a>Ayrılmış alt görevler  
 Bir alt görev bir üst görev tarafından oluşturulsa da, varsayılan olarak üst görevden bağımsızdır. Aşağıdaki örnekte, bir üst görev basit bir alt görev oluşturur. Örnek kodu birden çok kez çalıştırırsanız, örnekteki çıktının gösterilenden farklı olduğunu ve kodu her çalıştırdığınızda çıktının değişebileceğini fark edebilirsiniz. Bu, üst görev ve alt görevlerin birbirinden bağımsız olarak yürütülmesinden oluşur; çocuk müstakil bir görevdir. Örnek yalnızca üst görevin tamamlanmasını bekler ve alt görev konsol uygulaması sona ermeden önce yürütülmeyebilir veya tamamlayamayabilir.  
  
 [!code-csharp[TPL_ChildTasks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/nested1.cs#1)]
 [!code-vb[TPL_ChildTasks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/nested1.vb#1)]  
  
 Alt görev bir nesne yerine <xref:System.Threading.Tasks.Task%601> bir <xref:System.Threading.Tasks.Task> nesne tarafından temsil edilirse, ana görevin, ayrılmış bir alt <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> görev olsa bile çocuğun özelliğine erişerek çocuğun tamamlanmasını bekleyeceğinden emin olabilirsiniz. Aşağıdaki <xref:System.Threading.Tasks.Task%601.Result%2A> örnekte görüldüğü gibi, görevi tamamlanana kadar özellik engeller.  
  
 [!code-csharp[TPL_ChildTasks#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/childtasks.cs#4)]
 [!code-vb[TPL_ChildTasks#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/tpl_childtasks.vb#4)]  
  
## <a name="attached-child-tasks"></a>Ekli alt görevler  
 Ayrılmış alt görevlerin aksine, eklenen alt görevler üst öğeyle yakından eşitlenir. Önceki örnekteki ayrılmış alt görevi, aşağıdaki örnekte gösterildiği gibi <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> görev oluşturma deyimindeki seçeneği kullanarak ekli alt görev olarak değiştirebilirsiniz. Bu kodda, ekli alt görev üst önce tamamlar. Sonuç olarak, kodu her çalıştırdığınızda örnekteki çıktı aynıdır.  
  
 [!code-csharp[TPL_ChildTasks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/child1.cs#2)]
 [!code-vb[TPL_ChildTasks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/child1.vb#2)]  
  
 Eşzamanlı işlemlerin sıkı bir şekilde senkronize edilmiş grafiklerini oluşturmak için ekli alt görevleri kullanabilirsiniz.  
  
 Ancak, bir alt görev yalnızca üst öğesi eklenmiş alt görevleri yasaklamazsa, üst öğesine eklenebilir. Üst görevler, üst görevin sınıf oluşturucusunda <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> veya yönteminde seçeneği belirterek alt <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> görevlerin bunlara eklenmesini açıkça engelleyebilir. Üst görevler, yöntem çağırılarak oluşturulduklarında alt görevlerin bunlara bağlanmasını <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> dolaylı olarak engeller. Aşağıdaki örnek bunu göstermektedir. Ana görevin <xref:System.Threading.Tasks.Task.Run%28System.Action%29?displayProperty=nameWithType> <xref:System.Threading.Tasks.TaskFactory.StartNew%28System.Action%29?displayProperty=nameWithType> yöntem yerine yöntem çağırılarak oluşturulması dışında, önceki örnekle aynıdır. Alt görev üst öğesine eklenemediğiiçin, örnekten çıktı öngörülemez. <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> Aşırı yüklemeler için varsayılan görev <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>oluşturma seçenekleri içerdiğinden, bu örnek işlevsel olarak "Ayrılmış alt görevler" bölümündeki ilk örneğe eşdeğerdir.  
  
 [!code-csharp[TPL_ChildTasks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_childtasks/cs/child1a.cs#3)]
 [!code-vb[TPL_ChildTasks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_childtasks/vb/child1a.vb#3)]  
  
## <a name="exceptions-in-child-tasks"></a>Alt görevlerdeki özel durumlar  
 Ayrılmış bir alt görev bir özel durum atarsa, bu özel durum iç içe olmayan herhangi bir görevde olduğu gibi doğrudan ana görevde izlenmeli veya işlenmelidir. Ekli bir alt görev özel durum atarsa, özel durum otomatik olarak üst göreve yayılır ve görevin <xref:System.Threading.Tasks.Task%601.Result%2A?displayProperty=nameWithType> özelliğini bekleyen veya erişmeye çalışan iş parçacığına geri döner. Bu nedenle, ekli alt görevleri kullanarak, arama iş parçacığı için arama <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> nın yalnızca bir noktasında tüm özel durumları işleyebilirsiniz. Daha fazla bilgi için [bkz.](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md)  
  
## <a name="cancellation-and-child-tasks"></a>İptal ve alt görevler  
 Görev iptali işbirliğidir. Diğer bir gelimi, iptal edilebilmek için, ekli veya ayrılmış her alt görevin iptal jetonunun durumunu izlemesi gerekir. Bir üst öğeyi ve tüm alt larını bir iptal isteği kullanarak iptal etmek istiyorsanız, tüm görevlere bağımsız değişken olarak aynı belirteci geçer ve her görevde isteğe yanıt verme mantığını sağlarsınız. Daha fazla bilgi için görev [iptali](../../../docs/standard/parallel-programming/task-cancellation.md) ve nasıl yapılacağını görmek [için: Bir Görevi ve Çocuklarını İptal Et.](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)  
  
### <a name="when-the-parent-cancels"></a>Üst öğe iptal ettiğinde  
 Bir üst öğe, alt görevi başlamadan önce kendisini iptal ederse, alt öğe hiç başlamaz. Bir üst öğe, alt görevi zaten başladıktan sonra kendisini iptal ederse, kendi iptal mantığı yoksa alt öğe tamamlanmak üzere çalışır. Daha fazla bilgi için [Görev İptal'e](../../../docs/standard/parallel-programming/task-cancellation.md)bakın.  
  
### <a name="when-a-detached-child-task-cancels"></a>Ayrılmış bir alt görev iptal ettiğinde  
 Ayrılmış bir alt görev, ebeveyne geçirilen aynı belirteci kullanarak kendisini iptal ederse ve ebeveyn alt görevi beklemezse, özel durum iyi huylu işbirliği iptali olarak kabul edildiğinden, hiçbir istisna yayılır. Bu davranış, herhangi bir üst düzey görevile aynıdır.  
  
### <a name="when-an-attached-child-task-cancels"></a>Ekli bir alt görev iptal ettiğinde  
 Ekli bir alt görev, üst görevine geçirilen aynı belirteç kullanılarak kendini <xref:System.Threading.Tasks.TaskCanceledException> iptal ettiğinde, bir <xref:System.AggregateException>' in içindeki birleştirme iş parçacığına yayılır. Ekli alt görevlerin grafiğinde yayılan tüm hatalı özel durumlara ek olarak tüm iyi huylu özel durumları işleyebilir, böylece üst görevi beklemeniz gerekir.  
  
 Daha fazla bilgi için [bkz.](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md)  
  
## <a name="preventing-a-child-task-from-attaching-to-its-parent"></a>Alt görevin üst öğesine bağlanmasını engelleme  
 Alt görev tarafından atılan işlenmemiş bir özel durum üst göreve yayılır. Bu davranışı, görev ler ağacını geçmek yerine tek bir kök görevden tüm alt görev özel durumlarını gözlemlemek için kullanabilirsiniz. Ancak, bir üst görev diğer kodlardan ek beklemediğinde, özel durum yayılımı sorunlu olabilir. Örneğin, bir <xref:System.Threading.Tasks.Task> nesneden üçüncü taraf kitaplık bileşeni çağıran bir uygulama düşünün. Üçüncü taraf kitaplık bileşeni de <xref:System.Threading.Tasks.Task> bir nesne oluşturur <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> ve üst göreve eklemek için belirtir, alt görev meydana gelen tüm işlenmemiş özel durumlar üst yayMak. Bu, ana uygulamada beklenmeyen davranışlara yol açabilir.  
  
 Alt görevin üst göreve eklenmesini önlemek için, üst <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> nesneoluştururken seçeneği belirtin. Bir görev üst öğesine iliştirmeye çalıştığında <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> ve üst öğe seçeneği belirttiğinde, alt görev bir üst öğeye eklenemez ve <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> seçenek belirtilmemiş gibi yürütülür.  
  
 Ayrıca, alt görev zamanında bitmediğinde bir alt görevin üst öğesine bağlanmasını da engelleyebilirsiniz. Bir üst görev tüm alt görevler bitene kadar bitmedığından, uzun süren bir alt görev genel uygulamanın kötü performans göstermesine neden olabilir. Bir görevin üst görevine eklenmesini engelleyerek uygulama performansını nasıl artırılabildiğini gösteren bir örnek için [bkz.](../../../docs/standard/parallel-programming/how-to-prevent-a-child-task-from-attaching-to-its-parent.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
- [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
