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
ms.openlocfilehash: 46e3356df6578f2adf2ceee00b1363b65fd014ea
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760233"
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="765f0-102">FLockClrVersionCallback İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="765f0-102">FLockClrVersionCallback Function Pointer</span></span>
<span data-ttu-id="765f0-103">Başlatmanın belirtmek için ortak dil çalışma zamanı (CLR) çağrıları çalışmaya veya tamamlanmış bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="765f0-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="765f0-104">Bu işlev işaretçisi .NET Framework 4'te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="765f0-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="765f0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="765f0-105">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="765f0-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="765f0-106">Remarks</span></span>  
 <span data-ttu-id="765f0-107">Bu işlev, ana bilgisayar tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="765f0-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="765f0-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="765f0-108">Requirements</span></span>  
 <span data-ttu-id="765f0-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="765f0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="765f0-110">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="765f0-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="765f0-111">**Kitaplığı:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="765f0-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="765f0-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="765f0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="765f0-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="765f0-113">See also</span></span>

- [<span data-ttu-id="765f0-114">LockClrVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="765f0-114">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)
- [<span data-ttu-id="765f0-115">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="765f0-115">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
