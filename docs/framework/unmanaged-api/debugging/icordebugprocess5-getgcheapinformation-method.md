---
title: ICorDebugProcess5::GetGCHeapInformation Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetGCHeapInformation
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetGCHeapInformation
helpviewer_keywords:
- ICorDebugProcess5::GetGCHeapInformation method [.NET Framework debugging]
- GetGCHeapInformation method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: b9538ceb-230a-4079-9cb2-903dbf5c1848
topic_type:
- apiref
ms.openlocfilehash: 3aa9fe884b16a239f5105dd262edeb8fc3e4abaa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084401"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="38f05-102">ICorDebugProcess5::GetGCHeapInformation Metodu</span><span class="sxs-lookup"><span data-stu-id="38f05-102">ICorDebugProcess5::GetGCHeapInformation Method</span></span>
<span data-ttu-id="38f05-103">Çöp toplama yığını hakkında şu anda numaralandırılabilir olup olmadığı dahil genel bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="38f05-103">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38f05-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38f05-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38f05-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="38f05-105">Parameters</span></span>  
 `pHeapInfo`  
 <span data-ttu-id="38f05-106">dışı Çöp toplama yığını hakkında genel bilgi sağlayan bir [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) değeri işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="38f05-106">[out] A pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38f05-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="38f05-107">Remarks</span></span>  
 <span data-ttu-id="38f05-108">İşlemdeki çöp toplama yapılarının Şu anda geçerli olduğundan emin olmak için yığın veya ayrı yığın bölgelerini numaralandırmadan önce `ICorDebugProcess5::GetGCHeapInformation` yöntemi çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="38f05-108">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="38f05-109">Atık toplama yığını, bir koleksiyon devam ederken eklenebilir olamaz.</span><span class="sxs-lookup"><span data-stu-id="38f05-109">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="38f05-110">Aksi takdirde, numaralandırma geçersiz çöp toplama yapılarını yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="38f05-110">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38f05-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="38f05-111">Requirements</span></span>  
 <span data-ttu-id="38f05-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38f05-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38f05-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="38f05-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38f05-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="38f05-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38f05-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38f05-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38f05-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38f05-116">See also</span></span>

- [<span data-ttu-id="38f05-117">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="38f05-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="38f05-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="38f05-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
