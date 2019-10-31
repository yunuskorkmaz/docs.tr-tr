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
ms.openlocfilehash: 89ab2bb18e5fe00a4d1b79d911bb0f7524b83104
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124209"
---
# <a name="how-to-perform-action-when-a-dataflow-block-receives-data"></a>Nasıl yapılır: Veri Akışı Bloğu Veri Aldığında İşlem Gerçekleştirme
*Yürütme veri akışı blok* türleri, veri alırken Kullanıcı tarafından sağlanmış bir temsilciyi çağırır. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>ve <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType> sınıfları yürütme veri akışı blok türleridir. Yürütme veri akışı bloğuna bir çalışma işlevi sağladığınızda `delegate` anahtar sözcüğünü (Visual Basic`Sub`), <xref:System.Action%601>, <xref:System.Func%602>veya lambda ifadesini kullanabilirsiniz. Bu belgede, yürütme blokları üzerinde işlem gerçekleştirmek için <xref:System.Func%602> ve lambda ifadelerinin nasıl kullanılacağı açıklanmaktadır.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Örnek  
 Aşağıdaki örnek, diskten bir dosyayı okumak için veri akışını kullanır ve bu dosyada sıfıra eşit olan bayt sayısını hesaplar. Dosyayı okumak ve sıfır bayt sayısını hesaplamak için <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> kullanır ve sıfır bayt sayısını konsola yazdırmak için <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>. <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> nesnesi, bloklar veri alırken iş gerçekleştirilecek bir <xref:System.Func%602> nesnesini belirtir. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesnesi, konsola yazdırmak için bir lambda ifadesi kullanır ve okunan sıfır bayt sayısı.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#1)]
 [!code-vb[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#1)]  
  
 <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> nesnesine bir lambda ifadesi sağlayabilseniz de bu örnek, diğer kodun `CountBytes` metodunu kullanmasını sağlamak için <xref:System.Func%602> kullanır. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesnesi bir lambda ifadesi kullanır, çünkü gerçekleştirilecek iş bu göreve özeldir ve diğer koddan faydalı olma olasılığı yoktur. Lambda ifadelerinin görev paralel kitaplığı 'nda nasıl çalıştığı hakkında daha fazla bilgi için bkz. [PLıNQ ve TPL Içindeki lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) belgesindeki temsilci türlerinin Bölüm özeti, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>ve <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> nesnelerine sağlayabilmeniz için sağladığınız temsilci türlerini özetler. Tablo ayrıca temsilci türünün zaman uyumlu veya zaman uyumsuz olarak çalışıp çalışmadığını belirtir.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bu örnek, veri akışı bloğu görevini eşzamanlı olarak gerçekleştirmek için <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> nesnesine <xref:System.Func%602> bir temsilci sağlar. Veri akışı bloğunun zaman uyumsuz olarak davranmasına olanak tanımak için, veri akışı bloğuna <xref:System.Func%601> türünde bir temsilci sağlayın. Bir veri akışı bloğu zaman uyumsuz olarak davrandığı zaman, veri akışı bloğunun görevi yalnızca döndürülen <xref:System.Threading.Tasks.Task%601> nesnesi bittiğinde tamamlanır. Aşağıdaki örnek, `CountBytes` yöntemini değiştirir ve [zaman](../../csharp/language-reference/keywords/async.md) uyumsuz ve [await](../../csharp/language-reference/operators/await.md) işleçlerini[kullanır (Visual Basic içinde zaman uyumsuz](../../visual-basic/language-reference/modifiers/async.md) ve [await](../../visual-basic/language-reference/operators/await-operator.md) ). Bu, belirtilen dosyada sıfır olan toplam bayt sayısını zaman uyumsuz olarak hesaplar. <xref:System.IO.FileStream.ReadAsync%2A> yöntemi, zaman uyumsuz olarak dosya okuma işlemleri gerçekleştirir.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#2)]
 [!code-vb[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#2)]  
  
 Ayrıca, bir yürütme veri akışı bloğunda eylem gerçekleştirmek için zaman uyumsuz lambda ifadeleri de kullanabilirsiniz. Aşağıdaki örnek, bir önceki örnekte kullanılan <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> nesnesini değiştirerek çalışmayı zaman uyumsuz olarak gerçekleştirmek için bir lambda ifadesi kullanır.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#3)]
 [!code-vb[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
