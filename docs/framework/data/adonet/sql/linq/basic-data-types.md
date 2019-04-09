---
title: Temel Veri Türleri
ms.date: 03/30/2017
ms.assetid: eca2c472-9548-4800-bd31-5d8d9f11752b
ms.openlocfilehash: 00d5c6d866453fe9ece7f2e22a579aa43c09c23e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072889"
---
# <a name="basic-data-types"></a>Temel Veri Türleri
Transact-SQL önce için LINQ to SQL sorgularında Çevir çünkü bunlar Microsoft SQL Server üzerinde yürütülür. LINQ to SQL, temel veri türleri için SQL Server'ın yaptığı aynı yerleşik işlevselliğinin destekler.  
  
## <a name="casting"></a>Atama  
 SQL Server içinde benzer ve geçerli bir dönüştürme ise örtük veya açık yayınları bir hedef CLR türü bir CLR türü kaynaktan etkinleştirilir. CLR atama hakkında daha fazla bilgi için bkz. [CType işlevi](~/docs/visual-basic/language-reference/functions/ctype-function.md) (Visual Basic) ve [olarak](~/docs/csharp/language-reference/keywords/as.md). Dönüştürme işleminden sonra atamaları doğal olarak hedef türe harita diğer CLR ifadeler davranışını eşleştirmek için CLR ifade üzerinde gerçekleştirilen işlemlerin davranışını değiştirin. Yayınları devralma eşleme bağlamında çevrilebilir. Böylece alt özgü verilerine erişilebilir nesneler için daha özel varlık subtypes çevirebilirsiniz.  
  
## <a name="equality-operators"></a>Eşitlik İşleçleri  
 LINQ to SQL temel veri türleri içinde LINQ to SQL sorguları aşağıdaki eşitlik işleçleri destekler:  
  
-   Eşit ve eşitsizlik işleci: Eşitlik ve eşitsizlik işleçleri için sayısal, desteklenen <xref:System.Boolean>, <xref:System.DateTime>, ve <xref:System.TimeSpan> türleri. Visual Basic işleçleri hakkında daha fazla bilgi için `=` ve `<>`, bkz: [Karşılaştırma işleçleri](~/docs/visual-basic/language-reference/operators/comparison-operators.md). Hakkında daha fazla bilgi için C# Karşılaştırma işleçleri `==` ve `!=`, bkz: [eşitlik işleçleri](~/docs/csharp/language-reference/operators/equality-operators.md).
  
-   Is işleci: `IS` Devralma eşleme kullanıldığında desteklenen çeviri işleci vardır. Bu doğrudan ayrıştırıcı sütununu test yerine bir nesne belirli bir varlık türüdür ve ayrıştırıcı sütunu üzerinde bir denetimi çevrildiğinde olup olmadığını belirlemek için kullanılabilir. Visual Basic hakkında daha fazla bilgi ve C# bulunan işleç, bkz: [işleci olan](~/docs/visual-basic/language-reference/operators/is-operator.md) ve [olduğu](~/docs/csharp/language-reference/keywords/is.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL-CLR Tür Eşlemesi](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [Veri Türleri ve İşlevleri](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
