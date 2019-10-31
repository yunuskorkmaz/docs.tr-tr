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
ms.openlocfilehash: 58927803b741acf6c1964b35f6603e6901f9cbf1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139282"
---
# <a name="how-to-write-messages-to-and-read-messages-from-a-dataflow-block"></a>Nasıl yapılır: Veri Akışı Bloğuna İletiler Yazma ve Veri Akışı Bloğundan İletiler Okuma
Bu belgede, bir veri akışı bloğunda ileti yazmak ve iletileri okumak için TPL veri akışı kitaplığı 'nın nasıl kullanılacağı açıklanmaktadır. TPL veri akışı kitaplığı, veri akışı bloğundan ileti yazmak ve iletileri okumak için hem zaman uyumlu hem de zaman uyumsuz yöntemler sağlar. Bu belge <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType> sınıfını kullanır. <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> sınıfı iletileri arabelleğe alır ve hem ileti kaynağı hem de ileti hedefi olarak davranır.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="writing-to-and-reading-from-a-dataflow-block-synchronously"></a>Veri akışı bloğundan eşzamanlı olarak yazma ve okuma  
 Aşağıdaki örnek, bir <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> veri akışı bloğuna yazmak için <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> yöntemini ve aynı nesneden okumak için <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> yöntemini kullanır.  
  
 [!code-csharp[TPLDataflow_ReadWrite#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#2)]
 [!code-vb[TPLDataflow_ReadWrite#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#2)]  
  
 Aşağıdaki örnekte gösterildiği gibi, bir veri akışı bloğundan okumak için <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> yöntemini de kullanabilirsiniz. <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> yöntemi geçerli iş parçacığını engellemez ve zaman zaman veri yokladığınızda yararlıdır.  
  
 [!code-csharp[TPLDataflow_ReadWrite#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#3)]
 [!code-vb[TPLDataflow_ReadWrite#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#3)]  
  
 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> yöntemi eşzamanlı olarak davrandığı için, önceki örneklerde <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> nesnesi ikinci döngüden verileri okumadan önce tüm verileri alır. Aşağıdaki örnek, aynı anda ileti bloğundan okumak ve yazmak için <xref:System.Threading.Tasks.Parallel.Invoke%2A> kullanarak ilk örneği genişletir. <xref:System.Threading.Tasks.Parallel.Invoke%2A> eylemleri eşzamanlı olarak gerçekleştirdiğinden, değerler belirli bir sırada <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> nesnesine yazılmaz.  
  
 [!code-csharp[TPLDataflow_ReadWrite#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#4)]
 [!code-vb[TPLDataflow_ReadWrite#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#4)]  
  
## <a name="writing-to-and-reading-from-a-dataflow-block-asynchronously"></a>Veri akışı bloğundan zaman uyumsuz olarak yazma ve okuma  
 Aşağıdaki örnek, aynı nesneden zaman uyumsuz olarak okumak için bir <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> nesnesine ve <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> yöntemine zaman uyumsuz olarak yazmak üzere <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> yöntemini kullanır. Bu örnek, verileri zaman uyumsuz ve hedef bloğundan okumak için [](../../visual-basic/language-reference/operators/await-operator.md) zaman [uyumsuz](../../csharp/language-reference/keywords/async.md) ve [await](../../csharp/language-reference/operators/await.md) [işleçlerini (Visual Basic](../../visual-basic/language-reference/modifiers/async.md) ) kullanır. <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> yöntemi, iletileri ertelemek için bir veri akışı bloğunu etkinleştirmeniz gerektiğinde faydalıdır. <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> yöntemi, verileri kullanılabilir hale geldiğinde veri üzerinde işlem yapmak istediğinizde faydalıdır. İletilerin ileti blokları arasında nasıl yayılır hakkında daha fazla bilgi için, [veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)' na geçirme bölümüne bakın.  
  
 [!code-csharp[TPLDataflow_ReadWrite#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#5)]
 [!code-vb[TPLDataflow_ReadWrite#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#5)]  
  
## <a name="a-complete-example"></a>Tüm örnek  
 Aşağıdaki örnek, bu belge için tüm kodu gösterir.  
  
 [!code-csharp[TPLDataflow_ReadWrite#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#1)]
 [!code-vb[TPLDataflow_ReadWrite#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#1)]  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu örnek, doğrudan bir ileti bloğundan okuma ve yazma işlemlerinin nasıl yapılacağını gösterir. Veri akışı bloklarını, veri akışı bloklarının grafik dizileri olan *ardışık düzenleri*ve veri akışı bloklarının grafikleri olan *ağları*oluşturmak için de bağlayabilirsiniz. Bir ardışık düzen veya ağda, kaynaklar, veriler kullanılabilir oldukça zaman uyumsuz olarak hedeflere yayarlar. Temel bir veri akışı işlem hattı oluşturan bir örnek için bkz. [Izlenecek yol: veri akışı Işlem hattı oluşturma](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md). Daha karmaşık bir veri akışı ağı oluşturan bir örnek için bkz. [Izlenecek yol: Windows Forms uygulamasında veri akışı kullanma](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
