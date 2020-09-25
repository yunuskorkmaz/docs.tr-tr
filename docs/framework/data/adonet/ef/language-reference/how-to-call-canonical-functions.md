---
title: 'Nasıl yapılır: Kurallı İşlevler Çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
ms.openlocfilehash: acfbdbaf21fe1d454b68dfef5bf4f88d8020ea65
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204456"
---
# <a name="how-to-call-canonical-functions"></a>Nasıl yapılır: Kurallı İşlevler Çağırma

<xref:System.Data.Objects.EntityFunctions>Sınıfı, LINQ to Entities sorgularda kullanılacak kurallı işlevleri kullanıma sunan yöntemler içerir. Kurallı işlevler hakkında daha fazla bilgi için bkz. [kurallı işlevler](canonical-functions.md).  
  
> [!NOTE]
> <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A>Sınıfındaki ve <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> yöntemlerinin <xref:System.Data.Objects.EntityFunctions> Kurallı işlev eşdeğerleri yoktur.  
  
 Bir değer kümesi üzerinde hesaplama gerçekleştiren ve tek bir değer döndüren (Toplama kurallı işlevler olarak da bilinir) kurallı işlevler doğrudan çağrılabilir. Diğer kurallı işlevler, yalnızca bir LINQ to Entities sorgusunun parçası olarak çağrılabilir. Bir toplama işlevini doğrudan çağırmak için, işlevine bir öğesine geçirmeniz gerekir <xref:System.Data.Objects.ObjectQuery%601> . Daha fazla bilgi için aşağıdaki ikinci örneğe bakın.  
  
 LINQ to Entities sorgularda ortak dil çalışma zamanı (CLR) yöntemlerini kullanarak, bazı kurallı işlevleri çağırabilirsiniz. Kurallı işlevlerle eşlenen CLR yöntemlerinin listesi için bkz. [CLR yöntemi Ile kurallı Işlev eşleme](clr-method-to-canonical-function-mapping.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)kullanır. Örnek, <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> ve arasındaki farkın `SellEndDate` `SellStartDate` 365 günden daha az olduğu tüm ürünleri döndürmek için yöntemini kullanan LINQ to Entities bir sorgu yürütür:  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)kullanır. Örnek, <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> alt toplamların standart sapmasını döndürmek için doğrudan toplama yöntemini çağırır `SalesOrderHeader` . Öğesinin bir <xref:System.Data.Objects.ObjectQuery%601> LINQ to Entities sorgusunun parçası olmadan çağrılmasına izin veren işleve geçtiğini unutmayın.  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Entities Sorgularında Çağırma İşlevleri](calling-functions-in-linq-to-entities-queries.md)
- [LINQ to Entities Sorguları](queries-in-linq-to-entities.md)
