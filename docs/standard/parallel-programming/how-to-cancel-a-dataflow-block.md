---
title: "Nasıl yapılır: Veri Akışı Bloğunu İptal Etme"
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
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
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3ef7fa62513072e1ee0dc7a8fecf3e600f9c26f2
ms.sourcegitcommit: 6a9030eb5bd0f00e1d144f81958adb195cfb1f6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-cancel-a-dataflow-block"></a>Nasıl yapılır: Veri Akışı Bloğunu İptal Etme
Bu belge, uygulamanızda iptalini etkinleştir gösterilmiştir. Bu örnekte, iş öğelerini bir veri akışı ardışık yanı sıra iptal etkilerini etkin olduğu göstermek için Windows Forms kullanır.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a>Form uygulama Windows oluşturmak için  
  
1.  Bir C# veya Visual Basic oluşturma **Windows Forms uygulaması** projesi. Aşağıdaki adımlarda proje adı `CancellationWinForms`.  
  
2.  Form1.cs ana form için form tasarımcısında (Form1.vb için [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), ekleme bir <xref:System.Windows.Forms.ToolStrip> denetim.  
  
3.  Ekleme bir <xref:System.Windows.Forms.ToolStripButton> denetimini <xref:System.Windows.Forms.ToolStrip> denetim. Ayarlama <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> özelliğine <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> ve <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğine **çalışma öğeleri ekleme**.  
  
4.  İkinci bir ekleme <xref:System.Windows.Forms.ToolStripButton> denetimini <xref:System.Windows.Forms.ToolStrip> denetim. Ayarlama <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> özelliğine <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, <xref:System.Windows.Forms.ToolStripItem.Text%2A> özelliğine **iptal**ve <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> özelliğine `False`.  
  
5.  Dört eklemek <xref:System.Windows.Forms.ToolStripProgressBar> nesneleri <xref:System.Windows.Forms.ToolStrip> denetim.  
  
## <a name="creating-the-dataflow-pipeline"></a>Veri akışı ardışık düzenleri oluşturma  
 Bu bölümde, iş öğelerini işler ve ilerleme çubukları güncelleştiren veri akışı ardışık düzen oluşturmak açıklar.  
  
### <a name="to-create-the-dataflow-pipeline"></a>Veri akışı ardışık düzen oluşturmak için  
  
1.  Projenizde, System.Threading.Tasks.Dataflow.dll bir başvuru ekleyin.  
  
2.  Sağlamak Bu Form1.cs (Form1.vb için [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) aşağıdakileri içerir `using` deyimleri (`Imports` içinde [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3.  Ekleme `WorkItem` sınıfı bir iç türü olarak `Form1` sınıfı.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4.  Aşağıdaki veri üye ekleme `Form1` sınıfı.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5.  Aşağıdaki yöntemi ekleyin `CreatePipeline`, `Form1` sınıfı.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 Çünkü `incrementProgress` ve `decrementProgress` veri akışı blokları hareket kullanıcı arabiriminde, onu önemlidir bu eylemler kullanıcı arabirimi iş parçacığı üzerinde gerçekleştirilir. Bu, oluşturma sırasında bu nesnelerin her sağlamak gerçekleştirmek için bir <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> olan nesneyi <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> özelliğini <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> Yöntemi oluşturur bir <xref:System.Threading.Tasks.TaskScheduler> geçerli eşitleme bağlamı üzerinde çalışmayı gerçekleştiren nesne. Çünkü `Form1` Oluşturucusu eylemleri için kullanıcı arabirimi iş parçacığı çağrılır `incrementProgress` ve `decrementProgress` veri akışı blokları kullanıcı arabirimi iş parçacığı üzerinde de çalışır.  
  
 Bu örnek ayarlar <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> ardışık düzen üyeleri yapılandırdığında özelliği. Çünkü <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> özelliği kalıcı olarak veri akışı bloğu yürütme iptal eder, sonra kullanıcı işlemi iptal ve ardışık düzene daha fazla iş öğelerini eklemek istediği tüm ardışık düzeni yeniden oluşturulmalıdır. Böylece bir işlem iptal edildikten sonra diğer iş gerçekleştirilebilir veri akışı bloğunu iptal etmek için alternatif bir yol gösteren bir örnek için bkz: [izlenecek yol: veri akışı kullanarak bir Windows Forms uygulamasında](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a>Veri akışı ardışık düzeni için kullanıcı arabirimi bağlanma  
 Bu bölümde, veri akışı ardışık düzeni için kullanıcı arabirimi bağlanmak açıklar. Ardışık düzen oluşturma hem çalışma öğelerini ardışık düzenine eklemek için olay işleyicisi tarafından denetlenen **çalışma öğeleri ekleme** düğmesi. İptal tarafından başlatılır **iptal** düğmesi. Kullanıcı ya da bu düğmeleri tıkladığında, uygun eylemi bir zaman uyumsuz olarak başlatılır.  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a>Veri akışı ardışık düzeni için kullanıcı arabirimi bağlanmak için  
  
1.  Ana form için form designer'ı oluşturmak için bir olay işleyicisi <xref:System.Windows.Forms.ToolStripItem.Click> olayı için **çalışma öğeleri ekleme** düğmesi.  
  
2.  Uygulama <xref:System.Windows.Forms.ToolStripItem.Click> olayı için **çalışma öğeleri ekleme** düğmesi.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3.  Ana form için form designer'ı oluşturmak için bir olay işleyicisi <xref:System.Windows.Forms.ToolStripItem.Click> için olay işleyicisini **iptal** düğmesi.  
  
4.  Uygulama <xref:System.Windows.Forms.ToolStripItem.Click> için olay işleyicisini **iptal** düğmesi.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek Form1.cs için tam kod gösterilir (Form1.vb için [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 Aşağıdaki çizimde çalışan uygulama gösterir.  
  
 ![Windows Forms uygulaması](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")  

## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
