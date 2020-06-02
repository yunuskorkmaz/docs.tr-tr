---
title: 'Nasıl yapılır: Veri Akışı Bloğunda Görev Zamanlayıcı Belirtme'
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
ms.openlocfilehash: 76c9e75f787c28657af143b46bb22d08039e2dc4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288140"
---
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a>Nasıl yapılır: Veri Akışı Bloğunda Görev Zamanlayıcı Belirtme
Bu belgede, uygulamanızda veri akışı kullandığınızda belirli bir görev zamanlayıcısını nasıl ilişkilenbileceğiniz gösterilmektedir. Örnek, <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> okuyucu görevlerinin etkin olduğu ve bir yazıcı görevinin etkin olduğu zaman göstermek için bir Windows Forms uygulamasındaki sınıfını kullanır. Ayrıca, <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> bir veri akışı bloğunun Kullanıcı arabirimi iş parçacığında çalışmasını sağlamak için yöntemini kullanır.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="to-create-the-windows-forms-application"></a>Windows Forms uygulamasını oluşturmak için  
  
1. Visual C# veya Visual Basic **Windows Forms uygulama** projesi oluşturun. Aşağıdaki adımlarda proje adlandırılır `WriterReadersWinForms` .  
  
2. Ana formun form tasarımcısında, Form1.cs (Visual Basic için Form1. vb), dört <xref:System.Windows.Forms.CheckBox> denetim ekleyin. Özelliği için <xref:System.Windows.Forms.Control.Text%2A> **Reader 1** , için okuyucu `checkBox1` **2** , için okuyucu `checkBox2` **3** `checkBox3` ve **Yazıcı** olarak ayarlayın `checkBox4` . <xref:System.Windows.Forms.Control.Enabled%2A>Her denetim için özelliğini olarak ayarlayın `False` .  
  
3. Forma bir <xref:System.Windows.Forms.Timer> denetim ekleyin. <xref:System.Windows.Forms.Timer.Interval%2A>Özelliğini olarak ayarlayın `2500` .  
  
## <a name="adding-dataflow-functionality"></a>Veri akışı Işlevselliği ekleme  
 Bu bölümde, uygulamaya katılan veri akışı bloklarının oluşturulması ve bunların her birinin bir Görev Zamanlayıcısı ile ilişkilendirilmesi açıklanmaktadır.  
  
### <a name="to-add-dataflow-functionality-to-the-application"></a>Uygulamaya veri akışı Işlevselliği eklemek için  
  
1. Projenizde, System. Threading. Tasks. Dataflow. dll ' ye bir başvuru ekleyin.  
  
2. Form1.cs (Visual Basic için Form1. vb) 'in aşağıdaki deyimlerini (Visual Basic) içerdiğinden emin olun `using` `Imports` .  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3. Sınıfına bir <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> veri üyesi ekleyin `Form1` .  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4. `Form1`Oluşturucuda, çağrısından sonra `InitializeComponent` , <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesnelerin durumuna geçiş yapan bir nesne oluşturun <xref:System.Windows.Forms.CheckBox> .  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5. Oluşturucuda, `Form1` her bir nesne için bir nesne <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> ve dört nesne oluşturun <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> <xref:System.Windows.Forms.CheckBox> . Her bir <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesne için, <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> özelliği <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> Okuyucular için özelliği ve yazıcı özelliği olarak ayarlanmış bir nesne belirtin <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> .  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6. Oluşturucuda, `Form1` <xref:System.Windows.Forms.Timer> nesnesini başlatın.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7. Ana form için form tasarımcısında, süreölçer için olay için bir olay işleyicisi oluşturun <xref:System.Windows.Forms.Timer.Tick> .  
  
8. <xref:System.Windows.Forms.Timer.Tick>Süreölçer için olayı uygulayın.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 `toggleCheckBox`Veri akışı bloğu Kullanıcı arabiriminde davrandığı için, bu eylemin Kullanıcı arabirimi iş parçacığında gerçekleştirilmesi önemlidir. Bunu gerçekleştirmek için, oluşturma sırasında bu nesne <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> , <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> özelliği olarak ayarlanmış bir nesne sağlar <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> . <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A>Yöntemi, <xref:System.Threading.Tasks.TaskScheduler> geçerli eşitleme bağlamında çalışmayı gerçekleştiren bir nesnesi oluşturur. `Form1`Oluşturucu kullanıcı arabirimi iş parçacığından çağrıldığı için, `toggleCheckBox` veri akışı bloğu eylemi Kullanıcı arabirimi iş parçacığında da çalışır.  
  
 Bu örnek ayrıca, <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> bazı veri akışı bloklarının aynı anda çalışmasını sağlamak için sınıfını ve aynı nesne üzerinde çalışan diğer tüm veri akışı bloklarına göre özel olarak hareket etmek için başka bir veri akışı bloğunu kullanır <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> . Bu teknik, birden çok veri akışı bloğu bir kaynağı paylaşıyorsa ve bir kaynağa erişimi el ile eşitlemeye yönelik gereksinimi ortadan kaldırdığı için bu kaynağa özel erişim gerektirirken yararlıdır. El ile eşitlemenin eleme kodu daha verimli hale getirir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Form1.cs için tüm kodu gösterir (Visual Basic için Form1. vb).  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](dataflow-task-parallel-library.md)
