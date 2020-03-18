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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73091482"
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a>Nasıl yapılır: Üretici-Tüketici Veri Akışı Düzeni Uygulama
Bu belge, üretici-tüketici deseni uygulamak için TPL Veri Akışı Kitaplığı'nın nasıl kullanılacağını açıklar. Bu desende, *üretici* ileti bloğuna ileti gönderir ve *tüketici* bu bloktaki iletileri okur.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, veri akışını kullanan temel bir üretici-tüketici modelini göstermektedir. Yöntem, `Produce` bir <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> nesneye rasgele bayt veri içeren diziler yazar ve `Consume` yöntem <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> bir nesneden bayt okur. Türemiş <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> türleri <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> yerine, türemiş türleri yerine, arabirimler üzerinde hareket ederek, çeşitli veri akışı bloğu türlerine göre hareket edebilecek yeniden kullanılabilir kod yazabilirsiniz. Bu örnek, <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> sınıfı kullanır. <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> Sınıf hem kaynak bloğu hem de hedef blok olarak hareket ettiği için, üretici ve tüketici veri aktarmak için paylaşılan bir nesneyi kullanabilir.  
  
 Yöntem, `Produce` verileri <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> eşzamanlı olarak hedef bloya yazmak için bir döngüdeki yöntemi çağırır. `Produce` Yöntem tüm verileri hedef bloya yazdıktan <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> sonra, bloğun hiçbir zaman ek veri bulunamayacağını belirtmek için yöntemi çağırır. `Consume` Yöntem, <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> nesneden alınan toplam bayt sayısını eşzamanlı olarak hesaplamak için [async](../../csharp/language-reference/keywords/async.md) ve [await](../../csharp/language-reference/operators/await.md) işleçlerini (Görsel Temelde[Async](../../visual-basic/language-reference/modifiers/async.md) ve [Await)](../../visual-basic/language-reference/operators/await-operator.md) kullanır. Eşzamanlı hareket etmek için `Consume` yöntem, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> kaynak bloğunda veri olduğunda ve kaynak bloğunhiçbir zaman hiçbir zaman ek veri bulunamayacağımda bildirim almak için yöntem çağırır.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Önceki örnek, kaynak verileri işlemek için yalnızca bir tüketici kullanır. Uygulamanızda birden çok tüketici varsa, <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> aşağıdaki örnekte gösterildiği gibi kaynak bloktaki verileri okumak için yöntemi kullanın.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 Veri <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> olmadığında `False` yöntem döndürür. Birden çok tüketicinin kaynak bloğuna aynı anda erişmesi gerektiğinde, bu <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>mekanizma '' için yapılan çağrıdan sonra verilerin hala kullanılabilir olduğunu garanti eder.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
