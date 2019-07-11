---
title: AXL_AUTHENTICODE_SIGNER_INFO Yapısı
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 232c78db32aecd0ee1379d4d969fa0378db4159a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741360"
---
# <a name="axlauthenticodesignerinfo-structure"></a><span data-ttu-id="76f34-102">AXL_AUTHENTICODE_SIGNER_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="76f34-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>
<span data-ttu-id="76f34-103">Authenticode imzalayan bilgileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="76f34-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76f34-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="76f34-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="76f34-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="76f34-105">Members</span></span>  
  
|<span data-ttu-id="76f34-106">Üye</span><span class="sxs-lookup"><span data-stu-id="76f34-106">Member</span></span>|<span data-ttu-id="76f34-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76f34-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="76f34-108">Bu yapının boyutu.</span><span class="sxs-lookup"><span data-stu-id="76f34-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="76f34-109">Hata kodu.</span><span class="sxs-lookup"><span data-stu-id="76f34-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="76f34-110">Karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="76f34-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="76f34-111">Karma değeri.</span><span class="sxs-lookup"><span data-stu-id="76f34-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="76f34-112">Açıklaması.</span><span class="sxs-lookup"><span data-stu-id="76f34-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="76f34-113">Açıklama URL'si.</span><span class="sxs-lookup"><span data-stu-id="76f34-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="76f34-114">İmzalayan zincirini bağlamı.</span><span class="sxs-lookup"><span data-stu-id="76f34-114">The chain context of the signer.</span></span> <span data-ttu-id="76f34-115">Bkz: [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) yapısı.</span><span class="sxs-lookup"><span data-stu-id="76f34-115">See the [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="76f34-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76f34-116">See also</span></span>

- [<span data-ttu-id="76f34-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="76f34-117">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
