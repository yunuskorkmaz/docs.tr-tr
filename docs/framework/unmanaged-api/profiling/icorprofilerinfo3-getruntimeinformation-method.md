---
title: ICorProfilerInfo3::GetRuntimeInformation Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetRuntimeInformation Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetRuntimeInformation
helpviewer_keywords:
- GetRuntimeInformation method [.NET Framework profiling]
- ICorProfilerInfo3::GetRuntimeInformation method [.NET Framework profiling]
ms.assetid: 4400fb8c-0407-4791-8557-f011fd2aee51
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a13e3e525c7f019e7dc49111b88ac374345830af
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164937"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a><span data-ttu-id="6a236-102">ICorProfilerInfo3::GetRuntimeInformation Metodu</span><span class="sxs-lookup"><span data-stu-id="6a236-102">ICorProfilerInfo3::GetRuntimeInformation Method</span></span>
<span data-ttu-id="6a236-103">Profili oluşturulan ortak dil çalışma zamanı (CLR) sürüm bilgilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6a236-103">Provides version information about the common language runtime (CLR) that is being profiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a236-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a236-104">Syntax</span></span>  
  
```  
HRESULT GetRuntimeInformation(  
       [out] USHORT *pClrInstanceId,  
       [out] COR_PRF_RUNTIME_TYPE *pRuntimeType,  
       [out] USHORT *pMajorVersion,  
       [out] USHORT *pMinorVersion,  
       [out] USHORT *pBuildNumber,  
       [out] USHORT *pQFEVersion,  
       [in]  ULONG  cchVersionString,  
       [out] ULONG  *pcchVersionString,  
       [out, size_is(cchVersionString), length_is(*pcchVersionString)]  
                   WCHAR  szVersionString[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a236-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6a236-105">Parameters</span></span>  
 `pClrInstanceId`  
 <span data-ttu-id="6a236-106">[out] Bir işlemde çalışan bir CLR örneği temsilcisi kimliği.</span><span class="sxs-lookup"><span data-stu-id="6a236-106">[out] The representative ID of a running CLR instance in a process.</span></span> <span data-ttu-id="6a236-107">Bu, aynı `ClrInstanceID` Windows (ETW) başlangıç olayı için olay izleme olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="6a236-107">This is the same as the `ClrInstanceID` that the event tracing for Windows (ETW) startup event reports.</span></span>  
  
 `pRuntimeType`  
 <span data-ttu-id="6a236-108">[out] Çalışma zamanı türü.</span><span class="sxs-lookup"><span data-stu-id="6a236-108">[out] The runtime type.</span></span> <span data-ttu-id="6a236-109">Bu parametre döndürür `COR_PRF_DESKTOP_CLR` Masaüstü CLR sürümü için veya `COR_PRF_CORE_CLR` çekirdek Silverlight'ta kullanılan CLR sürümü için.</span><span class="sxs-lookup"><span data-stu-id="6a236-109">This parameter returns `COR_PRF_DESKTOP_CLR` for the desktop version of the CLR, or `COR_PRF_CORE_CLR` for the core version of the CLR used in Silverlight.</span></span>  
  
 `pMajorVersion`  
 <span data-ttu-id="6a236-110">[out] CLR sürüm sayısı.</span><span class="sxs-lookup"><span data-stu-id="6a236-110">[out] The major version number of the CLR.</span></span>  
  
 `pMinorVersion`  
 <span data-ttu-id="6a236-111">[out] İkincil sürüm numarası CLR.</span><span class="sxs-lookup"><span data-stu-id="6a236-111">[out] The minor version number of the CLR.</span></span>  
  
 `pBuildVersion`  
 <span data-ttu-id="6a236-112">[out] Derleme sürüm numarası CLR.</span><span class="sxs-lookup"><span data-stu-id="6a236-112">[out] The build version number of the CLR.</span></span>  
  
 `pQFEVersion`  
 <span data-ttu-id="6a236-113">[out] Bir yazılım güncelleştirmesiyle ilişkili CLR sürüm sayısı.</span><span class="sxs-lookup"><span data-stu-id="6a236-113">[out] The version number of the CLR that is associated with a software update.</span></span>  
  
 `cchVersionString`  
 <span data-ttu-id="6a236-114">[in] Arabelleğin karakter cinsinden uzunluğu, `szVersionString` işaret eder.</span><span class="sxs-lookup"><span data-stu-id="6a236-114">[in] The length, in characters, of the buffer that `szVersionString` points to.</span></span>  
  
 `pcchVersionString`  
 <span data-ttu-id="6a236-115">[out] Karakter cinsinden uzunluğu, `szVersionString`.</span><span class="sxs-lookup"><span data-stu-id="6a236-115">[out] The length, in characters, of `szVersionString`.</span></span>  
  
 `szVersionString`  
 <span data-ttu-id="6a236-116">[out] CLR sürüm dizesi.</span><span class="sxs-lookup"><span data-stu-id="6a236-116">[out] The CLR version string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a236-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a236-117">Remarks</span></span>  
 <span data-ttu-id="6a236-118">Her parametre için null değeri geçirmeye.</span><span class="sxs-lookup"><span data-stu-id="6a236-118">You may pass null for any parameter.</span></span> <span data-ttu-id="6a236-119">Ancak, `pcchVersionString` null olamaz sürece `szVersionString` de null.</span><span class="sxs-lookup"><span data-stu-id="6a236-119">However, `pcchVersionString` cannot be null unless `szVersionString` is also null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a236-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a236-120">Requirements</span></span>  
 <span data-ttu-id="6a236-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a236-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a236-122">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6a236-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6a236-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a236-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a236-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a236-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a236-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a236-125">See also</span></span>

- [<span data-ttu-id="6a236-126">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a236-126">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="6a236-127">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6a236-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="6a236-128">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6a236-128">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
