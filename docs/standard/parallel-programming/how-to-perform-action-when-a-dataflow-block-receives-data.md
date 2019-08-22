---
title: 'Nasıl yapılır: Veri Akışı Bloğu Veri Aldığında İşlem Gerçekleştirme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, receiving data
ms.assetid: fc2585dc-965e-4632-ace7-73dd02684ed3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54eb9723f44924919ca1b4631e35e1e4da4af2af
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666352"
---
# <a name="how-to-perform-action-when-a-dataflow-block-receives-data"></a>Nasıl yapılır: Veri Akışı Bloğu Veri Aldığında İşlem Gerçekleştirme
*Yürütme veri akışı blok* türleri, veri alırken Kullanıcı tarafından sağlanmış bir temsilciyi çağırır. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType>, Vesınıfları<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType> yürütme veri akışı blok türleridir. <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType> Yürütme veri akışı bloğuna `delegate` bir çalışma`Sub` işlevi sağladığınızda anahtar sözcüğünü <xref:System.Action%601>( <xref:System.Func%602>Visual Basic),,, veya lambda ifadesini kullanabilirsiniz. Bu belgede <xref:System.Func%602> , yürütme blokları üzerinde işlem gerçekleştirmek için ve lambda ifadelerinin nasıl kullanılacağı açıklanmaktadır.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Örnek  
 Aşağıdaki örnek, diskten bir dosyayı okumak için veri akışını kullanır ve bu dosyada sıfıra eşit olan bayt sayısını hesaplar. Bu, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> dosyayı okumak ve sıfır bayt sayısını hesaplamak ve <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> sıfır bayt sayısını konsola yazdırmak için kullanır. Nesne, bloklar veri <xref:System.Func%602> alırken iş gerçekleştirilecek bir nesne belirtir. <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Nesnesi, konsola yazdırmak için bir lambda ifadesi kullanır ve okunan sıfır bayt sayısı.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#1)]
 [!code-vb[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#1)]  
  
 Bir <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> nesneye lambda ifadesi sağlayabilseniz de bu örnek, `CountBytes` diğer kodun metodunu kullanmasını <xref:System.Func%602> sağlamak için kullanır. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Nesne bir lambda ifadesi kullanır, çünkü gerçekleştirilecek iş bu göreve özeldir ve diğer koddan faydalı olma olasılığı yoktur. Lambda ifadelerinin görev paralel kitaplığı 'nda nasıl çalıştığı hakkında daha fazla bilgi için bkz. [PLıNQ ve TPL Içindeki lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) belgesindeki temsilci türlerinin Bölüm Özeti, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, ve <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> nesnelerine sağlayabilmeniz için temsilci türlerini özetler. Tablo ayrıca temsilci türünün zaman uyumlu veya zaman uyumsuz olarak çalışıp çalışmadığını belirtir.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bu örnek, veri akışı bloğu görevini <xref:System.Func%602> eşzamanlı olarak <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> gerçekleştirmek için nesnesine türünde bir temsilci sağlar. Veri akışı bloğunun zaman uyumsuz olarak davranmasına izin vermek için, veri akışı bloğuna <xref:System.Func%601> türünde bir temsilci sağlayın. Bir veri akışı bloğu zaman uyumsuz olarak davrandığı zaman, veri akışı bloğunun görevi yalnızca döndürülen <xref:System.Threading.Tasks.Task%601> nesne bittiğinde tamamlanır. Aşağıdaki `CountBytes` örnek, Yöntemi değiştirir ve [zaman](../../csharp/language-reference/keywords/async.md) uyumsuz ve [await](../../csharp/language-reference/keywords/await.md) işleçlerini (Visual Basic içinde[Async](../../visual-basic/language-reference/modifiers/async.md) ve [await](../../visual-basic/language-reference/operators/await-operator.md) ) kullanır. Bu, belirtilen dosyada sıfır olan toplam bayt sayısını zaman uyumsuz olarak hesaplar. Yöntemi <xref:System.IO.FileStream.ReadAsync%2A> , zaman uyumsuz olarak dosya okuma işlemleri gerçekleştirir.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#2)]
 [!code-vb[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#2)]  
  
 Ayrıca, bir yürütme veri akışı bloğunda eylem gerçekleştirmek için zaman uyumsuz lambda ifadeleri de kullanabilirsiniz. Aşağıdaki örnek, bir önceki <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> örnekte kullanılan nesneyi değiştirerek çalışmayı zaman uyumsuz olarak gerçekleştirmek için bir lambda ifadesi kullanır.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#3)]
 [!code-vb[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
