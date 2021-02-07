---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugRemoteTarget arabirimi'
title: ICorDebugRemoteTarget Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget
helpviewer_keywords:
- ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: bd9936a6-cc24-4869-8761-0988664464e6
topic_type:
- apiref
ms.openlocfilehash: c6567ebb76c7a3c415c9978dc50941cb0b8985a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717881"
---
# <a name="icordebugremotetarget-interface"></a><span data-ttu-id="cd59f-103">ICorDebugRemoteTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cd59f-103">ICorDebugRemoteTarget Interface</span></span>

<span data-ttu-id="cd59f-104">Geliştiricilerin, ortak dil çalışma zamanı (CLR) ortamında Silverlight tabanlı uygulamalarda hata ayıklamalarına olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cd59f-104">Provides methods that enable developers to debug Silverlight-based applications in the common language runtime (CLR) environment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd59f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="cd59f-105">Syntax</span></span>  
  
```cpp  
interface ICorDebugRemoteTarget  : IUnknown  
{  
    HRESULT GetHostName (  
        [in]  ULONG32                    cchHostName,  
        [out] ULONG32*                   pcchHostName,  
        [out, size_is(cchHostName),  
              length_is(*pcchHostName)]  
                  WCHAR szHostName[]  
        );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="cd59f-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cd59f-106">Methods</span></span>  
  
|<span data-ttu-id="cd59f-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cd59f-107">Method</span></span>|<span data-ttu-id="cd59f-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd59f-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cd59f-109">ICorDebugRemoteTarget::GetHostName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cd59f-109">ICorDebugRemoteTarget::GetHostName Method</span></span>](icordebugremotetarget-gethostname-method.md)|<span data-ttu-id="cd59f-110">Uzak makinenin ana bilgisayar adını veya IP adresini döndürür.</span><span class="sxs-lookup"><span data-stu-id="cd59f-110">Returns the host name or the IP address of a remote machine.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd59f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cd59f-111">Remarks</span></span>  

 <span data-ttu-id="cd59f-112">Karma mod (yani, yönetilen ve yerel kod) hata ayıklaması Windows 95, Windows 98 veya Windows ME 'de veya x86 olmayan platformlarda (IA-64 ve AMD64 gibi) desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="cd59f-112">Mixed-mode (that is, managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA-64 and AMD64).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd59f-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cd59f-113">Requirements</span></span>  

 <span data-ttu-id="cd59f-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd59f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd59f-115">**Üst bilgi:** CorDebug. IDL</span><span class="sxs-lookup"><span data-stu-id="cd59f-115">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="cd59f-116">**Library:** : corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cd59f-116">**Library:** : CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd59f-117">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="cd59f-117">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd59f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd59f-118">See also</span></span>

- [<span data-ttu-id="cd59f-119">ICorDebugRemote Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cd59f-119">ICorDebugRemote Interface</span></span>](icordebugremote-interface.md)
- [<span data-ttu-id="cd59f-120">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cd59f-120">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="cd59f-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cd59f-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
