---
title: 'Nasıl yapılır: Paralel İşlemleri Yürütmek için Parallel.Invoke Kullanma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d0870d23c5606fbdd8b4a2f78c4d8b9f4ddc93e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44178136"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>Nasıl yapılır: Paralel İşlemleri Yürütmek için Parallel.Invoke Kullanma
Bu örnekte, işlemleri kullanarak paralel hale getirmek gösterilmektedir <xref:System.Threading.Tasks.Parallel.Invoke%2A> görev paralel Kitaplığı'nda. Üç işlemi bir paylaşılan veri kaynağı üzerinde gerçekleştirilir. İşlemlerden hiçbiri kaynak değiştirdiğinden, bunlar basit bir şekilde paralel olarak gerçekleştirilebilir.  
  
> [!NOTE]
>  TPL'de temsilciler tanımlamak için bu belgede lambda ifadeleri kullanılır. C# veya Visual Basic'te lambda ifadelerine aşina değilseniz bkz [PLINQ ve TPL'deki Lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
 [!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]  
  
 İle dikkat <xref:System.Threading.Tasks.Parallel.Invoke%2A>, eşzamanlı olarak çalıştırmak istediğiniz eylemleri yalnızca express ve çalışma zamanı zamanlama ayrıntıları, ana bilgisayarda çekirdek sayısı için otomatik olarak ölçeklendirme dahil olmak üzere tüm iş parçacığı işler.  
  
 Bu örnekte, işlemler, veri parallelizes. Alternatif bir yaklaşım PLINQ kullanarak LINQ sorgularını paralel hale getirmek ve sorguları sırayla çalışır. Alternatif olarak, PLINQ kullanarak verileri paralel. Başka bir sorgu hem görevleri paralel hale getirmek için bir seçenektir. Ortaya çıkan performans nispeten daha az sayıda işlemcilere sahip ana bilgisayarlara ek yükü azaltabilir olsa da, birçok işlemcilere sahip bilgisayarlarda çok daha iyi ölçekleyecektir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Kopyalama, örneğin tamamını Microsoft Visual Studio 2010 projesine yapıştırın ve F5 tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)  
- [Nasıl yapılır: Bir Görevi ve Alt Öğelerini İptal Etme](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)  
- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
