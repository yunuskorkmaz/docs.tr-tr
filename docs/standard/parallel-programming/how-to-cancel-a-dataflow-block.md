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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140087"
---
# <a name="how-to-cancel-a-dataflow-block"></a>Nasıl yapılır: Veri Akışı Bloğunu İptal Etme
Bu belge, başvurunuzda iptalin nasıl etkinleştirilebildiğini gösterir. Bu örnek, iş öğelerinin veri akışı ardışık etki alanında etkin olduğu yeri ve ayrıca iptalin etkilerini göstermek için Windows Formları'nı kullanır.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a>Windows Forms Uygulamasını Oluşturmak İçin  
  
1. C# veya Visual Basic **Windows Forms Application** projesi oluşturun. Aşağıdaki adımlarda, proje adlandırılmış. `CancellationWinForms`  
  
2. Ana form için form tasarımcısı, Form1.cs (Visual Basic için Form1.vb), bir <xref:System.Windows.Forms.ToolStrip> denetim ekleyin.  
  
3. <xref:System.Windows.Forms.ToolStrip> Denetime bir <xref:System.Windows.Forms.ToolStripButton> denetim ekleyin. İş <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> Öğeleri <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> **Ekle** <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğini ve özelliğini ayarlayın.  
  
4. <xref:System.Windows.Forms.ToolStrip> Denetime ikinci <xref:System.Windows.Forms.ToolStripButton> bir denetim ekleyin. <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> <xref:System.Windows.Forms.ToolStripItem.Text%2A> <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> `False` **Cancel**Özelliği, İptal Etme özelliğine, özelliği de . <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>  
  
5. <xref:System.Windows.Forms.ToolStrip> Denetime dört <xref:System.Windows.Forms.ToolStripProgressBar> nesne ekleyin.  
  
## <a name="creating-the-dataflow-pipeline"></a>Veri Akışı Ardışık Akışını Oluşturma  
 Bu bölümde, iş öğelerini işleyen ve ilerleme çubuklarını güncelleyen veri akışı ardışık akışının nasıl oluşturulacak ları açıklanmaktadır.  
  
### <a name="to-create-the-dataflow-pipeline"></a>Veri Akışı Ardışık Ardışık Ardışık Bir Neden Oluşturmak İçin  
  
1. Projenizde System.Threading.Tasks.Dataflow.dll adresine bir başvuru ekleyin.  
  
2. Form1.cs (Visual Basic için Form1.vb) `using` aşağıdaki`Imports` ifadeleri içerdiğinden emin olun (Visual Basic'te).  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3. `WorkItem` Sınıfı sınıfın iç türü olarak `Form1` ekleyin.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4. Aşağıdaki veri üyelerini sınıfa `Form1` ekleyin.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5. Sınıfa aşağıdaki `CreatePipeline`yöntemi ekleyin. `Form1`  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 `incrementProgress` Ve `decrementProgress` veri akışı blokları kullanıcı arabiriminde hareket ettiği için, bu eylemlerin kullanıcı arabirimi iş parçacığında oluşması önemlidir. Bunu gerçekleştirmek için, inşaat sırasında bu <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> nesnelerin her <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> özelliği <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>ayarlanmış bir nesne sağlar. Yöntem, <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> geçerli <xref:System.Threading.Tasks.TaskScheduler> eşitleme bağlamında çalışma gerçekleştiren bir nesne oluşturur. Oluşturucu kullanıcı arabirimi iş parçacığından çağrıldığından, `incrementProgress` `decrementProgress` kullanıcı arabirimi iş parçacığıüzerinde veri akışı ve veri akışı bloklarıiçin eylemler de çalışır. `Form1`  
  
 Bu örnek, <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> ardışık yapının üyelerini inşa ettiğinde özelliği ayarlar. <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> Özellik veri akışı bloğu yürütmesini kalıcı olarak iptal ettiği için, kullanıcı işlemi iptal ettikten sonra tüm ardışık işlemin yeniden oluşturulması ve ardından ardışık öğeye daha fazla iş öğesi eklemek istemesi gerekir. İşlem iptal edildikten sonra başka çalışmaların gerçekleştirilebilmeleri için veri akışı bloğunu iptal etmenin alternatif bir yolunu gösteren [bir](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)örnek için bkz.  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a>Veri Akışı Ardışık Akışını Kullanıcı Arabirimine Bağlama  
 Bu bölümde, veri akışı ardışık biriminin kullanıcı arabirimine nasıl bağlanılabildiğini açıklanmaktadır. Hem ardışık hatlar oluşturma hem de iş öğeleriekleme, **İş Öğeleri Ekle** düğmesi için olay işleyicisi tarafından denetlenir. İptal İptal **düğmesi** tarafından başlatılır. Kullanıcı bu düğmelerden birini tıklattığında, uygun eylem eşzamanlı bir şekilde başlatılır.  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a>Veri Akışı Ardışık Hattını Kullanıcı Arabirimine Bağlamak İçin  
  
1. Ana formiçin form tasarımcısında, **İş Öğeleri** Ekle <xref:System.Windows.Forms.ToolStripItem.Click> düğmesi için etkinlik için bir olay işleyicisi oluşturun.  
  
2. İş <xref:System.Windows.Forms.ToolStripItem.Click> **Öğeleri Ekle** düğmesi için etkinliği uygulayın.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3. Ana formiçin form tasarımcısında, **İptal** düğmesi için <xref:System.Windows.Forms.ToolStripItem.Click> olay işleyicisi için bir olay işleyicisi oluşturun.  
  
4. İptal <xref:System.Windows.Forms.ToolStripItem.Click> düğmesi için olay **Cancel** işleyicisini uygulayın.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte Form1.cs için tam kod gösterilmektedir (Visual Basic için Form1.vb).  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 Aşağıdaki resimde çalışan uygulama gösterilmektedir.  
  
 ![Windows Formları Uygulaması](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")  

## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
