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
ms.openlocfilehash: f1ad414c30788801e14a33e98a0893e2a0f58d0c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136515"
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="b1bd6-102">FLockClrVersionCallback İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="b1bd6-102">FLockClrVersionCallback Function Pointer</span></span>
<span data-ttu-id="b1bd6-103">Ortak dil çalışma zamanının (CLR) başlatmanın başlatıldığını veya tamamlandığını göstermek için çağırdığı bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="b1bd6-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="b1bd6-104">Bu işlev işaretçisi .NET Framework 4 ' te kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="b1bd6-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1bd6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1bd6-105">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="b1bd6-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1bd6-106">Remarks</span></span>  
 <span data-ttu-id="b1bd6-107">Bu işlev, ana bilgisayar tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b1bd6-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1bd6-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b1bd6-108">Requirements</span></span>  
 <span data-ttu-id="b1bd6-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1bd6-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1bd6-110">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b1bd6-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b1bd6-111">**Kitaplık:** MSCorWks. dll</span><span class="sxs-lookup"><span data-stu-id="b1bd6-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="b1bd6-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1bd6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1bd6-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1bd6-113">See also</span></span>

- [<span data-ttu-id="b1bd6-114">LockClrVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="b1bd6-114">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)
- [<span data-ttu-id="b1bd6-115">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b1bd6-115">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
