---
title: "Select Tümcesi (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QuerySelect
helpviewer_keywords:
- Select statement [Visual Basic]
- Select clause [Visual Basic]
- queries [Visual Basic], Select
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a9d8cabcbd8554ca2aee639eaac8a52f0485a266
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="select-clause-visual-basic"></a>Select Tümcesi (Visual Basic)
Bir sorgunun sonucu tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## <a name="parts"></a>Bölümler  
 `var1`  
 İsteğe bağlı. Sütun ifadesi sonuçlarını başvurmak için kullanılan bir diğer ad.  
  
 `fieldName1`  
 Gerekli. Sorgu sonucunda döndürülecek alanının adı.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz `Select` bir sorgudan döndürülecek sonuç tanımlamak için yan tümcesi. Bu, ya da bir sorgu tarafından oluşturulan yeni bir anonim tür üyelerini tanımlamak ya da bir sorgu tarafından döndürülen adlandırılmış bir türün üyeleri hedef sağlar. `Select` Yan tümcesi bir sorgu için gerekli değildir. Öyle değilse `Select` yan tümcesi belirtilirse, sorgu geçerli kapsam için tanımlanan aralık değişkeni tüm üyeleri dayanan bir türü döndürür. Daha fazla bilgi için bkz: [anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md). Bir adlandırılmış türü bir sorgu oluşturduğunda, bir sonuç türü döndürülecek <xref:System.Collections.Generic.IEnumerable%601> burada `T` oluşturulan türüdür.  
  
 `Select` Yan tümcesi geçerli kapsamdaki herhangi bir değişkeni başvuru. Bu aralık değişkeni tanımlanan içerir `From` yan tümcesi (veya `From` yan tümceleri). Ayrıca tarafından diğer ad ile oluşturulan tüm yeni değişkenlerini içerir `Aggregate`, `Let`, `Group By`, veya `Group Join` yan tümcesi ya da bir önceki değişkenlerinden `Select` sorgu ifadesinde yan tümcesi. `Select` Yan tümcesi de statik değerleri içerir. Örneğin, aşağıdaki kod örneğinde bir sorgu ifadesi içinde gösterilir ve `Select` yan tümcesi dört üyeleri sahip yeni anonim bir tür olarak sorgu sonucu tanımlar: `ProductName`, `Price`, `Discount`, ve `DiscountedPrice`. `ProductName` Ve `Price` üye değerlerinin tanımlanan ürün aralık değişkeni gelen alınır `From` yan tümcesi. `DiscountedPrice` Üye değeri hesaplanan `Let` yan tümcesi. `Discount` Üye statik bir değerdir.  
  
 [!code-vb[VbSimpleQuerySamples#27](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_1.vb)]  
  
 `Select` Yan tümcesinin aralık değişkeni sonraki sorgu yan tümceleri için yeni bir dizi tanıtır ve önceki aralığı değişkenlerdir artık kapsamda. Son `Select` yan tümcesi bir sorgu ifadesinde sorgu dönüş değerini belirler. Örneğin, aşağıdaki sorguyu şirket toplam 500 aşan her müşteri siparişi için adı ve sıra kimliği döndürür. İlk `Select` yan tümcesi tanımlar için aralık değişkeni `Where` yan tümcesi ve ikinci `Select` yan tümcesi. İkinci `Select` yan tümcesi yeni anonim bir tür olarak sorgu tarafından döndürülen değerleri tanımlar.  
  
 [!code-vb[VbSimpleQuerySamples#28](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_2.vb)]  
  
 Varsa `Select` yan tümcesi tanımlar dönmek için tek bir öğe, bu tek öğe türünü birtakım sorgu ifadesi döndürür. Varsa `Select` yan tümcesi döndürmek için birden çok öğe tanımlar, sorgu ifadesi seçili öğeleri temel alan yeni anonim bir tür koleksiyonunu döndürür. Örneğin, aşağıdaki iki sorguları temel iki farklı türler döndürür `Select` yan tümcesi. İlk sorguyu şirket adları topluluğu dize olarak döndürür. İkinci sorguyu koleksiyonunu döndürür `Customer` nesneleri şirket adlarını ve adres bilgilerini ile doldurulur.  
  
 [!code-vb[VbSimpleQuerySamples#29](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_3.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sorgu ifade kullanan bir `From` yan tümcesinin aralık değişkeni bildirmek için `cust` için `customers` koleksiyonu. `Select` Yan tümcesi müşteri adı ve kimliği değeri seçer ve dolduran `CompanyName` ve `CustomerID` yeni aralık değişkeni sütunlarının. `For Each` Deyimi döngü döndürülen her nesne ve görüntüler `CompanyName` ve `CustomerID` her kayıt için sütun.  
  
 [!code-vb[VbSimpleQuerySamples#30](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_4.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Sorguları](../../../visual-basic/language-reference/queries/queries.md)  
 [From yan tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Burada yan tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)  
 [Order By tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Anonim türler](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
