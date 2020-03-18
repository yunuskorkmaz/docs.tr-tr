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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73122227"
---
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a>Nasıl yapılır: Veri Akışı Bloğunda Görev Zamanlayıcısı Belirtme
Bu belge, uygulamanızda veri akışını kullandığınızda belirli bir görev zamanlayıcısının nasıl ilişkilendirilen bir belgeyi gösterir. Örnek, okuyucu <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> görevlerinin ne zaman etkin olduğunu ve bir yazar görevinin etkin olduğunu göstermek için Windows Forms uygulamasındaki sınıfı kullanır. Ayrıca, bir <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> veri akışı bloğunun kullanıcı arabirimi iş parçacığı üzerinde çalışmasını sağlamak için yöntemi kullanır.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="to-create-the-windows-forms-application"></a>Windows Forms Uygulamasını Oluşturmak İçin  
  
1. Visual C# veya Visual Basic **Windows Forms Application** project oluşturun. Aşağıdaki adımlarda, proje adlandırılmış. `WriterReadersWinForms`  
  
2. Ana form için form tasarımcısı, Form1.cs (Visual Basic için Form1.vb), dört <xref:System.Windows.Forms.CheckBox> denetim ekleyin. Için <xref:System.Windows.Forms.Control.Text%2A> Reader **1** özelliğini `checkBox1`ayarlayın `checkBox2`, Reader `checkBox3` **2** için `checkBox4`, **Reader 3** için , ve **Yazar** için . Her <xref:System.Windows.Forms.Control.Enabled%2A> denetim için özelliği `False`' ye ayarla.  
  
3. Forma <xref:System.Windows.Forms.Timer> bir denetim ekleyin. Özelliği <xref:System.Windows.Forms.Timer.Interval%2A> ' `2500`ye ayarlayın.  
  
## <a name="adding-dataflow-functionality"></a>Veri Akışı İşlevselliği Ekleme  
 Bu bölümde, uygulamaya katılan veri akışı bloklarının nasıl oluşturulacak ve her birinin görev zamanlayıcısıyla nasıl ilişkilendirilen açıklanmaktadır.  
  
### <a name="to-add-dataflow-functionality-to-the-application"></a>Uygulamaya Veri Akışı İşlevselliği Eklemek Için  
  
1. Projenizde System.Threading.Tasks.Dataflow.dll adresine bir başvuru ekleyin.  
  
2. Form1.cs (Visual Basic için Form1.vb) `using` aşağıdaki`Imports` ifadeleri içerdiğinden emin olun (Visual Basic'te).  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3. Sınıfa <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> `Form1` bir veri üyesi ekleyin.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4. Oluşturucuda, `Form1` çağrıdan sonra `InitializeComponent`, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> <xref:System.Windows.Forms.CheckBox> nesnelerin durumunu başka bir nesne yiyerek bir nesne oluşturun.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5. Oluşturucuolarak, `Form1` <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> bir nesne ve <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> dört nesne, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> her <xref:System.Windows.Forms.CheckBox> nesne için bir nesne oluşturun. Her <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesne için, <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> okuyucular için <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> özellik ayarlanmış bir nesne ve <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> yazar için özellik belirtin.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6. Oluşturucuda `Form1` nesneyi <xref:System.Windows.Forms.Timer> başlatın.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7. Ana form için form tasarımcısı üzerinde, zamanlayıcı <xref:System.Windows.Forms.Timer.Tick> için olay için bir olay işleyicisi oluşturun.  
  
8. <xref:System.Windows.Forms.Timer.Tick> Zamanlayıcı için olayı uygulayın.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 `toggleCheckBox` Veri akışı bloğu kullanıcı arabiriminde etki yaptığından, bu eylemin kullanıcı arabirimi iş parçacığında oluşması önemlidir. Bunu gerçekleştirmek için, inşaat sırasında <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> bu nesne <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> özelliği <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>ayarlanmış bir nesne sağlar. Yöntem, <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> geçerli <xref:System.Threading.Tasks.TaskScheduler> eşitleme bağlamında çalışma gerçekleştiren bir nesne oluşturur. `Form1` Oluşturucu kullanıcı arabirimi iş parçacığından çağrıldığından, `toggleCheckBox` veri akışı bloğu için eylem de kullanıcı arabirimi iş parçacığı üzerinde çalışır.  
  
 Bu örnek, <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> bazı veri akışı bloklarının aynı anda hareket etmesini sağlamak için sınıfı ve aynı <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> nesne üzerinde çalışan diğer tüm veri akışı bloklarıyla ilgili olarak özel olarak hareket etmek için başka bir veri akışı bloğu kullanır. Bu teknik, birden çok veri akışı bloğu bir kaynağı paylaştığında ve bazıları bu kaynağa özel erişim gerektirdiğinde yararlıdır, çünkü bu kaynağa erişimi el ile eşitleme gereksinimini ortadan kaldırır. Manuel eşitlemenin ortadan kaldırılması kodu daha verimli hale getirebilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte Form1.cs için tam kod gösterilmektedir (Visual Basic için Form1.vb).  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
