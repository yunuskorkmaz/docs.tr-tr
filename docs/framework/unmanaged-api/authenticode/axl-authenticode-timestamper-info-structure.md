---
title: AXL_AUTHENTICODE_TIMESTAMPER_INFO Yapısı
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c89845008307e4cfb00d0f9b9a168a43ba5378c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402369"
---
# <a name="axlauthenticodetimestamperinfo-structure"></a><span data-ttu-id="f07bf-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="f07bf-102">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>
<span data-ttu-id="f07bf-103">Authenticode zaman stamper bilgilerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f07bf-103">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f07bf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f07bf-104">Syntax</span></span>  
  
```  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="f07bf-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f07bf-105">Members</span></span>  
  
|<span data-ttu-id="f07bf-106">Üye</span><span class="sxs-lookup"><span data-stu-id="f07bf-106">Member</span></span>|<span data-ttu-id="f07bf-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f07bf-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="f07bf-108">Bu yapı boyutu.</span><span class="sxs-lookup"><span data-stu-id="f07bf-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="f07bf-109">Hata kodu.</span><span class="sxs-lookup"><span data-stu-id="f07bf-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="f07bf-110">Karma algoritması.</span><span class="sxs-lookup"><span data-stu-id="f07bf-110">The hash algorithm.</span></span>|  
|`ftTimestamp`|<span data-ttu-id="f07bf-111">Zaman damgası zamanı.</span><span class="sxs-lookup"><span data-stu-id="f07bf-111">The time of the time stamp.</span></span>|  
|`pChainContext`|<span data-ttu-id="f07bf-112">Zaman stamper's zinciri bağlamı.</span><span class="sxs-lookup"><span data-stu-id="f07bf-112">The time stamper’s chain context.</span></span>  <span data-ttu-id="f07bf-113">Bkz: [CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx) yapısı.</span><span class="sxs-lookup"><span data-stu-id="f07bf-113">See the [CERT_CONTEXT](http://msdn.microsoft.com/library/windows/desktop/aa377189.aspx) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f07bf-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f07bf-114">See Also</span></span>  
 [<span data-ttu-id="f07bf-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="f07bf-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
