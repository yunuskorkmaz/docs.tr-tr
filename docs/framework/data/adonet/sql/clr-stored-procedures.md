---
title: "CLR saklı yordamlar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1e55222c16d223a86e1e11ce2b985ec0f4d8eaa3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="clr-stored-procedures"></a><span data-ttu-id="679cd-102">CLR saklı yordamlar</span><span class="sxs-lookup"><span data-stu-id="679cd-102">CLR Stored Procedures</span></span>
<span data-ttu-id="679cd-103">Saklı yordamlar skaler ifadelerinde kullanılamaz yordamları ' dir.</span><span class="sxs-lookup"><span data-stu-id="679cd-103">Stored procedures are routines that cannot be used in scalar expressions.</span></span> <span data-ttu-id="679cd-104">Tablo sonuçları ve iletileri istemciye Döndür, veri tanımlama dili (DDL) ve veri işleme dili (DML) deyimleri çağırma ve çıkış parametreleri dönün.</span><span class="sxs-lookup"><span data-stu-id="679cd-104">They can return tabular results and messages to the client, invoke data definition language (DDL) and data manipulation language (DML) statements, and return output parameters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="679cd-105">Microsoft Visual Basic, Microsoft Visual C# yapan aynı şekilde çıkış parametreleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="679cd-105">Microsoft Visual Basic does not support output parameters in the same way that Microsoft Visual C# does.</span></span> <span data-ttu-id="679cd-106">Başvuruya göre parametre geçirmek ve uygulamak için belirtmelisiniz \<Out() > özniteliği aşağıdaki gibi bir çıktı parametresi temsil etmek için:</span><span class="sxs-lookup"><span data-stu-id="679cd-106">You must specify to pass the parameter by reference and apply the \<Out()> attribute to represent an output parameter, as in the following:</span></span>  
  
```  
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```  
  
 <span data-ttu-id="679cd-107">Daha ayrıntılı bilgi için SQL Server Books Online'nın sürümü, kullanmakta olduğunuz SQL Server sürümü için bkz.</span><span class="sxs-lookup"><span data-stu-id="679cd-107">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="679cd-108">**SQL Server Çevrimiçi Kitapları**</span><span class="sxs-lookup"><span data-stu-id="679cd-108">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="679cd-109">CLR saklı yordamlar</span><span class="sxs-lookup"><span data-stu-id="679cd-109">CLR Stored Procedures</span></span>](http://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a><span data-ttu-id="679cd-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="679cd-110">See Also</span></span>  
 [<span data-ttu-id="679cd-111">Yönetilen kodda SQL Server 2005'te nesneleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="679cd-111">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/en-us/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="679cd-112">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="679cd-112">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
