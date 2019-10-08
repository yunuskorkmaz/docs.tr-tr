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
ms.openlocfilehash: 087472c51d203be083fea0d39ade6f12066cfcb4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004741"
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
 @No__t-0 yan tümcesini kullanarak bir sorgudan döndürülecek sonuçları tanımlayabilirsiniz. Bu, bir sorgu tarafından oluşturulan yeni bir anonim türün üyelerini tanımlamanızı ya da bir sorgu tarafından döndürülen adlandırılmış türün üyelerini hedeflemenize olanak sağlar. @No__t-0 yan tümcesi bir sorgu için gerekli değildir. @No__t-0 yan tümcesi belirtilmemişse sorgu, geçerli kapsam için tanımlanan Aralık değişkenlerinin tüm üyelerini temel alan bir tür döndürür. Daha fazla bilgi için bkz. [anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md). Bir sorgu adlandırılmış bir tür oluşturduğunda, <xref:System.Collections.Generic.IEnumerable%601> türünde bir sonuç döndürür; burada `T` oluşturulan tür.  
  
 @No__t-0 yan tümcesi geçerli kapsamdaki değişkenlere başvurabilir. Bu, `From` yan tümcesinde (veya `From` yan tümcelerinde) tanımlanan Aralık değişkenlerini içerir. Ayrıca, `Aggregate`, `Let`, `Group By` veya `Group Join` yan tümcelerinden diğer adla oluşturulan yeni değişkenler veya sorgu ifadesinde önceki `Select` yan tümcesinin değişkenleri de içerir. @No__t-0 yan tümcesi statik değerler de içerebilir. Örneğin, aşağıdaki kod örneği, `Select` yan tümcesinin sorgu sonucunu dört üye ile yeni bir anonim tür olarak tanımladığı bir sorgu ifadesi gösterir: `ProductName`, `Price`, `Discount` ve `DiscountedPrice`. @No__t-0 ve `Price` üye değerleri `From` yan tümcesinde tanımlanan ürün aralığı değişkeninden alınır. @No__t-0 üye değeri `Let` yan tümcesinde hesaplanır. @No__t-0 üyesi statik bir değerdir.  
  
 [!code-vb[VbSimpleQuerySamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#27)]  
  
 @No__t-0 yan tümcesi, sonraki sorgu yan tümceleri için yeni bir Aralık değişkenleri kümesi tanıtır ve önceki Aralık değişkenleri artık kapsamda değildir. Bir sorgu ifadesindeki son `Select` yan tümcesi sorgunun dönüş değerini belirler. Örneğin, aşağıdaki sorgu toplam 500 ' ı aşan her müşteri siparişi için şirket adı ve sipariş KIMLIĞINI döndürür. İlk `Select` yan tümcesi `Where` yan tümcesinin Aralık değişkenlerini ve ikinci `Select` yan tümcesini tanımlar. İkinci `Select` yan tümcesi, yeni bir anonim tür olarak sorgu tarafından döndürülen değerleri tanımlar.  
  
 [!code-vb[VbSimpleQuerySamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#28)]  
  
 @No__t-0 yan tümcesi döndürülecek tek bir öğeyi tanımlarsa, sorgu ifadesi bu tek öğe türünün bir koleksiyonunu döndürür. @No__t-0 yan tümcesi döndürülecek birden çok öğeyi tanımlarsa, sorgu ifadesi seçili öğelere göre yeni bir anonim türün koleksiyonunu döndürür. Örneğin, aşağıdaki iki sorgu `Select` yan tümcesini temel alan iki farklı türdeki koleksiyonları döndürür. İlk sorgu, bir şirket adları koleksiyonunu dize olarak döndürür. İkinci sorgu, şirket adları ve adres bilgileriyle doldurulmuş `Customer` nesnelerinin bir koleksiyonunu döndürür.  
  
 [!code-vb[VbSimpleQuerySamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#29)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifadesi bir `From` yan tümcesini kullanarak `customers` koleksiyonu için-1 @no__t bir Aralık değişkeni bildirir. @No__t-0 yan tümcesi, müşteri adı ve KIMLIK değerini seçer ve yeni Aralık değişkeninin `CompanyName` ve `CustomerID` sütunlarını doldurur. @No__t-0 ifadesinde döndürülen her nesne için döngü yapılır ve her kayıt için `CompanyName` ve `CustomerID` sütunları görüntülenir.  
  
 [!code-vb[VbSimpleQuerySamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#30)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic LINQ 'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](../../../visual-basic/language-reference/queries/index.md)
- [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)
- [Where Yan Tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)
- [Order By Yan Tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Anonim Tipler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
