---
title: 'Nasıl yapılır: Veri Akışı Bloğunda Görev Zamanlayıcısı Belirtme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TPL dataflow library, linking to task scheduler in TPL
- Task Parallel Library, dataflows
- task scheduler, linking from TPL
ms.assetid: 27ece374-ed5b-49ef-9cec-b20db34a65e8
ms.openlocfilehash: 2abac1ccf45fc9c9c28e27c132e72fe483a24d75
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122227"
---
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a>Nasıl yapılır: Veri Akışı Bloğunda Görev Zamanlayıcısı Belirtme
Bu belgede, uygulamanızda veri akışı kullandığınızda belirli bir görev zamanlayıcısını nasıl ilişkilenbileceğiniz gösterilmektedir. Örnek, okuyucu görevlerinin etkin olduğu ve bir yazıcı görevinin etkin olduğu zaman göstermek için bir Windows Forms uygulamasındaki <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> sınıfını kullanır. Ayrıca, bir veri akışı bloğunun Kullanıcı arabirimi iş parçacığında çalışmasını sağlamak için <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> yöntemini kullanır.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="to-create-the-windows-forms-application"></a>Windows Forms uygulamasını oluşturmak için  
  
1. Bir görsel C# veya Visual Basic **Windows Forms uygulama** projesi oluşturun. Aşağıdaki adımlarda, proje `WriterReadersWinForms`olarak adlandırılmıştır.  
  
2. Ana formun form tasarımcısında, Form1.cs (Visual Basic için Form1. vb), dört <xref:System.Windows.Forms.CheckBox> denetimi ekleyin. `checkBox1`için <xref:System.Windows.Forms.Control.Text%2A> özelliğini **Reader 1** , `checkBox2`için okuyucu **2** , `checkBox3`için **okuyucu 3** ve `checkBox4`için **Yazıcı** olarak ayarlayın. Her denetim için <xref:System.Windows.Forms.Control.Enabled%2A> özelliğini `False`olarak ayarlayın.  
  
3. Forma <xref:System.Windows.Forms.Timer> denetimi ekleyin. <xref:System.Windows.Forms.Timer.Interval%2A> özelliğini `2500`olarak ayarlayın.  
  
## <a name="adding-dataflow-functionality"></a>Veri akışı Işlevselliği ekleme  
 Bu bölümde, uygulamaya katılan veri akışı bloklarının oluşturulması ve bunların her birinin bir Görev Zamanlayıcısı ile ilişkilendirilmesi açıklanmaktadır.  
  
### <a name="to-add-dataflow-functionality-to-the-application"></a>Uygulamaya veri akışı Işlevselliği eklemek için  
  
1. Projenizde, System. Threading. Tasks. Dataflow. dll ' ye bir başvuru ekleyin.  
  
2. Form1.cs (Visual Basic için Form1. vb) 'in aşağıdaki `using` deyimlerini (`Imports` Visual Basic) içerdiğinden emin olun.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3. `Form1` sınıfına <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> veri üyesi ekleyin.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4. `Form1` oluşturucuda, `InitializeComponent`çağrısından sonra <xref:System.Windows.Forms.CheckBox> nesnelerinin durumuna geçiş yapan bir <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesnesi oluşturun.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5. `Form1` oluşturucuda, her <xref:System.Windows.Forms.CheckBox> nesnesi için bir <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> nesnesi ve dört <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesnesi oluşturun. Her bir <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesnesi için, <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> özelliği, okuyucular için <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> özelliği ve yazıcı için <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> özelliği olarak ayarlanmış bir <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> nesnesi belirtin.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6. `Form1` oluşturucuda <xref:System.Windows.Forms.Timer> nesnesini başlatın.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7. Ana form için form tasarımcısında, Zamanlayıcı için <xref:System.Windows.Forms.Timer.Tick> olayı için bir olay işleyicisi oluşturun.  
  
8. Zamanlayıcı için <xref:System.Windows.Forms.Timer.Tick> olayını uygulayın.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 `toggleCheckBox` veri akışı bloğu Kullanıcı arabiriminde davrandığı için, bu eylemin Kullanıcı arabirimi iş parçacığında oluşması önemlidir. Bunu gerçekleştirmek için, oluşturma sırasında bu nesne <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>olarak ayarlanan <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> özelliği olan bir <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> nesnesi sağlar. <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> yöntemi, geçerli eşitleme bağlamında çalışmayı gerçekleştiren bir <xref:System.Threading.Tasks.TaskScheduler> nesnesi oluşturur. `Form1` Oluşturucu kullanıcı arabirimi iş parçacığından çağrıldığı için, `toggleCheckBox` veri akışı bloğunun eylemi Kullanıcı arabirimi iş parçacığında da çalışır.  
  
 Bu örnek ayrıca, bazı veri akışı bloklarının aynı anda çalışmasını sağlamak için <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> sınıfını ve aynı <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> nesnesi üzerinde çalışan diğer tüm veri akışı bloklarıyla ilgili olarak özel bir veri akışı bloğunu kullanır. Bu teknik, birden çok veri akışı bloğu bir kaynağı paylaşıyorsa ve bir kaynağa erişimi el ile eşitlemeye yönelik gereksinimi ortadan kaldırdığı için bu kaynağa özel erişim gerektirirken yararlıdır. El ile eşitlemenin eleme kodu daha verimli hale getirir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Form1.cs için tüm kodu gösterir (Visual Basic için Form1. vb).  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
