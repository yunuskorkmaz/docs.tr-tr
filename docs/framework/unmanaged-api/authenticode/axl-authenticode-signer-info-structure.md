---
title: AXL_AUTHENTICODE_SIGNER_INFO Yapısı
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd07707b5a80ec0980fc50b27caddf0a24398fd1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400451"
---
# <a name="axlauthenticodesignerinfo-structure"></a><span data-ttu-id="3df0c-102">AXL_AUTHENTICODE_SIGNER_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="3df0c-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>
<span data-ttu-id="3df0c-103">Authenticode imzalayan bilgilerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3df0c-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3df0c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3df0c-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="3df0c-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3df0c-105">Members</span></span>  
  
|<span data-ttu-id="3df0c-106">Üye</span><span class="sxs-lookup"><span data-stu-id="3df0c-106">Member</span></span>|<span data-ttu-id="3df0c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3df0c-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="3df0c-108">Bu yapı boyutu.</span><span class="sxs-lookup"><span data-stu-id="3df0c-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="3df0c-109">Hata kodu.</span><span class="sxs-lookup"><span data-stu-id="3df0c-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="3df0c-110">Karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="3df0c-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="3df0c-111">Karma.</span><span class="sxs-lookup"><span data-stu-id="3df0c-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="3df0c-112">Açıklaması.</span><span class="sxs-lookup"><span data-stu-id="3df0c-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="3df0c-113">Açıklama URL'si.</span><span class="sxs-lookup"><span data-stu-id="3df0c-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="3df0c-114">İmzalayan zincirini bağlamı.</span><span class="sxs-lookup"><span data-stu-id="3df0c-114">The chain context of the signer.</span></span> <span data-ttu-id="3df0c-115">Bkz: [CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx) yapısı.</span><span class="sxs-lookup"><span data-stu-id="3df0c-115">See the [CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3df0c-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3df0c-116">See Also</span></span>  
 [<span data-ttu-id="3df0c-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="3df0c-117">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
