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
ms.openlocfilehash: 6cc4dc3a0692000958d66222e6cdc30acf874189
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666374"
---
# <a name="how-to-write-messages-to-and-read-messages-from-a-dataflow-block"></a>Nasıl yapılır: Veri Akışı Bloğuna İletiler Yazma ve Veri Akışı Bloğundan İletiler Okuma
Bu belgede, bir veri akışı bloğunda ileti yazmak ve iletileri okumak için TPL veri akışı kitaplığı 'nın nasıl kullanılacağı açıklanmaktadır. TPL veri akışı kitaplığı, veri akışı bloğundan ileti yazmak ve iletileri okumak için hem zaman uyumlu hem de zaman uyumsuz yöntemler sağlar. Bu belge <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType> sınıfını kullanır. <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> Sınıfı iletileri arabelleğe alır ve hem ileti kaynağı hem de ileti hedefi olarak davranır.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="writing-to-and-reading-from-a-dataflow-block-synchronously"></a>Veri akışı bloğundan eşzamanlı olarak yazma ve okuma  
 Aşağıdaki örnek, bir <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> veri akışı bloğuna yazmak için yöntemini ve aynı nesneden okuma yönteminikullanır.<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A>  
  
 [!code-csharp[TPLDataflow_ReadWrite#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#2)]
 [!code-vb[TPLDataflow_ReadWrite#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#2)]  
  
 Aşağıdaki örnekte gösterildiği gibi, <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> bir veri akışı bloğundan okumak için yöntemini de kullanabilirsiniz. <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> Yöntemi, geçerli iş parçacığını engellemez ve zaman zaman veri yokladığınızda yararlıdır.  
  
 [!code-csharp[TPLDataflow_ReadWrite#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#3)]
 [!code-vb[TPLDataflow_ReadWrite#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#3)]  
  
 Yöntem zaman uyumlu <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> olarak hareket ettiğinden, önceki örneklerdeki nesne ikinci döngüden verileri okumadan önce tüm verileri alır. <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> Aşağıdaki örnek, ile ileti bloğunu aynı anda okumak <xref:System.Threading.Tasks.Parallel.Invoke%2A> ve yazmak için kullanarak ilk örneği genişletir. Eylemleri eşzamanlı olarak <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> gerçekleştirdiğinden, değerler nesneye belirli bir sırada yazılmaz. <xref:System.Threading.Tasks.Parallel.Invoke%2A>  
  
 [!code-csharp[TPLDataflow_ReadWrite#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#4)]
 [!code-vb[TPLDataflow_ReadWrite#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#4)]  
  
## <a name="writing-to-and-reading-from-a-dataflow-block-asynchronously"></a>Veri akışı bloğundan zaman uyumsuz olarak yazma ve okuma  
 Aşağıdaki örnek, bir <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> nesneye zaman uyumsuz olarak yazma için yöntemini ve <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> aynı nesneden zaman uyumsuz olarak okuma yöntemini kullanır. Bu örnek, verileri zaman uyumsuz ve hedef bloğundan[](../../visual-basic/language-reference/modifiers/async.md) okumak için [](../../visual-basic/language-reference/operators/await-operator.md) zaman [uyumsuz](../../csharp/language-reference/keywords/async.md) ve [await](../../csharp/language-reference/keywords/await.md) işleçlerini (Visual Basic) kullanır. Yöntemi <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> , iletileri ertelemek için bir veri akışı bloğunu etkinleştirmeniz gerektiğinde faydalıdır. Bu <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> Yöntem, veriler kullanılabilir hale geldiğinde veriler üzerinde işlem yapmak istediğinizde faydalıdır. İletilerin ileti blokları arasında nasıl yayılır hakkında daha fazla bilgi için, [veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)' na geçirme bölümüne bakın.  
  
 [!code-csharp[TPLDataflow_ReadWrite#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#5)]
 [!code-vb[TPLDataflow_ReadWrite#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#5)]  
  
## <a name="a-complete-example"></a>Tüm örnek  
 Aşağıdaki örnek, bu belge için tüm kodu gösterir.  
  
 [!code-csharp[TPLDataflow_ReadWrite#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#1)]
 [!code-vb[TPLDataflow_ReadWrite#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#1)]  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu örnek, doğrudan bir ileti bloğundan okuma ve yazma işlemlerinin nasıl yapılacağını gösterir. Veri akışı bloklarını, veri akışı bloklarının grafik dizileri olan *ardışık düzenleri*ve veri akışı bloklarının grafikleri olan *ağları*oluşturmak için de bağlayabilirsiniz. Bir ardışık düzen veya ağda, kaynaklar, veriler kullanılabilir oldukça zaman uyumsuz olarak hedeflere yayarlar. Temel bir veri akışı işlem hattı oluşturan bir örnek için bkz [. İzlenecek yol: Veri akışı işlem hattı](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md)oluşturma. Daha karmaşık bir veri akışı ağı oluşturan bir örnek için bkz [. İzlenecek yol: Windows Forms uygulamasında](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)veri akışı kullanma.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
