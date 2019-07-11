---
title: ICorProfilerInfo3::GetStringLayout2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetStringLayout2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetStringLayout2
helpviewer_keywords:
- ICorProfilerInfo3::GetStringLayout2 method [.NET Framework profiling]
- GetStringLayout2 method [.NET Framework profiling]
ms.assetid: 1a268496-ee51-4d84-8700-ee56fd0c499d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1ac724db000f84e37995a34e808d3df4b1e7a960
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765413"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="2d731-102">ICorProfilerInfo3::GetStringLayout2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2d731-102">ICorProfilerInfo3::GetStringLayout2 Method</span></span>
<span data-ttu-id="2d731-103">Bir dize nesnesinin düzeni hakkındaki bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="2d731-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="2d731-104">Bu yöntem yerine geçer [Icorprofilerınfo2::getstringlayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2d731-104">This method supersedes the [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d731-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d731-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d731-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2d731-106">Parameters</span></span>  
 `pStringLengthOffset`  
 <span data-ttu-id="2d731-107">[out] İşaretçisi konumuna göre uzaklığı `ObjectID` dizenin uzunluğunu depolayan bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2d731-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="2d731-108">Uzunluğu olarak depolanan bir `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="2d731-108">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="2d731-109">[out] Göreli yolu arabellek uzaklığı için bir işaretçi `ObjectID` geniş karakter dizesini depolar işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="2d731-109">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d731-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d731-110">Remarks</span></span>  
 <span data-ttu-id="2d731-111">Dizeleri olabilir veya null ile sonlandırılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="2d731-111">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d731-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d731-112">Requirements</span></span>  
 <span data-ttu-id="2d731-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d731-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d731-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2d731-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2d731-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d731-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d731-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d731-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d731-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d731-117">See also</span></span>

- [<span data-ttu-id="2d731-118">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2d731-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="2d731-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2d731-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
