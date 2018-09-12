---
title: 'Nasıl yapılır: Basit bir Parallel.ForEach Döngüsü Yazma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03aaae7cd0faa7e7628da2e2e8f622f0967102cf
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44494154"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a>Nasıl yapılır: Basit bir Parallel.ForEach Döngüsü Yazma
Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> veri paralelliği herhangi birini etkinleştirmek için döngü <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> veri kaynağı.  
  
> [!NOTE]
>  Bu belgede lambda ifadeleri PLINQ'te temsilciler tanımlamak için kullanılır. C# veya Visual Basic'te lambda ifadelerine aşina değilseniz bkz [PLINQ ve TPL'deki Lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
 [!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]  
  
 A <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngü çalışır gibi bir <xref:System.Threading.Tasks.Parallel.For%2A> döngü. Kaynak koleksiyonu bölümlenen ve sistem ortama bağlı birden çok iş parçacığında iş zamanlanır. Daha fazla işlemci sistem üzerinde paralel yöntemi daha hızlı çalışır. Bazı kaynak koleksiyonları için hızlı, kaynak ve gerçekleştirilmekte olan iş türünü boyutuna bağlı olarak sıralı bir döngü olabilir. Performans hakkında daha fazla bilgi için bkz: [veri ve görev Paralelliğinde olası Tuzaklar](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)  
  
 Paralel döngüler hakkında daha fazla bilgi için bkz: [nasıl yapılır: basit bir Parallel.For döngüsü yazma](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).  
  
 Kullanılacak <xref:System.Threading.Tasks.Parallel.ForEach%2A> kullanabileceğiniz bir genel olmayan koleksiyonu ile <xref:System.Linq.Enumerable.Cast%2A> genişletme yöntemi, aşağıdaki örnekte gösterildiği gibi genel bir koleksiyon için koleksiyon dönüştürmek için:  
  
 [!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
 [!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]  
  
 Paralel LINQ (PLINQ) işlenmesini paralel hale getirmek için de kullanabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> veri kaynakları. PLINQ, döngü davranışı ifade etmek için bildirim temelli bir sorgu söz dizimi kullanmanıza olanak sağlar. Daha fazla bilgi için [paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Bu kodu kopyalayıp bir Visual Studio 2010 konsol uygulaması projesine yapıştırın.  
  
-   System.Drawing.dll bir başvuru ekleyin  
  
-   F5 tuşuna basın  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)  
- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
