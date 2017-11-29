---
title: "Nasıl yapılır: çağrı kurallı işlevleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 26bd528a7c2ad77cb801eb294c34e43c60d2bf76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-canonical-functions"></a>Nasıl yapılır: çağrı kurallı işlevleri
<xref:System.Data.Objects.EntityFunctions> Sınıfı LINQ to Entities sorgularında kullanmak için kurallı işlevleri yöntemlerini içerir. Kurallı işlevleri hakkında daha fazla bilgi için bkz: [kurallı işlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).  
  
> [!NOTE]
>  <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> Ve <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> yöntemleri <xref:System.Data.Objects.EntityFunctions> sınıfı kurallı işlevi eşdeğerleri sahip değil.  
  
 Doğrudan bir değerler kümesi üzerinde bir hesaplama gerçekleştirmek ve tek bir değer (olarak da bilinen toplama kurallı işlevleri) döndürmesi kurallı işlevler çağrılabilir. Kurallı diğer işlevleri yalnızca bir LINQ to Entities sorgusunun bir parçası olarak çağrılabilir. Bir toplama işlevi doğrudan çağırmak için geçmesi gereken bir <xref:System.Data.Objects.ObjectQuery%601> işlevi. Daha fazla bilgi için aşağıdaki ikinci örneğe bakın.  
  
 Ortak dil çalışma zamanı (CLR) yöntemleri LINQ to Entities sorgularında kullanarak bazı kurallı işlevleri çağırabilir. Kurallı işlevlere Eşle CLR yöntemlerin listesi için bkz: [kurallı işlev eşleme CLR yönteme](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır [AdventureWorks satış modeli](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832). Örnek bir LINQ to kullanan varlıklar sorgu yürütür <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> tüm ürünleri için döndürülecek yöntemi arasındaki farkı `SellEndDate` ve `SellStartDate` 365 günden:  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır [AdventureWorks satış modeli](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832). Örnek toplama çağırır <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> standart sapmasını doğrudan döndürülecek yöntemi `SalesOrderHeader` toplamları. Unutmayın bir <xref:System.Data.Objects.ObjectQuery%601> bir LINQ to Entities sorgusunun parçası olmadan çağrılmasına izin veren işlevi geçirilir.  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to Entities sorgularında işlevleri çağırma](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [LINQ to Entities sorguları](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
