---
title: Select Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySelect
helpviewer_keywords:
- Select statement [Visual Basic]
- Select clause [Visual Basic]
- queries [Visual Basic], Select
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
ms.openlocfilehash: a909b1d79b10f82ece03bab788ae889c64b27124
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359700"
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
 Gereklidir. Sorgu sonucuna döndürülecek alanın adı.  
  
## <a name="remarks"></a>Açıklamalar  
 `Select`Bir sorgudan döndürülecek sonuçları tanımlamak için yan tümcesini kullanabilirsiniz. Bu, bir sorgu tarafından oluşturulan yeni bir anonim türün üyelerini tanımlamanızı ya da bir sorgu tarafından döndürülen adlandırılmış türün üyelerini hedeflemenize olanak sağlar. `Select`Bir sorgu için yan tümce gerekli değildir. Hiçbir `Select` yan tümce belirtilmemişse, sorgu geçerli kapsam için tanımlanan Aralık değişkenlerinin tüm üyelerini temel alan bir tür döndürür. Daha fazla bilgi için bkz. [anonim türler](../../programming-guide/language-features/objects-and-classes/anonymous-types.md). Bir sorgu adlandırılmış bir tür oluşturduğunda, oluşturulduğu tür bir sonuç döndürür <xref:System.Collections.Generic.IEnumerable%601> `T` .  
  
 `Select`Yan tümce geçerli kapsamdaki değişkenlere başvurabilir. Bu, `From` yan tümcesinde (veya `From` yan tümcelerde) tanımlanan Aralık değişkenlerini içerir. Ayrıca,,, veya yan tümceleri tarafından oluşturulan yeni değişkenler `Aggregate` `Let` `Group By` `Group Join` veya `Select` sorgu ifadesinde Previous yan tümcesinin değişkenleri de içerir. `Select`Yan tümce statik değerler de içerebilir. Örneğin, aşağıdaki kod örneği, `Select` yan tümcesinin sorgu sonucunu dört üyeli yeni bir anonim tür olarak tanımladığı bir sorgu ifadesi gösterir: `ProductName` , `Price` , `Discount` ve `DiscountedPrice` . `ProductName`Ve `Price` üye değerleri, yan tümcesinde tanımlanan ürün aralığı değişkeninden alınır `From` . `DiscountedPrice`Üye değeri `Let` yan tümcesinde hesaplanır. `Discount`Üye statik bir değerdir.  
  
 [!code-vb[VbSimpleQuerySamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#27)]  
  
 `Select`Yan tümcesi, sonraki sorgu yan tümceleri için yeni bir Aralık değişkenleri kümesi tanıtır ve önceki Aralık değişkenleri artık kapsamda değildir. `Select`Sorgu ifadesindeki son yan tümce sorgunun dönüş değerini belirler. Örneğin, aşağıdaki sorgu toplam 500 ' ı aşan her müşteri siparişi için şirket adı ve sipariş KIMLIĞINI döndürür. İlk `Select` yan tümce, `Where` yan tümce ve ikinci yan tümce için Aralık değişkenlerini tanımlar `Select` . İkinci `Select` yan tümce, yeni bir anonim tür olarak sorgu tarafından döndürülen değerleri tanımlar.  
  
 [!code-vb[VbSimpleQuerySamples#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#28)]  
  
 `Select`Yan tümcesi döndürülecek tek bir öğeyi tanımlarsa, sorgu ifadesi bu tek öğe türünün bir koleksiyonunu döndürür. `Select`Yan tümcesi döndürülecek birden çok öğeyi tanımlarsa, sorgu ifadesi seçili öğelere göre yeni bir anonim türün koleksiyonunu döndürür. Örneğin, aşağıdaki iki sorgu yan tümcesini temel alan iki farklı türdeki koleksiyonları döndürür `Select` . İlk sorgu, bir şirket adları koleksiyonunu dize olarak döndürür. İkinci sorgu, `Customer` Şirket adları ve adres bilgileriyle doldurulmuş bir nesne koleksiyonu döndürür.  
  
 [!code-vb[VbSimpleQuerySamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#29)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifadesi, `From` koleksiyon için bir Aralık değişkeni bildirmek üzere bir yan tümce kullanır `cust` `customers` . `Select`Yan tümce, müşteri adı ve kimlik değerini seçer ve `CompanyName` `CustomerID` Yeni Aralık değişkeninin ve sütunlarını doldurur. `For Each`İfade döndürülen her nesnenin üzerinde döngü alır ve her bir `CompanyName` `CustomerID` kayıt için ve sütunlarını görüntüler.  
  
 [!code-vb[VbSimpleQuerySamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#30)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de LINQ'e Giriş](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](index.md)
- [From yan tümcesi](from-clause.md)
- [WHERE yan tümcesi](where-clause.md)
- [Order By Yan Tümcesi](order-by-clause.md)
- [Anonim Türler](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
