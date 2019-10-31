---
title: "Nasıl yapılır: Birden Fazla Kaynaktan Okumak için JoinBlock'u Kullanma"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, joining blocks in
- dataflow blocks, joining in TPL
ms.assetid: e9c1ada4-ac57-4704-87cb-2f5117f8151d
ms.openlocfilehash: 66fd7ed7a98b8be8f88f65ecb52710a1e40af778
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139743"
---
# <a name="how-to-use-joinblock-to-read-data-from-multiple-sources"></a>Nasıl yapılır: Birden Fazla Kaynaktan Okumak için JoinBlock'u Kullanma
Bu belgede, verileri birden çok kaynaktan kullanılabilir olduğunda bir işlemi gerçekleştirmek için <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> sınıfının nasıl kullanılacağı açıklanmaktadır. Ayrıca, birden çok JOIN bloklarının bir veri kaynağını daha verimli bir şekilde paylaşmasını sağlamak için doyumsuz olmayan modu nasıl kullanacağınızı gösterir.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Örnek  
 Aşağıdaki örnek üç kaynak türünü tanımlar, `NetworkResource`, `FileResource`ve `MemoryResource`ve kaynakları kullanılabilir hale geldiğinde işlemleri gerçekleştirir. Bu örnekte, ikinci işlemi gerçekleştirmek için ilk işlemi ve bir `FileResource` ve `MemoryResource` çiftini gerçekleştirmek üzere bir `NetworkResource` ve `MemoryResource` çifti gerekir. Tüm gerekli kaynaklar kullanılabilir olduğunda bu işlemlerin gerçekleşmesini sağlamak için, bu örnek <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> sınıfını kullanır. Bir <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> nesnesi tüm kaynaklardaki verileri aldığında, bu verileri hedefine yayar, bu örnekte bir <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesnesidir. Her iki <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> nesnesi de `MemoryResource` nesnelerden oluşan paylaşılan havuzdan okundu.  
  
 [!code-csharp[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_nongreedyjoin/cs/nongreedyjoin.cs#1)]
 [!code-vb[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_nongreedyjoin/vb/nongreedyjoin.vb#1)]  
  
 `MemoryResource` nesnelerinin paylaşılan havuzunun verimli kullanımını sağlamak için bu örnek, <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> özelliği, doyumsuz olmayan modda davranan <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> nesneleri oluşturmak için `False` olarak ayarlanmış bir <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions> nesnesini belirtir. Doyumsuz olmayan bir JOIN bloğu, her kaynaktan bir tane kullanılabilir olana kadar gelen tüm iletileri erteler. Ertelenen iletilerden herhangi biri başka bir blok tarafından kabul edildiyse, JOIN bloğu işlemi yeniden başlatır. Doyumsuz olmayan mod, diğer blokların veri beklemesi durumunda ileri ilerleme durumuna getirmek için bir veya daha fazla kaynak bloğunu paylaşan JOIN blokları sağlar. Bu örnekte, `memoryResources` havuzuna bir `MemoryResource` nesnesi eklenirse, ikinci veri kaynağını almak için ilk JOIN bloğu ilerlemeye devam edebilir. Bu örnek, varsayılan olan doyumsuz modunu kullanıyorsa, tek bir JOIN bloğu `MemoryResource` nesnesini alabilir ve ikinci kaynağın kullanılabilir hale gelmesini bekleyebilir. Ancak, diğer bir JOIN bloğunun ikinci veri kaynağı varsa, `MemoryResource` nesnesi diğer bir JOIN bloğu tarafından alındığından ileri ilerleme yapamaz.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Doyumsuz olmayan birleşimlerin kullanımı uygulamanızda kilitlenmeyi önlemenize de yardımcı olabilir. Bir yazılım uygulamasında, iki veya daha fazla işlem bir kaynağı her tutar ve başka bir işlemin başka bir kaynağı serbest bırakma işlemini karşılıklı olarak beklemek durumunda *kilitlenme* oluşur. İki <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> nesnesini tanımlayan bir uygulama düşünün. Her iki nesnenin her ikisi de iki paylaşılan kaynak blobundan okur. Doyumsuz modunda, bir JOIN bloğunun ilk kaynaktan okuduğu ve ikinci kaynaktan ikinci bir JOIN bloğunun okuduğu, uygulama kilitlenmeye neden olabileceğinden, her iki JOIN bloğu, kaynağını serbest bırakmalarını karşılıklı olarak bekler. Doyumsuz olmayan modda, her bir JOIN bloğu kaynaklarından yalnızca tüm veriler kullanılabilir olduğunda okur ve bu nedenle, kilitlenme riski ortadan kalkar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
