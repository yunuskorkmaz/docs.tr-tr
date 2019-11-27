---
title: ICorProfilerInfo2::GetStringLayout Yöntemi
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
ms.openlocfilehash: 71e2bc1d60e050d817429db5bc6926b3b16c637c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431411"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a><span data-ttu-id="1a350-102">ICorProfilerInfo2::GetStringLayout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a350-102">ICorProfilerInfo2::GetStringLayout Method</span></span>
<span data-ttu-id="1a350-103">Bir dize nesnesinin yerleşimi hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="1a350-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="1a350-104">Bu yöntem .NET Framework 4 ' te kullanım dışıdır ve yerine [ICorProfilerInfo3:: GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) yöntemi almıştır.</span><span class="sxs-lookup"><span data-stu-id="1a350-104">This method is deprecated in the .NET Framework 4, and is superseded by the [ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a350-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a350-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a350-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1a350-106">Parameters</span></span>  
 `pBufferLengthOffset`  
 <span data-ttu-id="1a350-107">dışı Dizenin uzunluğunu depolayan `ObjectID` işaretçisine göre konum uzaklığına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1a350-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string.</span></span> <span data-ttu-id="1a350-108">Uzunluk bir `DWORD`olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="1a350-108">The length is stored as a `DWORD`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1a350-109">Bu parametre, arabelleğin uzunluğunu değil, dizenin kendisinin uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="1a350-109">This parameter returns the length of the string itself, not the length of the buffer.</span></span> <span data-ttu-id="1a350-110">Arabelleğin uzunluğu artık kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="1a350-110">The length of the buffer is no longer available.</span></span>  
  
 `PStringLengthOffset`  
 <span data-ttu-id="1a350-111">dışı Konumun, dizenin uzunluğunu depolayan `ObjectID` işaretçisine göre konum uzaklığına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1a350-111">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="1a350-112">Uzunluk bir `DWORD`olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="1a350-112">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="1a350-113">dışı Geniş karakter dizesini depolayan `ObjectID` işaretçisine göre arabelleğin uzaklığına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1a350-113">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, that stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a350-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1a350-114">Remarks</span></span>  
 <span data-ttu-id="1a350-115">`GetStringLayout` yöntemi, aşağıdakilerin depolandığı konumların `ObjectID` işaretçisine göre uzaklıkları alır:</span><span class="sxs-lookup"><span data-stu-id="1a350-115">The `GetStringLayout` method gets the offsets, relative to the `ObjectID` pointer, of the locations in which the following are stored:</span></span>  
  
- <span data-ttu-id="1a350-116">Dize arabelleğinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="1a350-116">The length of the string's buffer.</span></span>  
  
- <span data-ttu-id="1a350-117">Dizenin kendisi için uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="1a350-117">The length of the string itself.</span></span>  
  
- <span data-ttu-id="1a350-118">Geniş karakterlerden oluşan gerçek dizeyi içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="1a350-118">The buffer that contains the actual string of wide characters.</span></span>  
  
 <span data-ttu-id="1a350-119">Dizeler null ile sonlandırılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="1a350-119">Strings may be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a350-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a350-120">Requirements</span></span>  
 <span data-ttu-id="1a350-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a350-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a350-122">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1a350-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1a350-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1a350-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a350-124">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a350-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a350-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a350-125">See also</span></span>

- [<span data-ttu-id="1a350-126">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a350-126">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="1a350-127">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a350-127">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
