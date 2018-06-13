---
title: FLockClrVersionCallback İşlev İşaretçisi
ms.date: 03/30/2017
api_name:
- FLockClrVersionCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FLockClrVersionCallback
helpviewer_keywords:
- FLockClrVersionCallback function pointer [.NET Framework hosting]
ms.assetid: 98a4762d-9ad2-45bd-9d03-39064a028b44
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c884d07fa35c053b1a3b65c04426ac0e3712621
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429679"
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="fc630-102">FLockClrVersionCallback İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="fc630-102">FLockClrVersionCallback Function Pointer</span></span>
<span data-ttu-id="fc630-103">Noktaları başlatmanın göstermek için ortak dil çalışma zamanı (CLR) çağrıları başlatılan ya da tamamlanan bir işlev.</span><span class="sxs-lookup"><span data-stu-id="fc630-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="fc630-104">Bu işlev işaretçisi kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fc630-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc630-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc630-105">Syntax</span></span>  
  
```  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="fc630-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fc630-106">Remarks</span></span>  
 <span data-ttu-id="fc630-107">Bu işlev ana bilgisayar tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="fc630-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc630-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fc630-108">Requirements</span></span>  
 <span data-ttu-id="fc630-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc630-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc630-110">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fc630-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fc630-111">**Kitaplığı:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="fc630-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="fc630-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc630-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc630-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fc630-113">See Also</span></span>  
 [<span data-ttu-id="fc630-114">LockClrVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="fc630-114">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)  
 [<span data-ttu-id="fc630-115">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="fc630-115">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
