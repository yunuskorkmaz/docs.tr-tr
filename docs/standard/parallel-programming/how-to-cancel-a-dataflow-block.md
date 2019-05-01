---
title: 'Nasıl yapılır: Veri Akışı Bloğunu İptal Etme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- dataflow blocks, canceling in TPL
- TPL dataflow library,canceling dataflow blocks
ms.assetid: fbddda0d-da3b-4ec8-a1d6-67ab8573fcd7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b95f0a3535716c4a01dae52abe38eb850f080cf0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018962"
---
# <a name="how-to-cancel-a-dataflow-block"></a>Nasıl yapılır: Veri Akışı Bloğunu İptal Etme
Bu belge, uygulamanızdaki iptalin gösterilmiştir. Bu örnekte, iş öğelerini bir veri akışı işlem hattı ve ayrıca iptal etkilerini etkin olduğu göstermek için Windows Forms kullanır.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a>Formları uygulaması Windows oluşturmak için  
  
1. Bir C# veya Visual Basic oluşturma **Windows Forms uygulaması** proje. Aşağıdaki adımlarda, proje adı `CancellationWinForms`.  
  
2. Ana form için form tasarımcıda Form1.cs (Visual Basic için Form1.vb), ekleme bir <xref:System.Windows.Forms.ToolStrip> denetimi.  
  
3. Ekleme bir <xref:System.Windows.Forms.ToolStripButton> denetimini <xref:System.Windows.Forms.ToolStrip> denetimi. Ayarlama <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> özelliğini <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> ve <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğini **çalışma öğeleri ekleme**.  
  
4. İkinci bir ekleme <xref:System.Windows.Forms.ToolStripButton> denetimini <xref:System.Windows.Forms.ToolStrip> denetimi. Ayarlama <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> özelliğini <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğini **iptal**ve <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> özelliğini `False`.  
  
5. Dört ekleme <xref:System.Windows.Forms.ToolStripProgressBar> nesneleri için <xref:System.Windows.Forms.ToolStrip> denetimi.  
  
## <a name="creating-the-dataflow-pipeline"></a>Veri akışı işlem hattı oluşturma  
 Bu bölümde iş öğelerini işler ve ilerleme çubukları güncelleştiren veri akışı işlem hattı oluşturmayı açıklar.  
  
### <a name="to-create-the-dataflow-pipeline"></a>Veri akışı işlem hattını oluşturmak için  
  
1. Projenizde, System.Threading.Tasks.Dataflow.dll'ye birer başvuru ekleyin.  
  
2. Form1.cs (Visual Basic için Form1.vb) aşağıdaki içerdiğinden emin olun `using` deyimleri (`Imports` Visual Basic'te).  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3. Ekleme `WorkItem` sınıfı iç bir tür olarak `Form1` sınıfı.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4. Aşağıdaki veri üyelerini ekleyin `Form1` sınıfı.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5. Aşağıdaki yöntemi ekleyin `CreatePipeline`, `Form1` sınıfı.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 Çünkü `incrementProgress` ve `decrementProgress` veri akışı blokları hareket kullanıcı arabiriminde, önemlidir bu eylemler kullanıcı arabirimi iş parçacığı üzerinde oluşur. Bu, bu nesnelerin her sağlamak yapım sırasında gerçekleştirmek için bir <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> nesnesi <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> özelliğini <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> Yöntemi oluşturur bir <xref:System.Threading.Tasks.TaskScheduler> geçerli eşitleme kapsamının üzerinde işini gerçekleştiren nesne. Çünkü `Form1` Oluşturucusu eylemleri için kullanıcı arabirimi iş parçacığından çağrılır `incrementProgress` ve `decrementProgress` veri akışı bloklarının kullanıcı arabirimi iş parçacığı üzerinde de çalışır.  
  
 Bu örnekte ayarlar <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> üyeleri işlem hattının yapılandırdığında özelliği. Çünkü <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> özelliği veri akışı bloğu yürütme kalıcı olarak iptal eder, kullanıcı işlemi iptal eder ve daha fazla iş öğelerini işlem hattının eklemek istiyor sonra işlem hattının tamamını yeniden oluşturulmalıdır. Böylece bir işlem iptal edildikten sonra diğer iş gerçekleştirilebilir bir veri akışı bloğunu iptal etme alternatif bir yolu gösteren bir örnek için bkz: [izlenecek yol: Veri akışı kullanarak bir Windows Forms uygulamalarındaki](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a>Veri akışı işlem hattı kullanıcı arabirimine bağlanma  
 Bu bölümde, veri akışı işlem hattı kullanıcı arabirimine bağlamak açıklar. İşlem hattı oluşturmak ve iş öğelerini işlem hattının ekleme için olay işleyicisi tarafından denetlenen **iş öğeleri ekleme** düğmesi. İptal tarafından başlatılır **iptal** düğmesi. Kullanıcı bir düğmeye tıkladığında, uygun eylemi zaman uyumsuz olarak başlatılır.  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a>Veri akışı işlem hattı kullanıcı arabirimine bağlamak için  
  
1. Ana form için form tasarımcıda oluşturmak için bir olay işleyicisi <xref:System.Windows.Forms.ToolStripItem.Click> olayı **çalışma öğeleri ekleme** düğmesi.  
  
2. Uygulama <xref:System.Windows.Forms.ToolStripItem.Click> olayı **çalışma öğeleri ekleme** düğmesi.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3. Ana form için form tasarımcıda oluşturmak için bir olay işleyicisi <xref:System.Windows.Forms.ToolStripItem.Click> için olay işleyicisi **iptal** düğmesi.  
  
4. Uygulama <xref:System.Windows.Forms.ToolStripItem.Click> için olay işleyicisi **iptal** düğmesi.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Form1.cs (Visual Basic için Form1.vb) için tam kod gösterilir.  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 Aşağıdaki çizim, çalışan uygulamayı gösterir.  
  
 ![Windows Forms uygulamalarındaki](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")  

## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
