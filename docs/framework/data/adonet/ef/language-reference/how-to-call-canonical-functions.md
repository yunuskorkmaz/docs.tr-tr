---
title: 'Nasıl yapılır: Kurallı İşlevleri Çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
ms.openlocfilehash: 6e555b3d896862db491b34e11564e70bbe2d15eb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213161"
---
# <a name="how-to-call-canonical-functions"></a>Nasıl yapılır: Kurallı İşlevleri Çağırma
<xref:System.Data.Objects.EntityFunctions> Sınıfı LINQ to Entities sorgularında kullanmak için kurallı işlevler sunan yöntemlerini içerir. Kurallı işlevler hakkında daha fazla bilgi için bkz: [kurallı işlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).  
  
> [!NOTE]
>  <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> Ve <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> yöntemleri <xref:System.Data.Objects.EntityFunctions> sınıfı kurallı işlev eşdeğerleri sahip değil.  
  
 Bir değerler kümesi üzerinde bir hesaplama gerçekleştirmek ve (diğer adıyla toplu kurallı işlevler) tek bir değer döndürmesi kurallı işlevler doğrudan çağrılabilir. Diğer kurallı işlevler yalnızca bir LINQ to Entities sorgusunda bir parçası olarak çağrılabilir. Bir toplama işlevi doğrudan çağırmak için geçmelidir bir <xref:System.Data.Objects.ObjectQuery%601> işlevi. Daha fazla bilgi için aşağıdaki ikinci örneğe bakın.  
  
 Ortak dil çalışma zamanı (CLR) yöntemleri LINQ to Entities sorgularında kullanarak bazı kurallı işlevler çağırabilir. Kurallı işlevler için harita CLR yöntemlerinde listesi için bkz. [CLR yöntemini kurallı işlev eşleme Mapping](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte [AdventureWorks satışları modeli](https://archive.codeplex.com/?p=msftdbprodsamples). Örnek bir LINQ to Entities sorgusunda, kullanır yürütür <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> tüm ürünler için döndürülecek yöntemi arasındaki farkı `SellEndDate` ve `SellStartDate` küçüktür 365 gün:  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte [AdventureWorks satışları modeli](https://archive.codeplex.com/?p=msftdbprodsamples). Örnek toplama çağırır <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> standart sapmasını doğrudan döndürülecek yöntemi `SalesOrderHeader` alt toplamları. Unutmayın bir <xref:System.Data.Objects.ObjectQuery%601> bir LINQ to Entities sorgusunda parçası olmadan çağrılmasına izin veren işleve geçirilir.  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Entities Sorgularında Çağırma İşlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
- [LINQ to Entities Sorguları](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
