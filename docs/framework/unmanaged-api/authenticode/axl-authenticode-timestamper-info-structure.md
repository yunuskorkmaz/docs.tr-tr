---
title: AXL_AUTHENTICODE_TIMESTAMPER_INFO Yapısı
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d7f4fff4f2c2b3dd04625f4cf50b8b19a0ef6f39
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525087"
---
# <a name="axlauthenticodetimestamperinfo-structure"></a><span data-ttu-id="0a63e-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="0a63e-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>
<span data-ttu-id="0a63e-103">Zaman stamper Authenticode bilgileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0a63e-103">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a63e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0a63e-104">Syntax</span></span>  
  
```  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="0a63e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0a63e-105">Members</span></span>  
  
|<span data-ttu-id="0a63e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="0a63e-106">Member</span></span>|<span data-ttu-id="0a63e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a63e-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="0a63e-108">Bu yapının boyutu.</span><span class="sxs-lookup"><span data-stu-id="0a63e-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="0a63e-109">Hata kodu.</span><span class="sxs-lookup"><span data-stu-id="0a63e-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="0a63e-110">Karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="0a63e-110">The hash algorithm.</span></span>|  
|`ftTimestamp`|<span data-ttu-id="0a63e-111">Zaman damgası saat.</span><span class="sxs-lookup"><span data-stu-id="0a63e-111">The time of the time stamp.</span></span>|  
|`pChainContext`|<span data-ttu-id="0a63e-112">Zaman stamper's zinciri bağlamı.</span><span class="sxs-lookup"><span data-stu-id="0a63e-112">The time stamper’s chain context.</span></span>  <span data-ttu-id="0a63e-113">Bkz: [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) yapısı.</span><span class="sxs-lookup"><span data-stu-id="0a63e-113">See the [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0a63e-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0a63e-114">See Also</span></span>  
 [<span data-ttu-id="0a63e-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="0a63e-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
