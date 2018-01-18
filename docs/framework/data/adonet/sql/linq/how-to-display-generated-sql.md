---
title: "Nasıl yapılır: görüntü oluşturulan SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 626492c0-5ee3-4675-88e8-8c40379510b6
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5c75ac8734a92fc76613643c3831d0b767e92feb
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-display-generated-sql"></a>Nasıl yapılır: görüntü oluşturulan SQL
Sorgular ve değişikliği kullanarak işleme için oluşturulan SQL kodu görüntüleyebilirsiniz <xref:System.Data.Linq.DataContext.Log%2A> özelliği. Bu yaklaşımı anlamak için kullanışlıdır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] işlevselliği ve belirli sorunları hata ayıklama için.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır <xref:System.Data.Linq.DataContext.Log%2A> kod yürütülmeden önce SQL kodunu konsol penceresinde görüntülenecek özelliği.  Bu özelliği kullanmak sorgu, Ekle, Güncelleştir ve komutları silin.  
  
 Konsol penceresinde satırlarından yürüttüğünüzde gördüğünüzü olan [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] veya aşağıdaki C# kodu.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Desteği](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)
