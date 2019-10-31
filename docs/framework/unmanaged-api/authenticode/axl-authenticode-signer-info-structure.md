---
title: AXL_AUTHENTICODE_SIGNER_INFO Yapısı
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
ms.openlocfilehash: 00132bb378d69c0db9fe9d762407707346238917
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132507"
---
# <a name="axl_authenticode_signer_info-structure"></a><span data-ttu-id="bddae-102">AXL_AUTHENTICODE_SIGNER_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="bddae-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>
<span data-ttu-id="bddae-103">Authenticode imzalayan bilgilerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bddae-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bddae-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bddae-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="bddae-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="bddae-105">Members</span></span>  
  
|<span data-ttu-id="bddae-106">Üye</span><span class="sxs-lookup"><span data-stu-id="bddae-106">Member</span></span>|<span data-ttu-id="bddae-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bddae-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="bddae-108">Bu yapının boyutu.</span><span class="sxs-lookup"><span data-stu-id="bddae-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="bddae-109">Hata kodu.</span><span class="sxs-lookup"><span data-stu-id="bddae-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="bddae-110">Karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="bddae-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="bddae-111">Karma.</span><span class="sxs-lookup"><span data-stu-id="bddae-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="bddae-112">Açıklama.</span><span class="sxs-lookup"><span data-stu-id="bddae-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="bddae-113">Açıklamanın URL 'SI.</span><span class="sxs-lookup"><span data-stu-id="bddae-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="bddae-114">İmzalayanın zincir bağlamı.</span><span class="sxs-lookup"><span data-stu-id="bddae-114">The chain context of the signer.</span></span> <span data-ttu-id="bddae-115">Bkz. [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) yapısı.</span><span class="sxs-lookup"><span data-stu-id="bddae-115">See the [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bddae-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bddae-116">See also</span></span>

- [<span data-ttu-id="bddae-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="bddae-117">Authenticode</span></span>](index.md)
