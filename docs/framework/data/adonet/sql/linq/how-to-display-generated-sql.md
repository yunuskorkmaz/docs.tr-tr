---
title: "Nasıl yapılır: oluşturulan SQL 'i görüntüleme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 626492c0-5ee3-4675-88e8-8c40379510b6
ms.openlocfilehash: 15fc6a50d232ea12b229b7b2790c0398bc1c370d
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002974"
---
# <a name="how-to-display-generated-sql"></a>Nasıl yapılır: oluşturulan SQL 'i görüntüleme
Sorgular için oluşturulan SQL kodunu ve <xref:System.Data.Linq.DataContext.Log%2A> özelliğini kullanarak değişiklik işlemeyi görüntüleyebilirsiniz. Bu yaklaşım, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] işlevselliğini anlamak ve belirli sorunları gidermek için yararlı olabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, kod yürütülmeden önce konsol penceresinde SQL kodunu göstermek için <xref:System.Data.Linq.DataContext.Log%2A> özelliğini kullanır.  Bu özelliği sorgu, INSERT, Update ve DELETE komutlarıyla birlikte kullanabilirsiniz.  
  
 Konsol penceresindeki satırlar, aşağıdaki Visual Basic veya C# kodu yürüttüğünüzde gördüğünüz şeydir.  
  
```console  
SELECT [t0].[CustomerID], [t0].[CompanyName], [t0].[ContactName], [t0].[ContactT  
itle], [t0].[Address], [t0].[City], [t0].[Region], [t0].[PostalCode], [t0].[Coun  
try], [t0].[Phone], [t0].[Fax]  
FROM [dbo].[Customers] AS [t0]  
WHERE [t0].[City] = @p0  
-- @p0: Input String (Size = 6; Prec = 0; Scale = 0) [London]  
-- Context: SqlProvider(Sql2005) Model: AttributedMetaModel Build: 3.5.20810.0  
```  
  
```console  
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
