---
title: 'Nasıl yapılır: üretici-tüketici veri akışı modelini uygulama'
description: .NET 'teki TPL veri akışı kitaplığını kullanarak bir üretici-tüketici veri akışı deseninin nasıl uygulanacağını anlayın.
ms.date: 09/24/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TPL dataflow library, implementing producer-consumer pattern
- Task Parallel Library, dataflows
- producer-consumer patterns, implementing [TPL]
ms.assetid: 47a1d38c-fe9c-44aa-bd15-937bd5659b0b
ms.openlocfilehash: fc68d9e678dab88ec5008b6c15ef17a5d20f25ae
ms.sourcegitcommit: d04388f94dbcd756ffd608536c869aee3242cdb0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91206386"
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a>Nasıl yapılır: üretici-tüketici veri akışı modelini uygulama

Bu makalede, bir üretici tüketicisi modelini uygulamak için TPL veri akışı kitaplığı 'nı nasıl kullanacağınızı öğreneceksiniz. Bu düzende, *üretici* iletileri bir ileti bloğuna gönderir ve *Tüketici* bu bloktaki iletileri okur.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, veri akışı kullanan temel bir üretici tüketici modelini göstermektedir. `Produce`Yöntemi bir nesnesine rastgele bayt veri içeren dizileri yazar <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> ve `Consume` yöntemi bir nesneden baytları okur <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> . <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>Ve <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> arabirimlerini, türetilmiş türleri yerine hareket eterek, çeşitli veri akışı blok türleri üzerinde işlem görecek yeniden kullanılabilir kod yazabilirsiniz. Bu örnek sınıfını kullanır <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> . <xref:System.Threading.Tasks.Dataflow.BufferBlock%601>Sınıfı hem kaynak bloğu hem de hedef blok olarak davrandığı için, üretici ve tüketici verileri aktarmak için paylaşılan bir nesne kullanabilir.

 `Produce`Yöntemi, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> hedef bloğa eşzamanlı olarak veri yazmak için bir döngüsünde yöntemini çağırır. Yöntemi, `Produce` tüm verileri hedef bloğuna yazdıktan sonra, <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> bloğun hiçbir şey ek veriye sahip olacağını belirtmek için yöntemini çağırır. `Consume`Yöntemi, nesneden alınan toplam bayt sayısını zaman uyumsuz olarak hesaplamak için [Async](../../csharp/language-reference/keywords/async.md) ve [await](../../csharp/language-reference/operators/await.md) işleçlerini (Visual Basic[zaman uyumsuz](../../visual-basic/language-reference/modifiers/async.md) ve [await](../../visual-basic/language-reference/operators/await-operator.md) ) kullanır <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> . Zaman uyumsuz olarak hareket etmek için `Consume` yöntemi, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> kaynak bloğunda kullanılabilir veriler olduğunda ve kaynak bloğunda hiçbir zaman ek veri yoksa bildirim almak için yöntemini çağırır.

 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]

## <a name="robust-programming"></a>Güçlü programlama

 Yukarıdaki örnek, kaynak verileri işlemek için yalnızca bir tüketici kullanır. Uygulamanızda birden çok tüketici varsa, <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> Aşağıdaki örnekte gösterildiği gibi, kaynak bloğundan verileri okumak için yöntemini kullanın.

 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]

 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A>Yöntemi, `False` kullanılabilir veri olmadığında döndürür. Kaynak bloğuna aynı anda birden çok tüketici erişmesi gerektiğinde, bu mekanizma, ' a yapılan çağrıdan sonra verilerin hala kullanılabilir olmasını güvence altına alır <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> .

## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](dataflow-task-parallel-library.md)
