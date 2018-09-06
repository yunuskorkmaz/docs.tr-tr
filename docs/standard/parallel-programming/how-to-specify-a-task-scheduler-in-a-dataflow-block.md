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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9338d06cf7774e1451a0c470c7e078cdb17510ae
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43879083"
---
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a>Nasıl yapılır: Veri Akışı Bloğunda Görev Zamanlayıcısı Belirtme
Bu belge, uygulamanızda veri akışı kullandığınızda belirli bir Görev Zamanlayıcı ilişkilendirilecek gösterilmiştir. Örnekte <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> görevleri okuyucu etkin olduğunda ve bir yazıcı görev etkin olduğunda gösterilecek bir Windows Forms uygulamasında sınıfı. Ayrıca kullanan <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> kullanıcı arabirimi iş parçacığı üzerinde çalıştırılacak bir veri akışı bloğu etkinleştirmek için yöntemi.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="to-create-the-windows-forms-application"></a>Formları uygulaması Windows oluşturmak için  
  
1.  Bir Visual C# veya Visual Basic oluşturma **Windows Forms uygulaması** proje. Aşağıdaki adımlarda, proje adı `WriterReadersWinForms`.  
  
2.  Ana form için form tasarımcıda Form1.cs (Visual Basic için Form1.vb), ekleme dört <xref:System.Windows.Forms.CheckBox> kontrol eder. Ayarlama <xref:System.Windows.Forms.Control.Text%2A> özelliğini **Okuyucu 1** için `checkBox1`, **okuyucu 2** için `checkBox2`, **okuyucu 3** için `checkBox3`, ve  **Yazıcı** için `checkBox4`. Ayarlama <xref:System.Windows.Forms.Control.Enabled%2A> özelliği için her denetim için `False`.  
  
3.  Ekleme bir <xref:System.Windows.Forms.Timer> forma. Ayarlama <xref:System.Windows.Forms.Timer.Interval%2A> özelliğini `2500`.  
  
## <a name="adding-dataflow-functionality"></a>Veri akışı işlevsellik ekleme  
 Bu bölümde, uygulama içinde katılan veri akışı blokları oluşturma ve her biri bir Görev Zamanlayıcısı ile ilişkilendirmek nasıl açıklanmaktadır.  
  
### <a name="to-add-dataflow-functionality-to-the-application"></a>Uygulama veri akışı işlevselliği eklemek için  
  
1.  Projenizde, System.Threading.Tasks.Dataflow.dll'ye birer başvuru ekleyin.  
  
2.  Form1.cs (Visual Basic için Form1.vb) aşağıdaki içerdiğinden emin olun `using` deyimleri (`Imports` Visual Basic'te).  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3.  Ekleme bir <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> veri üyesi `Form1` sınıfı.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4.  İçinde `Form1` çağrısından sonra bir oluşturucu `InitializeComponent`, oluşturun bir <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> durumunu değiştirir nesne <xref:System.Windows.Forms.CheckBox> nesneleri.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5.  İçinde `Form1` oluşturucusu, oluşturun bir <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> nesne ve dört <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesneleri, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> her nesne <xref:System.Windows.Forms.CheckBox> nesne. Her <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesne, belirtin bir <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> nesnesi <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> özelliğini <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> okuyucular için özellik ve <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> yazıcısı için özelliği.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6.  İçinde `Form1` oluşturucusu, başlangıç <xref:System.Windows.Forms.Timer> nesne.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7.  Ana form için form tasarımcıda oluşturmak için bir olay işleyicisi <xref:System.Windows.Forms.Timer.Tick> süreölçer olayı.  
  
8.  Uygulama <xref:System.Windows.Forms.Timer.Tick> süreölçer olayı.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 Çünkü `toggleCheckBox` veri akışı bloğu davranır kullanıcı arabiriminde önemlidir Bu eylem kullanıcı arabirimi iş parçacığı üzerinde oluşur. Bu nesne sağlar yapım sırasında bunu gerçekleştirmek için bir <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> nesnesi <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> özelliğini <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> Yöntemi oluşturur bir <xref:System.Threading.Tasks.TaskScheduler> geçerli eşitleme kapsamının üzerinde işini gerçekleştiren nesne. Çünkü `Form1` Oluşturucu eylem için kullanıcı arabirimi iş parçacığından çağrılır `toggleCheckBox` veri akışı bloğu kullanıcı arabirimi iş parçacığı üzerinde de çalışır.  
  
 Bu örnekte ayrıca <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> eşzamanlı olarak görev yapacak bazı veri akışı bloklarının etkinleştirmek için sınıf ve başka bir veri akışı bloğunun aynı çalıştıran diğer tüm veri akışı bloklarının göre özel olarak davranacak şekilde <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> nesne. El ile bu kaynağa erişimi eşitleme gereksinimini ortadan kaldırdığından bu tekniği birden çok veri akışı bloklarının kaynağı paylaşmak ve bu kaynağa özel erişim gerektiren bazı yararlı olur. El ile eşitleme saydamlığından kod daha verimli olmasını sağlayabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Form1.cs (Visual Basic için Form1.vb) için tam kod gösterilir.  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
