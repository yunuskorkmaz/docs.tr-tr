---
title: ICorDebugThread4::GetBlockingObjects Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetBlockingObjects Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetBlockingObjects
helpviewer_keywords:
- GetBlockingObjects method [.NET Framework debugging]
- ICorDebugThread4::GetBlockingObjects method [.NET Framework debugging]
ms.assetid: a7e6c54e-7be9-4e52-bbb4-95f52458e8e4
topic_type:
- apiref
ms.openlocfilehash: 366b5124cc66a4e9a1c3bd4e77f604f15ba8d8a8
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379679"
---
# <a name="icordebugthread4getblockingobjects-method"></a><span data-ttu-id="91a22-102">ICorDebugThread4::GetBlockingObjects Metodu</span><span class="sxs-lookup"><span data-stu-id="91a22-102">ICorDebugThread4::GetBlockingObjects Method</span></span>
<span data-ttu-id="91a22-103">İş parçacığı engelleme bilgileri sağlayan [CorDebugBlockingObject](cordebugblockingobject-structure.md) yapılarının sıralı bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="91a22-103">Provides an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91a22-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="91a22-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
## <a name="parameters"></a><span data-ttu-id="91a22-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="91a22-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="91a22-106">dışı [CorDebugBlockingObject](cordebugblockingobject-structure.md) yapılarının sıralı numaralandırması için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="91a22-106">[out] A pointer to an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91a22-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="91a22-107">Remarks</span></span>  
 <span data-ttu-id="91a22-108">Döndürülen Numaralandırmadaki ilk öğe, iş parçacığını engelleyen ilk yapıya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="91a22-108">The first element in the returned enumeration corresponds to the first structure that is blocking the thread.</span></span> <span data-ttu-id="91a22-109">İkinci öğe, ilk kez engellendiğinde zaman uyumsuz yordam çağrısı (APC) çalıştırılırken karşılaşılan bir engelleme öğesine karşılık gelir ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="91a22-109">The second element corresponds to a blocking item that is encountered while running an asynchronous procedure call (APC) when blocked on the first, and so on.</span></span>  
  
 <span data-ttu-id="91a22-110">Sabit listesi yalnızca geçerli eşitlenmiş durumun süresi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="91a22-110">The enumeration is valid only for the duration of the current synchronized state.</span></span>  
  
 <span data-ttu-id="91a22-111">Hata ayıklanan, eşitlenmiş durumda olduğu sürece bu yöntem çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="91a22-111">This method must be called while the debuggee is in a synchronized state.</span></span>  
  
 <span data-ttu-id="91a22-112">`ppBlockingObjectEnum`Geçerli bir işaretçi değilse, sonuç tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="91a22-112">If `ppBlockingObjectEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="91a22-113">Bir iş parçacığı engellenirse ve hata belirlenemiyorsa, yöntem hatayı gösteren bir HRESULT döndürür; Aksi takdirde, S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="91a22-113">If a thread is blocked and the error cannot be determined, the method returns an HRESULT that indicates failure; otherwise, it returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91a22-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="91a22-114">Requirements</span></span>  
 <span data-ttu-id="91a22-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91a22-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91a22-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="91a22-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91a22-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="91a22-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91a22-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91a22-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91a22-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91a22-119">See also</span></span>

- [<span data-ttu-id="91a22-120">ICorDebugThread4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="91a22-120">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="91a22-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="91a22-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="91a22-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="91a22-122">Debugging</span></span>](index.md)
