---
title: "Nasıl yapılır: Üretici-Tüketici Veri Akışı Düzeni Uygulama"
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
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
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3758ec77a722a66c6faa287d299e5e9c38858be5
ms.sourcegitcommit: 6a9030eb5bd0f00e1d144f81958adb195cfb1f6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a>Nasıl yapılır: Üretici-Tüketici Veri Akışı Düzeni Uygulama
Bu belge TPL veri akışı kitaplığı üretici-tüketici düzeni uygulama için nasıl kullanılacağını açıklar. Bu modelde *üretici* ileti bloğu iletileri gönderir ve *tüketici* bu bloğundan iletileri okur.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, veri akışı kullanan bir temel üretici-tüketici modeli gösterir. `Produce` Yöntemi Yazar rastgele bayt veri içeren diziler bir <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType> nesne ve `Consume` yöntemi okur bayt, kaynağı bir <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType> nesnesi. Üzerinde davranarak <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> ve <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> kendi türetilmiş türler yerine arabirimleri çeşitli veri akışı bloğu türlerini davranamaz yeniden kullanılabilir kod yazabilirsiniz. Bu örnekte <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> sınıfı. Çünkü <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> hem bir kaynak sınıfı görür engelleme ve hedef blok üretici ve tüketici paylaşılan bir nesnenin veri aktarmak için kullanabilirsiniz.  
  
 `Produce` Yöntem çağrılarını <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> zaman uyumlu olarak hedef blok veri yazmak için bir döngü yöntemi. Sonra `Produce` yöntemi Yazar tüm verilerin hedef bloğuna çağırır <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> blok hiçbir zaman ek veriler kullanılabilir olduğunu belirtmek için yöntem. `Consume` Yöntemi kullanan [zaman uyumsuz](~/docs/csharp/language-reference/keywords/async.md) ve [await](~/docs/csharp/language-reference/keywords/await.md) işleçleri ([zaman uyumsuz](~/docs/visual-basic/language-reference/modifiers/async.md) ve [bekleme](~/docs/visual-basic/language-reference/operators/await-operator.md) içinde [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) için Toplam alınan bayt sayısı zaman uyumsuz işlem <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> nesne. Zaman uyumsuz olarak davranacak şekilde `Consume` yöntem çağrılarını <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> kaynak blok verileri kullanılabilir ve kaynak blok hiçbir zaman ek veriler kullanılabilir olduğunda olduğunda bir bildirim almak için yöntem.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Örnek kodu kopyalayın ve bir Visual Studio projesi yapıştırın veya adlı bir dosyaya yapıştırın `DataflowProducerConsumer.cs` (`DataflowProducerConsumer.vb` için [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), ve ardından Visual Studio komut istemi penceresinde aşağıdaki komutu çalıştırın.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowProducerConsumer.vb**  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bu örnek yalnızca tek bir tüketici kaynak verileri işlemek için kullanır. Birden çok tüketiciye uygulamanızda varsa, <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> yöntemi aşağıdaki örnekte gösterildiği gibi kaynak bloğundan veri okunamıyor.  
  
 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]  
  
 <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> Yöntemi döndürür `False` hiçbir veri olduğunda kullanılabilir. Birden çok tüketiciye eşzamanlı olarak kaynak blok erişmesi gerektiğinde bu mekanizma veri çağrısından sonra hala kullanılabilir olduğunu garanti <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
