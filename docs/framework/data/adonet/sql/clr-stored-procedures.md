---
title: CLR Saklı Yordamları
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: aa14c96ed226ac80a9613d3e229f35dbf5085f3b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173620"
---
# <a name="clr-stored-procedures"></a><span data-ttu-id="ad129-102">CLR Saklı Yordamları</span><span class="sxs-lookup"><span data-stu-id="ad129-102">CLR Stored Procedures</span></span>

<span data-ttu-id="ad129-103">Saklı yordamlar, skalar ifadelerde kullanılamayan yordamlardır.</span><span class="sxs-lookup"><span data-stu-id="ad129-103">Stored procedures are routines that cannot be used in scalar expressions.</span></span> <span data-ttu-id="ad129-104">Bunlar istemciye tablo sonuçları ve iletileri döndürebilir, veri tanımlama dili (DDL) ve veri işleme dili (DML) deyimlerini çağırabilir ve çıkış parametrelerini döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="ad129-104">They can return tabular results and messages to the client, invoke data definition language (DDL) and data manipulation language (DML) statements, and return output parameters.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ad129-105">Microsoft Visual Basic, çıkış parametrelerini Microsoft Visual C# ' nin desteklediği şekilde desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ad129-105">Microsoft Visual Basic does not support output parameters in the same way that Microsoft Visual C# does.</span></span> <span data-ttu-id="ad129-106">Parametreyi başvuruya göre geçirmek ve \<Out()> aşağıdaki gibi bir çıkış parametresini temsil etmek için özniteliğini uygulamak için belirtmelisiniz:</span><span class="sxs-lookup"><span data-stu-id="ad129-106">You must specify to pass the parameter by reference and apply the \<Out()> attribute to represent an output parameter, as in the following:</span></span>  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
<span data-ttu-id="ad129-107">Daha ayrıntılı bilgi için, kullanmakta olduğunuz SQL Server sürümü için [SQL Server belgelerine](/sql) bakın.</span><span class="sxs-lookup"><span data-stu-id="ad129-107">For more detailed information, see the version of [SQL Server documentation](/sql) for the version of SQL Server you're using.</span></span>
  
 <span data-ttu-id="ad129-108">**SQL Server belgeleri**</span><span class="sxs-lookup"><span data-stu-id="ad129-108">**SQL Server documentation**</span></span>

1. <span data-ttu-id="ad129-109">[CLR Saklı Yordamları](/previous-versions/sql/sql-server-2008/ms131094(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="ad129-109">[CLR Stored Procedures](/previous-versions/sql/sql-server-2008/ms131094(v=sql.100))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad129-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad129-110">See also</span></span>

- <span data-ttu-id="ad129-111">[Yönetilen kodda SQL Server 2005 nesneleri oluşturma](/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="ad129-111">[Creating SQL Server 2005 Objects In Managed Code](/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))</span></span>
- [<span data-ttu-id="ad129-112">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ad129-112">ADO.NET Overview</span></span>](../ado-net-overview.md)
