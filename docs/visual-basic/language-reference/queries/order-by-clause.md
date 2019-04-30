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
ms.openlocfilehash: 1c84a4cdb4a149154d459ca4d9c290ed360d1772
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61712571"
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
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifadesi kullanan `Order By` sorgu sonucuna göre azalan düzende fiyatı sıralamak için yan tümcesi. Kitapları ile aynı fiyat üzerinden, artan düzende başlığa göre sıralanır.  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifadesi kullanan bir `Select` yan kitap başlığını seçin, fiyat, yayımlama tarihi ve yazar. Ardından doldurur `Title`, `Price`, `PublishDate`, ve `Author` yeni kapsam için Aralık değişkeninin alanları. `Order By` Yan tümcesi yeni aralık değişkeni yazar adı, kitap başlığı ve fiyat göre sıralar. Her sütun (artan) varsayılan sıraya göre sıralanır.  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](../../../visual-basic/language-reference/queries/index.md)
- [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)
- [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)
