---
title: AXL_AUTHENTICODE_TIMESTAMPER_INFO Yapısı
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
ms.openlocfilehash: b6852519da6cf4e12669aa2efa24862053adbc03
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674248"
---
# <a name="axl_authenticode_timestamper_info-structure"></a><span data-ttu-id="44982-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="44982-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>

<span data-ttu-id="44982-103">Authenticode zaman Stamper bilgilerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="44982-103">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44982-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="44982-104">Syntax</span></span>  
  
```cpp  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="44982-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="44982-105">Members</span></span>  
  
|<span data-ttu-id="44982-106">Üye</span><span class="sxs-lookup"><span data-stu-id="44982-106">Member</span></span>|<span data-ttu-id="44982-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44982-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="44982-108">Bu yapının boyutu.</span><span class="sxs-lookup"><span data-stu-id="44982-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="44982-109">Hata kodu.</span><span class="sxs-lookup"><span data-stu-id="44982-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="44982-110">Karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="44982-110">The hash algorithm.</span></span>|  
|`ftTimestamp`|<span data-ttu-id="44982-111">Zaman damgasının saati.</span><span class="sxs-lookup"><span data-stu-id="44982-111">The time of the time stamp.</span></span>|  
|`pChainContext`|<span data-ttu-id="44982-112">Zaman stamplayıcı zinciri bağlamı.</span><span class="sxs-lookup"><span data-stu-id="44982-112">The time stamper’s chain context.</span></span>  <span data-ttu-id="44982-113">[CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) yapısına bakın.</span><span class="sxs-lookup"><span data-stu-id="44982-113">See the [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="44982-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44982-114">See also</span></span>

- [<span data-ttu-id="44982-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="44982-115">Authenticode</span></span>](index.md)
