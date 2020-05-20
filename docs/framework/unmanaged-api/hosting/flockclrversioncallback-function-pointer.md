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
ms.openlocfilehash: af42de820b2d835e8ea137a2643a51678e382ff0
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617288"
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="fccea-102">FLockClrVersionCallback İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="fccea-102">FLockClrVersionCallback Function Pointer</span></span>
<span data-ttu-id="fccea-103">Ortak dil çalışma zamanının (CLR) başlatmanın başlatıldığını veya tamamlandığını göstermek için çağırdığı bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="fccea-103">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="fccea-104">Bu işlev işaretçisi .NET Framework 4 ' te kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="fccea-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fccea-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fccea-105">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="fccea-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fccea-106">Remarks</span></span>  
 <span data-ttu-id="fccea-107">Bu işlev, ana bilgisayar tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="fccea-107">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fccea-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fccea-108">Requirements</span></span>  
 <span data-ttu-id="fccea-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fccea-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fccea-110">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fccea-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fccea-111">**Kitaplık:** MSCorWks. dll</span><span class="sxs-lookup"><span data-stu-id="fccea-111">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="fccea-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fccea-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fccea-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fccea-113">See also</span></span>

- [<span data-ttu-id="fccea-114">LockClrVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="fccea-114">LockClrVersion Function</span></span>](lockclrversion-function.md)
- [<span data-ttu-id="fccea-115">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="fccea-115">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
