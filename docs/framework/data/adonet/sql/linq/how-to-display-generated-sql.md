---
title: 'Nasıl yapılır: Oluşturulan SQL’i Görüntüleme'
description: LINQ to SQL işlevlerinin ve hata ayıklamanın anlaşılmasına yardımcı olmak için Log özelliğini kullanarak sorgular için oluşturulan SQL kodunu görüntülemeyi öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 626492c0-5ee3-4675-88e8-8c40379510b6
ms.openlocfilehash: 5e75a8aadf4631f0a6e50641db72ba7b83af41fe
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286384"
---
# <a name="how-to-display-generated-sql"></a>Nasıl yapılır: Oluşturulan SQL’i Görüntüleme
Özelliğini kullanarak sorgular için oluşturulan SQL kodunu ve değişiklik işlemeyi görüntüleyebilirsiniz <xref:System.Data.Linq.DataContext.Log%2A> . Bu yaklaşım, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] işlevselliği anlamak ve belirli sorunların hatalarını ayıklamak için yararlı olabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Data.Linq.DataContext.Log%2A> kod yürütülmeden önce konsol PENCERESINDE SQL kodunu göstermek için özelliğini kullanır.  Bu özelliği sorgu, INSERT, Update ve DELETE komutlarıyla birlikte kullanabilirsiniz.  
  
 Konsol penceresindeki satırlar, aşağıdaki Visual Basic veya C# kodunu çalıştırdığınızda gördüğünüz şeydir.  
  
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
