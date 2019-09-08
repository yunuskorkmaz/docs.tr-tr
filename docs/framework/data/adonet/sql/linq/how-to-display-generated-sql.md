---
title: 'Nasıl yapılır: Oluşturulan SQL’i Görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 626492c0-5ee3-4675-88e8-8c40379510b6
ms.openlocfilehash: f3ed431709266b636804c6c00450b26684550d8b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793761"
---
# <a name="how-to-display-generated-sql"></a>Nasıl yapılır: Oluşturulan SQL’i Görüntüleme
<xref:System.Data.Linq.DataContext.Log%2A> Özelliğini kullanarak sorgular için oluşturulan SQL kodunu ve değişiklik işlemeyi görüntüleyebilirsiniz. Bu yaklaşım, işlevselliği anlamak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ve belirli sorunların hatalarını ayıklamak için yararlı olabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, kod yürütülmeden <xref:System.Data.Linq.DataContext.Log%2A> önce konsol penceresinde SQL kodunu göstermek için özelliğini kullanır.  Bu özelliği sorgu, INSERT, Update ve DELETE komutlarıyla birlikte kullanabilirsiniz.  
  
 Konsol penceresindeki satırlar, aşağıdaki Visual Basic veya C# kodu yürüttüğünüzde gördüğünüz şeydir.  
  
```  
SELECT [t0].[CustomerID], [t0].[CompanyName], [t0].[ContactName], [t0].[ContactT  
itle], [t0].[Address], [t0].[City], [t0].[Region], [t0].[PostalCode], [t0].[Coun  
try], [t0].[Phone], [t0].[Fax]  
FROM [dbo].[Customers] AS [t0]  
WHERE [t0].[City] = @p0  
-- @p0: Input String (Size = 6; Prec = 0; Scale = 0) [London]  
-- Context: SqlProvider(Sql2005) Model: AttributedMetaModel Build: 3.5.20810.0  
```  
  
```  
AROUT  
BSBEV  
CONSH  
EASTC  
NORTS  
SEVES  
```  
  
 [!code-csharp[DLinqDebuggingSupport#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#1)]
 [!code-vb[DLinqDebuggingSupport#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Desteği](debugging-support.md)
