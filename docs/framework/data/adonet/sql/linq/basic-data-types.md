---
title: Temel Veri Türleri
ms.date: 03/30/2017
ms.assetid: eca2c472-9548-4800-bd31-5d8d9f11752b
ms.openlocfilehash: b01a49afa99fc7ecdb7a113a5056e37d901527a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964072"
---
# <a name="basic-data-types"></a>Temel Veri Türleri
LINQ to SQL sorguları, Microsoft SQL Server yürütülmeden önce Transact-SQL ' e çevirdiklerinden. LINQ to SQL, temel veri türleri için SQL Server gereken yerleşik işlevlerin çoğunu destekler.  
  
## <a name="casting"></a>Atama  
 SQL Server içinde benzer bir geçerli dönüştürme varsa örtük veya açık yayınlar bir kaynak CLR türünden hedef CLR türüne etkinleştirilir. CLR atama hakkında daha fazla bilgi için bkz. [CType işlevi](../../../../../visual-basic/language-reference/functions/ctype-function.md) (Visual Basic) ve [tür-test ve cast işleçleri](../../../../../csharp/language-reference/operators/type-testing-and-cast.md). Dönüştürmeden sonra, bir CLR ifadesinde gerçekleştirilen işlemlerin davranışını, doğal olarak hedef türüyle eşlenen diğer CLR ifadelerinin davranışıyla eşleşecek şekilde değiştirir. Ayrıca, devralma eşleme bağlamına de çevrilebilir. Nesneler, alt türe özgü verilere erişilebilmesi için daha fazla belirli varlık alt türüne dönüşebilir.  
  
## <a name="equality-operators"></a>Eşitlik İşleçleri  
 LINQ to SQL, LINQ to SQL sorguları içindeki temel veri türlerinde aşağıdaki eşitlik işleçlerini destekler:  
  
- Eşittir ve eşitsizlik Işleci: Eşitlik ve eşitsizlik işleçleri, sayısal, <xref:System.Boolean>, <xref:System.DateTime>, ve <xref:System.TimeSpan> türler için desteklenir. Visual Basic işleçleri `=` ve `<>`hakkında daha fazla bilgi için bkz. [karşılaştırma işleçleri](../../../../../visual-basic/language-reference/operators/comparison-operators.md). Karşılaştırma işleçleri C# `==` ve `!=`hakkında daha fazla bilgi için bkz. [eşitlik işleçleri](../../../../../csharp/language-reference/operators/equality-operators.md).
  
- İşleç: Devralma eşlemesi kullanılırken işlecin desteklenen bir çevirisi vardır. `IS` Bir nesnenin belirli bir varlık türünde olup olmadığını ve ayrıştırıcı sütununda bir denetim 'e döndürülüp çevrilmeyeceğini anlamak için ayrıştırıcı sütununun doğrudan test edilmesi yerine kullanılabilir. Visual Basic ve C# işleçleri hakkında daha fazla bilgi için bkz. [işleç](../../../../../visual-basic/language-reference/operators/is-operator.md) ve [,](../../../../../csharp/language-reference/operators/type-testing-and-cast.md#is-operator).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL-CLR Tür Eşlemesi](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [Veri Türleri ve İşlevleri](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
