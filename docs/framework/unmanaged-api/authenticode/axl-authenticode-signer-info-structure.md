---
title: AXL_AUTHENTICODE_SIGNER_INFO Yapısı
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff50ee18dc3155bf784d6b752da8efc841aa6ce5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559443"
---
# <a name="axlauthenticodesignerinfo-structure"></a><span data-ttu-id="80897-102">AXL_AUTHENTICODE_SIGNER_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="80897-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>
<span data-ttu-id="80897-103">Authenticode imzalayan bilgileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="80897-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80897-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80897-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="80897-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="80897-105">Members</span></span>  
  
|<span data-ttu-id="80897-106">Üye</span><span class="sxs-lookup"><span data-stu-id="80897-106">Member</span></span>|<span data-ttu-id="80897-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80897-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="80897-108">Bu yapının boyutu.</span><span class="sxs-lookup"><span data-stu-id="80897-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="80897-109">Hata kodu.</span><span class="sxs-lookup"><span data-stu-id="80897-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="80897-110">Karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="80897-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="80897-111">Karma değeri.</span><span class="sxs-lookup"><span data-stu-id="80897-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="80897-112">Açıklaması.</span><span class="sxs-lookup"><span data-stu-id="80897-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="80897-113">Açıklama URL'si.</span><span class="sxs-lookup"><span data-stu-id="80897-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="80897-114">İmzalayan zincirini bağlamı.</span><span class="sxs-lookup"><span data-stu-id="80897-114">The chain context of the signer.</span></span> <span data-ttu-id="80897-115">Bkz: [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) yapısı.</span><span class="sxs-lookup"><span data-stu-id="80897-115">See the [CERT_CONTEXT](/windows/desktop/api/wincrypt/ns-wincrypt-_cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="80897-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80897-116">See also</span></span>
- [<span data-ttu-id="80897-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="80897-117">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
