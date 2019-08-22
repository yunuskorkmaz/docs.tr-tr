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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 044e726a1c668335780fe3d4322fbce83d8dcbba
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666357"
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a>Nasıl yapılır: Üretici-Tüketici Veri Akışı Düzeni Uygulama
Bu belgede, bir üretici tüketicisi modelini uygulamak için TPL veri akışı kitaplığı 'nın nasıl kullanılacağı açıklanmaktadır. Bu düzende, *üretici* iletileri bir ileti bloğuna gönderir ve *Tüketici* bu bloktaki iletileri okur.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, veri akışı kullanan temel bir üretici tüketici modelini göstermektedir. Yöntemi bir <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> nesnesine rastgele bayt veri içeren dizileri yazar ve `Consume` yöntemi bir <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> nesneden baytları okur. `Produce` <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> Ve<xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> arabirimlerini, türetilmiş türleri yerine hareket eterek, çeşitli veri akışı blok türleri üzerinde işlem görecek yeniden kullanılabilir kod yazabilirsiniz. Bu örnek <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> sınıfını kullanır. <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> Sınıfı hem kaynak bloğu hem de hedef blok olarak davrandığı için, üretici ve tüketici verileri aktarmak için paylaşılan bir nesne kullanabilir.  
  
 Yöntemi, hedef bloğa <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> eşzamanlı olarak veri yazmak için bir döngüsünde yöntemini çağırır. `Produce` Yöntemi, `Produce` tüm verileri hedef bloğuna yazdıktan sonra, bloğun hiçbir şey ek veriye <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> sahip olacağını belirtmek için yöntemini çağırır. [](../../csharp/language-reference/keywords/async.md) [](../../visual-basic/language-reference/operators/await-operator.md) [](../../csharp/language-reference/keywords/await.md) [](../../visual-basic/language-reference/modifiers/async.md) Yöntemi, nesneden<xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> alınan toplam bayt sayısını zaman uyumsuz olarak hesaplamak için Async ve await işleçlerini (Visual Basic zaman uyumsuz ve await) kullanır. `Consume` Zaman uyumsuz olarak `Consume` hareket etmek için yöntemi, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> kaynak bloğunda kullanılabilir veriler olduğunda ve kaynak bloğunda hiçbir zaman ek veri yoksa bildirim almak için yöntemini çağırır.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Yukarıdaki örnek, kaynak verileri işlemek için yalnızca bir tüketici kullanır. Uygulamanızda birden çok tüketici varsa, aşağıdaki örnekte gösterildiği gibi, <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> kaynak bloğundan verileri okumak için yöntemini kullanın.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 Yöntemi <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> , kullanılabilir `False` veri olmadığında döndürür. Kaynak bloğuna aynı anda birden çok tüketici erişmesi gerektiğinde, bu mekanizma, ' a yapılan çağrıdan <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>sonra verilerin hala kullanılabilir olmasını güvence altına alır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
