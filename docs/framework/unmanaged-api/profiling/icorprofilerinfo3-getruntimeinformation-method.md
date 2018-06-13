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
ms.openlocfilehash: 67e1d20f7faf38fa37083f1a5b1cc0c1060b7a32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461574"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a><span data-ttu-id="63288-102">ICorProfilerInfo3::GetRuntimeInformation Metodu</span><span class="sxs-lookup"><span data-stu-id="63288-102">ICorProfilerInfo3::GetRuntimeInformation Method</span></span>
<span data-ttu-id="63288-103">Profili oluşturuluyor ortak dil çalışma zamanı (CLR) sürüm bilgilerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="63288-103">Provides version information about the common language runtime (CLR) that is being profiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63288-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63288-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="63288-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="63288-105">Parameters</span></span>  
 `pClrInstanceId`  
 <span data-ttu-id="63288-106">[out] Bir işlemde çalışan bir CLR örneği temsilcisi kimliği.</span><span class="sxs-lookup"><span data-stu-id="63288-106">[out] The representative ID of a running CLR instance in a process.</span></span> <span data-ttu-id="63288-107">Bu aynı sonucu verir `ClrInstanceID` Windows (ETW) başlangıç olayı için olay izleme raporları.</span><span class="sxs-lookup"><span data-stu-id="63288-107">This is the same as the `ClrInstanceID` that the event tracing for Windows (ETW) startup event reports.</span></span>  
  
 `pRuntimeType`  
 <span data-ttu-id="63288-108">[out] Çalışma zamanı türü.</span><span class="sxs-lookup"><span data-stu-id="63288-108">[out] The runtime type.</span></span> <span data-ttu-id="63288-109">Bu parametre döndürür `COR_PRF_DESKTOP_CLR` Masaüstü CLR sürümü için veya `COR_PRF_CORE_CLR` Silverlight'ta kullanılan CLR çekirdek sürümü.</span><span class="sxs-lookup"><span data-stu-id="63288-109">This parameter returns `COR_PRF_DESKTOP_CLR` for the desktop version of the CLR, or `COR_PRF_CORE_CLR` for the core version of the CLR used in Silverlight.</span></span>  
  
 `pMajorVersion`  
 <span data-ttu-id="63288-110">[out] CLR ana sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="63288-110">[out] The major version number of the CLR.</span></span>  
  
 `pMinorVersion`  
 <span data-ttu-id="63288-111">[out] CLR ikincil sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="63288-111">[out] The minor version number of the CLR.</span></span>  
  
 `pBuildVersion`  
 <span data-ttu-id="63288-112">[out] CLR derleme sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="63288-112">[out] The build version number of the CLR.</span></span>  
  
 `pQFEVersion`  
 <span data-ttu-id="63288-113">[out] Bir yazılım güncelleştirmesiyle ilişkili CLR sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="63288-113">[out] The version number of the CLR that is associated with a software update.</span></span>  
  
 `cchVersionString`  
 <span data-ttu-id="63288-114">[in] Arabellek karakter cinsinden uzunluğu, `szVersionString` işaret eder.</span><span class="sxs-lookup"><span data-stu-id="63288-114">[in] The length, in characters, of the buffer that `szVersionString` points to.</span></span>  
  
 `pcchVersionString`  
 <span data-ttu-id="63288-115">[out] Karakter cinsinden uzunluğu, `szVersionString`.</span><span class="sxs-lookup"><span data-stu-id="63288-115">[out] The length, in characters, of `szVersionString`.</span></span>  
  
 `szVersionString`  
 <span data-ttu-id="63288-116">[out] CLR sürüm dizesi.</span><span class="sxs-lookup"><span data-stu-id="63288-116">[out] The CLR version string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63288-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="63288-117">Remarks</span></span>  
 <span data-ttu-id="63288-118">Her parametre için null iletebilir.</span><span class="sxs-lookup"><span data-stu-id="63288-118">You may pass null for any parameter.</span></span> <span data-ttu-id="63288-119">Ancak, `pcchVersionString` null olamaz sürece `szVersionString` de NULL'dur.</span><span class="sxs-lookup"><span data-stu-id="63288-119">However, `pcchVersionString` cannot be null unless `szVersionString` is also null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63288-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="63288-120">Requirements</span></span>  
 <span data-ttu-id="63288-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63288-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63288-122">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="63288-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="63288-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63288-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63288-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63288-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63288-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="63288-125">See Also</span></span>  
 [<span data-ttu-id="63288-126">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="63288-126">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="63288-127">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="63288-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="63288-128">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="63288-128">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
