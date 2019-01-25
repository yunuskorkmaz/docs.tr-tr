---
title: ICorProfilerInfo2::GetStringLayout Metodu
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b87444165f0504964b6489beb562ca2e8bd4697e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524292"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a><span data-ttu-id="25660-102">ICorProfilerInfo2::GetStringLayout Metodu</span><span class="sxs-lookup"><span data-stu-id="25660-102">ICorProfilerInfo2::GetStringLayout Method</span></span>
<span data-ttu-id="25660-103">Bir dize nesnesinin düzeni hakkındaki bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="25660-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="25660-104">Bu metot kullanımdan kaldırılmıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]ve yerine geçen [Icorprofilerınfo3::getstringlayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="25660-104">This method is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], and is superseded by the [ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25660-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="25660-105">Syntax</span></span>  
  
```  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="25660-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="25660-106">Parameters</span></span>  
 `pBufferLengthOffset`  
 <span data-ttu-id="25660-107">[out] İşaretçisi konumuna göre uzaklığı `ObjectID` dizenin uzunluğunu depolayan bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="25660-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string.</span></span> <span data-ttu-id="25660-108">Uzunluğu olarak depolanan bir `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="25660-108">The length is stored as a `DWORD`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="25660-109">Bu parametre, dizenin uzunluğu kendisi değil arabellek uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="25660-109">This parameter returns the length of the string itself, not the length of the buffer.</span></span> <span data-ttu-id="25660-110">Arabellek uzunluğu artık kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="25660-110">The length of the buffer is no longer available.</span></span>  
  
 `PStringLengthOffset`  
 <span data-ttu-id="25660-111">[out] İşaretçisi konumuna göre uzaklığı `ObjectID` dizenin uzunluğunu depolayan bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="25660-111">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="25660-112">Uzunluğu olarak depolanan bir `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="25660-112">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="25660-113">[out] Göreli yolu arabellek uzaklığı için bir işaretçi `ObjectID` geniş karakter dizesini depolayan bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="25660-113">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, that stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25660-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="25660-114">Remarks</span></span>  
 <span data-ttu-id="25660-115">`GetStringLayout` Yöntemi göreli uzaklıkları alır `ObjectID` işaretçisinin konumları aşağıdaki depolanır:</span><span class="sxs-lookup"><span data-stu-id="25660-115">The `GetStringLayout` method gets the offsets, relative to the `ObjectID` pointer, of the locations in which the following are stored:</span></span>  
  
-   <span data-ttu-id="25660-116">Dizenin arabellek uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="25660-116">The length of the string's buffer.</span></span>  
  
-   <span data-ttu-id="25660-117">Dize uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="25660-117">The length of the string itself.</span></span>  
  
-   <span data-ttu-id="25660-118">Gerçek geniş karakter dizesini içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="25660-118">The buffer that contains the actual string of wide characters.</span></span>  
  
 <span data-ttu-id="25660-119">Null ile sonlandırılmış dizeler olabilir.</span><span class="sxs-lookup"><span data-stu-id="25660-119">Strings may be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25660-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="25660-120">Requirements</span></span>  
 <span data-ttu-id="25660-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25660-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25660-122">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="25660-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="25660-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25660-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25660-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25660-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25660-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25660-125">See also</span></span>
- [<span data-ttu-id="25660-126">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25660-126">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="25660-127">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25660-127">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
