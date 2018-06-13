---
title: CLR saklı yordamlar
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: c0a318d2d11788d274da637cd1846f72159cd013
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358595"
---
# <a name="clr-stored-procedures"></a><span data-ttu-id="9a277-102">CLR saklı yordamlar</span><span class="sxs-lookup"><span data-stu-id="9a277-102">CLR Stored Procedures</span></span>
<span data-ttu-id="9a277-103">Saklı yordamlar skaler ifadelerinde kullanılamaz yordamları ' dir.</span><span class="sxs-lookup"><span data-stu-id="9a277-103">Stored procedures are routines that cannot be used in scalar expressions.</span></span> <span data-ttu-id="9a277-104">Tablo sonuçları ve iletileri istemciye Döndür, veri tanımlama dili (DDL) ve veri işleme dili (DML) deyimleri çağırma ve çıkış parametreleri dönün.</span><span class="sxs-lookup"><span data-stu-id="9a277-104">They can return tabular results and messages to the client, invoke data definition language (DDL) and data manipulation language (DML) statements, and return output parameters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a277-105">Microsoft Visual Basic, Microsoft Visual C# yapan aynı şekilde çıkış parametreleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="9a277-105">Microsoft Visual Basic does not support output parameters in the same way that Microsoft Visual C# does.</span></span> <span data-ttu-id="9a277-106">Başvuruya göre parametre geçirmek ve uygulamak için belirtmelisiniz \<Out() > özniteliği aşağıdaki gibi bir çıktı parametresi temsil etmek için:</span><span class="sxs-lookup"><span data-stu-id="9a277-106">You must specify to pass the parameter by reference and apply the \<Out()> attribute to represent an output parameter, as in the following:</span></span>  
  
```  
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```  
  
 <span data-ttu-id="9a277-107">Daha ayrıntılı bilgi için SQL Server Books Online'nın sürümü, kullanmakta olduğunuz SQL Server sürümü için bkz.</span><span class="sxs-lookup"><span data-stu-id="9a277-107">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="9a277-108">**SQL Server Çevrimiçi Kitapları**</span><span class="sxs-lookup"><span data-stu-id="9a277-108">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="9a277-109">CLR Saklı Yordamları</span><span class="sxs-lookup"><span data-stu-id="9a277-109">CLR Stored Procedures</span></span>](http://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a><span data-ttu-id="9a277-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9a277-110">See Also</span></span>  
 [<span data-ttu-id="9a277-111">Yönetilen kodda SQL Server 2005'te nesneleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="9a277-111">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="9a277-112">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="9a277-112">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
