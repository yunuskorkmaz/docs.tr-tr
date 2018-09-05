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
ms.openlocfilehash: 71573de48cc51c48291fc4b82a0628d2d0f96caa
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43556815"
---
# <a name="from-clause-visual-basic"></a>From Tümcesi (Visual Basic)
Bir veya daha fazla aralık değişkenleri ve bir sorgu koleksiyonu belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`element`|Gerekli. A *aralık değişkeni* koleksiyon öğelerinde yineleme yapmak için kullanılır. Aralık değişkeni için her üye için kullanılır `collection` sorgu gezinir gibi `collection`. Sıralanabilir bir tür olmalıdır.|  
|`type`|İsteğe bağlı. Türünü `element`. Hayır ise `type` belirtilen türü `element` içinden gösterilen `collection`.|  
|`collection`|Gerekli. Koleksiyona sorgulanacağı anlamına gelir. Sıralanabilir bir tür olmalıdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `From` Yan tümcesi bir sorgu ve kaynak koleksiyonu bir öğesine başvurmak için kullanılan değişkenleri için kaynak verilerini tanımlamak için kullanılır. Bu değişkenleri olarak adlandırılmasının *aralık değişkenleri*. `From` Aşağıdakiler haricinde bir sorgu yan tümcesi gereklidir `Aggregate` yan tümcesi döndürür yalnızca toplu sonuçları, bir sorgu tanımlamak için kullanılır. Daha fazla bilgi için [Aggregate tümcesi](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Birden çok belirtebilirsiniz `From` birleştirilecek olan birden çok koleksiyon belirlemek üzere bir sorgu yan tümcelerinde. Birden çok koleksiyon belirtildiğinde, bunlar üzerinden bağımsız olarak yinelendiğinde veya ilişkili oldukları varsa bunları birleştirebilirsiniz. Kullanarak, örtük olarak bir koleksiyonları birleştirebilirsiniz `Select` yan tümcesi kullanılarak açık şekilde veya `Join` veya `Group Join` yan tümceleri. Alternatif olarak, birden çok aralık değişkenleri ve Koleksiyonlar tek bir belirtebilirsiniz `From` her ilgili aralık değişkeni ve diğerlerinden virgülle ayırarak toplama yan tümcesi. Aşağıdaki kod örneği her iki sözdizimi seçeneklerini gösterir `From` yan tümcesi.  
  
 [!code-vb[VbSimpleQuerySamples#21](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_1.vb)]  
  
 `From` Yan tümcesi bir sorgu kapsamına benzer kapsamını tanımlar bir `For` döngü. Bu nedenle, her `element` aralık değişkeni bir sorgu kapsamında benzersiz adlara sahip olmalıdır. Birden çok belirtebildiğinizden `From` izleyen bir sorgu için yan tümceler `From` yan tümceleri aralık değişkenleri başvurabilir `From` yan tümcesi veya başvurabilir aralık değişkenleri önceki `From` yan tümcesi. Örneğin, aşağıdaki örnekte iç içe bir gösterir `From` burada ikinci yan tümcesinde toplama temel bir özelliği birinci yan tümce de Aralık değişkeninin yan tümcesi.  
  
 [!code-vb[VbSimpleQuerySamples#22](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_2.vb)]  
  
 Her `From` yan tümcesi sorguyu daraltmak için ek sorgu yan tümceleri herhangi bir birleşimi tarafından takip. Sorgu aşağıdaki yollarla daraltabilirsiniz:  
  
-   Örtük olarak kullanarak birden çok koleksiyon birleştirme `From` ve `Select` yan tümcesi kullanılarak açık şekilde veya `Join` veya `Group Join` yan tümceleri.  
  
-   Kullanım `Where` sorgu sonucu filtrelemek için yan tümcesi.  
  
-   Sonuç kullanarak sıralama `Order By` yan tümcesi.  
  
-   Şuna benzer sonuçlar gruplamak kullanarak `Group By` yan tümcesi.  
  
-   Kullanım `Aggregate` yan tümcesi için tüm sorgu sonucu değerlendiremedik toplama işlevleri tanımlamak için.  
  
-   Kullanım `Let` yan tanıtan bir yineleme değişkeninin değeri ifade yerine bir koleksiyona göre belirlenir.  
  
-   Kullanım `Distinct` yan yinelenen sorgu sonuçları yoksay.  
  
-   Kullanarak, döndürülecek sonuç parçalarını tanımlamak `Skip`, `Take`, `Skip While`, ve `Take While` yan tümceleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifadesi kullanan bir `From` yan tümcesinin aralık değişkenini bildirmek için `cust` her `Customer` nesnesine `customers` koleksiyonu. `Where` Yan tümcesi, çıkış belirtilen bölgeden müşterilere kısıtlamak için aralık değişkeni kullanır. `For Each` Döngü, her müşteri için şirket adı sorgu sonucu görüntüler.  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_3.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorgular](../../../visual-basic/language-reference/queries/index.md)  
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
