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
ms.openlocfilehash: 62d45da44a95eae399fbbd287aa997a5f913d0b0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209662"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="0b72d-102">ICorDebugProcess5::GetGCHeapInformation Metodu</span><span class="sxs-lookup"><span data-stu-id="0b72d-102">ICorDebugProcess5::GetGCHeapInformation Method</span></span>
<span data-ttu-id="0b72d-103">Çöp toplama yığını hakkında şu anda numaralandırılabilir olup olmadığı dahil genel bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b72d-103">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b72d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b72d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b72d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0b72d-105">Parameters</span></span>  
 `pHeapInfo`  
 <span data-ttu-id="0b72d-106">dışı Çöp toplama yığını hakkında genel bilgi sağlayan [COR_HEAPINFO](cor-heapinfo-structure.md) değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0b72d-106">[out] A pointer to a [COR_HEAPINFO](cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b72d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b72d-107">Remarks</span></span>  
 <span data-ttu-id="0b72d-108">`ICorDebugProcess5::GetGCHeapInformation`İşlemdeki çöp toplama yapılarının Şu anda geçerli olduğundan emin olmak için, yığın veya ayrı yığın bölgelerini numaralandırmadan önce yöntemi çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0b72d-108">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="0b72d-109">Atık toplama yığını, bir koleksiyon devam ederken eklenebilir olamaz.</span><span class="sxs-lookup"><span data-stu-id="0b72d-109">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="0b72d-110">Aksi takdirde, numaralandırma geçersiz çöp toplama yapılarını yakalayabilir.</span><span class="sxs-lookup"><span data-stu-id="0b72d-110">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b72d-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b72d-111">Requirements</span></span>  
 <span data-ttu-id="0b72d-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b72d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b72d-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0b72d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b72d-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0b72d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b72d-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b72d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b72d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b72d-116">See also</span></span>

- [<span data-ttu-id="0b72d-117">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b72d-117">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="0b72d-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0b72d-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
