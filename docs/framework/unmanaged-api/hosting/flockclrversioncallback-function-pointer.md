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
ms.openlocfilehash: ef308b624525c3a139c892e6118a24d6adb6e14a
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490456"
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="07246-102">FLockClrVersionCallback İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="07246-102">FLockClrVersionCallback Function Pointer</span></span>
<span data-ttu-id="07246-103">Başlatmanın belirtmek için ortak dil çalışma zamanı (CLR) çağrıları çalışmaya veya tamamlanmış bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="07246-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="07246-104">Bu işlev işaretçisi .NET Framework 4'te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="07246-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07246-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07246-105">Syntax</span></span>  
  
```  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="07246-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07246-106">Remarks</span></span>  
 <span data-ttu-id="07246-107">Bu işlev, ana bilgisayar tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="07246-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07246-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07246-108">Requirements</span></span>  
 <span data-ttu-id="07246-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07246-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07246-110">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="07246-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="07246-111">**Kitaplığı:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="07246-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="07246-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07246-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07246-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07246-113">See also</span></span>

- [<span data-ttu-id="07246-114">LockClrVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="07246-114">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)
- [<span data-ttu-id="07246-115">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="07246-115">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
