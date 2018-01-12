---
title: "Nasıl yapılır: Veri Akışı Bloğu Veri Aldığında İşlem Gerçekleştirme"
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, receiving data
ms.assetid: fc2585dc-965e-4632-ace7-73dd02684ed3
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4aee0462e641e755830b63d3d708bf51b22cd797
ms.sourcegitcommit: 6a9030eb5bd0f00e1d144f81958adb195cfb1f6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-perform-action-when-a-dataflow-block-receives-data"></a>Nasıl yapılır: Veri Akışı Bloğu Veri Aldığında İşlem Gerçekleştirme
*Yürütme veri akışı bloğunda* türleri veri aldıklarında bir kullanıcı tarafından sağlanan temsilci çağırma. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, Ve <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType> sınıflardır yürütme veri akışı blok türü. Kullanabileceğiniz `delegate` anahtar sözcüğü (`Sub` içinde [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), <xref:System.Action%601>, <xref:System.Func%602>, veya bir çalışma işlevi bir yürütme veri akışı bloğuna sağladığınızda lambda ifadesi. Bu belge nasıl kullanılacağını açıklar <xref:System.Func%602> ve yürütme bloklarında eylemi gerçekleştirmek için lambda ifadesi.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir dosya diskten okumak için veri akışı kullanır ve bu dosyaya sıfıra eşit bayt sayısı hesaplar. Kullandığı <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> dosyayı okuma ve sıfır bayt sayısı işlem ve <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Konsolu'na sıfır bayt sayısı yazdırmak için. <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> Nesnesini belirtir. bir <xref:System.Func%602> bloğu veri aldığında iş gerçekleştirmek için nesne. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Nesnesi salt okunurdur sıfır bayt sayısı konsola yazdırmak için bir lambda ifadesi kullanır.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#1)]
 [!code-vb[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#1)]  
  
 Lambda ifadesi olarak sağlayabilirse bir <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> nesnesi, bu örnek kullanır <xref:System.Func%602> kullanmak başka bir kod etkinleştirmek için `CountBytes` yöntemi. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Yapılması iş bu göreve özeldir ve büyük olasılıkla diğer koddan yararlı olmadığından nesnesini kullanan bir lambda ifadesi. Lambda ifadeleri görev paralel Kitaplığı'nda nasıl çalıştığı hakkında daha fazla bilgi için bkz: [PLINQ ve TPL'deki Lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 Temsilci türleri özeti bölüm içinde [veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) belge özetler sağlamak temsilci türleri <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, ve <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> nesneleri. Tabloda ayrıca temsilci türü eşzamanlı veya zaman uyumsuz olarak çalışıp çalışmayacağını belirtir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Örnek kodu kopyalayın ve bir Visual Studio projesi yapıştırın veya adlı bir dosyaya yapıştırın `DataflowExecutionBlocks.cs` (`DataflowExecutionBlocks.vb` için [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), ve ardından Visual Studio komut istemi penceresinde aşağıdaki komutu çalıştırın.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowExecutionBlocks.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowExecutionBlocks.vb**  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bu örnek bir temsilci türü sağlar <xref:System.Func%602> için <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> eşzamanlı olarak veri akışı bloğu görev gerçekleştirmek için nesne. Zaman uyumsuz olarak davranacak şekilde veri akışı bloğu etkinleştirmek için bir temsilci türü sağlar <xref:System.Func%601> veri akışı bloğuna. Bir veri akışı bloğu zaman uyumsuz olarak davranır, veri akışı bloğu görevini tam yalnızca olduğunda olduğunda döndürülen <xref:System.Threading.Tasks.Task%601> nesne biter. Aşağıdaki örnek değiştirir `CountBytes` yöntemi ve kullandığı [zaman uyumsuz](~/docs/csharp/language-reference/keywords/async.md) ve [await](~/docs/csharp/language-reference/keywords/await.md) işleçleri ([zaman uyumsuz](~/docs/visual-basic/language-reference/modifiers/async.md) ve [bekleme](~/docs/visual-basic/language-reference/operators/await-operator.md) içinde [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) sağlanan dosyasındaki sıfır bayt sayısı toplam zaman uyumsuz olarak hesaplamak için. <xref:System.IO.FileStream.ReadAsync%2A> Yöntemi dosya okuma işlemlerini zaman uyumsuz olarak gerçekleştirir.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#2)]
 [!code-vb[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#2)]  
  
 Zaman uyumsuz lambda ifadeleri, bir yürütme veri akışı bloğunda eylemi gerçekleştirmek için de kullanabilirsiniz. Aşağıdaki örnek değiştirir <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> lambda ifadesi iş zaman uyumsuz olarak gerçekleştirmek için kullandığı şekilde, önceki örnekte kullanılan nesne.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#3)]
 [!code-vb[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#3)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
