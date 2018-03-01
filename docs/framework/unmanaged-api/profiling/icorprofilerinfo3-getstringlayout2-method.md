---
title: ICorProfilerInfo3::GetStringLayout2 Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 97f4ab9eefa8bf1f2b3a5057f24b6a940ba91f41
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="5ce40-102">ICorProfilerInfo3::GetStringLayout2 Metodu</span><span class="sxs-lookup"><span data-stu-id="5ce40-102">ICorProfilerInfo3::GetStringLayout2 Method</span></span>
<span data-ttu-id="5ce40-103">Bir dize nesnesi düzeni hakkındaki bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="5ce40-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="5ce40-104">Bu yöntem yerini [Icorprofilerınfo2::getstringlayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5ce40-104">This method supersedes the [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ce40-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ce40-105">Syntax</span></span>  
  
```  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5ce40-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5ce40-106">Parameters</span></span>  
 `pStringLengthOffset`  
 <span data-ttu-id="5ce40-107">[out] Konuma göre uzaklığını gösteren bir işaretçi `ObjectID` dize uzunluğu depolayan işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="5ce40-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="5ce40-108">Uzunluk olarak saklanan bir `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="5ce40-108">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="5ce40-109">[out] Bağıntı arabellek uzaklığı bir işaretçi `ObjectID` geniş karakter dizesi depolar işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5ce40-109">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ce40-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ce40-110">Remarks</span></span>  
 <span data-ttu-id="5ce40-111">Dizeleri olabilir veya null ile sonlandırılmış olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="5ce40-111">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ce40-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ce40-112">Requirements</span></span>  
 <span data-ttu-id="5ce40-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ce40-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ce40-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5ce40-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5ce40-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ce40-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ce40-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ce40-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ce40-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5ce40-117">See Also</span></span>  
 [<span data-ttu-id="5ce40-118">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5ce40-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="5ce40-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5ce40-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
