---
title: 'Nasıl yapılır: Oluşturulan SQL’i Görüntüleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 626492c0-5ee3-4675-88e8-8c40379510b6
ms.openlocfilehash: 8a69b3ae83d7f701428b3183f2b80e0d44a06537
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103629"
---
# <a name="how-to-display-generated-sql"></a><span data-ttu-id="a9f20-102">Nasıl yapılır: Oluşturulan SQL’i Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="a9f20-102">How to: Display Generated SQL</span></span>
<span data-ttu-id="a9f20-103">Sorgular ve değişiklik kullanarak işleme için oluşturulan SQL kodu görüntüleyebilirsiniz <xref:System.Data.Linq.DataContext.Log%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a9f20-103">You can view the SQL code generated for queries and change processing by using the <xref:System.Data.Linq.DataContext.Log%2A> property.</span></span> <span data-ttu-id="a9f20-104">Bu yaklaşım anlamak için yararlı olabilir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] işlevselliği ve belirli sorunları hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="a9f20-104">This approach can be useful for understanding [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] functionality and for debugging specific problems.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9f20-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="a9f20-105">Example</span></span>  
 <span data-ttu-id="a9f20-106">Aşağıdaki örnekte <xref:System.Data.Linq.DataContext.Log%2A> özelliği kod yürütülmeden önce SQL kodu konsol penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a9f20-106">The following example uses the <xref:System.Data.Linq.DataContext.Log%2A> property to display SQL code in the console window before the code is executed.</span></span>  <span data-ttu-id="a9f20-107">Bu özelliği kullanmak için sorgu, ekleme, güncelleştirme ve silme komutları.</span><span class="sxs-lookup"><span data-stu-id="a9f20-107">You can use this property with query, insert, update, and delete commands.</span></span>  
  
 <span data-ttu-id="a9f20-108">Visual Basic yürüttüğünüzde gördüğünüz satırla konsol penceresinden veya C# izleyen kod.</span><span class="sxs-lookup"><span data-stu-id="a9f20-108">The lines from the console window are what you see when you execute the Visual Basic or C# code that follows.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a9f20-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9f20-109">See also</span></span>

- [<span data-ttu-id="a9f20-110">Hata Ayıklama Desteği</span><span class="sxs-lookup"><span data-stu-id="a9f20-110">Debugging Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)
