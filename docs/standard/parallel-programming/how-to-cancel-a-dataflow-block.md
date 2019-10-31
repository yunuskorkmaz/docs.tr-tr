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
ms.openlocfilehash: aa175d95f27fcbf28c3f3da3eaa7b8f7988681e1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140087"
---
# <a name="how-to-cancel-a-dataflow-block"></a>Nasıl yapılır: Veri Akışı Bloğunu İptal Etme
Bu belgede, uygulamanızda iptalin nasıl etkinleştirileceği gösterilmektedir. Bu örnek, iş öğelerinin bir veri akışı ardışık düzeninde etkin olduğunu ve ayrıca İptalin etkilerini göstermek için Windows Forms kullanır.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a>Windows Forms uygulamasını oluşturmak için  
  
1. Bir C# veya Visual Basic **Windows Forms uygulama** projesi oluşturun. Aşağıdaki adımlarda, proje `CancellationWinForms`olarak adlandırılmıştır.  
  
2. Ana form için form tasarımcısında, Form1.cs (Visual Basic için Form1. vb), bir <xref:System.Windows.Forms.ToolStrip> denetimi ekleyin.  
  
3. <xref:System.Windows.Forms.ToolStrip> denetimine <xref:System.Windows.Forms.ToolStripButton> denetimi ekleyin. **Çalışma öğeleri eklemek**için <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> özelliğini <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> ve <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğini ayarlayın.  
  
4. <xref:System.Windows.Forms.ToolStrip> denetimine ikinci bir <xref:System.Windows.Forms.ToolStripButton> denetimi ekleyin. <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> özelliğini <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, **iptal**edilecek <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğini ve <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> özelliğini `False`olarak ayarlayın.  
  
5. <xref:System.Windows.Forms.ToolStrip> denetimine dört <xref:System.Windows.Forms.ToolStripProgressBar> nesne ekleyin.  
  
## <a name="creating-the-dataflow-pipeline"></a>Veri akışı işlem hattı oluşturma  
 Bu bölümde, iş öğelerini işleyen ve ilerleme çubuğunu güncelleştiren veri akışı işlem hattının nasıl oluşturulacağı açıklanmaktadır.  
  
### <a name="to-create-the-dataflow-pipeline"></a>Veri akışı ardışık düzeni oluşturmak için  
  
1. Projenizde, System. Threading. Tasks. Dataflow. dll ' ye bir başvuru ekleyin.  
  
2. Form1.cs (Visual Basic için Form1. vb) 'in aşağıdaki `using` deyimlerini (`Imports` Visual Basic) içerdiğinden emin olun.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3. `WorkItem` sınıfını `Form1` sınıfının iç türü olarak ekleyin.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4. Aşağıdaki veri üyelerini `Form1` sınıfına ekleyin.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5. Aşağıdaki yöntemi `CreatePipeline``Form1` sınıfına ekleyin.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 `incrementProgress` ve `decrementProgress` veri akışı blokları Kullanıcı arabiriminde işlem yaptığından, bu eylemlerin Kullanıcı arabirimi iş parçacığında gerçekleştirilmesi önemlidir. Bunu gerçekleştirmek için, oluşturma sırasında, bu nesnelerin her biri, <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> özelliği <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>olarak ayarlanmış <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> bir nesne sağlar. <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> yöntemi, geçerli eşitleme bağlamında çalışmayı gerçekleştiren bir <xref:System.Threading.Tasks.TaskScheduler> nesnesi oluşturur. `Form1` Oluşturucusu kullanıcı arabirimi iş parçacığından çağrıldığı için, `incrementProgress` ve `decrementProgress` veri akışı blokları için Eylemler kullanıcı arabirimi iş parçacığında da çalışır.  
  
 Bu örnek, işlem hattının üyelerini oluştururken <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> özelliğini ayarlar. <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> özelliği, veri akışı bloğu yürütmeyi kalıcı olarak iptal ettiğinden, Kullanıcı işlemi iptal ettikten sonra işlem hattına daha fazla iş öğesi eklemek istediğinde tüm işlem hattının yeniden oluşturulması gerekir. Bir işlem iptal edildikten sonra diğer çalışmanın gerçekleştirilebilmesi için bir veri akışı bloğunu iptal etmenin alternatif bir yolunu gösteren bir örnek için, bkz. [Izlenecek yol: Windows Forms uygulamasında veri akışı kullanma](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a>Veri akışı ardışık düzenini Kullanıcı arabirimine bağlama  
 Bu bölümde, veri akışı ardışık düzeninin Kullanıcı arabirimine nasıl bağlanacağı açıklanmaktadır. İşlem hattının oluşturulması ve iş öğelerinin işlem hattına eklenmesi, **Iş öğeleri ekle** düğmesi için olay işleyicisi tarafından denetlenir. İptali, **iptal** düğmesi tarafından başlatılır. Kullanıcı bu düğmelerden birini tıkladığında, uygun eylem zaman uyumsuz bir şekilde başlatılır.  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a>Veri akışı ardışık düzenini Kullanıcı arabirimine bağlamak için  
  
1. Ana form için form tasarımcısında, **Iş öğeleri ekle** düğmesi için <xref:System.Windows.Forms.ToolStripItem.Click> olayı için bir olay işleyicisi oluşturun.  
  
2. **Iş öğeleri ekle** düğmesine yönelik <xref:System.Windows.Forms.ToolStripItem.Click> olayını uygulayın.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3. Ana form için form tasarımcısında, **iptal** düğmesi için <xref:System.Windows.Forms.ToolStripItem.Click> olay işleyicisi için bir olay işleyicisi oluşturun.  
  
4. **İptal** düğmesi için <xref:System.Windows.Forms.ToolStripItem.Click> olay işleyicisini uygulayın.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Form1.cs için tüm kodu gösterir (Visual Basic için Form1. vb).  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 Aşağıdaki çizimde çalışan uygulama gösterilmektedir.  
  
 ![Windows Forms uygulaması](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")  

## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
