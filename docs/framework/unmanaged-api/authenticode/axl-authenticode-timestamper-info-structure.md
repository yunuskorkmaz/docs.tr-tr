---
title: "AXL_AUTHENTICODE_TIMESTAMPER_INFO Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ada8f5b21328d008ad34f4ac96cbf24e881a93b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="axlauthenticodetimestamperinfo-structure"></a><span data-ttu-id="e2eff-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="e2eff-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>
<span data-ttu-id="e2eff-103">Authenticode zaman stamper bilgilerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e2eff-103">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2eff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2eff-104">Syntax</span></span>  
  
```  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="e2eff-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e2eff-105">Members</span></span>  
  
|<span data-ttu-id="e2eff-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e2eff-106">Member</span></span>|<span data-ttu-id="e2eff-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2eff-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="e2eff-108">Bu yapı boyutu.</span><span class="sxs-lookup"><span data-stu-id="e2eff-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="e2eff-109">Hata kodu.</span><span class="sxs-lookup"><span data-stu-id="e2eff-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="e2eff-110">Karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="e2eff-110">The hash algorithm.</span></span>|  
|`ftTimestamp`|<span data-ttu-id="e2eff-111">Zaman damgası zamanı.</span><span class="sxs-lookup"><span data-stu-id="e2eff-111">The time of the time stamp.</span></span>|  
|`pChainContext`|<span data-ttu-id="e2eff-112">Zaman stamper's zinciri bağlamı.</span><span class="sxs-lookup"><span data-stu-id="e2eff-112">The time stamper’s chain context.</span></span>  <span data-ttu-id="e2eff-113">Bkz: [CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx) yapısı.</span><span class="sxs-lookup"><span data-stu-id="e2eff-113">See the [CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e2eff-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e2eff-114">See Also</span></span>  
 [<span data-ttu-id="e2eff-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="e2eff-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
