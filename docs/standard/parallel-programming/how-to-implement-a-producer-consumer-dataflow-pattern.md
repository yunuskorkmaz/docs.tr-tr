---
title: 'Nasıl yapılır: Üretici-Tüketici Veri Akışı Düzeni Uygulama'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TPL dataflow library, implementing producer-consumer pattern
- Task Parallel Library, dataflows
- producer-consumer patterns, implementing [TPL]
ms.assetid: 47a1d38c-fe9c-44aa-bd15-937bd5659b0b
ms.openlocfilehash: 2db8cfcfc26b001703e08a501c430be4313aca03
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091482"
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a>Nasıl yapılır: Üretici-Tüketici Veri Akışı Düzeni Uygulama
Bu belgede, bir üretici tüketicisi modelini uygulamak için TPL veri akışı kitaplığı 'nın nasıl kullanılacağı açıklanmaktadır. Bu düzende, *üretici* iletileri bir ileti bloğuna gönderir ve *Tüketici* bu bloktaki iletileri okur.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, veri akışı kullanan temel bir üretici tüketici modelini göstermektedir. `Produce` yöntemi bir <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> nesnesine rastgele bayt veri içeren diziler yazar ve `Consume` yöntemi <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> nesnesinden baytları okur. Türetilmiş türleri yerine <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> ve <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> arabirimlerini gerçekleştirerek, çeşitli veri akışı blok türleri üzerinde işlem yapacak yeniden kullanılabilir kod yazabilirsiniz. Bu örnek <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> sınıfını kullanır. <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> sınıfı hem kaynak bloğu hem de hedef blok olarak davrandığı için, üretici ve tüketici verileri aktarmak için paylaşılan bir nesne kullanabilir.  
  
 `Produce` yöntemi, hedef bloğa eşzamanlı olarak veri yazmak için bir döngüde <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> yöntemini çağırır. `Produce` yöntemi tüm verileri hedef bloğuna yazdıktan sonra, bloğun hiçbir şekilde ek veri olmadığını belirtmek için <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> yöntemini çağırır. `Consume` yöntemi, <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> nesnesinden alınan toplam bayt sayısını zaman uyumsuz olarak hesaplamak için [Async](../../csharp/language-reference/keywords/async.md) ve [await](../../csharp/language-reference/operators/await.md) Işleçlerini (Visual Basic içinde[Async](../../visual-basic/language-reference/modifiers/async.md) ve [await](../../visual-basic/language-reference/operators/await-operator.md) ) kullanır. Zaman uyumsuz olarak hareket etmek için `Consume` yöntemi, kaynak bloğunda kullanılabilir veriler olduğunda ve kaynak bloğunda hiçbir zaman ek veri yoksa bildirim almak için <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> yöntemini çağırır.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Yukarıdaki örnek, kaynak verileri işlemek için yalnızca bir tüketici kullanır. Uygulamanızda birden çok tüketici varsa, aşağıdaki örnekte gösterildiği gibi, kaynak bloğundan verileri okumak için <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> yöntemini kullanın.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> yöntemi, kullanılabilir veri olmadığında `False` döndürür. Birden çok tüketici kaynak bloğuna aynı anda erişmesi gerektiğinde, bu mekanizma <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>çağrısından sonra verilerin hala kullanılabilir olmasını güvence altına alır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
