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
ms.openlocfilehash: f3727343755d7014202f844be28414d31ce55bc1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862262"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="fed85-102">ICorProfilerInfo3::GetStringLayout2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fed85-102">ICorProfilerInfo3::GetStringLayout2 Method</span></span>
<span data-ttu-id="fed85-103">Bir dize nesnesinin yerleşimi hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="fed85-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="fed85-104">Bu yöntem [ICorProfilerInfo2:: GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) yönteminin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="fed85-104">This method supersedes the [ICorProfilerInfo2::GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fed85-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fed85-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fed85-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fed85-106">Parameters</span></span>  
 `pStringLengthOffset`  
 <span data-ttu-id="fed85-107">dışı Konumun, dizenin uzunluğunu depolayan `ObjectID` işaretçisine göre konum uzaklığına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fed85-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="fed85-108">Uzunluk bir `DWORD`olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="fed85-108">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="fed85-109">dışı Geniş karakter dizesini depolayan `ObjectID` işaretçisine göre arabelleğin uzaklığına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fed85-109">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fed85-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fed85-110">Remarks</span></span>  
 <span data-ttu-id="fed85-111">Dizeler null ile sonlandırılmış olabilir veya olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="fed85-111">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fed85-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fed85-112">Requirements</span></span>  
 <span data-ttu-id="fed85-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fed85-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fed85-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fed85-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fed85-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fed85-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fed85-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fed85-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fed85-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fed85-117">See also</span></span>

- [<span data-ttu-id="fed85-118">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fed85-118">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="fed85-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fed85-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
