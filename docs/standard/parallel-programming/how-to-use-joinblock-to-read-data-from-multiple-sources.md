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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a7becba9c7626e79f9d001a6a21ed92a336e9d11
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591984"
---
# <a name="how-to-use-joinblock-to-read-data-from-multiple-sources"></a>Nasıl yapılır: Birden Fazla Kaynaktan Okumak için JoinBlock'u Kullanma
Bu belgenin nasıl kullanıldığını açıklar <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> birden fazla kaynaktan veri kullanılabilir olduğunda bir işlemi gerçekleştirmek için sınıf. Ayrıca, birden çok birleştirme bloğunun bir veri kaynağını daha verimli bir şekilde paylaşmak etkinleştirmek için doyumsuz olmayan modda kullanmayı gösterir.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Örnek  
 Aşağıdaki örnek, üç kaynak türleri tanımlar `NetworkResource`, `FileResource`, ve `MemoryResource`ve kaynaklar kullanılabilir olduğunda işlemleri gerçekleştirir. Bu örnek gerektirir bir `NetworkResource` ve `MemoryResource` ilk işlemi gerçekleştirmek için çifti ve `FileResource` ve `MemoryResource` ikinci işlemi gerçekleştirmek için çifti. Bu işlemler, tüm gerekli kaynakları kullanılabilir olduğunda gerçekleşecek şekilde etkinleştirmek için bu örnekte <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> sınıfı. Olduğunda bir <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> nesne tüm kaynaklardan gelen verileri alır, bu verileri olduğundan, hedef yayar bir <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesne. Her ikisi de <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> nesneleri okumak paylaşılan havuzundan `MemoryResource` nesneleri.  
  
 [!code-csharp[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_nongreedyjoin/cs/nongreedyjoin.cs#1)]
 [!code-vb[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_nongreedyjoin/vb/nongreedyjoin.vb#1)]  
  
 Paylaşılan havuzu etkili kullanımını etkinleştirmek için `MemoryResource` nesneleri, bu örnek belirtir bir <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions> nesnesi <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> özelliğini `False` oluşturmak için <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> doyumsuz olmayan modda davranan nesneleri. Doyumsuz olmayan birleştirme bloğu, her bir kaynaktan bir kullanılabilir hale gelene kadar gelen tüm iletileri ertelemesi. Birleştirme bloğu Ertelenen iletilerden birini başka bir bloğu tarafından kabul edilmedi, işlemi yeniden başlatır. Doyumsuz olmayan mod diğer bloklardan tamamlanmasını bekleyen veri için ilerleme gerçekleştirmek için bir veya daha fazla kaynak bloklar paylaşan birleştirme bloğunun sağlar. Bu örnekte, varsa bir `MemoryResource` eklenir `memoryResources` havuz, birinci, ikinci bir veri kaynağı almak için blok ilerleme yapabilirsiniz. Bir birleştirme bloğu varsayılan olan doyumsuz modda kullanmak için bu örnek olsaydı, sürebilir `MemoryResource` nesne ve ikinci bir kaynak kullanılabilir olana kadar bekleyin. Bir birleştirme bloğu kendi ikinci veri kaynağı varsa, ancak bunu ilerleme çünkü yapamazsınız `MemoryResource` nesne bir birleştirme bloğu tarafından alınmış.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Doyumsuz olmayan birleştirmeler kullanımını da uygulamanızdaki kilitlenme önlemenize yardımcı olabilir. Bir yazılım uygulamasındaki *kilitlenme* iki veya daha fazla işlem her bir kaynak basılı tutun ve karşılıklı olarak başka bir kaynağı serbest bırakmak başka bir işlemin tamamlanmasını beklemek oluşur. İki tanımlayan bir uygulama düşünün <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> nesneleri. Her iki nesne iki paylaşılan kaynak bloklardan verileri okuyamadı. Doyumsuz modda, bir birleştirme bloğu ilk kaynağından okur ve her ikisi birbirini blokları katılmak için ikinci birleştirme bloğu ikinci kaynağından okur uygulama kilitlenebilir diğer kaynağı serbest bırakmak bekleyin. Doyumsuz olmayan modda, yalnızca tüm veriler kullanılabilir olduğunda, kaynakları ve bu nedenle, kilitlenme riski okumalardan her birleştirme bloğu ortadan kalkar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
