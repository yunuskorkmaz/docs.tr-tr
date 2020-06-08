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
ms.openlocfilehash: b8e503af11fa1d02aac2ec83edde0ffbd562d8e5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496405"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a><span data-ttu-id="220d0-102">ICorProfilerInfo3::GetRuntimeInformation Metodu</span><span class="sxs-lookup"><span data-stu-id="220d0-102">ICorProfilerInfo3::GetRuntimeInformation Method</span></span>
<span data-ttu-id="220d0-103">Profili oluşturulan ortak dil çalışma zamanı (CLR) hakkında sürüm bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="220d0-103">Provides version information about the common language runtime (CLR) that is being profiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="220d0-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="220d0-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="220d0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="220d0-105">Parameters</span></span>  
 `pClrInstanceId`  
 <span data-ttu-id="220d0-106">dışı İşlemdeki çalışan bir CLR örneğinin temsili KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="220d0-106">[out] The representative ID of a running CLR instance in a process.</span></span> <span data-ttu-id="220d0-107">Bu, `ClrInstanceID` Windows için olay izleme (ETW) başlatma olay raporlarıdır.</span><span class="sxs-lookup"><span data-stu-id="220d0-107">This is the same as the `ClrInstanceID` that the event tracing for Windows (ETW) startup event reports.</span></span>  
  
 `pRuntimeType`  
 <span data-ttu-id="220d0-108">dışı Çalışma zamanı türü.</span><span class="sxs-lookup"><span data-stu-id="220d0-108">[out] The runtime type.</span></span> <span data-ttu-id="220d0-109">Bu parametre `COR_PRF_DESKTOP_CLR` , clr 'nin masaüstü sürümü veya `COR_PRF_CORE_CLR` Silverlight 'DA kullanılan CLR 'nin çekirdek sürümü için döndürür.</span><span class="sxs-lookup"><span data-stu-id="220d0-109">This parameter returns `COR_PRF_DESKTOP_CLR` for the desktop version of the CLR, or `COR_PRF_CORE_CLR` for the core version of the CLR used in Silverlight.</span></span>  
  
 `pMajorVersion`  
 <span data-ttu-id="220d0-110">dışı CLR 'nin ana sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="220d0-110">[out] The major version number of the CLR.</span></span>  
  
 `pMinorVersion`  
 <span data-ttu-id="220d0-111">dışı CLR 'nin ikincil sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="220d0-111">[out] The minor version number of the CLR.</span></span>  
  
 `pBuildVersion`  
 <span data-ttu-id="220d0-112">dışı CLR 'nin derleme sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="220d0-112">[out] The build version number of the CLR.</span></span>  
  
 `pQFEVersion`  
 <span data-ttu-id="220d0-113">dışı Bir yazılım güncelleştirmesiyle ilişkilendirilen CLR 'nin sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="220d0-113">[out] The version number of the CLR that is associated with a software update.</span></span>  
  
 `cchVersionString`  
 <span data-ttu-id="220d0-114">'ndaki ' I işaret eden arabelleğin karakter cinsinden uzunluğu `szVersionString` .</span><span class="sxs-lookup"><span data-stu-id="220d0-114">[in] The length, in characters, of the buffer that `szVersionString` points to.</span></span>  
  
 `pcchVersionString`  
 <span data-ttu-id="220d0-115">dışı Karakter cinsinden uzunluğu `szVersionString` .</span><span class="sxs-lookup"><span data-stu-id="220d0-115">[out] The length, in characters, of `szVersionString`.</span></span>  
  
 `szVersionString`  
 <span data-ttu-id="220d0-116">dışı CLR sürüm dizesi.</span><span class="sxs-lookup"><span data-stu-id="220d0-116">[out] The CLR version string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="220d0-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="220d0-117">Remarks</span></span>  
 <span data-ttu-id="220d0-118">Herhangi bir parametre için null değeri geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="220d0-118">You may pass null for any parameter.</span></span> <span data-ttu-id="220d0-119">Ancak `pcchVersionString` aynı zamanda null olmadığı için null olamaz `szVersionString` .</span><span class="sxs-lookup"><span data-stu-id="220d0-119">However, `pcchVersionString` cannot be null unless `szVersionString` is also null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="220d0-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="220d0-120">Requirements</span></span>  
 <span data-ttu-id="220d0-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="220d0-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="220d0-122">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="220d0-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="220d0-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="220d0-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="220d0-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="220d0-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="220d0-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="220d0-125">See also</span></span>

- [<span data-ttu-id="220d0-126">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="220d0-126">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="220d0-127">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="220d0-127">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="220d0-128">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="220d0-128">Profiling</span></span>](index.md)
