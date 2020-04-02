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
ms.openlocfilehash: 623466e0e960ea991ae92e5de432171b70bad1d2
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588628"
---
# <a name="merge-options-in-plinq"></a>PLINQ'te Birleştirme Seçenekleri
Bir sorgu paralel olarak yürütüldüğünde, PLINQ kaynak sırasını bölümler, böylece birden çok iş parçacığı genellikle ayrı iş parçacıkları üzerinde olmak üzere farklı parçalar üzerinde aynı anda çalışabilir. Sonuçlar bir iş parçacığı üzerinde tüketilecekse, `foreach` örneğin, (Visual`For Each` Basic'te) bir döngüde, her iş parçacığının sonuçları tek bir dizide birleştirilmelidir. PLINQ'un gerçekleştirdiği birleştirme türü, sorguda bulunan işleçlere bağlıdır. Örneğin, sonuçlara yeni bir düzen getiren işleçlerin tüm iş parçacıklarındaki tüm öğeleri arabelleğe alması gerekir. Tüketen iş parçacığı (aynı zamanda uygulama kullanıcısının) perspektifinden, tam arabelleğe alan bir sorgu, ilk sonucunu üretmeden önce fark edilir bir süre boyunca çalışabilir. Diğer işleçler, varsayılan olarak, kısmen arabelleğe alınır; sonuçlarını toplu olarak verirler. Bir işleç, <xref:System.Linq.ParallelEnumerable.ForAll%2A> varsayılan olarak arabelleğe alınmaz. Tüm iş parçacıklarından tüm öğeleri hemen verir.  
  
 <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> Aşağıdaki örnekte gösterildiği gibi yöntemi kullanarak PLINQ'a ne tür bir birleştirme gerçekleştireceklerini gösteren bir ipucu sağlayabilirsiniz.  
  
 [!code-csharp[PLINQ#26](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#26)]
 [!code-vb[PLINQ#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#26)]  
  
 Tam örnek için [bkz: PLINQ'da Birleştirme Seçeneklerini Belirtin.](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)  
  
 Belirli bir sorgu istenen seçeneği destekleyemiyorsa, seçenek yalnızca yoksayılır. Çoğu durumda, PLINQ sorgusu için birleştirme seçeneği belirtmeniz gerekmez. Ancak, bazı durumlarda, bir sorgunun varsayılan olmayan bir modda en iyi şekilde yürütüldettiğini sınayabilir ve ölçebilirsiniz. Bu seçeneğin yaygın kullanımı, daha duyarlı bir kullanıcı arabirimi sağlamak için bir yığın birleştirme işlecinin sonuçlarını akışa zorlamaktır.  
  
## <a name="parallelmergeoptions"></a>ParallelMergeOptions  
 Numaralandırma, <xref:System.Linq.ParallelMergeOptions> desteklenen sorgu şekilleri için, sonuçlar tek bir iş parçacığı üzerinde tüketildiğinde sorgunun son çıktısının nasıl veriş olduğunu belirten aşağıdaki seçenekleri içerir:  
  
- `Not Buffered`  
  
     Bu <xref:System.Linq.ParallelMergeOptions.NotBuffered> seçenek, işlenen her öğenin üretilir üretilmez her iş parçacığından döndürülmeye neden olur. Bu davranış, çıktıyı "akış" ile benzer. <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> İşleç sorguda varsa, `NotBuffered` kaynak öğelerin sırasını korur. Kullanılabilir `NotBuffered` oldukları anda sonuç vermeye başlasa da, tüm sonuçları üretmek için gereken toplam süre diğer birleştirme seçeneklerinden birini kullanmaktan daha uzun olabilir.  
  
- `Auto Buffered`  
  
     Seçenek, <xref:System.Linq.ParallelMergeOptions.AutoBuffered> sorgunun öğeleri arabelleğe toplamasına ve arabellek içeriğini düzenli aralıklarla tüketen iş parçacığına aynı anda teslim almasına neden olur. Bu, kaynak verilerin "akış" davranışını `NotBuffered`kullanmak yerine "yığınlar" halinde veri vermeye benzer. `AutoBuffered`tüketen iş `NotBuffered` parçacığı üzerinde ilk öğeyi kullanılabilir hale getirmek için daha uzun sürebilir. Arabelleğin boyutu ve tam verimli davranış yapılandırılamaz ve sorguyla ilgili çeşitli etkenlere bağlı olarak değişebilir.  
  
- `FullyBuffered`  
  
     Seçenek, <xref:System.Linq.ParallelMergeOptions.FullyBuffered> öğelerden herhangi biri verilmeden önce tüm sorgunun çıktısının arabelleğe alınmasına neden olur. Bu seçeneği kullandığınızda, ilk öğenin tüketen iş parçacığında kullanılabilir olması daha uzun sürebilir, ancak tam sonuçlar diğer seçenekleri kullanmaktan daha hızlı üretilebilir.  
  
## <a name="query-operators-that-support-merge-options"></a>Birleştirme Seçeneklerini Destekleyen Sorgu Operatörleri  
 Aşağıdaki tablo, belirtilen kısıtlamalara tabi olarak tüm birleştirme seçeneği modlarını destekleyen işleçleri listeler.  
  
|İşleç|Kısıtlamalar|  
|--------------|------------------|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|None|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|None|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Yalnızca Bir Dizi veya Liste kaynağı olan sıralı olmayan sorgular.|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|None|  
|<xref:System.Linq.ParallelEnumerable.OfType%2A>|None|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Yalnızca Bir Dizi veya Liste kaynağı olan sıralı olmayan sorgular.|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|None|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|None|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|None|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|None|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|None|  
  
 Diğer tüm PLINQ sorgu işleçleri, kullanıcı tarafından sağlanan birleştirme seçeneklerini yok sayabilir. Örneğin, bazı sorgu <xref:System.Linq.ParallelEnumerable.Reverse%2A> işleçleri, <xref:System.Linq.ParallelEnumerable.OrderBy%2A>tümü üretilene ve yeniden sıralanana kadar herhangi bir öğe veremez. Bu nedenle, <xref:System.Linq.ParallelMergeOptions> aynı zamanda bir işleç içeren <xref:System.Linq.ParallelEnumerable.Reverse%2A>bir sorgukullanıldığında , birleştirme davranışı bu işleç sonuçlarını üretilene kadar sorguda uygulanmaz.  
  
 Bazı işleçlerin birleştirme seçeneklerini işleme yeteneği kaynak dizinin türüne ve <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> işlecinin sorguda daha önce kullanılıp kullanılmadığına bağlıdır. <xref:System.Linq.ParallelEnumerable.ForAll%2A>her <xref:System.Linq.ParallelMergeOptions.NotBuffered> zaman ; elemanlarını hemen verir. <xref:System.Linq.ParallelEnumerable.OrderBy%2A>her <xref:System.Linq.ParallelMergeOptions.FullyBuffered>zaman ; verim vermeden önce tüm listeyi sıralamalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
- [Nasıl yapılır: PLINQ'te Birleştirme Seçeneklerini Belirtme](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)
