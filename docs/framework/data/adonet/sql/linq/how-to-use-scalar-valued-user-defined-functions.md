---
title: 'Nasıl yapılır: Skaler Değerli Kullanıcı Tanımlı İşlevler Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
ms.openlocfilehash: 0d757e3c37f347014eb2ef90b4e61ddd205dd012
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938663"
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a>Nasıl yapılır: Skaler Değerli Kullanıcı Tanımlı İşlevler Kullanma
<xref:System.Data.Linq.Mapping.FunctionAttribute> Özniteliğini kullanarak, bir sınıfta tanımlanan istemci yöntemini Kullanıcı tanımlı bir işlev ile eşleyebilirsiniz. Yöntemin gövdesi, yöntem çağrısının amacını yakalayan bir ifade oluşturur ve bu ifadeyi <xref:System.Data.Linq.DataContext> çeviri ve yürütmeye geçirir.  
  
> [!NOTE]
> Doğrudan yürütme yalnızca işlev bir sorgu dışında çağrıldığında gerçekleşir. Daha fazla bilgi için [nasıl yapılır: Kullanıcı tanımlı Işlevleri satır Içinde](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md)çağırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki SQL kodu, skaler değerli Kullanıcı tanımlı bir işlev `ReverseCustName()`gösterir.  
  
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
  
 Bu kod için aşağıdaki gibi bir istemci yöntemi eşleyebilirsiniz:  
  
 [!code-csharp[DLinqUDFS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#3)]
 [!code-vb[DLinqUDFS#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanıcı Tanımlı İşlevler](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
