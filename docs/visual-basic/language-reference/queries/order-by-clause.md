---
title: Order By Yan Tümcesi
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
ms.openlocfilehash: 63f454064e88bc18f252940f3abd8e59b8900e5b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359754"
---
# <a name="order-by-clause-visual-basic"></a>Order By Tümcesi (Visual Basic)
Bir sorgu sonucu için sıralama düzenini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a>Bölümler  
 `orderExp1`  
 Gereklidir. Geçerli sorgu sonucundan döndürülen değerlerin nasıl sıraya alınacağını belirleyen bir veya daha fazla alan. Alan adları virgüller (,) ile ayrılmalıdır. `Ascending`Veya anahtar sözcüklerini kullanarak her bir alanı artan veya azalan düzende sıralanmış olarak belirleyebilirsiniz `Descending` . Hayır `Ascending` veya `Descending` anahtar sözcüğü belirtilmemişse, varsayılan sıralama düzeni artan olur. Sıralama düzeni alanlarına soldan sağa öncelik verilir.  
  
## <a name="remarks"></a>Açıklamalar  
 `Order By`Bir sorgunun sonuçlarını sıralamak için yan tümcesini kullanabilirsiniz. `Order By`Yan tümce yalnızca geçerli kapsamın Aralık değişkenine göre bir sonuç sıralayabilir. Örneğin `Select` yan tümcesi, bir sorgu ifadesinde bu kapsam için yeni yineleme değişkenleriyle yeni bir kapsam sağlar. Sorgudaki bir yan tümce öncesinde tanımlanan Aralık değişkenleri `Select` , `Select` yan tümcesinden sonra kullanılamaz. Bu nedenle, sonuçlarınızı yan tümcesinde kullanılamayan bir alana göre sıralamak isterseniz, yan tümcesini `Select` yan tümce önüne koymanız gerekir `Order By` `Select` . Bunu yapmanız gereken bir örnek, sorgunuzu sonucun bir parçası olarak döndürülmüyor alanlara göre sıralamak isteeceklerdir.  
  
 Bir alan için artan ve azalan sıralama, <xref:System.IComparable> alanın veri türü için arabirim uygulamasına göre belirlenir. Veri türü arabirimi uygulamadığı takdirde <xref:System.IComparable> sıralama düzeni yok sayılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifadesi, `From` koleksiyon için bir Aralık değişkeni bildirmek üzere bir yan tümce kullanır `book` `books` . `Order By`Yan tümcesi, sorgu sonucunu fiyata göre artan sırada sıralar (varsayılan). Aynı fiyata sahip olan kitaplar başlığa göre artan sırada sıralanır. `Select`Yan tümcesi, `Title` ve `Price` özelliklerini sorgu tarafından döndürülen değerler olarak seçer.  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifadesi, `Order By` sorgu sonucunu fiyata göre azalan sırada sıralamak için yan tümcesini kullanır. Aynı fiyata sahip olan kitaplar başlığa göre artan sırada sıralanır.  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifadesi, `Select` kitap başlığı, Fiyat, yayımlama tarihi ve yazar seçmek için bir yan tümce kullanır. Ardından, `Title` `Price` `PublishDate` `Author` Yeni kapsamın aralık değişkeninin,, ve alanlarını doldurur. `Order By`Yan tümcesi, yeni Aralık değişkenini yazar adı, kitap başlığı ve sonra fiyat olarak sıralar. Her sütun varsayılan sırada sıralanır (artan).  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de LINQ'e Giriş](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](index.md)
- [Select yan tümcesi](select-clause.md)
- [From yan tümcesi](from-clause.md)
