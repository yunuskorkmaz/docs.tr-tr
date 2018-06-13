---
title: Order By Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryOrderBy
- vb.QueryAscending
- vb.QueryDescending
helpviewer_keywords:
- queries [Visual Basic], Order By
- Order By clause [Visual Basic]
- Order By statement [Visual Basic]
ms.assetid: fa911282-6b81-44c7-acfa-46b5bb93df75
ms.openlocfilehash: 7c60156ee81618530b42d5f61dbcac6f59c4f675
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604126"
---
# <a name="order-by-clause-visual-basic"></a>Order By Tümcesi (Visual Basic)
Sorgu sonucu için sıralama düzenini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a>Bölümler  
 `orderExp1`  
 Gerekli. Döndürülen değerlerini sıralamak nasıl tanımlayan bir veya daha fazla alanlarından geçerli sorgu sonucu. Alan adları (,) virgülle ayrılmış olması gerekir. Her bir alan olarak kullanarak azalan veya artan düzende sıralanmış olarak tanımlayabilirsiniz `Ascending` veya `Descending` anahtar sözcükler. Öyle değilse `Ascending` veya `Descending` anahtar sözcüğü belirtilmediyse, varsayılan sıralama düzeni artan. Sıralama sipariş alanlar soldan sağa öncelik verilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz `Order By` bir sorgunun sonuçlarını sıralamak için yan tümcesi. `Order By` Yan tümcesi yalnızca geçerli kapsam için aralık değişkeni dayalı bir sonuç sıralayın. Örneğin, `Select` yan tümcesi bu kapsam için bir sorgu ifadesinde yeni yineleme değişkenleri ile yeni bir kapsam tanıtır. Aralık önce tanımlanan değişkenler bir `Select` bir sorgu yan tümcesinde kullanılamaz sonra `Select` yan tümcesi. Bu nedenle, sonuçlarınızı kullanılamaz bir alana göre sıralamak istiyorsanız `Select` yan tümcesi olmalıdır yerleştirme `Order By` önce yan tümcesi `Select` yan tümcesi. Bir zaman bunu yapmak olurdu örneğidir sorgunuzu sonucu bir parçası olarak döndürülmez alanlara göre sıralamak istediğinizde.  
  
 Artan veya azalan bir alan uygulaması tarafından belirlenir için <xref:System.IComparable> alanın veri türü için arabirim. Veri türü uygulamazsa <xref:System.IComparable> arabirimi, sıralama düzeni göz ardı edilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifade kullanan bir `From` yan tümcesinin aralık değişkeni bildirmek için `book` için `books` koleksiyonu. `Order By` Yan tümcesi göre artan sırada (varsayılan) fiyatı sorgu sonucu sıralar. Aynı fiyatla Books artan düzende başlığa göre sıralanır. `Select` Yan tümcesi seçer `Title` ve `Price` sorgu tarafından döndürülen değer olarak özellikleri.  
  
 [!code-vb[VbSimpleQuerySamples#24](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_1.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifadesi kullanır `Order By` göre azalan sırada fiyatı sorgu sonucu sıralamak için yan tümcesi. Aynı fiyatla Books artan düzende başlığa göre sıralanır.  
  
 [!code-vb[VbSimpleQuerySamples#25](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_2.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifade kullanan bir `Select` yan tümcesini defteri başlığı seçin, fiyat, yayımlama tarihi ve yazar. Ardından doldurur `Title`, `Price`, `PublishDate`, ve `Author` yeni kapsam için Aralık değişkeninin alanları. `Order By` Yan tümcesi siparişleri yazar adı, kitap başlığı ve ardından fiyat yeni aralık değişkeni. Her sütunun (artan) varsayılan sıraya göre sıralanır.  
  
 [!code-vb[VbSimpleQuerySamples#26](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_3.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Sorgular](../../../visual-basic/language-reference/queries/queries.md)  
 [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)
