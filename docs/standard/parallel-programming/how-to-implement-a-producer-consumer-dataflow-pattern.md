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
ms.openlocfilehash: 0ff0cc339a26ef97e8036d905bf3c9530d5dee94
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593118"
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a>Nasıl yapılır: Üretici-Tüketici Veri Akışı Düzeni Uygulama
Bu belge, TPL veri akışı kitaplığı bir üretici-tüketici modeli uygulamak için kullanmayı açıklar. Bu modelde *üretici* iletiler gönderen bir ileti bloğu ve *tüketici* bu iletileri okuduğu.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, veri akışı kullanan bir temel üretici-tüketici modeli gösterir. `Produce` Yöntemi içeren veri için rastgele bayt dizileri Yazar bir <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> nesne ve `Consume` yöntemi okur bayt bir <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> nesne. Üzerinde davranarak <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> ve <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> arabirimleri, kendi türetilmiş türler yerine veri akışı bloğu türleri çeşitli davranabilir yeniden kullanılabilir kod yazabilirsiniz. Bu örnekte <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> sınıfı. Çünkü <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> hem bir kaynak olarak davranır sınıf engellemek ve bir hedef blok üretici ve tüketici paylaşılan bir nesnenin veri aktarmak için kullanabilirsiniz.  
  
 `Produce` Yöntem çağrılarını <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> zaman uyumlu olarak hedef bloğa veri yazmak için bir döngü yöntemi. Sonra `Produce` yöntemi Yazar tüm verileri hedef bloğa çağırdığı <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> blok hiçbir zaman ek veriler kullanılabilir olacağını belirtmek için yöntemi. `Consume` Yöntemi kullanan [zaman uyumsuz](~/docs/csharp/language-reference/keywords/async.md) ve [await](~/docs/csharp/language-reference/keywords/await.md) işleçleri ([zaman uyumsuz](~/docs/visual-basic/language-reference/modifiers/async.md) ve [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) Visual Basic'te) için zaman uyumsuz olarak alınan bayt sayısı işlem <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> nesne. Zaman uyumsuz olarak görev yapacak `Consume` yöntem çağrılarını <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> kaynak blok veri yok ve ne zaman kaynak blok ek veriler kullanılabilir hiçbir zaman alacaktır sahip olduğunda bir bildirim almak için yöntemi.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Önceki örnekte, yalnızca tek bir tüketici kaynak verileri işlemek için kullanır. Uygulamanızda birden fazla tüketici kullanılması kullanırsanız <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> aşağıdaki örnekte gösterildiği gibi kaynak bloktaki veri okumak için yöntem.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> Yöntemi döndürür `False` veri ne zaman kullanılabilir. Birden fazla tüketici eşzamanlı olarak kaynak blok erişmesi gerektiğinde, bu mekanizma veri çağrısından sonra hala kullanılabilir olacağını garanti eden <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
