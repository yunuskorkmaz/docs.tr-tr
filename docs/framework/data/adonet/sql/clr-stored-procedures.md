---
description: 'Daha fazla bilgi edinin: CLR saklı yordamları'
title: CLR Saklı Yordamları
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: d136d3dcb12be2f87276a410c9fa0e713b7dfd52
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723627"
---
# <a name="clr-stored-procedures"></a><span data-ttu-id="9bfa0-103">CLR Saklı Yordamları</span><span class="sxs-lookup"><span data-stu-id="9bfa0-103">CLR Stored Procedures</span></span>

<span data-ttu-id="9bfa0-104">Saklı yordamlar, skalar ifadelerde kullanılamayan yordamlardır.</span><span class="sxs-lookup"><span data-stu-id="9bfa0-104">Stored procedures are routines that cannot be used in scalar expressions.</span></span> <span data-ttu-id="9bfa0-105">Bunlar istemciye tablo sonuçları ve iletileri döndürebilir, veri tanımlama dili (DDL) ve veri işleme dili (DML) deyimlerini çağırabilir ve çıkış parametrelerini döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="9bfa0-105">They can return tabular results and messages to the client, invoke data definition language (DDL) and data manipulation language (DML) statements, and return output parameters.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9bfa0-106">Microsoft Visual Basic, çıkış parametrelerini Microsoft Visual C# ' nin desteklediği şekilde desteklemez.</span><span class="sxs-lookup"><span data-stu-id="9bfa0-106">Microsoft Visual Basic does not support output parameters in the same way that Microsoft Visual C# does.</span></span> <span data-ttu-id="9bfa0-107">Parametreyi başvuruya göre geçirmek ve \<Out()> aşağıdaki gibi bir çıkış parametresini temsil etmek için özniteliğini uygulamak için belirtmelisiniz:</span><span class="sxs-lookup"><span data-stu-id="9bfa0-107">You must specify to pass the parameter by reference and apply the \<Out()> attribute to represent an output parameter, as in the following:</span></span>  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
<span data-ttu-id="9bfa0-108">Daha ayrıntılı bilgi için, kullanmakta olduğunuz SQL Server sürümü için [SQL Server belgelerine](/sql) bakın.</span><span class="sxs-lookup"><span data-stu-id="9bfa0-108">For more detailed information, see the version of [SQL Server documentation](/sql) for the version of SQL Server you're using.</span></span>
  
 <span data-ttu-id="9bfa0-109">**SQL Server belgeleri**</span><span class="sxs-lookup"><span data-stu-id="9bfa0-109">**SQL Server documentation**</span></span>

1. <span data-ttu-id="9bfa0-110">[CLR Saklı Yordamları](/previous-versions/sql/sql-server-2008/ms131094(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="9bfa0-110">[CLR Stored Procedures](/previous-versions/sql/sql-server-2008/ms131094(v=sql.100))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bfa0-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9bfa0-111">See also</span></span>

- <span data-ttu-id="9bfa0-112">[Yönetilen kodda SQL Server 2005 nesneleri oluşturma](/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="9bfa0-112">[Creating SQL Server 2005 Objects In Managed Code](/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))</span></span>
- [<span data-ttu-id="9bfa0-113">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9bfa0-113">ADO.NET Overview</span></span>](../ado-net-overview.md)
