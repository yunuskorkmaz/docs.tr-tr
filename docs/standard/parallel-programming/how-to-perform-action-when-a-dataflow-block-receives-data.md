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
ms.openlocfilehash: 369559feca4edab6de587a3494588973e0c2e1b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937481"
---
# <a name="how-to-perform-action-when-a-dataflow-block-receives-data"></a>Nasıl yapılır: Veri Akışı Bloğu Veri Aldığında İşlem Gerçekleştirme
*Yürütme veri akışı bloğu* veri aldıklarında çağrı bir kullanıcı tarafından sağlanan temsilci türleri. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, Ve <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType> yürütme veri akışı bloğu türleri sınıflardır. Kullanabileceğiniz `delegate` anahtar sözcüğü (`Sub` Visual Basic'te), <xref:System.Action%601>, <xref:System.Func%602>, ya da bir iş işlevi bir yürütme veri akışı bloğuna sağladığınızda bir lambda ifadesi. Bu belgenin nasıl kullanılacağını açıklar <xref:System.Func%602> ve lambda ifadeleri, yürütme blokları eylemi gerçekleştirmek için.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir dosyayı diskten okumak için veri akışı kullanır ve bu dosyanın sıfır bayt sayısını hesaplar. Kullandığı <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> dosyayı okumak ve sıfır bayt sayısı işlem ve <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> sıfır bayt konsola yazdırmak için. <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> Nesnesini belirtir bir <xref:System.Func%602> bloğu veri aldığında çalışmayı gerçekleştirmek için nesne. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Nesne okunur sıfır bayt sayısı konsola yazdırmak için bir lambda ifadesi kullanır.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#1)]
 [!code-vb[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#1)]  
  
 Bir lambda ifadesi sağlamasına karşın bir <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> nesnesi, bu örnekte <xref:System.Func%602> kullanmak başka bir kod etkinleştirmek için `CountBytes` yöntemi. <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Nesnesi, gerçekleştirilmesi gereken iş bu görevin özgüdür ve başka bir koddan yararlı olabilir olmadığından bir lambda ifadesi kullanır. Lambda ifadeleri görev paralel Kitaplığı'nda nasıl çalıştığı hakkında daha fazla bilgi için bkz. [PLINQ ve TPL'deki Lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 Temsilci türlerinin özeti bölümü içinde [veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) belge sağlayabileceğiniz temsilci türleri özetlenmektedir <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, ve <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> nesneleri. Tablo de temsilci türünün zaman uyumlu veya zaman uyumsuz olarak çalışıp çalışmayacağını belirtir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Örnek kodu kopyalayın ve bir Visual Studio projesine yapıştırın veya adlı bir dosyaya yapıştırın `DataflowExecutionBlocks.cs` (`DataflowExecutionBlocks.vb` Visual Basic için), ve ardından Geliştirici komut istemi penceresi Visual Studio için aşağıdaki komutu çalıştırın.  
  
 Visual C#  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowExecutionBlocks.cs**  
  
 Visual Basic  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowExecutionBlocks.vb**  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bu örnek, bir temsilci türü sağlar <xref:System.Func%602> için <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> eşzamanlı olarak veri akışı bloğu görevini gerçekleştirmek için nesne. Zaman uyumsuz olarak davranacak şekilde veri akışı bloğu etkinleştirmek için bir temsilci türü sağlar <xref:System.Func%601> veri akışı bloğu için. Bir veri akışı bloğu zaman uyumsuz olarak davranır, ancak veri akışı bloğu görevini olduğundan döndürülen <xref:System.Threading.Tasks.Task%601> nesne biter. Aşağıdaki örnek `CountBytes` yöntemi ve kullanımları [zaman uyumsuz](~/docs/csharp/language-reference/keywords/async.md) ve [await](~/docs/csharp/language-reference/keywords/await.md) işleçleri ([zaman uyumsuz](~/docs/visual-basic/language-reference/modifiers/async.md) ve [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) içinde Zaman uyumsuz olarak sağlanan dosyadaki sıfır bayt toplam sayısını hesaplamak için visual Basic). <xref:System.IO.FileStream.ReadAsync%2A> Yöntemi dosya okuma işlemi zaman uyumsuz olarak gerçekleştirir.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#2)]
 [!code-vb[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#2)]  
  
 Bir yürütme veri akışı bloğunda eylemi gerçekleştirmek için zaman uyumsuz lambda ifadeleri de kullanabilirsiniz. Aşağıdaki örnek <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> böylece iş zaman uyumsuz olarak gerçekleştirmek için bir lambda ifadesi kullanır, önceki örnekte kullanılan nesne.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#3)]
 [!code-vb[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
