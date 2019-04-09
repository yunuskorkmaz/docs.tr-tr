---
title: 'Nasıl yapılır: Skaler Değerli Kullanıcı Tanımlı İşlevler Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
ms.openlocfilehash: ffb24468c81cb4ec9f41645f8888c2c4ba021609
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127185"
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a>Nasıl yapılır: Skaler Değerli Kullanıcı Tanımlı İşlevler Kullanma
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
