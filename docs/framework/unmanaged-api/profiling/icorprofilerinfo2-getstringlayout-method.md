---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo2:: GetStringLayout yöntemi'
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
ms.openlocfilehash: 145d748d756fd30ef0522d1c516f8f63ca604545
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716386"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a><span data-ttu-id="031cf-103">ICorProfilerInfo2::GetStringLayout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="031cf-103">ICorProfilerInfo2::GetStringLayout Method</span></span>

<span data-ttu-id="031cf-104">Bir dize nesnesinin yerleşimi hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="031cf-104">Gets information about the layout of a string object.</span></span> <span data-ttu-id="031cf-105">Bu yöntem .NET Framework 4 ' te kullanım dışıdır ve yerine [ICorProfilerInfo3:: GetStringLayout2](icorprofilerinfo3-getstringlayout2-method.md) yöntemi almıştır.</span><span class="sxs-lookup"><span data-stu-id="031cf-105">This method is deprecated in the .NET Framework 4, and is superseded by the [ICorProfilerInfo3::GetStringLayout2](icorprofilerinfo3-getstringlayout2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="031cf-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="031cf-106">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="031cf-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="031cf-107">Parameters</span></span>  

 `pBufferLengthOffset`  
 <span data-ttu-id="031cf-108">dışı Dizenin uzunluğunu depolayan işaretçiye göre konum uzaklığına yönelik bir işaretçi `ObjectID` .</span><span class="sxs-lookup"><span data-stu-id="031cf-108">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string.</span></span> <span data-ttu-id="031cf-109">Uzunluk bir olarak depolanır `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="031cf-109">The length is stored as a `DWORD`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="031cf-110">Bu parametre, arabelleğin uzunluğunu değil, dizenin kendisinin uzunluğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="031cf-110">This parameter returns the length of the string itself, not the length of the buffer.</span></span> <span data-ttu-id="031cf-111">Arabelleğin uzunluğu artık kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="031cf-111">The length of the buffer is no longer available.</span></span>  
  
 `PStringLengthOffset`  
 <span data-ttu-id="031cf-112">dışı Dizenin kendisinin uzunluğunu depolayan işaretçiye göre konum uzaklığına yönelik bir işaretçi `ObjectID` .</span><span class="sxs-lookup"><span data-stu-id="031cf-112">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="031cf-113">Uzunluk bir olarak depolanır `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="031cf-113">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="031cf-114">dışı `ObjectID` Geniş karakter dizesini depolayan, işaretçiye göre arabelleğin uzaklığına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="031cf-114">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, that stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="031cf-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="031cf-115">Remarks</span></span>  

 <span data-ttu-id="031cf-116">`GetStringLayout`Yöntemi, aşağıdakilerin depolandığı konumların göreli olarak kaydırmalarını alır `ObjectID` :</span><span class="sxs-lookup"><span data-stu-id="031cf-116">The `GetStringLayout` method gets the offsets, relative to the `ObjectID` pointer, of the locations in which the following are stored:</span></span>  
  
- <span data-ttu-id="031cf-117">Dize arabelleğinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="031cf-117">The length of the string's buffer.</span></span>  
  
- <span data-ttu-id="031cf-118">Dizenin kendisi için uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="031cf-118">The length of the string itself.</span></span>  
  
- <span data-ttu-id="031cf-119">Geniş karakterlerden oluşan gerçek dizeyi içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="031cf-119">The buffer that contains the actual string of wide characters.</span></span>  
  
 <span data-ttu-id="031cf-120">Dizeler null ile sonlandırılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="031cf-120">Strings may be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="031cf-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="031cf-121">Requirements</span></span>  

 <span data-ttu-id="031cf-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="031cf-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="031cf-123">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="031cf-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="031cf-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="031cf-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="031cf-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="031cf-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="031cf-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="031cf-126">See also</span></span>

- [<span data-ttu-id="031cf-127">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="031cf-127">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="031cf-128">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="031cf-128">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
