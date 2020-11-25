---
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
ms.openlocfilehash: 4212597b5ba43f0e4767aa585ca28a011e73e07a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711994"
---
# <a name="icordebugremotetarget-interface"></a><span data-ttu-id="172d6-102">ICorDebugRemoteTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="172d6-102">ICorDebugRemoteTarget Interface</span></span>

<span data-ttu-id="172d6-103">Geliştiricilerin, ortak dil çalışma zamanı (CLR) ortamında Silverlight tabanlı uygulamalarda hata ayıklamalarına olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="172d6-103">Provides methods that enable developers to debug Silverlight-based applications in the common language runtime (CLR) environment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="172d6-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="172d6-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="172d6-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="172d6-105">Methods</span></span>  
  
|<span data-ttu-id="172d6-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="172d6-106">Method</span></span>|<span data-ttu-id="172d6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="172d6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="172d6-108">ICorDebugRemoteTarget::GetHostName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="172d6-108">ICorDebugRemoteTarget::GetHostName Method</span></span>](icordebugremotetarget-gethostname-method.md)|<span data-ttu-id="172d6-109">Uzak makinenin ana bilgisayar adını veya IP adresini döndürür.</span><span class="sxs-lookup"><span data-stu-id="172d6-109">Returns the host name or the IP address of a remote machine.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="172d6-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="172d6-110">Remarks</span></span>  

 <span data-ttu-id="172d6-111">Karma mod (yani, yönetilen ve yerel kod) hata ayıklaması Windows 95, Windows 98 veya Windows ME 'de veya x86 olmayan platformlarda (IA-64 ve AMD64 gibi) desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="172d6-111">Mixed-mode (that is, managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA-64 and AMD64).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="172d6-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="172d6-112">Requirements</span></span>  

 <span data-ttu-id="172d6-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="172d6-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="172d6-114">**Üst bilgi:** CorDebug. IDL</span><span class="sxs-lookup"><span data-stu-id="172d6-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="172d6-115">**Library:** : corguid. lib</span><span class="sxs-lookup"><span data-stu-id="172d6-115">**Library:** : CorGuids.lib</span></span>  
  
 <span data-ttu-id="172d6-116">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="172d6-116">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="172d6-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="172d6-117">See also</span></span>

- [<span data-ttu-id="172d6-118">ICorDebugRemote Arabirimi</span><span class="sxs-lookup"><span data-stu-id="172d6-118">ICorDebugRemote Interface</span></span>](icordebugremote-interface.md)
- [<span data-ttu-id="172d6-119">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="172d6-119">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="172d6-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="172d6-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
