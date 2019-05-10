---
title: PLINQ'te Birleştirme Seçenekleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, merge options
ms.assetid: e8f7be3b-88de-4f33-ab14-dc008e76c1ba
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7255ef11bfdf74afa6ae2032b0c86c8c44dbfe7d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647736"
---
# <a name="merge-options-in-plinq"></a>PLINQ'te Birleştirme Seçenekleri
Birden çok iş parçacığı üzerinde farklı bölümleri aynı anda genellikle ayrı iş parçacıklarına çalışabilmek ne zaman bir sorgu paralel, PLINQ bölümler kaynak sırası yürütüyor. Sonuçları bir iş parçacığı üzerinde kullanılması, örneğin, bir `foreach` (`For Each` Visual Basic'te) döngü sonra her iş parçacığı sonuçlardan bir dizisi olarak birleştirilmesi gerekir. PLINQ gerçekleştiren bir birleştirme türü, sorguda bulunan işleçleri bağlıdır. Örneğin, yeni bir sipariş sonuçlarına dayatır işleçleri tüm iş parçacıklarının tüm öğeleri arabellek gerekir. (Aynı zamanda olan, uygulama kullanıcısı) kullanan bir iş parçacığı açısından bir belirgin süre ilk sonucunu üreten önce tamamen arabelleğe alınan sorgu çalıştırabilirsiniz. Diğer işleçler varsayılan olarak, kısmen ara belleğe alınır; Bunlar, toplu sonuçlar. Bir işleç <xref:System.Linq.ParallelEnumerable.ForAll%2A> varsayılan olarak arabelleğe değil. Bunu tüm öğeleri tüm iş parçacıklarından hemen verir.  
  
 Kullanarak <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> yöntemi, aşağıdaki örnekte gösterildiği gibi sağlayabileceğiniz bir ipucu birleştirmenin gerçekleştirmek için ne tür gösteren PLINQ.  
  
 [!code-csharp[PLINQ#26](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#26)]
 [!code-vb[PLINQ#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#26)]  
  
 Tam bir örnek için bkz [nasıl yapılır: PLINQ'te birleştirme seçeneklerini belirtme](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md).  
  
 Belirli bir sorgu istenen seçeneği destekleyemiyorsa seçeneği yalnızca yoksayılacak. Çoğu durumda, bir PLINQ sorgusu için bir birleştirme seçeneği belirtmeniz gerekmez. Ancak, bazı durumlarda, test etme ve bir sorgu en iyi bir varsayılan olmayan modda yürütülür ölçüm bulabilirsiniz. Bir ortak bu seçenek, sonuçları daha hızlı yanıt veren bir kullanıcı arabirimi sağlamak amacıyla akış için bir öbek birleştirme işleci zorlamak için kullanılır.  
  
## <a name="parallelmergeoptions"></a>ParallelMergeOptions  
 <xref:System.Linq.ParallelMergeOptions> Numaralandırma belirtin, desteklenen sorgu şekiller için sorgunun son çıktı sonuçları bir iş parçacığında kullanılan zaman nasıl oluşturulur aşağıdaki seçenekleri içerir:  
  
- `Not Buffered`  
  
     <xref:System.Linq.ParallelMergeOptions.NotBuffered> Seçenek neden üretilmiş hemen sonra her bir iş parçacığından döndürülecek işlenen her öğe. Bu davranış, "çıkış akış için" benzer. Varsa <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> işleci sorguda varsa `NotBuffered` kaynak öğelerin sırasını korur. Ancak `NotBuffered` başlatır, bunlara erişilebilir hemen sonra sonuçlar verir. tüm sonuçları yine de üretmek için toplam süreyi bir birleştirme seçeneklerinden birini kullanarak daha uzun.  
  
- `Auto Buffered`  
  
     <xref:System.Linq.ParallelMergeOptions.AutoBuffered> Seçeneği bir arabelleğe öğeleri toplar ve düzenli aralıklarla arabellek içeriği aynı anda tüketim iş parçacığı yield sorgu neden olur. Bu "akış" davranışı kullanmak yerine, kaynak verileri "öbekler halinde" sonuçlanmıyor için benzer `NotBuffered`. `AutoBuffered` daha uzun sürebilir `NotBuffered` ilk öğeyi alabilir iş parçacığı üzerinde kullanılabilir hale getirmek için. Arabellek boyutuna ve tam yielding davranış, yapılandırılabilir olmayan ve sorgu ile ilgili çeşitli etkenlere bağlı olarak değişebilir.  
  
- `FullyBuffered`  
  
     <xref:System.Linq.ParallelMergeOptions.FullyBuffered> Seçeneği öğelerden üretilenleri kaydeder önce arabelleğe alınan tüm sorgu çıkışına neden olur. Bu seçeneği kullandığınızda, ilk öğeyi alabilir iş parçacığı üzerinde kullanılabilir, ancak tam sonuçları hala üretilen önce daha uzun sürebilir diğer seçenekleri kullanarak daha hızlı.  
  
## <a name="query-operators-that-support-merge-options"></a>Birleştirme seçeneklerini destekleyen sorgu işleçleri  
 Aşağıdaki tabloda, belirtilen kısıtlamalara tabi tüm birleştirme seçeneği modları destekleyen işleçleri listelenmektedir.  
  
|İşleç|Kısıtlamalar|  
|--------------|------------------|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|None|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Yok.|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Bir dizi ya da liste kaynağı yalnızca sahip olmayan sıralı sorgular.|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|None|  
|<xref:System.Linq.ParallelEnumerable.OfType%2A>|None|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Bir dizi ya da liste kaynağı yalnızca sahip olmayan sıralı sorgular.|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Yok.|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|Yok.|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|Yok.|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|Yok.|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Yok.|  
  
 Diğer tüm PLINQ sorgu işleçleri, kullanıcı tarafından sağlanan birleştirme seçeneklerini yoksay. Bazı sorgu işleçleri, örneğin, <xref:System.Linq.ParallelEnumerable.Reverse%2A> ve <xref:System.Linq.ParallelEnumerable.OrderBy%2A>, tüm üretilen yeniden ve kadar herhangi bir öğe döndürülemez. Bu nedenle, <xref:System.Linq.ParallelMergeOptions> da operatörün gibi içeren bir sorguda kullanılan <xref:System.Linq.ParallelEnumerable.Reverse%2A>, işleç sonuçlarını üretmiştir sonra birleştirme davranışı sorgu kadar uygulanmaz.  
  
 Birleştirme seçeneklerini işleyebilme yeteneği bazı işleçlerinin kaynak dizisinin türüne bağlıdır ve <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> sorgu işleci kullanıldı. <xref:System.Linq.ParallelEnumerable.ForAll%2A> her zaman <xref:System.Linq.ParallelMergeOptions.NotBuffered> ; öğelerinden hemen verir. <xref:System.Linq.ParallelEnumerable.OrderBy%2A> her zaman <xref:System.Linq.ParallelMergeOptions.FullyBuffered>; bunu verir önce listesinin tümünü sıralamanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
- [Nasıl yapılır: PLINQ'te birleştirme seçeneklerini belirtme](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)
