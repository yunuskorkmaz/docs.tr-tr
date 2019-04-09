---
title: ICorProfilerFunctionEnum::Skip Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
- ICorProfilerFunctionEnum::Skip method [.NET Framework profiling]
ms.assetid: 051465b9-e479-494a-804b-c880323b4cbe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f0e334c75afee60591db2b4e1f45cf0ec753ee2e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141659"
---
# <a name="icorprofilerfunctionenumskip-method"></a><span data-ttu-id="f1afd-102">ICorProfilerFunctionEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f1afd-102">ICorProfilerFunctionEnum::Skip Method</span></span>
<span data-ttu-id="f1afd-103">Böylece belirtilen sayıda öğeyi atlanır Numaralandırıcının imleç geçerli konumundan ilerler.</span><span class="sxs-lookup"><span data-stu-id="f1afd-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1afd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f1afd-104">Syntax</span></span>  
  
```  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1afd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f1afd-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="f1afd-106">[in] Atlanacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="f1afd-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1afd-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f1afd-107">Return Value</span></span>  
 <span data-ttu-id="f1afd-108">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="f1afd-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f1afd-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f1afd-109">HRESULT</span></span>|<span data-ttu-id="f1afd-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f1afd-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f1afd-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f1afd-111">S_OK</span></span>|`celt` <span data-ttu-id="f1afd-112">öğeler atlandı.</span><span class="sxs-lookup"><span data-stu-id="f1afd-112">elements were skipped.</span></span>|  
|<span data-ttu-id="f1afd-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="f1afd-113">S_FALSE</span></span>|<span data-ttu-id="f1afd-114">Az `celt` öğeler atlandı, daha fazla öğe olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f1afd-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1afd-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f1afd-115">Remarks</span></span>  
 <span data-ttu-id="f1afd-116">Bu Numaralandırıcının imleç yeni konumunu (geçerli) konumudur + `celt`.</span><span class="sxs-lookup"><span data-stu-id="f1afd-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1afd-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f1afd-117">Requirements</span></span>  
 <span data-ttu-id="f1afd-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1afd-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1afd-119">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f1afd-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f1afd-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1afd-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f1afd-121">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="f1afd-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f1afd-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1afd-122">See also</span></span>

- [<span data-ttu-id="f1afd-123">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f1afd-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="f1afd-124">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f1afd-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
