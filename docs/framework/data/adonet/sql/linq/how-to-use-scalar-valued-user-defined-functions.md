---
title: 'Nasıl yapılır: Skaler değerli kullanıcı tanımlı işlevler kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
ms.openlocfilehash: 33c6ae89184b90ba69cc9c3c01f0b1ec9d7ff1cb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54661691"
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a>Nasıl yapılır: Skaler değerli kullanıcı tanımlı işlevler kullanma
Kullanıcı tanımlı bir işlev için bir sınıf tarafından tanımlanan bir istemci yöntemi eşleyebilirsiniz <xref:System.Data.Linq.Mapping.FunctionAttribute> özniteliği. Yönteminin gövdesinin yöntem çağrısının hedefi yakalar ve bu ifadeyi geçirmeden bir ifade oluşturur Not <xref:System.Data.Linq.DataContext> çeviri ve yürütme için.  
  
> [!NOTE]
>  Yalnızca bir sorgu dışında işlev çağrılırsa, doğrudan yürütme gerçekleşir. Daha fazla bilgi için [nasıl yapılır: Kullanıcı tanımlı işlevleri satır içi olarak çağırdığınızda](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki SQL kodunu bir skaler değerli kullanıcı tanımlı işlev sunar `ReverseCustName()`.  
  
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
  
 Bu kod için bir istemci yöntemi aşağıdaki gibi eşlemeniz:  
  
 [!code-csharp[DLinqUDFS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#3)]
 [!code-vb[DLinqUDFS#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Kullanıcı Tanımlı İşlevler](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
