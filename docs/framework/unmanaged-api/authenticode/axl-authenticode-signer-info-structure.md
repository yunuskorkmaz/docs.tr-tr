---
title: AXL_AUTHENTICODE_SIGNER_INFO Yapısı
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b9f54c7c57d122ac1214b9f31cc4e1d1cddd71c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44039192"
---
# <a name="axlauthenticodesignerinfo-structure"></a><span data-ttu-id="6028e-102">AXL_AUTHENTICODE_SIGNER_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="6028e-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>
<span data-ttu-id="6028e-103">Authenticode imzalayan bilgileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6028e-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6028e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6028e-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="6028e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6028e-105">Members</span></span>  
  
|<span data-ttu-id="6028e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6028e-106">Member</span></span>|<span data-ttu-id="6028e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6028e-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="6028e-108">Bu yapının boyutu.</span><span class="sxs-lookup"><span data-stu-id="6028e-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="6028e-109">Hata kodu.</span><span class="sxs-lookup"><span data-stu-id="6028e-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="6028e-110">Karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="6028e-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="6028e-111">Karma değeri.</span><span class="sxs-lookup"><span data-stu-id="6028e-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="6028e-112">Açıklaması.</span><span class="sxs-lookup"><span data-stu-id="6028e-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="6028e-113">Açıklama URL'si.</span><span class="sxs-lookup"><span data-stu-id="6028e-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="6028e-114">İmzalayan zincirini bağlamı.</span><span class="sxs-lookup"><span data-stu-id="6028e-114">The chain context of the signer.</span></span> <span data-ttu-id="6028e-115">Bkz: [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) yapısı.</span><span class="sxs-lookup"><span data-stu-id="6028e-115">See the [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6028e-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6028e-116">See Also</span></span>  
 [<span data-ttu-id="6028e-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="6028e-117">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
