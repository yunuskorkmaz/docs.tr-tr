---
description: ': ICorProfilerInfo:: GetObjectSize yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerInfo::GetObjectSize Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetObjectSize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetObjectSize
helpviewer_keywords:
- GetObjectSize method [.NET Framework profiling]
- ICorProfilerInfo::GetObjectSize method [.NET Framework profiling]
ms.assetid: 9f02e763-73f7-42cb-a41c-f78499d9482c
topic_type:
- apiref
ms.openlocfilehash: c762b43e87c6f25b301f3f677728ca8cbe19b138
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788637"
---
# <a name="icorprofilerinfogetobjectsize-method"></a><span data-ttu-id="d82af-103">ICorProfilerInfo::GetObjectSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d82af-103">ICorProfilerInfo::GetObjectSize Method</span></span>

<span data-ttu-id="d82af-104">Belirtilen nesnenin boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="d82af-104">Gets the size of a specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d82af-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d82af-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d82af-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d82af-106">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="d82af-107">'ndaki Nesnenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="d82af-107">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="d82af-108">dışı Nesnenin boyutunun bayt cinsinden işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d82af-108">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d82af-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d82af-109">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d82af-110">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="d82af-110">This method is obsolete.</span></span> <span data-ttu-id="d82af-111">64-bit platformlarda 4.000'DEN büyük nesneler için COR_E_OVERFLOW döndürür.</span><span class="sxs-lookup"><span data-stu-id="d82af-111">It returns COR_E_OVERFLOW for objects greater than 4GB on 64-bit platforms.</span></span> <span data-ttu-id="d82af-112">Bunun yerine  [ICorProfilerInfo4:: GetObjectSize2](icorprofilerinfo4-getobjectsize2-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d82af-112">Use the  [ICorProfilerInfo4::GetObjectSize2](icorprofilerinfo4-getobjectsize2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="d82af-113">Aynı türdeki farklı nesneler genellikle aynı boyutta olur.</span><span class="sxs-lookup"><span data-stu-id="d82af-113">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="d82af-114">Ancak, diziler veya dizeler gibi bazı türlerin her nesne için farklı boyutta bir boyutu olabilir.</span><span class="sxs-lookup"><span data-stu-id="d82af-114">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
 <span data-ttu-id="d82af-115">Yöntem tarafından döndürülen boyut, `GetObjectSize` nesne çöp toplama yığınında olduktan sonra görünebilen herhangi bir hizalama dolgusu içermez.</span><span class="sxs-lookup"><span data-stu-id="d82af-115">The size returned by the `GetObjectSize` method does not include any alignment padding that may appear after the object is on the garbage collection heap.</span></span> <span data-ttu-id="d82af-116">`GetObjectSize`Çöp toplama yığınında nesnesinden nesneye ilerlemek için yöntemini kullanırsanız, gerektiğinde hizalama doldurmayı el ile ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d82af-116">If you use the `GetObjectSize` method to advance from object to object on the garbage collection heap, add alignment padding manually, as necessary.</span></span>  
  
- <span data-ttu-id="d82af-117">32 bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1 ve COR_PRF_GC_GEN_2 4 baytlık hizalama kullanın ve COR_PRF_GC_LARGE_OBJECT_HEAP 8 baytlık hizalama kullanır.</span><span class="sxs-lookup"><span data-stu-id="d82af-117">On 32-bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1, and COR_PRF_GC_GEN_2 use 4-byte alignment, and COR_PRF_GC_LARGE_OBJECT_HEAP uses 8-byte alignment.</span></span>  
  
- <span data-ttu-id="d82af-118">64 bit Windows üzerinde hizalama her zaman 8 bayttır.</span><span class="sxs-lookup"><span data-stu-id="d82af-118">On 64-bit Windows, the alignment is always 8 bytes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d82af-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d82af-119">Requirements</span></span>  

 <span data-ttu-id="d82af-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d82af-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d82af-121">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d82af-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d82af-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d82af-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d82af-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d82af-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d82af-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d82af-124">See also</span></span>

- [<span data-ttu-id="d82af-125">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d82af-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
