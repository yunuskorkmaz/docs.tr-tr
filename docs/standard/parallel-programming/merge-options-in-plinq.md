---
title: "PLINQ'te Birleştirme Seçenekleri"
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
helpviewer_keywords: PLINQ queries, merge options
ms.assetid: e8f7be3b-88de-4f33-ab14-dc008e76c1ba
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e9bf586c1805fc5b5f1cc5f96f4e6b08d80c199a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="merge-options-in-plinq"></a>PLINQ'te Birleştirme Seçenekleri
Birden çok iş parçacığı farklı bölümleri eşzamanlı olarak, genellikle ayrı iş parçacıklarına çalışabilmeniz için ne zaman bir sorgu paralel PLINQ bölümleri kaynak sıradaki yürütülüyor. Sonuçları bir iş parçacığı üzerinde tüketilmesi varsa örneğin, bir `foreach` (`For Each` içinde [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) döngü her iş parçacığı sonuçlarından bir sıralı geri birleştirilmelidir sonra. Sorguda mevcut işleçleri PLINQ gerçekleştirir birleştirme türünü bağlıdır. Örneğin, yeni bir sipariş sonuçlarını zorunlu tuttukları işleçleri tüm iş parçacıklarının tüm öğeleri arabellek gerekir. (Aynı zamanda olan, uygulama kullanıcısı) Süren iş parçacığı açısından bir belirgin süre ilk sonucu üreten önce tamamen arabelleğe alınan bir sorgu çalıştırabilirsiniz. Diğer işleçler varsayılan olarak, kısmen arabelleğe; Bunlar kendi yığınlardaki sonuçlar. Bir işleç <xref:System.Linq.ParallelEnumerable.ForAll%2A> varsayılan olarak arabelleğe değil. Bunu tüm öğeleri tüm iş parçacıklarından hemen verir.  
  
 Kullanarak <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> yöntemi, aşağıdaki örnekte gösterildiği gibi sağlayabileceğiniz bir ipucu gerçekleştirmek için birleştirmenin ne tür gösteren PLINQ.  
  
 [!code-csharp[PLINQ#26](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#26)]
 [!code-vb[PLINQ#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#26)]  
  
 Tam bir örnek için bkz: [nasıl yapılır: plınq'te birleştirme seçeneklerini belirtin](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md).  
  
 Belirli bir sorgu istenen seçeneği destekleyemiyorsa, seçeneği yalnızca yoksayılacak. Çoğu durumda, bir PLINQ sorgu için bir birleştirme seçeneği belirtmeniz gerekmez. Ancak, bazı durumlarda, test ve bir sorgu en iyi bir varsayılan olmayan modda yürütülür ölçüm tarafından bulabilirsiniz. Bir ortak bu seçeneğin sonuçlarını daha esnek bir kullanıcı arabirimi için akışını sağlamak için bir öbek birleştirme işleci zorlamak için kullanılır.  
  
## <a name="parallelmergeoptions"></a>ParallelMergeOptions  
 <xref:System.Linq.ParallelMergeOptions> Numaralandırma, desteklenen sorgu şekiller için sonuçları bir iş parçacığında kullanılan zaman sorgunun son Çıktıyı nasıl verdiğini belirtin aşağıdaki seçenekleri içerir:  
  
-   `Not Buffered`  
  
     <xref:System.Linq.ParallelMergeOptions.NotBuffered> Seçeneği, üretilen hemen her iş parçacığından döndürülecek işlenen her öğe neden olur. Bu davranış, "çıkış akış" benzerdir. Varsa <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> işlecidir sorgu, mevcut `NotBuffered` kaynak öğelerin sırasını korur. Ancak `NotBuffered` başlatır, kullanılabilir hemen sonuçları oluşturan tüm sonuçları yine üretmek için gereken toplam süre bir birleştirme seçeneklerinden birini kullanarak daha uzun.  
  
-   `Auto Buffered`  
  
     <xref:System.Linq.ParallelMergeOptions.AutoBuffered> Seçeneği bir arabelleğe öğeleri toplamak ve düzenli aralıklarla arabellek içeriği aynı anda süren iş parçacığı yield sorgu neden olur. Bu "akış" davranışını kullanmak yerine "öbek" kaynak verilerde sağlayan için benzer `NotBuffered`. `AutoBuffered`daha uzun sürebilir `NotBuffered` ilk öğe alabilir iş parçacığı üzerinde kullanılabilir hale getirmek. Arabellek boyutu tam yielding davranışı, yapılandırılabilir olmayan ve sorguya ilişkili çeşitli etkenlere bağlı olarak değişebilir.  
  
-   `FullyBuffered`  
  
     <xref:System.Linq.ParallelMergeOptions.FullyBuffered> Seçenek herhangi bir verdiğini önce arabelleğe alınan tüm sorgu çıktısı neden olur. Bu seçeneği kullandığınızda, ilk öğe alabilir iş parçacığı üzerinde kullanılabilir, ancak tüm sonuçları hala üretilen önce daha uzun sürebilir diğer seçenekleri kullanarak daha hızlı.  
  
## <a name="query-operators-that-support-merge-options"></a>Birleştirme seçeneklerini destekleyen sorgu işleçleri  
 Aşağıdaki tabloda belirtilen kısıtlamalarına tabidir tüm birleştirme seçeneği modlarını desteklemek işleçleri listeler.  
  
|İşleç|Kısıtlamalar|  
|--------------|------------------|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|Yok.|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Yok.|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Bir dizi veya liste kaynağı yalnızca sahip olmayan sıralı sorgular.|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|Yok.|  
|<xref:System.Linq.ParallelEnumerable.OfType%2A>|Yok.|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Bir dizi veya liste kaynağı yalnızca sahip olmayan sıralı sorgular.|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Yok.|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|Yok.|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|Yok.|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|Yok.|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Yok.|  
  
 Tüm diğer PLINQ sorgu işleçleri kullanıcı tarafından sağlanan birleştirme seçeneklerini yoksay. Bazı sorgu işleçleri, örneğin, <xref:System.Linq.ParallelEnumerable.Reverse%2A> ve <xref:System.Linq.ParallelEnumerable.OrderBy%2A>, tüm üretilen kaldırılmasında ve kadar herhangi bir öğe verim olamaz. Bu nedenle, <xref:System.Linq.ParallelMergeOptions> da operatörün gibi içeren bir sorguda kullanılan <xref:System.Linq.ParallelEnumerable.Reverse%2A>, işleç sonuçlarını üretilen sonra birleştirme davranışı sorgu kadar uygulanmaz.  
  
 Birleştirme seçeneklerini işleme yeteneği bazı işleçlerinin kaynak sırası türüne göre değişir ve olup <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> işleci sorgu daha önce kullanıldı. <xref:System.Linq.ParallelEnumerable.ForAll%2A>her zaman <xref:System.Linq.ParallelMergeOptions.NotBuffered> ; öğeleri hemen verir. <xref:System.Linq.ParallelEnumerable.OrderBy%2A>her zaman <xref:System.Linq.ParallelMergeOptions.FullyBuffered>; bunu verir önce tüm listeyi sıralamanız gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [Nasıl yapılır: PLINQ'te birleştirme seçeneklerini belirtme](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)
