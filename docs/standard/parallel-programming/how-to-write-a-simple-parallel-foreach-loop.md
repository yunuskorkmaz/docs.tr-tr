---
title: 'Nasıl yapılır: Basit bir Parallel.ForEach Döngüsü Yazma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
caps.latest.revision: 19
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 90b900bf98ab664e0fce5c70573f01e044d70803
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a>Nasıl yapılır: Basit bir Parallel.ForEach Döngüsü Yazma
Bu örnek nasıl kullanılacağını gösteren bir <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> veri paralelliği herhangi etkinleştirmek için döngü <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> veri kaynağı.  
  
> [!NOTE]
>  Bu belge lambda ifadeleri temsilciler PLINQ'te tanımlamak için kullanır. C# veya Visual Basic'deki lambda ifadeleri alışık değilseniz bkz [PLINQ ve TPL'deki Lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
 [!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]  
  
 A <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngü çalışır gibi bir <xref:System.Threading.Tasks.Parallel.For%2A> döngü. Kaynak koleksiyonu bölümlenmiş ve sistem ortamına bağlı birden çok iş parçacığı üzerinde çalışma zamanlanır. Daha fazla işlemci sistemdeki paralel yöntemi daha hızlı çalışır. Bazı kaynak koleksiyonlar için sıralı döngü hızlı, kaynak ve gerçekleştirilen iş türünü boyutuna bağlı olarak olabilir. Performansı hakkında daha fazla bilgi için bkz: [veri ve görev Paralelliğinde olası Tuzaklar](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)  
  
 Paralel döngüler hakkında daha fazla bilgi için bkz: [nasıl yapılır: basit bir Parallel.For döngüsü yazma](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).  
  
 Kullanılacak <xref:System.Threading.Tasks.Parallel.ForEach%2A> genel olmayan koleksiyonu ile kullandığınız <xref:System.Linq.Enumerable.Cast%2A> genişletme yöntemi aşağıdaki örnekte gösterildiği gibi genel bir koleksiyon için koleksiyon dönüştürmek için:  
  
 [!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
 [!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]  
  
 Paralel LINQ (PLINQ) işlenmesini paralel hale kullanabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> veri kaynakları. PLINQ döngü davranışı ifade etmek için bildirim temelli sorgu söz dizimi kullanmanıza olanak sağlar. Daha fazla bilgi için bkz: [paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Bu kodu kopyalayıp bir Visual Studio 2010 konsol uygulaması projesine yapıştırın.  
  
-   System.Drawing.dll bir başvuru ekleyin  
  
-   F5 tuşuna basın  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)  
 [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
