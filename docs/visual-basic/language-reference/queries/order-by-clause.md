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
ms.openlocfilehash: f8ee46b12e84f99629c3a92057fc3a7bb8a3c2e8
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004947"
---
# <a name="order-by-clause-visual-basic"></a>Order By Tümcesi (Visual Basic)
Bir sorgu sonucu için sıralama düzenini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a>Bölümler  
 `orderExp1`  
 Gerekli. Geçerli sorgu sonucundan döndürülen değerlerin nasıl sıraya alınacağını belirleyen bir veya daha fazla alan. Alan adları virgüller (,) ile ayrılmalıdır. @No__t-0 veya `Descending` anahtar sözcüklerini kullanarak her bir alanı artan veya azalan düzende sıralanmış olarak belirleyebilirsiniz. @No__t-0 veya `Descending` anahtar sözcüğü belirtilmemişse, varsayılan sıralama düzeni artan olur. Sıralama düzeni alanlarına soldan sağa öncelik verilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir sorgunun sonuçlarını sıralamak için `Order By` yan tümcesini kullanabilirsiniz. @No__t-0 yan tümcesi yalnızca geçerli kapsamın Aralık değişkenine göre bir sonuç sıralayabilir. Örneğin, `Select` yan tümcesi, bu kapsam için yeni yineleme değişkenleriyle bir sorgu ifadesinde yeni bir kapsam sunar. Sorgudaki `Select` yan tümcesinden önce tanımlanan Aralık değişkenleri `Select` yan tümcesinden sonra kullanılamaz. Bu nedenle, sonuçlarınızı `Select` yan tümcesinde kullanılamayan bir alana göre sıralamak isterseniz, `Select` yan tümcesinin önüne `Order By` yan tümcesini koymanız gerekir. Bunu yapmanız gereken bir örnek, sorgunuzu sonucun bir parçası olarak döndürülmüyor alanlara göre sıralamak isteeceklerdir.  
  
 Bir alan için artan ve azalan sıralama, alanın veri türü için <xref:System.IComparable> arabiriminin uygulamasına göre belirlenir. Veri türü <xref:System.IComparable> arabirimini uygulamadığı takdirde sıralama düzeni yok sayılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifadesi bir `From` yan tümcesini kullanarak `books` koleksiyonu için-1 @no__t bir Aralık değişkeni bildirir. @No__t-0 yan tümcesi, sorgu sonucunu fiyata göre artan sırada sıralar (varsayılan). Aynı fiyata sahip olan kitaplar başlığa göre artan sırada sıralanır. @No__t-0 yan tümcesi, sorgu tarafından döndürülen değerler olarak `Title` ve `Price` özelliklerini seçer.  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifadesi, sorgu sonucunu fiyata göre azalan sırada sıralamak için `Order By` yan tümcesini kullanır. Aynı fiyata sahip olan kitaplar başlığa göre artan sırada sıralanır.  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifadesi, kitap başlığı, Fiyat, yayımlama tarihi ve yazar seçmek için bir `Select` yan tümcesi kullanır. Ardından, yeni kapsamın aralık değişkeninin `Title`, `Price`, `PublishDate` ve `Author` alanlarını doldurur. @No__t-0 yan tümcesi, yeni Aralık değişkenini yazar adına, kitap başlığına ve ardından fiyata göre sıralar. Her sütun varsayılan sırada sıralanır (artan).  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic LINQ 'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](../../../visual-basic/language-reference/queries/index.md)
- [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)
- [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)
