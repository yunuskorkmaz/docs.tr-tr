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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae31506d4ba34bf262f49bc2321c6cfcd30f1b60
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782700"
---
# <a name="icordebugremotetarget-interface"></a><span data-ttu-id="93b4a-102">ICorDebugRemoteTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="93b4a-102">ICorDebugRemoteTarget Interface</span></span>
<span data-ttu-id="93b4a-103">Geliştiricilerin ortak dil çalışma zamanı (CLR) ortamında Silverlight tabanlı uygulamaların hatalarını ayıklamalarına olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="93b4a-103">Provides methods that enable developers to debug Silverlight-based applications in the common language runtime (CLR) environment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93b4a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="93b4a-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="93b4a-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="93b4a-105">Methods</span></span>  
  
|<span data-ttu-id="93b4a-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="93b4a-106">Method</span></span>|<span data-ttu-id="93b4a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="93b4a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="93b4a-108">ICorDebugRemoteTarget::GetHostName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="93b4a-108">ICorDebugRemoteTarget::GetHostName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-gethostname-method.md)|<span data-ttu-id="93b4a-109">Ana bilgisayar adı veya uzak bir makinenin IP adresini döndürür.</span><span class="sxs-lookup"><span data-stu-id="93b4a-109">Returns the host name or the IP address of a remote machine.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93b4a-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="93b4a-110">Remarks</span></span>  
 <span data-ttu-id="93b4a-111">Karma mod (diğer bir deyişle, yönetilen ve yerel kod) hata ayıklaması, Windows 95, Windows 98 veya Windows ME veya x86 olmayan platformları (örn. IA-64 ve AMD64 gibi) üzerinde desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="93b4a-111">Mixed-mode (that is, managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA-64 and AMD64).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93b4a-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="93b4a-112">Requirements</span></span>  
 <span data-ttu-id="93b4a-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93b4a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93b4a-114">**Üst bilgi:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="93b4a-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="93b4a-115">**Kitaplığı:** : CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93b4a-115">**Library:** : CorGuids.lib</span></span>  
  
 <span data-ttu-id="93b4a-116">**.NET framework sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="93b4a-116">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93b4a-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93b4a-117">See also</span></span>

- [<span data-ttu-id="93b4a-118">ICorDebugRemote Arabirimi</span><span class="sxs-lookup"><span data-stu-id="93b4a-118">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [<span data-ttu-id="93b4a-119">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="93b4a-119">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="93b4a-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="93b4a-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
