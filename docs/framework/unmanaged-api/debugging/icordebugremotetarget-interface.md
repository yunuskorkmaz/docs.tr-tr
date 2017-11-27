---
title: ICorDebugRemoteTarget Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRemoteTarget
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugRemoteTarget
helpviewer_keywords: ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: bd9936a6-cc24-4869-8761-0988664464e6
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 38357072b3a6e8e8a326a16600b2d7ed56cdcb2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugremotetarget-interface"></a><span data-ttu-id="571f4-102">ICorDebugRemoteTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="571f4-102">ICorDebugRemoteTarget Interface</span></span>
<span data-ttu-id="571f4-103">Ortak dil çalışma zamanı (CLR) ortamı Silverlight tabanlı uygulamalarda hata ayıklamak, geliştiricilerin yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="571f4-103">Provides methods that enable developers to debug Silverlight-based applications in the common language runtime (CLR) environment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="571f4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="571f4-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="571f4-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="571f4-105">Methods</span></span>  
  
|<span data-ttu-id="571f4-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="571f4-106">Method</span></span>|<span data-ttu-id="571f4-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="571f4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="571f4-108">Icordebugremotetarget::gethostname yöntemi</span><span class="sxs-lookup"><span data-stu-id="571f4-108">ICorDebugRemoteTarget::GetHostName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-gethostname-method.md)|<span data-ttu-id="571f4-109">Ana bilgisayar adı veya bir uzak makinenin IP adresini döndürür.</span><span class="sxs-lookup"><span data-stu-id="571f4-109">Returns the host name or the IP address of a remote machine.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="571f4-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="571f4-110">Remarks</span></span>  
 <span data-ttu-id="571f4-111">Karışık mod (diğer bir deyişle, yönetilen ve yerel kodu) hata ayıklama Windows 95, Windows 98 veya Windows ME ya da (örneğin, IA-64 ve AMD64) x86 olmayan platformlarda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="571f4-111">Mixed-mode (that is, managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA-64 and AMD64).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="571f4-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="571f4-112">Requirements</span></span>  
 <span data-ttu-id="571f4-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="571f4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="571f4-114">**Başlık:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="571f4-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="571f4-115">**Kitaplığı:** : CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="571f4-115">**Library:** : CorGuids.lib</span></span>  
  
 <span data-ttu-id="571f4-116">**.NET framework sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="571f4-116">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="571f4-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="571f4-117">See Also</span></span>  
 [<span data-ttu-id="571f4-118">Icordebugremote arabirimi</span><span class="sxs-lookup"><span data-stu-id="571f4-118">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [<span data-ttu-id="571f4-119">Icordebug arabirimi</span><span class="sxs-lookup"><span data-stu-id="571f4-119">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="571f4-120">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="571f4-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
