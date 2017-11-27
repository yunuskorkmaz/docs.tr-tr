---
title: ICorProfilerInfo3::GetStringLayout2 Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.GetStringLayout2 Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::GetStringLayout2
helpviewer_keywords:
- ICorProfilerInfo3::GetStringLayout2 method [.NET Framework profiling]
- GetStringLayout2 method [.NET Framework profiling]
ms.assetid: 1a268496-ee51-4d84-8700-ee56fd0c499d
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: de89776c6208ec7e3434fa747057edbf818ec013
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="9d630-102">ICorProfilerInfo3::GetStringLayout2 Metodu</span><span class="sxs-lookup"><span data-stu-id="9d630-102">ICorProfilerInfo3::GetStringLayout2 Method</span></span>
<span data-ttu-id="9d630-103">Bir dize nesnesi düzeni hakkındaki bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="9d630-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="9d630-104">Bu yöntem yerini [Icorprofilerınfo2::getstringlayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9d630-104">This method supersedes the [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d630-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d630-105">Syntax</span></span>  
  
```  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d630-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9d630-106">Parameters</span></span>  
 `pStringLengthOffset`  
 <span data-ttu-id="9d630-107">[out] Konuma göre uzaklığını gösteren bir işaretçi `ObjectID` dize uzunluğu depolayan işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="9d630-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="9d630-108">Uzunluk olarak saklanan bir `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="9d630-108">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="9d630-109">[out] Bağıntı arabellek uzaklığı bir işaretçi `ObjectID` geniş karakter dizesi depolar işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9d630-109">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d630-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d630-110">Remarks</span></span>  
 <span data-ttu-id="9d630-111">Dizeleri olabilir veya null ile sonlandırılmış olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="9d630-111">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d630-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d630-112">Requirements</span></span>  
 <span data-ttu-id="9d630-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d630-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d630-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9d630-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9d630-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d630-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d630-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d630-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d630-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9d630-117">See Also</span></span>  
 [<span data-ttu-id="9d630-118">Icorprofilerınfo3 arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d630-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="9d630-119">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9d630-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
