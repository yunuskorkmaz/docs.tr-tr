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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139282"
---
# <a name="how-to-write-messages-to-and-read-messages-from-a-dataflow-block"></a>Nasıl yapılır: Veri Akışı Bloğuna İletiler Yazma ve Veri Akışı Bloğundan İletiler Okuma
Bu belge, bir veri akışı bloğuna ileti yazmak ve iletileri okumak için TPL Veri Akışı Kitaplığı'nın nasıl kullanılacağını açıklar. TPL Veri Akışı Kitaplığı, veri akışı bloğuna ileti yazmak ve iletileri okumak için hem senkron hem de eşzamanlı yöntemler sağlar. Bu belge <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType> sınıfı kullanır. Sınıf <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> iletileri arabelleklendi ve hem ileti kaynağı hem de ileti hedefi olarak tepki veriyor.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="writing-to-and-reading-from-a-dataflow-block-synchronously"></a>Veri Akışı Bloğuna Eşit Olarak Yazma ve Okuma  
 Aşağıdaki örnek, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> veri <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> akışı bloğuna yazmak için <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> yöntemi ve aynı nesneden okumak için yöntemi kullanır.  
  
 [!code-csharp[TPLDataflow_ReadWrite#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#2)]
 [!code-vb[TPLDataflow_ReadWrite#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#2)]  
  
 Aşağıdaki örnekte <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> gösterildiği gibi, bir veri akışı bloğundan okumak için yöntemi de kullanabilirsiniz. Yöntem <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> geçerli iş parçacığı engellemez ve zaman zaman veri için yoklama yararlıdır.  
  
 [!code-csharp[TPLDataflow_ReadWrite#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#3)]
 [!code-vb[TPLDataflow_ReadWrite#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#3)]  
  
 <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> Yöntem eşzamanlı hareket ettiği için, önceki örneklerdeki <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> nesne, ikinci döngü verileri okumadan önce tüm verileri alır. Aşağıdaki örnek, ileti bloğundan <xref:System.Threading.Tasks.Parallel.Invoke%2A> aynı anda okumak ve yazmak için kullanarak ilk örneği genişletir. Eylemleri <xref:System.Threading.Tasks.Parallel.Invoke%2A> aynı anda gerçekleştirdiğinden, değerler <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> nesneye belirli bir sırada yazılmaz.  
  
 [!code-csharp[TPLDataflow_ReadWrite#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#4)]
 [!code-vb[TPLDataflow_ReadWrite#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#4)]  
  
## <a name="writing-to-and-reading-from-a-dataflow-block-asynchronously"></a>Veri Akışı Bloğuna Yazma ve Okuma  
 Aşağıdaki örnek, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> bir <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> nesneye eş senkronize bir <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> şekilde yazmak için yöntemi ve aynı nesneden eşzamanlı olarak okumak için yöntemi kullanır. Bu örnek, hedef bloktaki verileri eş senkronize bir şekilde göndermek ve verileri okumak için [async](../../csharp/language-reference/keywords/async.md) ve [await](../../csharp/language-reference/operators/await.md) işleçlerini (Görsel Temelde[Async](../../visual-basic/language-reference/modifiers/async.md) ve [Await)](../../visual-basic/language-reference/operators/await-operator.md) kullanır. Yöntem, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> iletileri ertelemek için bir veri akışı bloğunu etkinleştirmeniz gerektiğinde yararlıdır. Yöntem, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> veriler kullanılabilir olduğunda verilere göre hareket etmek istediğinizde yararlıdır. İletilerin ileti blokları arasında nasıl yayılış ları hakkında daha fazla bilgi için [Veri Akışı'nda](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)İleti Geçen bölümüne bakın.  
  
 [!code-csharp[TPLDataflow_ReadWrite#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#5)]
 [!code-vb[TPLDataflow_ReadWrite#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#5)]  
  
## <a name="a-complete-example"></a>Tam Bir Örnek  
 Aşağıdaki örnekte, bu belgenin tam kodu gösterilmektedir.  
  
 [!code-csharp[TPLDataflow_ReadWrite#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#1)]
 [!code-vb[TPLDataflow_ReadWrite#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#1)]  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu örnek, doğrudan ileti bloğundan nasıl okunup yazılanın yapılacağını gösterir. Veri akışı bloklarını, veri akışı bloklarının doğrusal dizileri veya veri akışı bloklarının grafikleri olan *ağları*oluşturan *ardışık hatlar*oluşturmak için de bağlayabilirsiniz. Bir ardışık düzen veya ağda, kaynaklar, veriler kullanılabilir oldukça zaman uyumsuz olarak hedeflere yayarlar. Temel bir veri akışı ardışık alanı oluşturan bir örnek [için](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md)bkz. Daha karmaşık bir veri akışı ağı oluşturan [bir](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)örnek için bkz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
