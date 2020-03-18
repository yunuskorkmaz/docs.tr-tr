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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73124209"
---
# <a name="how-to-perform-action-when-a-dataflow-block-receives-data"></a>Nasıl yapılır: Veri Akışı Bloğu Veri Aldığında İşlem Gerçekleştirme
*Yürütme veri akışı bloğu* türleri, verileri aldıklarında kullanıcı tarafından sağlanan bir temsilciyi çağırır. , <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>ve <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType> sınıflar yürütme veri akışı blok türleridir. Yürütme veri `delegate` akışı bloğuna iş <xref:System.Action%601>işlevi <xref:System.Func%602>sağlarken anahtar sözcüğü (Visual`Sub` Basic'te) veya lambda ifadesini kullanabilirsiniz. Bu belge, yürütme <xref:System.Func%602> bloklarında eylem gerçekleştirmek için nasıl kullanılacağını ve lambda ifadelerini açıklar.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Örnek  
 Aşağıdaki örnek, diskten bir dosyayı okumak için veri akışını kullanır ve bu dosyadaki sıfıra eşit bayt sayısını hesaplar. Dosyayı <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> okumak ve sıfır bayt sayısını hesaplamak ve <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> konsola sıfır bayt sayısını yazdırmak için kullanır. Nesne, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> bloklar <xref:System.Func%602> veri aldığında çalışması gerçekleştirmek için bir nesne belirtir. Nesne, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> konsola okunan sıfır bayt sayısını yazdırmak için bir lambda ifadesi kullanır.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#1)]
 [!code-vb[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#1)]  
  
 Bir <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> nesneye lambda ifadesi sağlayabilmenize <xref:System.Func%602> rağmen, bu örnek `CountBytes` yöntemi diğer kodu etkinleştirmek için kullanılır. Gerçekleştirilecek çalışma bu göreve özgü olduğundan ve diğer kodlardan yararlı olması olası olmadığından <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesne bir lambda ifadesi kullanır. Görev Paralel Kitaplığı'nda lambda ifadelerinin nasıl çalıştığı hakkında daha fazla bilgi için [PLINQ ve TPL'deki Lambda İfadeleri'ne](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)bakın.  
  
 [Veri Akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) belgesindeki Temsilci Türlerinin Bölüm Özeti, ,, ve <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> nesnelere sağlayabileceğiniz temsilci türlerini özetler. Tablo ayrıca temsilci türünün eşzamanlı mı yoksa eşzamanlı mı çalıştığını da belirtir.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bu örnek, veri <xref:System.Func%602> akışı <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> bloğu görevini eşzamanlı olarak gerçekleştirmek için nesneye bir tür temsilcisi sağlar. Veri akışı bloğunun eşsenkronize şekilde çalışmasını sağlamak için, <xref:System.Func%601> veri akışı bloğuna bir tür temsilcisi sağlayın. Bir veri akışı bloğu eşsenkronize şekilde işyaptığında, veri akışı bloğunun görevi <xref:System.Threading.Tasks.Task%601> yalnızca döndürülen nesne tamamlandığında tamamlanır. Aşağıdaki `CountBytes` örnek yöntemi değiştirir ve [async](../../csharp/language-reference/keywords/async.md) kullanır ve sağlanan dosyada sıfır olan bayt toplam sayısını eşzamanlı olarak hesaplamak için operatörleri[(Async](../../visual-basic/language-reference/modifiers/async.md) ve [await](../../csharp/language-reference/operators/await.md) [Await](../../visual-basic/language-reference/operators/await-operator.md) In Visual Basic) kullanır. Yöntem, <xref:System.IO.FileStream.ReadAsync%2A> dosya okuma işlemlerini eş senkronize olarak gerçekleştirir.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#2)]
 [!code-vb[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#2)]  
  
 Yürütme veri akışı bloğunda eylem gerçekleştirmek için eşsenkronize lambda ifadelerini de kullanabilirsiniz. Aşağıdaki örnek, önceki <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> örnekte kullanılan nesneyi, işi eşzamanlı olarak gerçekleştirmek için lambda ifadesini kullanabilmesi için değiştirir.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#3)]
 [!code-vb[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
