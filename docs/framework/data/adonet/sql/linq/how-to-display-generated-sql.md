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
# <a name="how-to-display-generated-sql"></a><span data-ttu-id="78fbf-102">Nasıl yapılır: oluşturulan SQL 'i görüntüleme</span><span class="sxs-lookup"><span data-stu-id="78fbf-102">How to: Display Generated SQL</span></span>
<span data-ttu-id="78fbf-103">Sorgular için oluşturulan SQL kodunu ve <xref:System.Data.Linq.DataContext.Log%2A> özelliğini kullanarak değişiklik işlemeyi görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78fbf-103">You can view the SQL code generated for queries and change processing by using the <xref:System.Data.Linq.DataContext.Log%2A> property.</span></span> <span data-ttu-id="78fbf-104">Bu yaklaşım, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] işlevselliğini anlamak ve belirli sorunları gidermek için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="78fbf-104">This approach can be useful for understanding [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] functionality and for debugging specific problems.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78fbf-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="78fbf-105">Example</span></span>  
 <span data-ttu-id="78fbf-106">Aşağıdaki örnek, kod yürütülmeden önce konsol penceresinde SQL kodunu göstermek için <xref:System.Data.Linq.DataContext.Log%2A> özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="78fbf-106">The following example uses the <xref:System.Data.Linq.DataContext.Log%2A> property to display SQL code in the console window before the code is executed.</span></span>  <span data-ttu-id="78fbf-107">Bu özelliği sorgu, INSERT, Update ve DELETE komutlarıyla birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78fbf-107">You can use this property with query, insert, update, and delete commands.</span></span>  
  
 <span data-ttu-id="78fbf-108">Konsol penceresindeki satırlar, aşağıdaki Visual Basic veya C# kodu yürüttüğünüzde gördüğünüz şeydir.</span><span class="sxs-lookup"><span data-stu-id="78fbf-108">The lines from the console window are what you see when you execute the Visual Basic or C# code that follows.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="78fbf-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78fbf-109">See also</span></span>

- [<span data-ttu-id="78fbf-110">Hata Ayıklama Desteği</span><span class="sxs-lookup"><span data-stu-id="78fbf-110">Debugging Support</span></span>](debugging-support.md)
