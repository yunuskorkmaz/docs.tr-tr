---
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2ad2092c902b137df0dfe108743ef4081ca5f04d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948121"
---
# <a name="icorprofilerinfogetobjectsize-method"></a><span data-ttu-id="92078-102">ICorProfilerInfo::GetObjectSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="92078-102">ICorProfilerInfo::GetObjectSize Method</span></span>
<span data-ttu-id="92078-103">Belirtilen nesnenin boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="92078-103">Gets the size of a specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92078-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92078-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92078-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="92078-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="92078-106">'ndaki Nesnenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="92078-106">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="92078-107">dışı Nesnenin boyutunun bayt cinsinden işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="92078-107">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92078-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="92078-108">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="92078-109">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="92078-109">This method is obsolete.</span></span> <span data-ttu-id="92078-110">64-bit platformlarda 4.000'den büyük nesneler için COR_E_OVERFLOW döndürür.</span><span class="sxs-lookup"><span data-stu-id="92078-110">It returns COR_E_OVERFLOW for objects greater than 4GB on 64-bit platforms.</span></span> <span data-ttu-id="92078-111">Bunun yerine [ICorProfilerInfo4:: GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="92078-111">Use the  [ICorProfilerInfo4::GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="92078-112">Aynı türdeki farklı nesneler genellikle aynı boyutta olur.</span><span class="sxs-lookup"><span data-stu-id="92078-112">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="92078-113">Ancak, diziler veya dizeler gibi bazı türlerin her nesne için farklı boyutta bir boyutu olabilir.</span><span class="sxs-lookup"><span data-stu-id="92078-113">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
 <span data-ttu-id="92078-114">`GetObjectSize` Yöntem tarafından döndürülen boyut, nesne çöp toplama yığınında olduktan sonra görünebilen herhangi bir hizalama dolgusu içermez.</span><span class="sxs-lookup"><span data-stu-id="92078-114">The size returned by the `GetObjectSize` method does not include any alignment padding that may appear after the object is on the garbage collection heap.</span></span> <span data-ttu-id="92078-115">Çöp toplama yığınında nesnesinden `GetObjectSize` nesneye ilerlemek için yöntemini kullanırsanız, gerektiğinde hizalama doldurmayı el ile ekleyin.</span><span class="sxs-lookup"><span data-stu-id="92078-115">If you use the `GetObjectSize` method to advance from object to object on the garbage collection heap, add alignment padding manually, as necessary.</span></span>  
  
- <span data-ttu-id="92078-116">32 bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1 ve COR_PRF_GC_GEN_2 4 baytlık hizalama kullanın ve COR_PRF_GC_LARGE_OBJECT_HEAP 8 baytlık hizalama kullanır.</span><span class="sxs-lookup"><span data-stu-id="92078-116">On 32-bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1, and COR_PRF_GC_GEN_2 use 4-byte alignment, and COR_PRF_GC_LARGE_OBJECT_HEAP uses 8-byte alignment.</span></span>  
  
- <span data-ttu-id="92078-117">64 bit Windows üzerinde hizalama her zaman 8 bayttır.</span><span class="sxs-lookup"><span data-stu-id="92078-117">On 64-bit Windows, the alignment is always 8 bytes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92078-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="92078-118">Requirements</span></span>  
 <span data-ttu-id="92078-119">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92078-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92078-120">**Üst bilgi** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="92078-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="92078-121">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="92078-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92078-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92078-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92078-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92078-123">See also</span></span>

- [<span data-ttu-id="92078-124">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92078-124">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
