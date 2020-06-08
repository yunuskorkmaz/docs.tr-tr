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
ms.openlocfilehash: 257cf24fa476c75d6ec949e17a5b83fc015b8d43
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496808"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a><span data-ttu-id="2ab8b-102">ICorProfilerInfo2::GetStringLayout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2ab8b-102">ICorProfilerInfo2::GetStringLayout Method</span></span>
<span data-ttu-id="2ab8b-103">Bir dize nesnesinin yerleşimi hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="2ab8b-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="2ab8b-104">Bu yöntem .NET Framework 4 ' te kullanım dışıdır ve yerine [ICorProfilerInfo3:: GetStringLayout2](icorprofilerinfo3-getstringlayout2-method.md) yöntemi almıştır.</span><span class="sxs-lookup"><span data-stu-id="2ab8b-104">This method is deprecated in the .NET Framework 4, and is superseded by the [ICorProfilerInfo3::GetStringLayout2](icorprofilerinfo3-getstringlayout2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ab8b-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2ab8b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ab8b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2ab8b-106">Parameters</span></span>  
 `pBufferLengthOffset`  
 <span data-ttu-id="2ab8b-107">dışı Dizenin uzunluğunu depolayan işaretçiye göre konum uzaklığına yönelik bir işaretçi `ObjectID` .</span><span class="sxs-lookup"><span data-stu-id="2ab8b-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string.</span></span> <span data-ttu-id="2ab8b-108">Uzunluk bir olarak depolanır `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="2ab8b-108">The length is stored as a `DWORD`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2ab8b-109">Bu parametre, arabelleğin uzunluğunu değil, dizenin kendisinin uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ab8b-109">This parameter returns the length of the string itself, not the length of the buffer.</span></span> <span data-ttu-id="2ab8b-110">Arabelleğin uzunluğu artık kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="2ab8b-110">The length of the buffer is no longer available.</span></span>  
  
 `PStringLengthOffset`  
 <span data-ttu-id="2ab8b-111">dışı Dizenin kendisinin uzunluğunu depolayan işaretçiye göre konum uzaklığına yönelik bir işaretçi `ObjectID` .</span><span class="sxs-lookup"><span data-stu-id="2ab8b-111">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="2ab8b-112">Uzunluk bir olarak depolanır `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="2ab8b-112">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="2ab8b-113">dışı `ObjectID`Geniş karakter dizesini depolayan, işaretçiye göre arabelleğin uzaklığına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2ab8b-113">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, that stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ab8b-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2ab8b-114">Remarks</span></span>  
 <span data-ttu-id="2ab8b-115">`GetStringLayout`Yöntemi, aşağıdakilerin depolandığı konumların göreli olarak kaydırmalarını alır `ObjectID` :</span><span class="sxs-lookup"><span data-stu-id="2ab8b-115">The `GetStringLayout` method gets the offsets, relative to the `ObjectID` pointer, of the locations in which the following are stored:</span></span>  
  
- <span data-ttu-id="2ab8b-116">Dize arabelleğinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="2ab8b-116">The length of the string's buffer.</span></span>  
  
- <span data-ttu-id="2ab8b-117">Dizenin kendisi için uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="2ab8b-117">The length of the string itself.</span></span>  
  
- <span data-ttu-id="2ab8b-118">Geniş karakterlerden oluşan gerçek dizeyi içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="2ab8b-118">The buffer that contains the actual string of wide characters.</span></span>  
  
 <span data-ttu-id="2ab8b-119">Dizeler null ile sonlandırılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="2ab8b-119">Strings may be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ab8b-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2ab8b-120">Requirements</span></span>  
 <span data-ttu-id="2ab8b-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ab8b-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ab8b-122">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2ab8b-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2ab8b-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2ab8b-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ab8b-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ab8b-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ab8b-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ab8b-125">See also</span></span>

- [<span data-ttu-id="2ab8b-126">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2ab8b-126">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="2ab8b-127">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2ab8b-127">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
