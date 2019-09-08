---
title: 'Nasıl yapılır: Satır Kümeleri Döndürme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 725718f5-da29-4841-9f53-aafef64ba977
ms.openlocfilehash: 5ec188e0345140297062d0a10dfbbc4a294bbb7d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781602"
---
# <a name="how-to-return-rowsets"></a>Nasıl yapılır: Satır Kümeleri Döndürme
Bu örnek, veritabanından bir satır kümesi döndürür ve sonucu filtrelemek için bir giriş parametresi içerir.  
  
 Bir satır kümesi döndüren bir saklı yordamı çalıştırdığınızda, saklı yordamdaki dönüşleri depolayan bir *sonuç* sınıfı kullanırsınız. Daha fazla bilgi için bkz. [LINQ to SQL kaynak kodu çözümleme](analyzing-linq-to-sql-source-code.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, müşteri satırları döndüren bir saklı yordamı temsil eder ve yalnızca müşteri şehri olarak "Londra" listesini içeren satırları döndürmek için bir giriş parametresi kullanır. Örnek, sıralanabilir `CustomersByCityResult` bir sınıfı varsayar.  
  
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

- [Saklı Yordamlar](stored-procedures.md)
- [Örnek Veritabanları İndirme](downloading-sample-databases.md)
