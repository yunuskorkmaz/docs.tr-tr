---
title: "Desteklenmeyen işlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b54bac0c9ce0b473ef8d86b039ef638b79af784f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="unsupported-functionality"></a><span data-ttu-id="1c0d0-102">Desteklenmeyen işlevi</span><span class="sxs-lookup"><span data-stu-id="1c0d0-102">Unsupported Functionality</span></span>
<span data-ttu-id="1c0d0-103">LINQ-SQL, aşağıdaki SQL işlevselliği varolan ortak dil çalışma zamanı (CLR) çeviri görüntülenemeyen ve .NET Framework oluşturur:</span><span class="sxs-lookup"><span data-stu-id="1c0d0-103">In LINQ to SQL, the following SQL functionality cannot be exposed through translation of existing common language runtime (CLR) and .NET Framework constructs:</span></span>  
  
-   `STDDEV`  
  
-   `LIKE`  
  
     <span data-ttu-id="1c0d0-104">Ancak `LIKE` desteklenmiyor benzer işlevselliği bulunmaktadır doğrudan çeviri <xref:System.Data.Linq.SqlClient.SqlMethods> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1c0d0-104">Although `LIKE` is not supported through direct translation, similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span> <span data-ttu-id="1c0d0-105">Daha fazla bilgi için bkz. <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1c0d0-105">For more information, see <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span></span>  
  
-   `DATEDIFF`  
  
     <span data-ttu-id="1c0d0-106">LINQ-SQL desteği sınırlı `DATEDIFF`.</span><span class="sxs-lookup"><span data-stu-id="1c0d0-106">LINQ to SQL has limited support for `DATEDIFF`.</span></span> <span data-ttu-id="1c0d0-107">Benzer işlevsellik mevcut <xref:System.Data.Linq.SqlClient.SqlMethods> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1c0d0-107">Similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span>  
  
-   `ROUND`  
  
     <span data-ttu-id="1c0d0-108">LINQ-SQL desteği sınırlı `ROUND`.</span><span class="sxs-lookup"><span data-stu-id="1c0d0-108">LINQ to SQL has limited support for `ROUND`.</span></span> <span data-ttu-id="1c0d0-109">Daha fazla bilgi için bkz: [System.Math yöntemleri](system-math-methods.md).</span><span class="sxs-lookup"><span data-stu-id="1c0d0-109">For more information, see [System.Math Methods](system-math-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c0d0-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1c0d0-110">See Also</span></span>  
 [<span data-ttu-id="1c0d0-111">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="1c0d0-111">Data Types and Functions</span></span>](data-types-and-functions.md)
