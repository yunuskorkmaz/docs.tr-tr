---
title: 'Nasıl yapılır: Veri Akışı Bloğunda Görev Zamanlayıcısı Belirtme'
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
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
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 15b1168c34a22394424f250e8ab1887ec8ee1a5e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a>Nasıl yapılır: Veri Akışı Bloğunda Görev Zamanlayıcısı Belirtme
Bu belge, veri akışı uygulamanızda kullandığınızda bir özel Görev Zamanlayıcı'yı ilişkilendirmek gösterilmiştir. Örnek kullanır <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> okuyucu görevleri etkin olduğunda ve bir yazıcı görev etkin olduğunda göstermek için bir Windows Forms uygulamasında sınıfı. Ayrıca kullanır <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> kullanıcı arabirimi iş parçacığı üzerinde çalıştırmak bir veri akışı bloğu etkinleştirmek için yöntemi.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="to-create-the-windows-forms-application"></a>Form uygulama Windows oluşturmak için  
  
1.  Bir Visual C# veya Visual Basic oluşturma **Windows Forms uygulaması** projesi. Aşağıdaki adımlarda proje adı `WriterReadersWinForms`.  
  
2.  Ana form için form Tasarımcısı üzerinde Form1.cs (Visual Basic Form1.vb) eklemek dört <xref:System.Windows.Forms.CheckBox> kontrol eder. Ayarlama <xref:System.Windows.Forms.Control.Text%2A> özelliğine **Okuyucu 1** için `checkBox1`, **okuyucu 2** için `checkBox2`, **okuyucu 3** için `checkBox3`, ve  **Yazıcı** için `checkBox4`. Ayarlama <xref:System.Windows.Forms.Control.Enabled%2A> özelliği için her denetim için `False`.  
  
3.  Ekleme bir <xref:System.Windows.Forms.Timer> forma denetim. Ayarlama <xref:System.Windows.Forms.Timer.Interval%2A> özelliğine `2500`.  
  
## <a name="adding-dataflow-functionality"></a>Veri akışı işlevsellik ekleme  
 Bu bölümde uygulamasında katılmak veri akışı blokları oluşturma ve Görev Zamanlayıcısı her biriyle ilişkilendirmek açıklar.  
  
### <a name="to-add-dataflow-functionality-to-the-application"></a>Uygulama veri akışı işlevsellik eklemek için  
  
1.  Projenizde, System.Threading.Tasks.Dataflow.dll bir başvuru ekleyin.  
  
2.  Form1.cs (Visual Basic Form1.vb) aşağıdaki içerdiğinden emin olun `using` deyimleri (`Imports` Visual Basic'te).  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3.  Ekleme bir <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> veri üyesini `Form1` sınıfı.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4.  İçinde `Form1` çağrısından sonra Oluşturucusu `InitializeComponent`, oluşturma bir <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> durumunu değiştirir nesne <xref:System.Windows.Forms.CheckBox> nesneleri.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5.  İçinde `Form1` oluşturucusu, oluşturma bir <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> nesne ve dört <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesneleri, bir <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> her nesne <xref:System.Windows.Forms.CheckBox> nesne. Her <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesne, belirtin bir <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> olan nesneyi <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> özelliğini <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> okuyucular için özellik ve <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> yazıcı için özellik.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6.  İçinde `Form1` oluşturucusu, başlangıç <xref:System.Windows.Forms.Timer> nesnesi.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7.  Ana form için form designer'ı oluşturmak için bir olay işleyicisi <xref:System.Windows.Forms.Timer.Tick> süreölçer olayı.  
  
8.  Uygulama <xref:System.Windows.Forms.Timer.Tick> süreölçer olayı.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 Çünkü `toggleCheckBox` veri akışı bloğu davranır kullanıcı arabiriminde, bu eylem kullanıcı arabirimi iş parçacığı üzerinde gerçekleşmesi önemli. Bu nesne sağlar oluşturma sırasında Bunu başarmak için bir <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> olan nesneyi <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> özelliğini <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> Yöntemi oluşturur bir <xref:System.Threading.Tasks.TaskScheduler> geçerli eşitleme bağlamı üzerinde çalışmayı gerçekleştiren nesne. Çünkü `Form1` Oluşturucusu eylem için kullanıcı arabirimi iş parçacığı çağrılır `toggleCheckBox` veri akışı bloğu kullanıcı arabirimi iş parçacığı üzerinde de çalışır.  
  
 Bu örnek ayrıca kullanır <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> eşzamanlı olarak davranacak şekilde bazı veri akışı blokları etkinleştirmek için sınıf ve başka bir veri akışı bloğu aynı çalıştıran diğer tüm veri akışı blokları göre özel hareket <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> nesnesi. Bu kaynağa erişim el ile eşitlemek için gereksinim attığından Bu teknik birden çok veri akışı blokları kaynak paylaşma ve bazı bu kaynağa özel erişim gerektiren kullanışlıdır. El ile eşitleme eleme kodu daha verimli hale getirebilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek eksiksiz kod Form1.cs (Visual Basic Form1.vb) gösterir.  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
