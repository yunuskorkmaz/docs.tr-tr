---
title: Select Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySelect
helpviewer_keywords:
- Select statement [Visual Basic]
- Select clause [Visual Basic]
- queries [Visual Basic], Select
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
ms.openlocfilehash: 5ebb813229d5d517b369036c69b2d23c8ee1c9f5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350404"
---
# <a name="select-clause-visual-basic"></a>Select Tümcesi (Visual Basic)
Bir sorgunun sonucunu tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## <a name="parts"></a>Bölümler  
 `var1`  
 İsteğe bağlı. Sütun ifadesinin sonuçlarına başvurmak için kullanılabilecek bir diğer ad.  
  
 `fieldName1`  
 Gerekli. Sorgu sonucuna döndürülecek alanın adı.  
  
## <a name="remarks"></a>Açıklamalar  
 `Select` yan tümcesini kullanarak bir sorgudan döndürülecek sonuçları tanımlayabilirsiniz. Bu, bir sorgu tarafından oluşturulan yeni bir anonim türün üyelerini tanımlamanızı ya da bir sorgu tarafından döndürülen adlandırılmış türün üyelerini hedeflemenize olanak sağlar. `Select` yan tümcesi bir sorgu için gerekli değildir. `Select` yan tümcesi belirtilmemişse, sorgu geçerli kapsam için tanımlanan Aralık değişkenlerinin tüm üyelerini temel alan bir tür döndürür. Daha fazla bilgi için bkz. [anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md). Bir sorgu adlandırılmış bir tür oluşturduğunda, `T` oluşturulan tür olan <xref:System.Collections.Generic.IEnumerable%601> türünde bir sonuç döndürür.  
  
 `Select` yan tümcesi geçerli kapsamdaki değişkenlere başvurabilir. Bu, `From` yan tümcesinde (veya `From` yan tümcelerinde) tanımlanan Aralık değişkenlerini içerir. Ayrıca, `Aggregate`, `Let`, `Group By`veya `Group Join` yan tümcelerinden diğer adla oluşturulan yeni değişkenler veya sorgu ifadesindeki önceki bir `Select` yan tümcesinin değişkenleri de içerir. `Select` yan tümcesi statik değerler de içerebilir. Örneğin, aşağıdaki kod örneği, `Select` yan tümcesinin sorgu sonucunu dört üyeli yeni bir anonim tür olarak tanımladığı bir sorgu ifadesi gösterir: `ProductName`, `Price`, `Discount`ve `DiscountedPrice`. `ProductName` ve `Price` üye değerleri `From` yan tümcesinde tanımlanan ürün aralığı değişkeninden alınır. `DiscountedPrice` üye değeri `Let` yan tümcesinde hesaplanır. `Discount` üyesi statik bir değerdir.  
  
 [!code-vb[VbSimpleQuerySamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#27)]  
  
 `Select` yan tümcesi, sonraki sorgu yan tümceleri için yeni bir Aralık değişkenleri kümesi tanıtır ve önceki Aralık değişkenleri artık kapsamda değildir. Bir sorgu ifadesindeki son `Select` yan tümcesi sorgunun dönüş değerini belirler. Örneğin, aşağıdaki sorgu toplam 500 ' ı aşan her müşteri siparişi için şirket adı ve sipariş KIMLIĞINI döndürür. İlk `Select` yan tümcesi, `Where` yan tümcesinin ve ikinci `Select` yan tümcesinin Aralık değişkenlerini tanımlar. İkinci `Select` yan tümcesi, yeni bir anonim tür olarak sorgu tarafından döndürülen değerleri tanımlar.  
  
 [!code-vb[VbSimpleQuerySamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#28)]  
  
 `Select` yan tümcesi döndürülecek tek bir öğeyi tanımlarsa, sorgu ifadesi bu tek öğe türünün bir koleksiyonunu döndürür. `Select` yan tümcesi döndürülecek birden çok öğeyi tanımlarsa, sorgu ifadesi seçili öğelere göre yeni bir anonim türün koleksiyonunu döndürür. Örneğin, aşağıdaki iki sorgu `Select` yan tümcesini temel alan iki farklı türdeki koleksiyonları döndürür. İlk sorgu, bir şirket adları koleksiyonunu dize olarak döndürür. İkinci sorgu, şirket adları ve adres bilgileriyle doldurulmuş `Customer` nesnelerinin bir koleksiyonunu döndürür.  
  
 [!code-vb[VbSimpleQuerySamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#29)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifadesi `customers` koleksiyonu için bir Aralık değişkeni `cust` bildirmek üzere bir `From` yan tümcesi kullanır. `Select` yan tümcesi, müşteri adı ve KIMLIK değerini seçer ve yeni Aralık değişkeninin `CompanyName` ve `CustomerID` sütunlarını doldurur. `For Each` bildiri, döndürülen her nesne için döngü alır ve her kayıt için `CompanyName` ve `CustomerID` sütunlarını görüntüler.  
  
 [!code-vb[VbSimpleQuerySamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#30)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic LINQ 'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](../../../visual-basic/language-reference/queries/index.md)
- [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)
- [Where Yan Tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)
- [Order By Yan Tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Anonim Tipler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
