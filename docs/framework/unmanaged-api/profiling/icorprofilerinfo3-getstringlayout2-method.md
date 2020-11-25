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
ms.openlocfilehash: dc4df7e7cb93f137013d0a0e4d805c7563d4fe1a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697902"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="50701-102">ICorProfilerInfo3::GetStringLayout2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50701-102">ICorProfilerInfo3::GetStringLayout2 Method</span></span>

<span data-ttu-id="50701-103">Bir dize nesnesinin yerleşimi hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="50701-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="50701-104">Bu yöntem [ICorProfilerInfo2:: GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) yönteminin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="50701-104">This method supersedes the [ICorProfilerInfo2::GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50701-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="50701-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50701-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="50701-106">Parameters</span></span>  

 `pStringLengthOffset`  
 <span data-ttu-id="50701-107">dışı Dizenin kendisinin uzunluğunu depolayan işaretçiye göre konum uzaklığına yönelik bir işaretçi `ObjectID` .</span><span class="sxs-lookup"><span data-stu-id="50701-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="50701-108">Uzunluk bir olarak depolanır `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="50701-108">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="50701-109">dışı Geniş karakter dizesini depolayan işaretçiye bağlı olarak, arabelleğin uzaklığına yönelik bir işaretçi `ObjectID` .</span><span class="sxs-lookup"><span data-stu-id="50701-109">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50701-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="50701-110">Remarks</span></span>  

 <span data-ttu-id="50701-111">Dizeler null ile sonlandırılmış olabilir veya olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="50701-111">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50701-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50701-112">Requirements</span></span>  

 <span data-ttu-id="50701-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50701-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50701-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="50701-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="50701-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="50701-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50701-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50701-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50701-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50701-117">See also</span></span>

- [<span data-ttu-id="50701-118">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="50701-118">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="50701-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="50701-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
