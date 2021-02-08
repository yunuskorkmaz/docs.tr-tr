---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Scalar-Valued User-Defined Işlevleri kullanma'
title: 'Nasıl yapılır: Skaler Değerli Kullanıcı Tanımlı İşlevler Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
ms.openlocfilehash: e606dd3f840b8f082928217c6118b48d8d4a2e5c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785817"
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a>Nasıl yapılır: Skaler Değerli Kullanıcı Tanımlı İşlevler Kullanma

Özniteliğini kullanarak, bir sınıfta tanımlanan istemci yöntemini Kullanıcı tanımlı bir işlev ile eşleyebilirsiniz <xref:System.Data.Linq.Mapping.FunctionAttribute> . Yöntemin gövdesi, yöntem çağrısının amacını yakalayan bir ifade oluşturur ve bu ifadeyi <xref:System.Data.Linq.DataContext> çeviri ve yürütmeye geçirir.  
  
> [!NOTE]
> Doğrudan yürütme yalnızca işlev bir sorgu dışında çağrıldığında gerçekleşir. Daha fazla bilgi için bkz. [nasıl yapılır: User-Defined Işlevlerini satır Içi çağırma](how-to-call-user-defined-functions-inline.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki SQL kodu, skaler değerli Kullanıcı tanımlı bir işlev gösterir `ReverseCustName()` .  
  
```sql  
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

- [Kullanıcı tanımlı Işlevler](user-defined-functions.md)
