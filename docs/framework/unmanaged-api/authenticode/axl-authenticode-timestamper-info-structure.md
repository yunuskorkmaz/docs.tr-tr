---
title: AXL_AUTHENTICODE_TIMESTAMPER_INFO Yapısı
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
ms.openlocfilehash: 036397928703aea6199a59ae9c1e66153c30ec7b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132499"
---
# <a name="axl_authenticode_timestamper_info-structure"></a><span data-ttu-id="041ee-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="041ee-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>
<span data-ttu-id="041ee-103">Authenticode zaman Stamper bilgilerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="041ee-103">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="041ee-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="041ee-104">Syntax</span></span>  
  
```cpp  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="041ee-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="041ee-105">Members</span></span>  
  
|<span data-ttu-id="041ee-106">Üye</span><span class="sxs-lookup"><span data-stu-id="041ee-106">Member</span></span>|<span data-ttu-id="041ee-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="041ee-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="041ee-108">Bu yapının boyutu.</span><span class="sxs-lookup"><span data-stu-id="041ee-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="041ee-109">Hata kodu.</span><span class="sxs-lookup"><span data-stu-id="041ee-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="041ee-110">Karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="041ee-110">The hash algorithm.</span></span>|  
|`ftTimestamp`|<span data-ttu-id="041ee-111">Zaman damgasının saati.</span><span class="sxs-lookup"><span data-stu-id="041ee-111">The time of the time stamp.</span></span>|  
|`pChainContext`|<span data-ttu-id="041ee-112">Zaman stamplayıcı zinciri bağlamı.</span><span class="sxs-lookup"><span data-stu-id="041ee-112">The time stamper’s chain context.</span></span>  <span data-ttu-id="041ee-113">Bkz. [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) yapısı.</span><span class="sxs-lookup"><span data-stu-id="041ee-113">See the [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="041ee-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="041ee-114">See also</span></span>

- [<span data-ttu-id="041ee-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="041ee-115">Authenticode</span></span>](index.md)
