---
title: Select Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySelect
helpviewer_keywords:
- Select statement [Visual Basic]
- Select clause [Visual Basic]
- queries [Visual Basic], Select
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
ms.openlocfilehash: 367d810c2358963bfe2f092a390443eccdc66941
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814451"
---
# <a name="select-clause-visual-basic"></a>Select Tümcesi (Visual Basic)
Bir sorgunun sonucu tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## <a name="parts"></a>Bölümler  
 `var1`  
 İsteğe bağlı. Sonuçları sütun ifadesi başvurmak için kullanılan bir diğer ad.  
  
 `fieldName1`  
 Gerekli. Sorgu sonucuna döndürülecek alanın adı.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz `Select` bir sorgudan döndürülecek sonuç tanımlamak için. Bu, ya da bir sorgu tarafından oluşturulan yeni bir anonim tür üyelerini tanımlamak için veya bir sorgu tarafından döndürülen bir adlandırılmış tür üyelerinin hedeflemek için sağlar. `Select` Yan tümcesi bir sorgu için gerekli değildir. Hayır ise `Select` yan tümcesi belirtildiğinde, sorgu, geçerli kapsam için tanımlanan aralık değişkenleri tüm üyelerinin göre bir türü döndürür. Daha fazla bilgi için [anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md). Adlandırılmış tür bir sorgu oluşturur, bu tür bir sonuç döndürür <xref:System.Collections.Generic.IEnumerable%601> burada `T` oluşturulan türüdür.  
  
 `Select` Yan tümcesi, değişkenlerin geçerli kapsamda başvurabilir. Bu aralık değişkenleri tanımlanan içerir `From` yan tümcesi (veya `From` yan tümceleri). Ayrıca bir diğer ad ile oluşturulan tüm yeni değişkenler içerir `Aggregate`, `Let`, `Group By`, veya `Group Join` yan tümcesi ya da bir önceki değişkenlerinden `Select` yan tümcesinde sorgu ifadesi. `Select` Yan tümcesi de statik değerleri içerir. Örneğin, aşağıdaki kod örneği bir sorgu ifadesi içinde gösterir `Select` yan tümcesi, dört üyeleri içeren yeni bir anonim tür olarak sorgu sonucu tanımlar: `ProductName`, `Price`, `Discount`, ve `DiscountedPrice`. `ProductName` Ve `Price` üye değerlerinin tanımlanan ürün aralık değişkeni verilerinden alınır `From` yan tümcesi. `DiscountedPrice` Üyenin değeri hesaplanır `Let` yan tümcesi. `Discount` Üye statik bir değerdir.  
  
 [!code-vb[VbSimpleQuerySamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#27)]  
  
 `Select` Yan tümcesinin aralık değişkenleri sonraki sorgu yan tümceleri için yeni bir dizi tanıtır ve önceki aralık değişkenleri artık aboneliklerinin kapsamda. Son `Select` yan tümcesi bir sorgu ifadesinde sorgu dönüş değerini belirler. Örneğin, aşağıdaki sorguyu şirket toplam 500 aşıyor her müşteri sipariş için adı ve sipariş kimliği döndürür. İlk `Select` yan tümcesinin aralık değişkenleri tanımlayan `Where` yan tümcesi ve ikinci `Select` yan tümcesi. İkinci `Select` yan tümcesi, yeni bir anonim tür olarak sorgu tarafından döndürülen değerleri tanımlar.  
  
 [!code-vb[VbSimpleQuerySamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#28)]  
  
 Varsa `Select` yan tümcesi tanımlar döndürmek için tek bir öğe, sorgu ifadesi türü o tek öğe koleksiyonunu döndürür. Varsa `Select` yan tümcesi tanımlar döndürmek için birden çok öğe, sorgu ifadesi seçili maddeler temel alınarak bir yeni bir anonim tür koleksiyonunu döndürür. Örneğin, aşağıdaki iki sorguları göre iki farklı türlerdeki koleksiyonlar geri `Select` yan tümcesi. İlk sorgu dizeleri olarak şirket adlarını koleksiyonunu döndürür. İkinci sorgu koleksiyonunu döndürür `Customer` nesneleri şirket adı ve adresi bilgileri ile doldurulur.  
  
 [!code-vb[VbSimpleQuerySamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#29)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifadesi kullanan bir `From` yan tümcesinin aralık değişkenini bildirmek için `cust` için `customers` koleksiyonu. `Select` Yan tümcesi müşteri adı ve kimliği değeri seçer ve dolduran `CompanyName` ve `CustomerID` yeni Aralık değişkeninin sütunları. `For Each` Deyimi döngüsü döndürülen her nesne ve görüntüler `CompanyName` ve `CustomerID` sütunları her kayıt için.  
  
 [!code-vb[VbSimpleQuerySamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#30)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](../../../visual-basic/language-reference/queries/index.md)
- [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)
- [Where Yan Tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)
- [Order By Yan Tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Anonim Tipler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
