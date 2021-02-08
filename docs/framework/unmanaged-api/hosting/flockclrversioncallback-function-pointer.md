---
description: ': FLockClrVersionCallback Işlev Işaretçisi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 3506cd30ab2a9e5a06b03f5010c9870280a38378
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785386"
---
# <a name="flockclrversioncallback-function-pointer"></a><span data-ttu-id="f3d1a-103">FLockClrVersionCallback İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="f3d1a-103">FLockClrVersionCallback Function Pointer</span></span>

<span data-ttu-id="f3d1a-104">Ortak dil çalışma zamanının (CLR) başlatmanın başlatıldığını veya tamamlandığını göstermek için çağırdığı bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="f3d1a-104">Points to a function that the common language runtime (CLR) calls to indicate that initialization has either started or completed.</span></span>  
  
 <span data-ttu-id="f3d1a-105">Bu işlev işaretçisi .NET Framework 4 ' te kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="f3d1a-105">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3d1a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f3d1a-106">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FLockClrVersionCallback) ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="f3d1a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f3d1a-107">Remarks</span></span>  

 <span data-ttu-id="f3d1a-108">Bu işlev, ana bilgisayar tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f3d1a-108">This function is implemented by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3d1a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f3d1a-109">Requirements</span></span>  

 <span data-ttu-id="f3d1a-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3d1a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3d1a-111">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f3d1a-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f3d1a-112">**Kitaplık:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="f3d1a-112">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="f3d1a-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3d1a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3d1a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3d1a-114">See also</span></span>

- [<span data-ttu-id="f3d1a-115">LockClrVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="f3d1a-115">LockClrVersion Function</span></span>](lockclrversion-function.md)
- [<span data-ttu-id="f3d1a-116">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="f3d1a-116">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
