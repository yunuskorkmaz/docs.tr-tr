---
title: CLR Saklı Yordamları
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: 9b31d93c1ebc0af9aa8e41b3a4c328af62da7e23
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61878337"
---
# <a name="clr-stored-procedures"></a><span data-ttu-id="a5a32-102">CLR Saklı Yordamları</span><span class="sxs-lookup"><span data-stu-id="a5a32-102">CLR Stored Procedures</span></span>
<span data-ttu-id="a5a32-103">Saklı yordamlar skaler ifadelerde kullanılamaz yordamlarını içindir.</span><span class="sxs-lookup"><span data-stu-id="a5a32-103">Stored procedures are routines that cannot be used in scalar expressions.</span></span> <span data-ttu-id="a5a32-104">Tablo sonuçları ve iletileri istemciye döndürür, veri tanımlama dili (DDL) ve veri işleme dili (DML) deyimleri çağırabilir ve çıkış parametresi döndür.</span><span class="sxs-lookup"><span data-stu-id="a5a32-104">They can return tabular results and messages to the client, invoke data definition language (DDL) and data manipulation language (DML) statements, and return output parameters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5a32-105">Microsoft Visual Basic, Microsoft Visual C# yaptığı aynı şekilde çıkış parametreleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="a5a32-105">Microsoft Visual Basic does not support output parameters in the same way that Microsoft Visual C# does.</span></span> <span data-ttu-id="a5a32-106">Parametre başvuruya göre geçirin ve uygulamak için belirtmelisiniz \<Out() > özniteliği aşağıdaki gibi bir çıktı parametresi temsil etmek için:</span><span class="sxs-lookup"><span data-stu-id="a5a32-106">You must specify to pass the parameter by reference and apply the \<Out()> attribute to represent an output parameter, as in the following:</span></span>  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
<span data-ttu-id="a5a32-107">Sürümü, daha ayrıntılı bilgi için bkz. [SQL Server belgeleri](/sql) kullanmakta olduğunuz SQL Server sürümü için.</span><span class="sxs-lookup"><span data-stu-id="a5a32-107">For more detailed information, see the version of [SQL Server documentation](/sql) for the version of SQL Server you're using.</span></span>
  
 <span data-ttu-id="a5a32-108">**SQL Server belgeleri**</span><span class="sxs-lookup"><span data-stu-id="a5a32-108">**SQL Server documentation**</span></span>

1. [<span data-ttu-id="a5a32-109">CLR Saklı Yordamları</span><span class="sxs-lookup"><span data-stu-id="a5a32-109">CLR Stored Procedures</span></span>](https://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a><span data-ttu-id="a5a32-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5a32-110">See also</span></span>

- <span data-ttu-id="a5a32-111">[Yönetilen kodda SQL Server 2005 nesneleri oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="a5a32-111">[Creating SQL Server 2005 Objects In Managed Code](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))</span></span>
- [<span data-ttu-id="a5a32-112">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="a5a32-112">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
