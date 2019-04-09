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
ms.openlocfilehash: e0957228489df30833790e59da1ca597fc1f92f5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076513"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="4cfbf-102">ICorProfilerInfo3::GetStringLayout2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4cfbf-102">ICorProfilerInfo3::GetStringLayout2 Method</span></span>
<span data-ttu-id="4cfbf-103">Bir dize nesnesinin düzeni hakkındaki bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="4cfbf-104">Bu yöntem yerine geçer [Icorprofilerınfo2::getstringlayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-104">This method supersedes the [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cfbf-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4cfbf-105">Syntax</span></span>  
  
```  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4cfbf-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4cfbf-106">Parameters</span></span>  
 `pStringLengthOffset`  
 <span data-ttu-id="4cfbf-107">[out] İşaretçisi konumuna göre uzaklığı `ObjectID` dizenin uzunluğunu depolayan bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="4cfbf-108">Uzunluğu olarak depolanan bir `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-108">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="4cfbf-109">[out] Göreli yolu arabellek uzaklığı için bir işaretçi `ObjectID` geniş karakter dizesini depolar işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-109">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cfbf-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4cfbf-110">Remarks</span></span>  
 <span data-ttu-id="4cfbf-111">Dizeleri olabilir veya null ile sonlandırılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-111">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cfbf-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4cfbf-112">Requirements</span></span>  
 <span data-ttu-id="4cfbf-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cfbf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cfbf-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4cfbf-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4cfbf-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4cfbf-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="4cfbf-116">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="4cfbf-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4cfbf-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4cfbf-117">See also</span></span>

- [<span data-ttu-id="4cfbf-118">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4cfbf-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="4cfbf-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4cfbf-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
