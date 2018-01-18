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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: aebc681482482c364f762b12065cf041f4976be9
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="clr-stored-procedures"></a><span data-ttu-id="a5cda-102">CLR saklı yordamlar</span><span class="sxs-lookup"><span data-stu-id="a5cda-102">CLR Stored Procedures</span></span>
<span data-ttu-id="a5cda-103">Saklı yordamlar skaler ifadelerinde kullanılamaz yordamları ' dir.</span><span class="sxs-lookup"><span data-stu-id="a5cda-103">Stored procedures are routines that cannot be used in scalar expressions.</span></span> <span data-ttu-id="a5cda-104">Tablo sonuçları ve iletileri istemciye Döndür, veri tanımlama dili (DDL) ve veri işleme dili (DML) deyimleri çağırma ve çıkış parametreleri dönün.</span><span class="sxs-lookup"><span data-stu-id="a5cda-104">They can return tabular results and messages to the client, invoke data definition language (DDL) and data manipulation language (DML) statements, and return output parameters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5cda-105">Microsoft Visual Basic, Microsoft Visual C# yapan aynı şekilde çıkış parametreleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="a5cda-105">Microsoft Visual Basic does not support output parameters in the same way that Microsoft Visual C# does.</span></span> <span data-ttu-id="a5cda-106">Başvuruya göre parametre geçirmek ve uygulamak için belirtmelisiniz \<Out() > özniteliği aşağıdaki gibi bir çıktı parametresi temsil etmek için:</span><span class="sxs-lookup"><span data-stu-id="a5cda-106">You must specify to pass the parameter by reference and apply the \<Out()> attribute to represent an output parameter, as in the following:</span></span>  
  
```  
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```  
  
 <span data-ttu-id="a5cda-107">Daha ayrıntılı bilgi için SQL Server Books Online'nın sürümü, kullanmakta olduğunuz SQL Server sürümü için bkz.</span><span class="sxs-lookup"><span data-stu-id="a5cda-107">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="a5cda-108">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="a5cda-108">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="a5cda-109">CLR Saklı Yordamları</span><span class="sxs-lookup"><span data-stu-id="a5cda-109">CLR Stored Procedures</span></span>](http://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a><span data-ttu-id="a5cda-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a5cda-110">See Also</span></span>  
 [<span data-ttu-id="a5cda-111">Yönetilen kodda SQL Server 2005'te nesneleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="a5cda-111">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/en-us/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="a5cda-112">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="a5cda-112">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
