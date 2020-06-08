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
ms.openlocfilehash: 51d5b2f2ee17cc177e3b0ddc7d2e0b82fd70063d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496379"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="4a75f-102">ICorProfilerInfo3::GetStringLayout2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4a75f-102">ICorProfilerInfo3::GetStringLayout2 Method</span></span>
<span data-ttu-id="4a75f-103">Bir dize nesnesinin yerleşimi hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="4a75f-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="4a75f-104">Bu yöntem [ICorProfilerInfo2:: GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) yönteminin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="4a75f-104">This method supersedes the [ICorProfilerInfo2::GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a75f-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="4a75f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a75f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4a75f-106">Parameters</span></span>  
 `pStringLengthOffset`  
 <span data-ttu-id="4a75f-107">dışı Dizenin kendisinin uzunluğunu depolayan işaretçiye göre konum uzaklığına yönelik bir işaretçi `ObjectID` .</span><span class="sxs-lookup"><span data-stu-id="4a75f-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="4a75f-108">Uzunluk bir olarak depolanır `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="4a75f-108">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="4a75f-109">dışı Geniş karakter dizesini depolayan işaretçiye bağlı olarak, arabelleğin uzaklığına yönelik bir işaretçi `ObjectID` .</span><span class="sxs-lookup"><span data-stu-id="4a75f-109">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a75f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a75f-110">Remarks</span></span>  
 <span data-ttu-id="4a75f-111">Dizeler null ile sonlandırılmış olabilir veya olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="4a75f-111">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a75f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4a75f-112">Requirements</span></span>  
 <span data-ttu-id="4a75f-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a75f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a75f-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4a75f-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4a75f-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4a75f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a75f-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a75f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a75f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a75f-117">See also</span></span>

- [<span data-ttu-id="4a75f-118">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4a75f-118">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="4a75f-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4a75f-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
