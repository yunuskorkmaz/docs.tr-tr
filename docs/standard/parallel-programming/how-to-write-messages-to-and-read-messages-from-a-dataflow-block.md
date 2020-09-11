---
title: 'Nasıl yapılır: veri akışı bloğundan ileti yazma ve okuma'
ms.date: 09/10/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, reading and writing messages
ms.assetid: 1a9bf078-aa82-46eb-b95a-f87237f028c5
ms.openlocfilehash: 8eb92d917bb2b03c2a505a2ba238598e0c1a450c
ms.sourcegitcommit: 6d4ee46871deb9ea1e45bb5f3784474e240bbc26
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90022863"
---
# <a name="how-to-write-and-read-messages-from-a-dataflow-block"></a>Nasıl yapılır: veri akışı bloğundan ileti yazma ve okuma

Bu makalede, bir veri akışı bloğunda ileti yazmak ve iletileri okumak için görev paralel kitaplığı (TPL) veri akışı kitaplığının nasıl kullanılacağı açıklanır. TPL veri akışı kitaplığı, veri akışı bloğundan ileti yazmak ve iletileri okumak için hem zaman uyumlu hem de zaman uyumsuz yöntemler sağlar. Bu makalede, sınıfının nasıl kullanılacağı gösterilmektedir <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType> . <xref:System.Threading.Tasks.Dataflow.BufferBlock%601>Sınıfı iletileri arabelleğe alır ve hem ileti kaynağı hem de ileti hedefi olarak davranır.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="writing-and-reading-synchronously"></a>Zaman uyumlu yazma ve okuma

Aşağıdaki örnek, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> bir veri akışı bloğuna yazmak için yöntemini <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> ve <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> aynı nesneden okuma yöntemini kullanır.

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="2":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="2":::

<xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A>Aşağıdaki örnekte gösterildiği gibi, bir veri akışı bloğundan okumak için yöntemini de kullanabilirsiniz. <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A>Yöntemi, geçerli iş parçacığını engellemez ve zaman zaman veri yokladığınızda yararlıdır.

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="3":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="3":::

<xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A>Yöntem zaman uyumlu olarak hareket ettiğinden, <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> önceki örneklerdeki nesne ikinci döngüden verileri okumadan önce tüm verileri alır. Aşağıdaki örnek, ile <xref:System.Threading.Tasks.Task.WhenAll(System.Threading.Tasks.Task[])?displayProperty=nameWithType> ileti bloğunu aynı anda okumak ve yazmak için kullanarak ilk örneği genişletir. <xref:System.Threading.Tasks.Task.WhenAll%2A>Eylemleri eşzamanlı olarak gerçekleştirdiğinden, değerler <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> nesneye belirli bir sırada yazılmaz.

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="4":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="4":::

## <a name="writing-and-reading-asynchronously"></a>Zaman uyumsuz olarak yazma ve okuma

Aşağıdaki örnek, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> bir nesneye zaman uyumsuz olarak yazma için yöntemini <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> ve <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> aynı nesneden zaman uyumsuz olarak okuma yöntemini kullanır. Bu örnek, verileri zaman uyumsuz ve hedef bloğundan okumak için [Await](../../visual-basic/language-reference/operators/await-operator.md) zaman [uyumsuz](../../csharp/language-reference/keywords/async.md) ve [await](../../csharp/language-reference/operators/await.md) [işleçlerini (Visual Basic](../../visual-basic/language-reference/modifiers/async.md) ) kullanır. <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A>Yöntemi, iletileri ertelemek için bir veri akışı bloğunu etkinleştirmeniz gerektiğinde faydalıdır. <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A>Bu yöntem, veriler kullanılabilir hale geldiğinde veriler üzerinde işlem yapmak istediğinizde faydalıdır. İletilerin ileti blokları arasında nasıl yayılır hakkında daha fazla bilgi için, [veri akışı](dataflow-task-parallel-library.md)' na geçirme bölümüne bakın.

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="5":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="5":::

## <a name="a-complete-example"></a>Tüm örnek

Aşağıdaki örnek, bu makalenin tüm kodunu gösterir.

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="1":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="1":::

## <a name="next-steps"></a>Sonraki adımlar

Bu örnek, doğrudan bir ileti bloğundan okuma ve yazma işlemlerinin nasıl yapılacağını gösterir. Veri akışı bloklarını, veri akışı bloklarının grafik dizileri olan *ardışık düzenleri*ve veri akışı bloklarının grafikleri olan *ağları*oluşturmak için de bağlayabilirsiniz. Bir ardışık düzen veya ağda, kaynaklar, veriler kullanılabilir oldukça zaman uyumsuz olarak hedeflere yayarlar. Temel bir veri akışı işlem hattı oluşturan bir örnek için bkz. [Izlenecek yol: veri akışı Işlem hattı oluşturma](walkthrough-creating-a-dataflow-pipeline.md). Daha karmaşık bir veri akışı ağı oluşturan bir örnek için bkz. [Izlenecek yol: Windows Forms uygulamasında veri akışı kullanma](walkthrough-using-dataflow-in-a-windows-forms-application.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Akışı (Görev Paralel Kitaplığı)](dataflow-task-parallel-library.md)
