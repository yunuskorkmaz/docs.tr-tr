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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 63ad2532240c9f18a00421281fae0d111dbfaec5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963801"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a><span data-ttu-id="f3f4a-102">ICorProfilerInfo2::GetStringLayout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f3f4a-102">ICorProfilerInfo2::GetStringLayout Method</span></span>
<span data-ttu-id="f3f4a-103">Bir dize nesnesinin yerleşimi hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="f3f4a-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="f3f4a-104">Bu yöntem .NET Framework 4 ' te kullanım dışıdır ve yerine [ICorProfilerInfo3:: GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) yöntemi almıştır.</span><span class="sxs-lookup"><span data-stu-id="f3f4a-104">This method is deprecated in the .NET Framework 4, and is superseded by the [ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3f4a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f3f4a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3f4a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f3f4a-106">Parameters</span></span>  
 `pBufferLengthOffset`  
 <span data-ttu-id="f3f4a-107">dışı Dizenin uzunluğunu depolayan `ObjectID` işaretçiye göre konum uzaklığına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f3f4a-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string.</span></span> <span data-ttu-id="f3f4a-108">Uzunluk bir `DWORD`olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="f3f4a-108">The length is stored as a `DWORD`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f3f4a-109">Bu parametre, arabelleğin uzunluğunu değil, dizenin kendisinin uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="f3f4a-109">This parameter returns the length of the string itself, not the length of the buffer.</span></span> <span data-ttu-id="f3f4a-110">Arabelleğin uzunluğu artık kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="f3f4a-110">The length of the buffer is no longer available.</span></span>  
  
 `PStringLengthOffset`  
 <span data-ttu-id="f3f4a-111">dışı Dizenin kendisinin uzunluğunu depolayan `ObjectID` işaretçiye göre konum uzaklığına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f3f4a-111">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="f3f4a-112">Uzunluk bir `DWORD`olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="f3f4a-112">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="f3f4a-113">dışı Geniş karakter dizesini depolayan, `ObjectID` işaretçiye göre arabelleğin uzaklığına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f3f4a-113">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, that stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3f4a-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f3f4a-114">Remarks</span></span>  
 <span data-ttu-id="f3f4a-115">Yöntemi, aşağıdakilerin depolandığı konumların göreli `ObjectID` olarak kaydırmalarını alır: `GetStringLayout`</span><span class="sxs-lookup"><span data-stu-id="f3f4a-115">The `GetStringLayout` method gets the offsets, relative to the `ObjectID` pointer, of the locations in which the following are stored:</span></span>  
  
- <span data-ttu-id="f3f4a-116">Dize arabelleğinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="f3f4a-116">The length of the string's buffer.</span></span>  
  
- <span data-ttu-id="f3f4a-117">Dizenin kendisi için uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="f3f4a-117">The length of the string itself.</span></span>  
  
- <span data-ttu-id="f3f4a-118">Geniş karakterlerden oluşan gerçek dizeyi içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="f3f4a-118">The buffer that contains the actual string of wide characters.</span></span>  
  
 <span data-ttu-id="f3f4a-119">Dizeler null ile sonlandırılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="f3f4a-119">Strings may be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3f4a-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f3f4a-120">Requirements</span></span>  
 <span data-ttu-id="f3f4a-121">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3f4a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3f4a-122">**Üst bilgi** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f3f4a-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f3f4a-123">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f3f4a-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3f4a-124">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3f4a-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3f4a-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3f4a-125">See also</span></span>

- [<span data-ttu-id="f3f4a-126">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f3f4a-126">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="f3f4a-127">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f3f4a-127">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
