---
title: 'Nasıl yapılır: Veri Akışı Bloğuna İletiler Yazma ve Veri Akışı Bloğundan İletiler Okuma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, reading and writing messages
ms.assetid: 1a9bf078-aa82-46eb-b95a-f87237f028c5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47a61a1d01984eeefb2f1f09774374dc29a774d3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44039231"
---
# <a name="how-to-write-messages-to-and-read-messages-from-a-dataflow-block"></a>Nasıl yapılır: Veri Akışı Bloğuna İletiler Yazma ve Veri Akışı Bloğundan İletiler Okuma
Bu belge, TPL veri akışı kitaplığı nasıl yazılacağını ve veri akışı bloğundan iletiler okuma için kullanmayı açıklar. TPL veri akışı kitaplığı, ileti ve veri akışı bloğu okuma iletileri yazmak için zaman uyumlu ve zaman uyumsuz yöntemler sağlar. Bu belgeyi kullanan <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType> sınıfı. <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> Sınıfı iletileri arabelleğe alır ve her iki ileti kaynağı olarak ve bir ileti hedefi olarak davranır.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="writing-to-and-reading-from-a-dataflow-block-synchronously"></a>Veri akışı bloğundan zaman uyumlu olarak okuma ve yazma  
 Aşağıdaki örnekte <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> yazılacak yöntemi bir <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> veri akışı bloğu ve <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> aynı nesneden okumak için yöntem.  
  
 [!code-csharp[TPLDataflow_ReadWrite#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#2)]
 [!code-vb[TPLDataflow_ReadWrite#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#2)]  
  
 Ayrıca <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> aşağıdaki örnekte gösterildiği gibi bir veri akışı bloğundan okumak için yöntem. <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> Yöntem geçerli iş parçacığını engellemez ve bazen verileri yoklayan olduğunda yararlıdır.  
  
 [!code-csharp[TPLDataflow_ReadWrite#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#3)]
 [!code-vb[TPLDataflow_ReadWrite#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#3)]  
  
 Çünkü <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> yöntemi davranır eş <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> nesne önceki örneklerde, ikinci döngü veri okumadan önce tüm verileri alır. Aşağıdaki örnekte ilk örnek kullanarak genişletir <xref:System.Threading.Tasks.Parallel.Invoke%2A> okuma ve ileti bloğu eşzamanlı yazma için. Çünkü <xref:System.Threading.Tasks.Parallel.Invoke%2A> eylemleri gerçekleştirir aynı anda değerleri yazılmadığına <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> herhangi belirli bir sırada nesne.  
  
 [!code-csharp[TPLDataflow_ReadWrite#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#4)]
 [!code-vb[TPLDataflow_ReadWrite#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#4)]  
  
## <a name="writing-to-and-reading-from-a-dataflow-block-asynchronously"></a>Veri akışı bloğundan zaman uyumsuz olarak okuma ve yazma  
 Aşağıdaki örnekte <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> yöntemi zaman uyumsuz olarak yazmak için bir <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> nesne ve <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> aynı nesneden zaman uyumsuz olarak okumak için yöntem. Bu örnekte [zaman uyumsuz](~/docs/csharp/language-reference/keywords/async.md) ve [await](~/docs/csharp/language-reference/keywords/await.md) işleçleri ([zaman uyumsuz](~/docs/visual-basic/language-reference/modifiers/async.md) ve [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) Visual Basic'te) zaman uyumsuz olarak veri göndermek ve okumak için hedef blok verileri. <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> Yöntemi, iletileri ertelemek bir veri akışı bloğu etkinleştirmeniz gerektiğinde kullanışlıdır. <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> Yöntemi, verilerin kullanılabilir duruma geldiğinde veri üzerinde oynama yapmak istediğinizde yararlıdır. İleti geçirme bölümü nasıl arasında ileti blokları ileti yayma hakkında daha fazla bilgi için bkz, [veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md).  
  
 [!code-csharp[TPLDataflow_ReadWrite#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#5)]
 [!code-vb[TPLDataflow_ReadWrite#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#5)]  
  
## <a name="a-complete-example"></a>Tam bir örnek  
 Aşağıdaki örnek, bu belge için tam kod gösterilir.  
  
 [!code-csharp[TPLDataflow_ReadWrite#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#1)]
 [!code-vb[TPLDataflow_ReadWrite#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Örnek kodu kopyalayın ve bir Visual Studio projesine yapıştırın veya adlı bir dosyaya yapıştırın `DataflowReadWrite.cs` (`DataflowReadWrite.vb` Visual Basic için), ve ardından bir Visual Studio komut istemi penceresinde aşağıdaki komutu çalıştırın.  
  
 Visual C#  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.cs**  
  
 Visual Basic  
  
 **Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReadWrite.vb**  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu örnek, bir ileti bloğu doğrudan yazma ve okuma gösterilmektedir. Veri akışı bloklarının forma bağlanabilir *işlem hatları*, veri akışı bloklarının doğrusal dizeleri veya *ağları*, veri akışı bloklarının grafikleri. Bir ardışık düzen veya ağda, kaynaklar, veriler kullanılabilir oldukça zaman uyumsuz olarak hedeflere yayarlar. Temel veri akışı işlem hattı oluşturur bir örnek için bkz: [izlenecek yol: veri akışı işlem hattı oluşturmaya](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md). Daha karmaşık bir veri akışı ağı oluşturan bir örnek için bkz [izlenecek yol: veri akışı kullanarak bir Windows Forms uygulamasındaki](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
