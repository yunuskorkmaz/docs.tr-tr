---
title: 'Nasıl yapılır: skaler değerli Kullanıcı tanımlı Işlevler kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 714e252f-c053-4bbb-b1f3-924111cd4d97
ms.openlocfilehash: dfe82fd50eb3eedeaff9082a4288901f72197795
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003230"
---
# <a name="how-to-use-scalar-valued-user-defined-functions"></a>Nasıl yapılır: skaler değerli Kullanıcı tanımlı Işlevler kullanma
@No__t-0 özniteliğini kullanarak, bir sınıfta tanımlanan bir istemci yöntemini Kullanıcı tanımlı bir işlev ile eşleyebilirsiniz. Yöntemin gövdesi, yöntem çağrısının amacını yakalayan bir ifade oluşturur ve bu ifadeyi çeviri ve yürütme için <xref:System.Data.Linq.DataContext> ' a geçirir.  
  
> [!NOTE]
> Doğrudan yürütme yalnızca işlev bir sorgu dışında çağrıldığında gerçekleşir. Daha fazla bilgi için bkz. [nasıl yapılır: Kullanıcı tanımlı Işlevleri Iç satır Içinde çağırma](how-to-call-user-defined-functions-inline.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki SQL kodu, skalar değerli Kullanıcı tanımlı bir işlevi `ReverseCustName()` ' dır.  
  
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

- [Kullanıcı Tanımlı İşlevler](user-defined-functions.md)
