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
ms.openlocfilehash: 530c231deeaba007975849ab6dc41f4da6a859ea
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84285553"
---
# <a name="how-to-cancel-a-dataflow-block"></a>Nasıl yapılır: Veri Akışı Bloğunu İptal Etme
Bu belgede, uygulamanızda iptalin nasıl etkinleştirileceği gösterilmektedir. Bu örnek, iş öğelerinin bir veri akışı ardışık düzeninde etkin olduğunu ve ayrıca İptalin etkilerini göstermek için Windows Forms kullanır.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a>Windows Forms uygulamasını oluşturmak için  
  
1. Bir C# veya Visual Basic **Windows Forms uygulama** projesi oluşturun. Aşağıdaki adımlarda proje adlandırılır `CancellationWinForms` .  
  
2. Ana form için form tasarımcısında, Form1.cs (Visual Basic için Form1. vb), bir <xref:System.Windows.Forms.ToolStrip> denetim ekleyin.  
  
3. <xref:System.Windows.Forms.ToolStripButton>Denetime denetim ekleyin <xref:System.Windows.Forms.ToolStrip> . <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> <xref:System.Windows.Forms.ToolStripItem.Text%2A> **Çalışma öğeleri eklemek**için özelliğini ve özelliğini ayarlayın.  
  
4. Denetime ikinci bir <xref:System.Windows.Forms.ToolStripButton> denetim ekleyin <xref:System.Windows.Forms.ToolStrip> . <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>Özelliğini <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> , <xref:System.Windows.Forms.ToolStripItem.Text%2A> **iptal**edilecek özelliği ve özelliğini olarak ayarlayın <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> `False` .  
  
5. Denetime dört <xref:System.Windows.Forms.ToolStripProgressBar> nesne ekleyin <xref:System.Windows.Forms.ToolStrip> .  
  
## <a name="creating-the-dataflow-pipeline"></a>Veri akışı işlem hattı oluşturma  
 Bu bölümde, iş öğelerini işleyen ve ilerleme çubuğunu güncelleştiren veri akışı işlem hattının nasıl oluşturulacağı açıklanmaktadır.  
  
### <a name="to-create-the-dataflow-pipeline"></a>Veri akışı ardışık düzeni oluşturmak için  
  
1. Projenizde, System. Threading. Tasks. Dataflow. dll ' ye bir başvuru ekleyin.  
  
2. Form1.cs (Visual Basic için Form1. vb) 'in aşağıdaki deyimlerini (Visual Basic) içerdiğinden emin olun `using` `Imports` .  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3. Sınıfını `WorkItem` sınıfının bir iç türü olarak ekleyin `Form1` .  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4. Sınıfına aşağıdaki veri üyelerini ekleyin `Form1` .  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5. Aşağıdaki yöntemini `CreatePipeline` `Form1` sınıfına ekleyin.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 `incrementProgress`Ve `decrementProgress` veri akışı blokları Kullanıcı arabiriminde işlem yaptığından, bu eylemlerin Kullanıcı arabirimi iş parçacığında gerçekleştirilmesi önemlidir. Bunu gerçekleştirmek için, oluşturma sırasında bu nesnelerin her biri, <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> özelliği olarak ayarlanmış bir nesne sağlar <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> . <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>Yöntemi, <xref:System.Threading.Tasks.TaskScheduler> geçerli eşitleme bağlamında çalışmayı gerçekleştiren bir nesnesi oluşturur. `Form1`Oluşturucu kullanıcı arabirimi iş parçacığından çağrıldığı için, `incrementProgress` ve `decrementProgress` veri akışı blokları için Eylemler kullanıcı arabirimi iş parçacığında da çalışır.  
  
 Bu örnek, <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> işlem hattının üyelerini oluştururken özelliği ayarlar. Özelliği, <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> veri akışı blok yürütmeyi kalıcı olarak iptal ettiğinden, Kullanıcı işlemi iptal ettikten sonra işlem hattına daha fazla iş öğesi eklemek istediğinde tüm işlem hattının yeniden oluşturulması gerekir. Bir işlem iptal edildikten sonra diğer çalışmanın gerçekleştirilebilmesi için bir veri akışı bloğunu iptal etmenin alternatif bir yolunu gösteren bir örnek için, bkz. [Izlenecek yol: Windows Forms uygulamasında veri akışı kullanma](walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a>Veri akışı ardışık düzenini Kullanıcı arabirimine bağlama  
 Bu bölümde, veri akışı ardışık düzeninin Kullanıcı arabirimine nasıl bağlanacağı açıklanmaktadır. İşlem hattının oluşturulması ve iş öğelerinin işlem hattına eklenmesi, **Iş öğeleri ekle** düğmesi için olay işleyicisi tarafından denetlenir. İptali, **iptal** düğmesi tarafından başlatılır. Kullanıcı bu düğmelerden birini tıkladığında, uygun eylem zaman uyumsuz bir şekilde başlatılır.  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a>Veri akışı ardışık düzenini Kullanıcı arabirimine bağlamak için  
  
1. Ana form için form tasarımcısında, <xref:System.Windows.Forms.ToolStripItem.Click> **Iş öğeleri ekle** düğmesine yönelik olay için bir olay işleyicisi oluşturun.  
  
2. <xref:System.Windows.Forms.ToolStripItem.Click> **Iş öğeleri ekle** düğmesine yönelik olayı uygulayın.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3. Ana form için form tasarımcısında, <xref:System.Windows.Forms.ToolStripItem.Click> **iptal** düğmesine yönelik olay işleyicisi için bir olay işleyicisi oluşturun.  
  
4. <xref:System.Windows.Forms.ToolStripItem.Click> **İptal** düğmesi için olay işleyicisini uygulayın.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Form1.cs için tüm kodu gösterir (Visual Basic için Form1. vb).  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 Aşağıdaki çizimde çalışan uygulama gösterilmektedir.  
  
 ![Windows Forms uygulaması](media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")  

## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](dataflow-task-parallel-library.md)
