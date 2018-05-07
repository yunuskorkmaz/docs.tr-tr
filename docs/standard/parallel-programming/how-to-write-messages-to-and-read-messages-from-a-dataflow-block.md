---
title: 'Nasıl yapılır: Veri Akışı Bloğuna İletiler Yazma ve Veri Akışı Bloğundan İletiler Okuma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, reading and writing messages
ms.assetid: 1a9bf078-aa82-46eb-b95a-f87237f028c5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 61f520b7f4d1827424466a5cc3537041ae37a3bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-messages-to-and-read-messages-from-a-dataflow-block"></a>Nasıl yapılır: Veri Akışı Bloğuna İletiler Yazma ve Veri Akışı Bloğundan İletiler Okuma
Bu belge, iletileri yazma ve veri akışı bloğundan iletiler okuma TPL veri akışı kitaplığı kullanmayı açıklar. TPL veri akışı kitaplığı iletileri ve bir veri akışı bloğu okuma iletilerden yazmak için zaman uyumlu ve zaman uyumsuz yöntemleri sağlar. Bu belgede <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType> sınıfı. <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> Sınıfı iletilerini arabelleğe alır ve her iki ileti kaynağı olarak ve bir ileti hedefine olarak davranır.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="writing-to-and-reading-from-a-dataflow-block-synchronously"></a>Veri akışı bloğundan eşzamanlı okuma ve yazma  
 Aşağıdaki örnek kullanır <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> yazmak için yöntemi bir <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> veri akışı bloğu ve <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> aynı nesneden okumak için yöntem.  
  
 [!code-csharp[TPLDataflow_ReadWrite#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#2)]
 [!code-vb[TPLDataflow_ReadWrite#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#2)]  
  
 Aynı zamanda <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> yöntemi aşağıdaki örnekte gösterildiği gibi bir veri akışı bloğundan okuyun. <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> Yöntemi geçerli iş parçacığının engellemez ve bazen verileri yoklamak durumlarda faydalıdır.  
  
 [!code-csharp[TPLDataflow_ReadWrite#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#3)]
 [!code-vb[TPLDataflow_ReadWrite#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#3)]  
  
 Çünkü <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> yöntemi davranır eşzamanlı olarak, <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> nesne önceki örneklerde, ikinci döngü veri okuyan önce tüm verileri alır. Aşağıdaki örnek ilk örneği kullanarak genişletir <xref:System.Threading.Tasks.Parallel.Invoke%2A> okuma ve ileti bloğu eşzamanlı olarak yazmak için. Çünkü <xref:System.Threading.Tasks.Parallel.Invoke%2A> eylemleri gerçekleştirir eşzamanlı olarak, değerleri için yazılmaz <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> belirli bir sıraya nesne.  
  
 [!code-csharp[TPLDataflow_ReadWrite#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#4)]
 [!code-vb[TPLDataflow_ReadWrite#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#4)]  
  
## <a name="writing-to-and-reading-from-a-dataflow-block-asynchronously"></a>Veri akışı bloğundan zaman uyumsuz olarak okuma ve yazma  
 Aşağıdaki örnek kullanır <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> yöntemi zaman uyumsuz olarak yazmak için bir <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> nesne ve <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> aynı nesneden zaman uyumsuz olarak okumak için yöntem. Bu örnekte [zaman uyumsuz](~/docs/csharp/language-reference/keywords/async.md) ve [await](~/docs/csharp/language-reference/keywords/await.md) işleçleri ([zaman uyumsuz](~/docs/visual-basic/language-reference/modifiers/async.md) ve [bekleme](~/docs/visual-basic/language-reference/operators/await-operator.md) Visual Basic'te) zaman uyumsuz olarak veri göndermek ve okumak için hedef blok verileri. <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> Yöntemi olduğunda yararlı iletileri ertelemek bir veri akışı bloğu etkinleştirmeniz gerekir. <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> Yöntemi, bu verileri kullanılabilir hale geldiğinde verilerde işlem yapmak istediğinizde yararlıdır. İletileri ileti blokları arasında nasıl yayılması hakkında daha fazla bilgi için ileti geçirme bölümüne bakın, [veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md).  
  
 [!code-csharp[TPLDataflow_ReadWrite#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#5)]
 [!code-vb[TPLDataflow_ReadWrite#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#5)]  
  
## <a name="a-complete-example"></a>Tam bir örnek  
 Aşağıdaki örnek, bu belge için tam kod gösterilir.  
  
 [!code-csharp[TPLDataflow_ReadWrite#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#1)]
 [!code-vb[TPLDataflow_ReadWrite#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Örnek kodu kopyalayın ve bir Visual Studio projesi yapıştırın veya adlı bir dosyaya yapıştırın `DataflowReadWrite.cs` (`DataflowReadWrite.vb` Visual Basic), ve ardından Visual Studio komut istemi penceresinde aşağıdaki komutu çalıştırın.  
  
 Visual C#  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.cs**  
  
 Visual Basic  
  
 **Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.vb**  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu örnek, okuma ve bir ileti bloğu doğrudan yazma gösterilmektedir. Forma veri akışı blokları da bağlanabilirsiniz *ardışık düzen*, veri akışı blokları ve doğrusal dizilerini olduğu veya *ağlar*, veri akışı blokları grafiklerini olduğu. Bir ardışık düzen veya ağda, kaynaklar, veriler kullanılabilir oldukça zaman uyumsuz olarak hedeflere yayarlar. Temel veri akışı işlem hattı oluşturur bir örnek için bkz: [izlenecek yol: bir veri akışı ardışık düzenleri oluşturma](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md). Daha karmaşık bir veri akışı ağ oluşturur bir örnek için bkz: [izlenecek yol: veri akışı kullanarak bir Windows Forms uygulamasında](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
