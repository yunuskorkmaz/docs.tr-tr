---
title: ICorProfilerInfo2::GetStringLayout Metodu
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
- ICorProfilerInfo2.GetStringLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStringLayout
helpviewer_keywords:
- GetStringLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetStringLayout method [.NET Framework profiling]
ms.assetid: 43189651-a535-4803-a1d1-f1c427ace2ca
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1ad91829fab31b47a1dd51bb6cc9118c2ebe4c3a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getstringlayout-method"></a><span data-ttu-id="2d976-102">ICorProfilerInfo2::GetStringLayout Metodu</span><span class="sxs-lookup"><span data-stu-id="2d976-102">ICorProfilerInfo2::GetStringLayout Method</span></span>
<span data-ttu-id="2d976-103">Bir dize nesnesi düzeni hakkındaki bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="2d976-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="2d976-104">Bu yöntem de kullanım dışı [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]ve yerine geçen [Icorprofilerınfo3::getstringlayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2d976-104">This method is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], and is superseded by the [ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d976-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d976-105">Syntax</span></span>  
  
```  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2d976-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2d976-106">Parameters</span></span>  
 `pBufferLengthOffset`  
 <span data-ttu-id="2d976-107">[out] Konuma göre uzaklığını gösteren bir işaretçi `ObjectID` dize uzunluğu depolayan işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="2d976-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string.</span></span> <span data-ttu-id="2d976-108">Uzunluk olarak saklanan bir `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="2d976-108">The length is stored as a `DWORD`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2d976-109">Bu parametre dize uzunluğu kendisini arabelleği uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="2d976-109">This parameter returns the length of the string itself, not the length of the buffer.</span></span> <span data-ttu-id="2d976-110">Arabelleğin uzunluğu artık kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="2d976-110">The length of the buffer is no longer available.</span></span>  
  
 `PStringLengthOffset`  
 <span data-ttu-id="2d976-111">[out] Konuma göre uzaklığını gösteren bir işaretçi `ObjectID` dize uzunluğu depolayan işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="2d976-111">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="2d976-112">Uzunluk olarak saklanan bir `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="2d976-112">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="2d976-113">[out] Bağıntı arabellek uzaklığı bir işaretçi `ObjectID` geniş karakter dizesi depolayan işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="2d976-113">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, that stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d976-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d976-114">Remarks</span></span>  
 <span data-ttu-id="2d976-115">`GetStringLayout` Yöntemi göreli uzaklıkları alır `ObjectID` aşağıdaki depolandığı konumun işaretçi:</span><span class="sxs-lookup"><span data-stu-id="2d976-115">The `GetStringLayout` method gets the offsets, relative to the `ObjectID` pointer, of the locations in which the following are stored:</span></span>  
  
-   <span data-ttu-id="2d976-116">Dizesinin arabellek uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="2d976-116">The length of the string's buffer.</span></span>  
  
-   <span data-ttu-id="2d976-117">Dize uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="2d976-117">The length of the string itself.</span></span>  
  
-   <span data-ttu-id="2d976-118">Geniş karakterler gerçek dizesi içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="2d976-118">The buffer that contains the actual string of wide characters.</span></span>  
  
 <span data-ttu-id="2d976-119">Null ile sonlandırılmış dizeler olabilir.</span><span class="sxs-lookup"><span data-stu-id="2d976-119">Strings may be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d976-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d976-120">Requirements</span></span>  
 <span data-ttu-id="2d976-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d976-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d976-122">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2d976-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2d976-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d976-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d976-124">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d976-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d976-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2d976-125">See Also</span></span>  
 [<span data-ttu-id="2d976-126">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d976-126">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="2d976-127">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d976-127">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
