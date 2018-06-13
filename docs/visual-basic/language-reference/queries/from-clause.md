---
title: From Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
ms.openlocfilehash: 1f113444efae83de7d299db330593937c7800bb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604724"
---
# <a name="from-clause-visual-basic"></a>From Tümcesi (Visual Basic)
Bir veya daha fazla aralık değişkeni ve sorgu bir koleksiyona belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`element`|Gerekli. A *aralık değişkeni* koleksiyonu öğelerinde yineleme yapmak için kullanılır. Aralık değişkeni için her üye başvurmak için kullanılan `collection` sorgu dolaşır gibi `collection`. Bir numaralandırma türü olmalıdır.|  
|`type`|İsteğe bağlı. Türü `element`. Öyle değilse `type` belirtilirse, türü `element` gelen olayla `collection`.|  
|`collection`|Gerekli. Sorgulanacak koleksiyona ifade eder. Bir numaralandırma türü olmalıdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `From` Yan tümcesi, bir sorgu ve kaynak koleksiyondan bir öğe olarak başvurmak için kullanılan değişkenler için kaynak verilerini tanımlamak için kullanılır. Bu değişkenler adlı *aralık değişkenleri*. `From` Ne zaman dışında bir sorgu için yan tümcesi gereklidir `Aggregate` yan tümcesi döndürür yalnızca sonuçları birleşik bir sorgu tanımlamak için kullanılır. Daha fazla bilgi için bkz: [Aggregate tümcesi](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Birden çok belirtebilirsiniz `From` birleştirilecek olan birden çok koleksiyon tanımlayacak bir sorgu yan tümcelerinde. Birden çok koleksiyon belirtildiğinde, bunlar üzerinden bağımsız olarak yinelendiğinde veya ilişkili oldukları varsa bunları katılabilirsiniz. Kullanarak koleksiyonları örtük olarak birleştirebilirsiniz `Select` yan tümcesi veya kullanarak açıkça `Join` veya `Group Join` yan tümceleri. Alternatif olarak, birden çok aralık değişkeni ve koleksiyonları tek bir belirtebilirsiniz `From` yan tümcesi, her ilgili aralık değişkeni ve diğerlerinden virgülle ayrılmış koleksiyonu. Aşağıdaki kod örneği iki sözdizimi seçeneklerini gösterir `From` yan tümcesi.  
  
 [!code-vb[VbSimpleQuerySamples#21](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_1.vb)]  
  
 `From` Yan tümcesi kapsamına benzer bir sorgu kapsamını tanımlayan bir `For` döngü. Bu nedenle, her `element` aralık değişkeni bir sorgu kapsamında benzersiz bir adı olması gerekir. Birden çok belirtebildiğinizden `From` sonraki bir sorgu için tümcecikleri `From` yan tümceleri aralık değişkenlerinin başvurabilir `From` yan tümcesi veya başvurabilir aralık değişkeni için önceki bir `From` yan tümcesi. Örneğin, aşağıdaki örnekte bir iç içe gösterir `From` burada ikinci tümce koleksiyonunda temel bir özelliğe ilk yan tümcesinde Aralık değişkeninin yan tümcesi.  
  
 [!code-vb[VbSimpleQuerySamples#22](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_2.vb)]  
  
 Her `From` yan tümcesi herhangi bir bileşimini sorguyu daraltmak için ek sorgu yan tümceleri takip. Sorgu aşağıdaki yollarla tanımlayabilirsiniz:  
  
-   Birden çok koleksiyon örtük olarak kullanarak birleştirme `From` ve `Select` yan tümceleri, veya kullanarak açıkça `Join` veya `Group Join` yan tümceleri.  
  
-   Kullanım `Where` sorgu sonucu filtrelemek için yan tümcesi.  
  
-   Sonuç kullanarak sıralama `Order By` yan tümcesi.  
  
-   Benzer sonuçlar gruplamak kullanarak `Group By` yan tümcesi.  
  
-   Kullanım `Aggregate` için tüm sorgu sonucu değerlendirmek için toplama işlevleri tanımlamak için yan tümcesi.  
  
-   Kullanım `Let` değerini bir deyim bir koleksiyon yerine belirlenir bir yineleme değişkeni tanıtmak için yan tümcesi.  
  
-   Kullanım `Distinct` yinelenen sorgu sonuçları yoksaymak için yan tümcesi.  
  
-   Kullanarak döndürülecek sonuç parçalarını tanımlamak `Skip`, `Take`, `Skip While`, ve `Take While` yan tümceleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifade kullanan bir `From` yan tümcesinin aralık değişkeni bildirmek için `cust` her `Customer` nesnesinde `customers` koleksiyonu. `Where` Yan tümcesi, çıkış müşterilere belirtilen bölgesinden kısıtlamak için aralık değişkeni kullanır. `For Each` Döngü sorgu sonucunda her müşteri için şirket adını görüntüler.  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_3.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorgular](../../../visual-basic/language-reference/queries/queries.md)  
 [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [For Each...Next Deyimi](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [For...Next Deyimi](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Where Yan Tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)  
 [Aggregate Yan Tümcesi](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [Distinct Yan Tümcesi](../../../visual-basic/language-reference/queries/distinct-clause.md)  
 [Join Yan Tümcesi](../../../visual-basic/language-reference/queries/join-clause.md)  
 [Group Join Yan Tümcesi](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [Order By Yan Tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Let Yan Tümcesi](../../../visual-basic/language-reference/queries/let-clause.md)  
 [Skip Yan Tümcesi](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [Take Yan Tümcesi](../../../visual-basic/language-reference/queries/take-clause.md)  
 [Skip While Yan Tümcesi](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Take While Yan Tümcesi](../../../visual-basic/language-reference/queries/take-while-clause.md)
