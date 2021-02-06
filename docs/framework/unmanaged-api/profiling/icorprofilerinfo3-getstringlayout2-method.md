---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo3:: GetStringLayout2 yöntemi'
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
ms.openlocfilehash: 398d06dc62245e6a2201feacb62ebbb1e4839ccb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646679"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="ed5da-103">ICorProfilerInfo3::GetStringLayout2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ed5da-103">ICorProfilerInfo3::GetStringLayout2 Method</span></span>

<span data-ttu-id="ed5da-104">Bir dize nesnesinin yerleşimi hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="ed5da-104">Gets information about the layout of a string object.</span></span> <span data-ttu-id="ed5da-105">Bu yöntem [ICorProfilerInfo2:: GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) yönteminin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="ed5da-105">This method supersedes the [ICorProfilerInfo2::GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed5da-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ed5da-106">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed5da-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ed5da-107">Parameters</span></span>  

 `pStringLengthOffset`  
 <span data-ttu-id="ed5da-108">dışı Dizenin kendisinin uzunluğunu depolayan işaretçiye göre konum uzaklığına yönelik bir işaretçi `ObjectID` .</span><span class="sxs-lookup"><span data-stu-id="ed5da-108">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="ed5da-109">Uzunluk bir olarak depolanır `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="ed5da-109">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="ed5da-110">dışı Geniş karakter dizesini depolayan işaretçiye bağlı olarak, arabelleğin uzaklığına yönelik bir işaretçi `ObjectID` .</span><span class="sxs-lookup"><span data-stu-id="ed5da-110">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed5da-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ed5da-111">Remarks</span></span>  

 <span data-ttu-id="ed5da-112">Dizeler null ile sonlandırılmış olabilir veya olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="ed5da-112">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed5da-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ed5da-113">Requirements</span></span>  

 <span data-ttu-id="ed5da-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed5da-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed5da-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ed5da-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ed5da-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ed5da-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed5da-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed5da-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed5da-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed5da-118">See also</span></span>

- [<span data-ttu-id="ed5da-119">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ed5da-119">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="ed5da-120">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ed5da-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
