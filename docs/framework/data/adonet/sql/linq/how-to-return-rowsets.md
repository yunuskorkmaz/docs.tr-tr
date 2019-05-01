---
title: 'Nasıl yapılır: Satır Kümeleri Döndürme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 725718f5-da29-4841-9f53-aafef64ba977
ms.openlocfilehash: 599ad6f722251003ab56547ce050cbd0e8da831d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903987"
---
# <a name="how-to-return-rowsets"></a>Nasıl yapılır: Satır Kümeleri Döndürme
Bu örnek veritabanından satır döndürür ve sonucu filtrelemek için bir giriş parametresi içerir.  
  
 Bir satır kümesi döndüren bir saklı yordamı çalıştırdığınızda, kullandığınız bir *sonucu* saklı yordamdan döndürür depolayan sınıf. Daha fazla bilgi için [çözümleme LINQ to SQL kaynak kodunu](../../../../../../docs/framework/data/adonet/sql/linq/analyzing-linq-to-sql-source-code.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, müşteriler satırlarını döndürür ve bu listeyi "London" müşterinin Şehir olarak yalnızca o satırlar döndürülecek giriş parametresi kullanan bir saklı yordam temsil eder. Örnek bir numaralandırılabilir varsayar `CustomersByCityResult` sınıfı.  
  
```  
CREATE PROCEDURE [dbo].[Customers By City]  
    (@param1 NVARCHAR(20))  
AS  
BEGIN  
    -- SET NOCOUNT ON added to prevent extra result sets from  
    -- interfering with SELECT statements.  
    SET NOCOUNT ON;  
    SELECT CustomerID, ContactName, CompanyName, City from Customers  
        as c where c.City=@param1  
END  
```  
  
 [!code-csharp[DLinqSprox#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#1)]
 [!code-vb[DLinqSprox#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Saklı Yordamlar](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
- [Örnek Veritabanları İndirme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
