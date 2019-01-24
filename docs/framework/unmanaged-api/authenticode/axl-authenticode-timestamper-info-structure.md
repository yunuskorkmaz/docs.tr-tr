---
title: AXL_AUTHENTICODE_TIMESTAMPER_INFO Yapısı
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d8060e95f06fd53ca985f84666cc81cfe49394fc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659663"
---
# <a name="axlauthenticodetimestamperinfo-structure"></a><span data-ttu-id="08e77-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="08e77-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>
<span data-ttu-id="08e77-103">Zaman stamper Authenticode bilgileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="08e77-103">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08e77-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08e77-104">Syntax</span></span>  
  
```  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="08e77-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="08e77-105">Members</span></span>  
  
|<span data-ttu-id="08e77-106">Üye</span><span class="sxs-lookup"><span data-stu-id="08e77-106">Member</span></span>|<span data-ttu-id="08e77-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08e77-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="08e77-108">Bu yapının boyutu.</span><span class="sxs-lookup"><span data-stu-id="08e77-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="08e77-109">Hata kodu.</span><span class="sxs-lookup"><span data-stu-id="08e77-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="08e77-110">Karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="08e77-110">The hash algorithm.</span></span>|  
|`ftTimestamp`|<span data-ttu-id="08e77-111">Zaman damgası saat.</span><span class="sxs-lookup"><span data-stu-id="08e77-111">The time of the time stamp.</span></span>|  
|`pChainContext`|<span data-ttu-id="08e77-112">Zaman stamper's zinciri bağlamı.</span><span class="sxs-lookup"><span data-stu-id="08e77-112">The time stamper’s chain context.</span></span>  <span data-ttu-id="08e77-113">Bkz: [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) yapısı.</span><span class="sxs-lookup"><span data-stu-id="08e77-113">See the [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="08e77-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08e77-114">See also</span></span>
- [<span data-ttu-id="08e77-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="08e77-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
