---
title: 'Nasıl yapılır: kullanıcı tanımlı işlevler skaler değerli kullanın'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
ms.openlocfilehash: 3748f7b865de22353c8c0a91aaf52e672455ed38
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355385"
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
