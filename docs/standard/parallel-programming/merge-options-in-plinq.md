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
ms.openlocfilehash: a2c238cb66c5018cd1dd4085c6541ef3c9371beb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290648"
---
# <a name="merge-options-in-plinq"></a>PLINQ'te Birleştirme Seçenekleri
Bir sorgu paralel olarak yürütülerek PLıNQ, kaynak dizisini birden çok iş parçacığının aynı anda farklı parçalar üzerinde, genellikle ayrı iş parçacıklarında çalışabilmesi için bölümler. Sonuçlar bir iş parçacığında tüketilecektir (örneğin, bir `foreach` ( `For Each` Visual Basic) döngüsünde, her iş parçacığının sonuçlarının tek bir sırayla birleştirilmesi gerekir. PLıNQ tarafından gerçekleştirilen birleştirme türü sorguda bulunan işleçlere bağlıdır. Örneğin, sonuçlara yeni bir sıra uygulayan işleçler tüm iş parçacıklarından tüm öğeleri arabelleğe almalıdır. Tüketim iş parçacığının perspektifinden (aynı zamanda uygulama kullanıcısının), tam olarak arabelleğe alınmış bir sorgu, ilk sonucunu oluşturmadan önce fark edilebilir bir süre için çalıştırılabilir. Diğer işleçler, varsayılan olarak kısmen arabelleğe alınır; sonuçları toplu işlerle sonuçlarlar. Bir işleç, <xref:System.Linq.ParallelEnumerable.ForAll%2A> Varsayılan olarak ara belleğe alınmadı. Tüm iş parçacıklarından tüm öğeleri hemen oluşturur.  
  
 <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A>Yöntemini kullanarak, aşağıdaki örnekte gösterildiği gibi, PLıNQ için ne tür birleştirme yapılacağını belirten bir ipucu sağlayabilirsiniz.  
  
 [!code-csharp[PLINQ#26](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#26)]
 [!code-vb[PLINQ#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#26)]  
  
 Tüm örnek için bkz. [nasıl yapılır: PLıNQ 'Te birleştirme seçeneklerini belirtme](how-to-specify-merge-options-in-plinq.md).  
  
 Belirli bir sorgu istenen seçeneği desteklenemez, bu durumda seçenek yalnızca yok sayılır. Çoğu durumda, PLıNQ sorgusu için bir birleştirme seçeneği belirtmeniz gerekmez. Ancak, bazı durumlarda bir sorgunun varsayılan olmayan bir modda en iyi şekilde yürütüldüğünü test ederek ve ölçüyle fark edebilirsiniz. Bu seçeneğin yaygın kullanımı, bir öbek birleştirme işlecinin, daha fazla yanıt veren bir kullanıcı arabirimi sağlamak için sonuçlarını akışını zorlamaktır.  
  
## <a name="parallelmergeoptions"></a>ParallelMergeOptions  
 <xref:System.Linq.ParallelMergeOptions>Sabit listesi, desteklenen sorgu şekilleri için, sonuçları bir iş parçacığında kullanılırken sorgunun son çıkışının nasıl yapılacağını belirten aşağıdaki seçenekleri içerir:  
  
- `Not Buffered`  
  
     Seçeneği, her bir <xref:System.Linq.ParallelMergeOptions.NotBuffered> işlenen öğenin, üretildiğinde her iş parçacığından döndürülmesini sağlar. Bu davranış, çıktıyı "akışa alma" ile benzerdir. <xref:System.Linq.ParallelEnumerable.AsOrdered%2A>Sorguda işleç varsa, `NotBuffered` kaynak öğelerin sırasını korur. `NotBuffered`, Sonuçları kullanılabilir duruma geldiğinde ortaya almaya başlasa da, tüm sonuçların üretilmesi için geçen toplam süre, diğer birleştirme seçeneklerinden birini kullanmaktan daha uzun olabilir.  
  
- `Auto Buffered`  
  
     Bu <xref:System.Linq.ParallelMergeOptions.AutoBuffered> seçenek sorgunun öğeleri bir arabelleğe toplamasına ve sonra düzenli aralıklarla arabellek içeriklerini tek seferde tüketim iş parçacığına getirmesine neden olur. Bu, kaynak verileri "akış" davranışının kullanılması yerine "parçalar" halinde ortaya yüklemeye benzer `NotBuffered` . `AutoBuffered``NotBuffered`ilk öğeyi tüketim iş parçacığında kullanılabilir hale getirmek daha uzun sürebilir. Arabelleğin boyutu ve kesin hale göre davranışı yapılandırılabilir değildir ve sorguyla ilgili çeşitli faktörlere bağlı olarak farklılık gösterebilir.  
  
- `FullyBuffered`  
  
     <xref:System.Linq.ParallelMergeOptions.FullyBuffered>Seçeneği, herhangi bir öğeden herhangi biri alınmadan önce tüm sorgunun çıkışının arabelleğe alınmasına neden olur. Bu seçeneği kullandığınızda, ilk öğe tüketim iş parçacığında kullanılabilir olmadan önce daha uzun sürebilir, ancak tüm sonuçlar yine de diğer seçenekler kullanılarak daha hızlı oluşturulabilir.  
  
## <a name="query-operators-that-support-merge-options"></a>Birleştirme seçeneklerini destekleyen sorgu Işleçleri  
 Aşağıdaki tabloda, belirtilen kısıtlamalara tabi olan tüm birleştirme seçeneği modlarını destekleyen işleçler listelenmektedir.  
  
|Operatör|Kısıtlamalar|  
|--------------|------------------|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|Hiçbiri|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Hiçbiri|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Yalnızca bir dizi veya liste kaynağına sahip sıralı olmayan sorgular.|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|Hiçbiri|  
|<xref:System.Linq.ParallelEnumerable.OfType%2A>|Hiçbiri|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Yalnızca bir dizi veya liste kaynağına sahip sıralı olmayan sorgular.|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Hiçbiri|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|Hiçbiri|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|Hiçbiri|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|Hiçbiri|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Hiçbiri|  
  
 Tüm diğer PLıNQ sorgu işleçleri Kullanıcı tarafından sağlanmış birleştirme seçeneklerini yok sayabilir. Örneğin, ve gibi bazı sorgu işleçleri <xref:System.Linq.ParallelEnumerable.Reverse%2A> , <xref:System.Linq.ParallelEnumerable.OrderBy%2A> Tümü üretilene ve yeniden oluşturulana kadar herhangi bir öğe alamaz. Bu nedenle, gibi <xref:System.Linq.ParallelMergeOptions> bir işleci de içeren bir sorguda kullanıldığında <xref:System.Linq.ParallelEnumerable.Reverse%2A> , bu işleç sonuçlarını üretene kadar birleştirme davranışı sorguya uygulanmaz.  
  
 Bazı işleçlerin birleştirme seçeneklerini işleme yeteneği, kaynak dizinin türüne ve <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> işlecin daha önce sorguda kullanılıp kullanılmadığını bağlıdır. <xref:System.Linq.ParallelEnumerable.ForAll%2A>her zaman, <xref:System.Linq.ParallelMergeOptions.NotBuffered> öğelerini hemen oluşturur. <xref:System.Linq.ParallelEnumerable.OrderBy%2A>her zaman, <xref:System.Linq.ParallelMergeOptions.FullyBuffered> Tüm listeyi vermeden önce sıralamalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel LINQ (PLINQ)](introduction-to-plinq.md)
- [Nasıl yapılır: PLINQ'te Birleştirme Seçeneklerini Belirtme](how-to-specify-merge-options-in-plinq.md)
