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
ms.openlocfilehash: d4abb5f0b75ae4069c1dbe695a5c810b1f7aa6e1
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42935493"
---
# <a name="order-by-clause-visual-basic"></a>Order By Tümcesi (Visual Basic)
Sorgu sonucu için sıralama düzenini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a>Bölümler  
 `orderExp1`  
 Gerekli. Döndürülen değerlerin nasıl tanımlayan bir veya daha fazla alanlardan geçerli sorgu sonucu. Alan adlarını, virgül (,) ile ayrılmalıdır. Her bir alan olarak kullanarak azalan veya artan düzende sıralanmış olarak tanımlayabilirsiniz `Ascending` veya `Descending` anahtar sözcükleri. Hayır ise `Ascending` veya `Descending` anahtar sözcüğü belirtilmediğinde, varsayılan sıralama artan düzendedir. Sıralama düzeni alanlarını öncelik soldan sağa atanır.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz `Order By` bir sorgunun sonuçlarını sıralamak için yan tümcesi. `Order By` Yan tümcesinin aralık değişkeni geçerli kapsam için temel bir sonuç yalnızca sıralayabilirsiniz. Örneğin, `Select` yan tümcesi bir sorgu ifadesinde yeni yineleme değişkenleri ile ilgili kapsam için yeni bir kapsam tanıtır. Aralık önce tanımlanan değişkenler bir `Select` sorgu yan tümcesinde kullanılamaz sonra `Select` yan tümcesi. Bu nedenle, sonuçlarınızı kullanılamaz bir alana göre sıralamak isterseniz `Select` yan tümcesi gerekir put `Order By` yan tümcesi önce `Select` yan tümcesi. Bir örneği olduğunda bunu yapmak gerekir, sorgu sonucu bir parçası olarak döndürülmez alanlara göre sıralamak istediğinizi olduğunda.  
  
 Artan ve azalan bir alan uygulaması tarafından belirlenir <xref:System.IComparable> alanın veri türü için arabirim. Veri türü uygulamazsa <xref:System.IComparable> arabirimi, sıralama düzeni göz ardı edilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifadesi kullanan bir `From` yan tümcesinin aralık değişkenini bildirmek için `book` için `books` koleksiyonu. `Order By` Yan tümce sorgu sonucuna göre artan düzende (varsayılan) fiyatı sıralar. Kitapları ile aynı fiyat üzerinden, artan düzende başlığa göre sıralanır. `Select` Yan tümcesi seçer `Title` ve `Price` sorgu tarafından döndürülen değer olarak özellikleri.  
  
 [!code-vb[VbSimpleQuerySamples#24](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_1.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifadesi kullanan `Order By` sorgu sonucuna göre azalan düzende fiyatı sıralamak için yan tümcesi. Kitapları ile aynı fiyat üzerinden, artan düzende başlığa göre sıralanır.  
  
 [!code-vb[VbSimpleQuerySamples#25](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_2.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifadesi kullanan bir `Select` yan kitap başlığını seçin, fiyat, yayımlama tarihi ve yazar. Ardından doldurur `Title`, `Price`, `PublishDate`, ve `Author` yeni kapsam için Aralık değişkeninin alanları. `Order By` Yan tümcesi yeni aralık değişkeni yazar adı, kitap başlığı ve fiyat göre sıralar. Her sütun (artan) varsayılan sıraya göre sıralanır.  
  
 [!code-vb[VbSimpleQuerySamples#26](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_3.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Sorgular](../../../visual-basic/language-reference/queries/index.md)  
 [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)
