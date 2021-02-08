---
description: 'Daha fazla bilgi edinin: AXL_AUTHENTICODE_SIGNER_INFO yapısı'
title: AXL_AUTHENTICODE_SIGNER_INFO Yapısı
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
ms.openlocfilehash: 940652cf184e26f141df806b060c391333d1bb95
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781967"
---
# <a name="axl_authenticode_signer_info-structure"></a><span data-ttu-id="5b242-103">AXL_AUTHENTICODE_SIGNER_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="5b242-103">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>

<span data-ttu-id="5b242-104">Authenticode imzalayan bilgilerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5b242-104">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b242-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5b242-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="5b242-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="5b242-106">Members</span></span>  
  
|<span data-ttu-id="5b242-107">Üye</span><span class="sxs-lookup"><span data-stu-id="5b242-107">Member</span></span>|<span data-ttu-id="5b242-108">Description</span><span class="sxs-lookup"><span data-stu-id="5b242-108">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="5b242-109">Bu yapının boyutu.</span><span class="sxs-lookup"><span data-stu-id="5b242-109">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="5b242-110">Hata kodu.</span><span class="sxs-lookup"><span data-stu-id="5b242-110">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="5b242-111">Karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="5b242-111">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="5b242-112">Karma.</span><span class="sxs-lookup"><span data-stu-id="5b242-112">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="5b242-113">Açıklama.</span><span class="sxs-lookup"><span data-stu-id="5b242-113">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="5b242-114">Açıklamanın URL 'SI.</span><span class="sxs-lookup"><span data-stu-id="5b242-114">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="5b242-115">İmzalayanın zincir bağlamı.</span><span class="sxs-lookup"><span data-stu-id="5b242-115">The chain context of the signer.</span></span> <span data-ttu-id="5b242-116">[CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) yapısına bakın.</span><span class="sxs-lookup"><span data-stu-id="5b242-116">See the [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5b242-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b242-117">See also</span></span>

- [<span data-ttu-id="5b242-118">Authenticode</span><span class="sxs-lookup"><span data-stu-id="5b242-118">Authenticode</span></span>](index.md)
