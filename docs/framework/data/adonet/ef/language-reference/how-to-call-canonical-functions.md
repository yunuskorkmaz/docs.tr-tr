---
title: 'Nasıl yapılır: Kurallı İşlevleri Çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
ms.openlocfilehash: a1c550b35142cffceeaf08f7d9ff049c766307e0
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397563"
---
# <a name="how-to-call-canonical-functions"></a>Nasıl yapılır: Kurallı İşlevleri Çağırma
Sınıfı <xref:System.Data.Objects.EntityFunctions> , LINQ to Entities sorgularda kullanılacak kurallı işlevleri kullanıma sunan yöntemler içerir. Kurallı işlevler hakkında daha fazla bilgi için bkz. [kurallı işlevler](canonical-functions.md).  
  
> [!NOTE]
> Sınıfındaki ve <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> yöntemlerinin Kurallı işlev eşdeğerleri yoktur. <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> <xref:System.Data.Objects.EntityFunctions>  
  
 Bir değer kümesi üzerinde hesaplama gerçekleştiren ve tek bir değer döndüren (Toplama kurallı işlevler olarak da bilinir) kurallı işlevler doğrudan çağrılabilir. Diğer kurallı işlevler, yalnızca bir LINQ to Entities sorgusunun parçası olarak çağrılabilir. Bir toplama işlevini doğrudan çağırmak için, işlevine bir <xref:System.Data.Objects.ObjectQuery%601> öğesine geçirmeniz gerekir. Daha fazla bilgi için aşağıdaki ikinci örneğe bakın.  
  
 LINQ to Entities sorgularda ortak dil çalışma zamanı (CLR) yöntemlerini kullanarak, bazı kurallı işlevleri çağırabilirsiniz. Kurallı işlevlerle eşlenen CLR yöntemlerinin listesi için bkz. [CLR yöntemi Ile kurallı Işlev eşleme](clr-method-to-canonical-function-mapping.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)kullanır. Örnek, ve <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> `SellEndDate` arasındaki`SellStartDate` farkın 365 günden daha az olduğu tüm ürünleri döndürmek için yöntemini kullanan LINQ to Entities bir sorgu yürütür:  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)kullanır. Örnek, `SalesOrderHeader` alt toplamların standart <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> sapmasını döndürmek için doğrudan toplama yöntemini çağırır. Öğesinin bir <xref:System.Data.Objects.ObjectQuery%601> LINQ to Entities sorgusunun parçası olmadan çağrılmasına izin veren işleve geçtiğini unutmayın.  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Entities Sorgularında Çağırma İşlevleri](calling-functions-in-linq-to-entities-queries.md)
- [LINQ to Entities Sorguları](queries-in-linq-to-entities.md)
