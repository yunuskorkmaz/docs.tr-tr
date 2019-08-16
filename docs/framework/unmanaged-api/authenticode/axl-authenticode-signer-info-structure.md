---
title: AXL_AUTHENTICODE_SIGNER_INFO Yapısı
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c69be0de98e2996176e7360bae0bb0736c1a797
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038434"
---
# <a name="axl_authenticode_signer_info-structure"></a><span data-ttu-id="85f4b-102">AXL_AUTHENTICODE_SIGNER_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="85f4b-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>
<span data-ttu-id="85f4b-103">Authenticode imzalayan bilgilerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="85f4b-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85f4b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="85f4b-104">Syntax</span></span>  
  
```cpp  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    LPCWSTR pwszHash  
    LPCWSTR pwszDescription;  
    LPCWSTR pwszDescriptionUrl;  
    PCCERT_CHAIN_CONTEXT pChainContext  
} AXL_AUTHENTICODE_SIGNER_INFO, * PAXL_AUTHENTICODE_SIGNER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="85f4b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="85f4b-105">Members</span></span>  
  
|<span data-ttu-id="85f4b-106">Üye</span><span class="sxs-lookup"><span data-stu-id="85f4b-106">Member</span></span>|<span data-ttu-id="85f4b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85f4b-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="85f4b-108">Bu yapının boyutu.</span><span class="sxs-lookup"><span data-stu-id="85f4b-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="85f4b-109">Hata kodu.</span><span class="sxs-lookup"><span data-stu-id="85f4b-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="85f4b-110">Karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="85f4b-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="85f4b-111">Karma.</span><span class="sxs-lookup"><span data-stu-id="85f4b-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="85f4b-112">Açıklama.</span><span class="sxs-lookup"><span data-stu-id="85f4b-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="85f4b-113">Açıklamanın URL 'SI.</span><span class="sxs-lookup"><span data-stu-id="85f4b-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="85f4b-114">İmzalayanın zincir bağlamı.</span><span class="sxs-lookup"><span data-stu-id="85f4b-114">The chain context of the signer.</span></span> <span data-ttu-id="85f4b-115">Bkz. [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) yapısı.</span><span class="sxs-lookup"><span data-stu-id="85f4b-115">See the [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="85f4b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85f4b-116">See also</span></span>

- [<span data-ttu-id="85f4b-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="85f4b-117">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
