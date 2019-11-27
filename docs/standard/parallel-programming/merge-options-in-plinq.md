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
ms.openlocfilehash: 18f233ac4c5afa63ec31e83d5fff8f0a57f9146f
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74203993"
---
# <a name="merge-options-in-plinq"></a>PLINQ'te Birleştirme Seçenekleri
Bir sorgu paralel olarak yürütülerek PLıNQ, kaynak dizisini birden çok iş parçacığının aynı anda farklı parçalar üzerinde, genellikle ayrı iş parçacıklarında çalışabilmesi için bölümler. Sonuçlar bir iş parçacığında tüketilebilir, örneğin, bir `foreach` (Visual Basic`For Each`) döngüsünde, her iş parçacığının sonuçları tek bir sırayla birleştirilmelidir. PLıNQ tarafından gerçekleştirilen birleştirme türü sorguda bulunan işleçlere bağlıdır. Örneğin, sonuçlara yeni bir sıra uygulayan işleçler tüm iş parçacıklarından tüm öğeleri arabelleğe almalıdır. Tüketim iş parçacığının perspektifinden (aynı zamanda uygulama kullanıcısının), tam olarak arabelleğe alınmış bir sorgu, ilk sonucunu oluşturmadan önce fark edilebilir bir süre için çalıştırılabilir. Diğer işleçler, varsayılan olarak kısmen arabelleğe alınır; sonuçları toplu işlerle sonuçlarlar. Tek operatör, <xref:System.Linq.ParallelEnumerable.ForAll%2A> varsayılan olarak ara belleğe alınmadı. Tüm iş parçacıklarından tüm öğeleri hemen oluşturur.  
  
 Aşağıdaki örnekte gösterildiği gibi <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> yöntemini kullanarak, PLıNQ için ne tür birleştirme yapılacağını belirten bir ipucu sağlayabilirsiniz.  
  
 [!code-csharp[PLINQ#26](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#26)]
 [!code-vb[PLINQ#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#26)]  
  
 Tüm örnek için bkz. [nasıl yapılır: PLıNQ 'Te birleştirme seçeneklerini belirtme](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md).  
  
 Belirli bir sorgu istenen seçeneği desteklenemez, bu durumda seçenek yalnızca yok sayılır. Çoğu durumda, PLıNQ sorgusu için bir birleştirme seçeneği belirtmeniz gerekmez. Ancak, bazı durumlarda bir sorgunun varsayılan olmayan bir modda en iyi şekilde yürütüldüğünü test ederek ve ölçüyle fark edebilirsiniz. Bu seçeneğin yaygın kullanımı, bir öbek birleştirme işlecinin, daha fazla yanıt veren bir kullanıcı arabirimi sağlamak için sonuçlarını akışını zorlamaktır.  
  
## <a name="parallelmergeoptions"></a>ParallelMergeOptions  
 <xref:System.Linq.ParallelMergeOptions> numaralandırması, desteklenen sorgu şekilleri için, sonuçlar bir iş parçacığında kullanılırken sorgunun son çıkışının nasıl sonuçlandırıldığını belirten aşağıdaki seçenekleri içerir:  
  
- `Not Buffered`  
  
     <xref:System.Linq.ParallelMergeOptions.NotBuffered> seçeneği, her bir işlenen öğenin, her bir iş parçacığından, üretildiğinde döndürülmesini sağlar. Bu davranış, çıktıyı "akışa alma" ile benzerdir. Sorguda <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> işleci varsa, `NotBuffered` kaynak öğelerin sırasını korur. `NotBuffered`, sonuçlar kullanılabilir duruma geldiğinde sonuçları almaya başlasa da, tüm sonuçları üreten toplam süre, diğer birleştirme seçeneklerinden birini kullanmaktan daha uzun olabilir.  
  
- `Auto Buffered`  
  
     <xref:System.Linq.ParallelMergeOptions.AutoBuffered> seçeneği, sorgunun öğeleri bir arabelleğe toplamasını ve daha sonra bir kez arabellek içeriğini tüketim iş parçacığına düzenli olarak elde etmesine neden olur. Bu, `NotBuffered`"akış" davranışının kullanılması yerine kaynak verileri "parçalar" halinde ortaya yüklemeye benzer. `AutoBuffered`, ilk öğeyi tüketen iş parçacığında kullanılabilir hale getirmek için `NotBuffered` daha uzun sürebilir. Arabelleğin boyutu ve kesin hale göre davranışı yapılandırılabilir değildir ve sorguyla ilgili çeşitli faktörlere bağlı olarak farklılık gösterebilir.  
  
- `FullyBuffered`  
  
     <xref:System.Linq.ParallelMergeOptions.FullyBuffered> seçeneği, herhangi bir öğeden herhangi biri alınmadan önce tüm sorgunun çıkışının arabelleğe alınmasına neden olur. Bu seçeneği kullandığınızda, ilk öğe tüketim iş parçacığında kullanılabilir olmadan önce daha uzun sürebilir, ancak tüm sonuçlar yine de diğer seçenekler kullanılarak daha hızlı oluşturulabilir.  
  
## <a name="query-operators-that-support-merge-options"></a>Birleştirme seçeneklerini destekleyen sorgu Işleçleri  
 Aşağıdaki tabloda, belirtilen kısıtlamalara tabi olan tüm birleştirme seçeneği modlarını destekleyen işleçler listelenmektedir.  
  
|İşleç|{1&gt;Kısıtlamalar&lt;1}|  
|--------------|------------------|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|Yok.|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Yok.|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Yalnızca bir dizi veya liste kaynağına sahip sıralı olmayan sorgular.|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|Yok.|  
|<xref:System.Linq.ParallelEnumerable.OfType%2A>|Yok.|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Yalnızca bir dizi veya liste kaynağına sahip sıralı olmayan sorgular.|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Yok.|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|Yok.|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|Yok.|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|Yok.|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Yok.|  
  
 Tüm diğer PLıNQ sorgu işleçleri Kullanıcı tarafından sağlanmış birleştirme seçeneklerini yok sayabilir. Bazı sorgu işleçleri (örneğin, <xref:System.Linq.ParallelEnumerable.Reverse%2A> ve <xref:System.Linq.ParallelEnumerable.OrderBy%2A>, hepsi üretilene ve yeniden sıralanana kadar herhangi bir öğe alamaz. Bu nedenle, <xref:System.Linq.ParallelEnumerable.Reverse%2A>gibi bir işleç de içeren bir sorguda <xref:System.Linq.ParallelMergeOptions> kullanıldığında, bu işleç sonuçlarını üretene kadar birleştirme davranışı sorguya uygulanmaz.  
  
 Bazı işleçlerin birleştirme seçeneklerini işleme yeteneği, kaynak dizinin türüne ve <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> işlecinin sorguda daha önce kullanılıp kullanılmadığını belirtir. <xref:System.Linq.ParallelEnumerable.ForAll%2A> her zaman <xref:System.Linq.ParallelMergeOptions.NotBuffered>; kendi öğelerini hemen oluşturur. <xref:System.Linq.ParallelEnumerable.OrderBy%2A> her zaman <xref:System.Linq.ParallelMergeOptions.FullyBuffered>; Tüm listeyi vermeden önce sıralaması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
- [Nasıl yapılır: PLINQ'te Birleştirme Seçeneklerini Belirtme](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)
