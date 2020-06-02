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
ms.openlocfilehash: 647e77f0c5e182cea90f6e90063826b705de354b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288179"
---
# <a name="how-to-perform-action-when-a-dataflow-block-receives-data"></a>Nasıl yapılır: Veri Akışı Bloğu Veri Aldığında İşlem Gerçekleştirme
*Yürütme veri akışı blok* türleri, veri alırken Kullanıcı tarafından sağlanmış bir temsilciyi çağırır. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType> Ve <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType> sınıfları yürütme veri akışı blok türleridir. `delegate` `Sub` <xref:System.Action%601> <xref:System.Func%602> Yürütme veri akışı bloğuna bir çalışma işlevi sağladığınızda anahtar sözcüğünü (Visual Basic),,, veya lambda ifadesini kullanabilirsiniz. Bu belgede <xref:System.Func%602> , yürütme blokları üzerinde işlem gerçekleştirmek için ve lambda ifadelerinin nasıl kullanılacağı açıklanmaktadır.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Örnek  
 Aşağıdaki örnek, diskten bir dosyayı okumak için veri akışını kullanır ve bu dosyada sıfıra eşit olan bayt sayısını hesaplar. Bu, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> dosyayı okumak ve sıfır bayt sayısını hesaplamak ve <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> sıfır bayt sayısını konsola yazdırmak için kullanır. <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>Nesne <xref:System.Func%602> , bloklar veri alırken iş gerçekleştirilecek bir nesne belirtir. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>Nesnesi, konsola yazdırmak için bir lambda ifadesi kullanır ve okunan sıfır bayt sayısı.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#1)]
 [!code-vb[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#1)]  
  
 Bir nesneye lambda ifadesi sağlayabilseniz de <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> Bu örnek, <xref:System.Func%602> diğer kodun metodunu kullanmasını sağlamak için kullanır `CountBytes` . <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>Nesne bir lambda ifadesi kullanır, çünkü gerçekleştirilecek iş bu göreve özeldir ve diğer koddan faydalı olma olasılığı yoktur. Lambda ifadelerinin görev paralel kitaplığı 'nda nasıl çalıştığı hakkında daha fazla bilgi için bkz. [PLıNQ ve TPL Içindeki lambda ifadeleri](lambda-expressions-in-plinq-and-tpl.md).  
  
 [Veri akışı](dataflow-task-parallel-library.md) belgesindeki temsilci türlerinin Bölüm özeti <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> ,, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> ve nesnelerine sağlayabilmeniz için temsilci türlerini özetler <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> . Tablo ayrıca temsilci türünün zaman uyumlu veya zaman uyumsuz olarak çalışıp çalışmadığını belirtir.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bu örnek, <xref:System.Func%602> <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> veri akışı bloğu görevini eşzamanlı olarak gerçekleştirmek için nesnesine türünde bir temsilci sağlar. Veri akışı bloğunun zaman uyumsuz olarak davranmasına izin vermek için, veri akışı bloğuna türünde bir temsilci sağlayın <xref:System.Func%601> . Bir veri akışı bloğu zaman uyumsuz olarak davrandığı zaman, veri akışı bloğunun görevi yalnızca döndürülen <xref:System.Threading.Tasks.Task%601> nesne bittiğinde tamamlanır. Aşağıdaki örnek, Yöntemi değiştirir `CountBytes` ve [zaman](../../csharp/language-reference/keywords/async.md) uyumsuz ve [await](../../csharp/language-reference/operators/await.md) işleçlerini (Visual Basic içinde[Async](../../visual-basic/language-reference/modifiers/async.md) ve [await](../../visual-basic/language-reference/operators/await-operator.md) ) kullanır. Bu, belirtilen dosyada sıfır olan toplam bayt sayısını zaman uyumsuz olarak hesaplar. <xref:System.IO.FileStream.ReadAsync%2A>Yöntemi, zaman uyumsuz olarak dosya okuma işlemleri gerçekleştirir.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#2)]
 [!code-vb[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#2)]  
  
 Ayrıca, bir yürütme veri akışı bloğunda eylem gerçekleştirmek için zaman uyumsuz lambda ifadeleri de kullanabilirsiniz. Aşağıdaki örnek, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> bir önceki örnekte kullanılan nesneyi değiştirerek çalışmayı zaman uyumsuz olarak gerçekleştirmek için bir lambda ifadesi kullanır.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#3)]
 [!code-vb[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](dataflow-task-parallel-library.md)
