---
title: "Veri Paralelliği (Görev Paralel Kitaplığı)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: parallelism, data
ms.assetid: 3f05f33f-f1da-4b16-81c2-9ceff1bef449
caps.latest.revision: "25"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 13788542fa368bd5bcf1c2f277c9d83f84b35cdb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="data-parallelism-task-parallel-library"></a>Veri Paralelliği (Görev Paralel Kitaplığı)
*Veri paralelliği* , aynı işlemi gerçekleştirilir eşzamanlı olarak senaryoları için ifade eder (diğer bir deyişle, içinde paralel) bir kaynak koleksiyonu veya dizideki öğeler üzerinde. Böylece birden çok iş parçacığı farklı parçaları üzerinde aynı anda çalışabilir verileri paralel işlemlerinde kaynak koleksiyonu bölümlenmiş.  
  
 Görev paralel kitaplığı (TPL) aracılığıyla veri paralelliği destekleyen <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> sınıfı. Bu sınıf yöntemi tabanlı paralel uygulamaları sağlar [için](~/docs/csharp/language-reference/keywords/for.md) ve [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) döngüleri (`For` ve `For Each` Visual Basic'te). Döngü mantığı için yazma bir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> veya <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> sıralı bir döngü yazmak istediğiniz kadar döngü. İş parçacığı oluşturabilir veya iş öğeleri kuyruğa gerekmez. Temel Döngülerde kilitleri olması gerekmez. TPL tüm alt düzey işini sizin için gerçekleştirir. Kullanımı hakkında ayrıntılı bilgi için <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>, belge indirme [paralel programlama desenleri: anlama ve .NET Framework 4 paralel desenlerle uygulama](http://www.microsoft.com/download/details.aspx?id=19222). Aşağıdaki kod örneği, basit bir gösterir `foreach` döngü ve paralel eşdeğeri.  
  
> [!NOTE]
>  TPL'de temsilciler tanımlamak için bu belgede lambda ifadeleri kullanılır. C# veya Visual Basic'deki lambda ifadeleri alışık değilseniz bkz [PLINQ ve TPL'deki Lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 [!code-csharp[TPL#20](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#20)]
 [!code-vb[TPL#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#20)]  
  
 Ne zaman paralel döngü çalıştırır, TPL bölümler veri kaynağı böylece döngü birden çok bölüm üzerinde aynı anda çalışabilir. Arka planda, Görev Zamanlayıcı'yı sistem kaynakları ve iş yükü göre görev bölümler. Mümkün olduğunda, iş yükü tutarsız hale gelirse Zamanlayıcı İş birden çok iş parçacığı ve işlemciler arasında yeniden dağıtır.  
  
> [!NOTE]
>  Ayrıca, kendi özel bölümleyici veya Zamanlayıcı belirtebilirsiniz. Daha fazla bilgi için bkz: [PLINQ ve TPL için özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md) ve [görev zamanlayıcılar](http://msdn.microsoft.com/library/638f8ea5-21db-47a2-a934-86e1e961bf65).  
  
 Hem <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> yöntemleri, durdurmak veya döngü yürütmeyi kesme, başka bir iş parçacığı üzerinde döngü durumunu izlemek, iş parçacığı yerel durumunu korumak, iş parçacığı yerel nesneleri Sonlandır, eşzamanlılık, derecesini kontrol olanak sağlayan birçok aşırı yüklemeye sahip ve benzeri. Bu işlevselliği etkinleştirmek yardımcı türler <xref:System.Threading.Tasks.ParallelLoopState>, <xref:System.Threading.Tasks.ParallelOptions>, <xref:System.Threading.Tasks.ParallelLoopResult>, <xref:System.Threading.CancellationToken>, ve <xref:System.Threading.CancellationTokenSource>.  
  
 Daha fazla bilgi için bkz: [, desenleri paralel programlama](http://go.microsoft.com/fwlink/p/?LinkId=265491).  
  
 Veri paralelliği bildirim temelli veya sorgu benzeri sözdizimi ile PLINQ tarafından desteklenir. Daha fazla bilgi için bkz: [paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: basit bir Parallel.For döngüsü yazma](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)|Nasıl yazılacağını açıklar bir <xref:System.Threading.Tasks.Parallel.For%2A> döngü bir dizisi üzerinden ya da dizine <xref:System.Collections.Generic.IEnumerable%601> kaynak koleksiyonu.|  
|[Nasıl yapılır: basit bir Parallel.ForEach döngüsü yazma](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-foreach-loop.md)|Nasıl yazılacağını açıklar bir <xref:System.Threading.Tasks.Parallel.ForEach%2A> herhangi döngü <xref:System.Collections.Generic.IEnumerable%601> kaynak koleksiyonu.|  
|[Nasıl yapılır: durdurun ya da bir Parallel.For döngüden bölün](http://msdn.microsoft.com/en-us/de52e4f1-9346-4ad5-b582-1a4d54dc7f7e)|Böylece tüm iş parçacıklarının eylemini bildirilir paralel bir döngüden bölün veya durdurmak açıklar.|  
|[Nasıl yapılır: iş parçacığı yerel değişkenleriyle bir Parallel.For döngüsü yazma](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)|Nasıl yazılacağını açıklar bir <xref:System.Threading.Tasks.Parallel.For%2A> döngü her iş parçacığı başka bir iş parçacığı ve döngü tamamlandığında tüm iş parçacıklarının sonuçlarından eşitlemeye nasıl görünür değil özel bir değişkene korur.|  
|[Nasıl yapılır: iş parçacığı yerel değişkenleriyle bir Parallel.ForEach döngüsü yazma](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-thread-local-variables.md)|Nasıl yazılacağını açıklar bir <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngü her iş parçacığı başka bir iş parçacığı ve döngü tamamlandığında tüm iş parçacıklarının sonuçlarından eşitlemeye nasıl görünür değil özel bir değişkene korur.|  
|[Nasıl yapılır: bir Parallel.For veya ForEach döngüsünü iptal etme](../../../docs/standard/parallel-programming/how-to-cancel-a-parallel-for-or-foreach-loop.md)|Paralel bir döngüden kullanarak iptal etmeyi açıklar bir<xref:System.Threading.CancellationToken?displayProperty=nameWithType>|  
|[Nasıl yapılır: küçük döngü gövdelerini hızlandırma](../../../docs/standard/parallel-programming/how-to-speed-up-small-loop-bodies.md)|Döngü gövdesine çok küçük olduğunda yürütmesini kurma hızı yollarından biri açıklanır.|  
|[Görev paralel kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Görev paralel kitaplığı genel bir bakış sağlar.|  
|[Paralel Programlama](../../../docs/standard/parallel-programming/index.md)|.NET Framework'te paralel programlama tanıtır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
