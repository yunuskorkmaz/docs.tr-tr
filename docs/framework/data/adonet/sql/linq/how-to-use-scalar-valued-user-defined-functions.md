---
title: "Nasıl yapılır: kullanıcı tanımlı işlevler skaler değerli kullanın"
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
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0788e70230fa78281d65be9eb6e0f45e58f25806
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a>Nasıl yapılır: kullanıcı tanımlı işlevler skaler değerli kullanın
Kullanıcı tanımlı bir işlev için bir sınıf tarafından tanımlanan bir istemci yöntemi eşleyebilirsiniz <xref:System.Data.Linq.Mapping.FunctionAttribute> özniteliği. Yönteminin gövdesi yöntem çağrısının amacı yakalar ve bu ifadeye aktaran bir ifade oluşturur Not <xref:System.Data.Linq.DataContext> çeviri ve yürütme.  
  
> [!NOTE]
>  Yalnızca bir sorgu dışında işlevi çağrıldıysa doğrudan yürütme oluşur. Daha fazla bilgi için bkz: [nasıl yapılır: Call User-Defined işlevler satır içi](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki SQL kod skaler değerli kullanıcı tanımlı bir işlev gösterir `ReverseCustName()`.  
  
```  
CREATE FUNCTION ReverseCustName(@string varchar(100))  
RETURNS varchar(100)  
AS  
BEGIN  
    DECLARE @custName varchar(100)  
    -- Implementation left as exercise for users.  
    RETURN @custName  
END  
```  
  
 Bu kodun aşağıdaki gibi bir istemci yöntemi eşleyen:  
  
 [!code-csharp[DLinqUDFS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#3)]
 [!code-vb[DLinqUDFS#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#3)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kullanıcı Tanımlı İşlevler](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
