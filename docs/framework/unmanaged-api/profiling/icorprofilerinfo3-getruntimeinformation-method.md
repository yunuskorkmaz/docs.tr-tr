---
description: 'Hakkında daha fazla bilgi edinin: ICorProfilerInfo3:: GetRuntimeInformation yöntemi'
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
ms.openlocfilehash: f615cc54e12b6f2f6eaa7335353f2f5f6a8ecfce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646718"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a><span data-ttu-id="eb4c5-103">ICorProfilerInfo3::GetRuntimeInformation Metodu</span><span class="sxs-lookup"><span data-stu-id="eb4c5-103">ICorProfilerInfo3::GetRuntimeInformation Method</span></span>

<span data-ttu-id="eb4c5-104">Profili oluşturulan ortak dil çalışma zamanı (CLR) hakkında sürüm bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb4c5-104">Provides version information about the common language runtime (CLR) that is being profiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb4c5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eb4c5-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="eb4c5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eb4c5-106">Parameters</span></span>  

 `pClrInstanceId`  
 <span data-ttu-id="eb4c5-107">dışı İşlemdeki çalışan bir CLR örneğinin temsili KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="eb4c5-107">[out] The representative ID of a running CLR instance in a process.</span></span> <span data-ttu-id="eb4c5-108">Bu, `ClrInstanceID` Windows için olay izleme (ETW) başlatma olay raporlarıdır.</span><span class="sxs-lookup"><span data-stu-id="eb4c5-108">This is the same as the `ClrInstanceID` that the event tracing for Windows (ETW) startup event reports.</span></span>  
  
 `pRuntimeType`  
 <span data-ttu-id="eb4c5-109">dışı Çalışma zamanı türü.</span><span class="sxs-lookup"><span data-stu-id="eb4c5-109">[out] The runtime type.</span></span> <span data-ttu-id="eb4c5-110">Bu parametre `COR_PRF_DESKTOP_CLR` , clr 'nin masaüstü sürümü veya `COR_PRF_CORE_CLR` Silverlight 'DA kullanılan CLR 'nin çekirdek sürümü için döndürür.</span><span class="sxs-lookup"><span data-stu-id="eb4c5-110">This parameter returns `COR_PRF_DESKTOP_CLR` for the desktop version of the CLR, or `COR_PRF_CORE_CLR` for the core version of the CLR used in Silverlight.</span></span>  
  
 `pMajorVersion`  
 <span data-ttu-id="eb4c5-111">dışı CLR 'nin ana sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="eb4c5-111">[out] The major version number of the CLR.</span></span>  
  
 `pMinorVersion`  
 <span data-ttu-id="eb4c5-112">dışı CLR 'nin ikincil sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="eb4c5-112">[out] The minor version number of the CLR.</span></span>  
  
 `pBuildVersion`  
 <span data-ttu-id="eb4c5-113">dışı CLR 'nin derleme sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="eb4c5-113">[out] The build version number of the CLR.</span></span>  
  
 `pQFEVersion`  
 <span data-ttu-id="eb4c5-114">dışı Bir yazılım güncelleştirmesiyle ilişkilendirilen CLR 'nin sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="eb4c5-114">[out] The version number of the CLR that is associated with a software update.</span></span>  
  
 `cchVersionString`  
 <span data-ttu-id="eb4c5-115">'ndaki ' I işaret eden arabelleğin karakter cinsinden uzunluğu `szVersionString` .</span><span class="sxs-lookup"><span data-stu-id="eb4c5-115">[in] The length, in characters, of the buffer that `szVersionString` points to.</span></span>  
  
 `pcchVersionString`  
 <span data-ttu-id="eb4c5-116">dışı Karakter cinsinden uzunluğu `szVersionString` .</span><span class="sxs-lookup"><span data-stu-id="eb4c5-116">[out] The length, in characters, of `szVersionString`.</span></span>  
  
 `szVersionString`  
 <span data-ttu-id="eb4c5-117">dışı CLR sürüm dizesi.</span><span class="sxs-lookup"><span data-stu-id="eb4c5-117">[out] The CLR version string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb4c5-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eb4c5-118">Remarks</span></span>  

 <span data-ttu-id="eb4c5-119">Herhangi bir parametre için null değeri geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb4c5-119">You may pass null for any parameter.</span></span> <span data-ttu-id="eb4c5-120">Ancak `pcchVersionString` aynı zamanda null olmadığı için null olamaz `szVersionString` .</span><span class="sxs-lookup"><span data-stu-id="eb4c5-120">However, `pcchVersionString` cannot be null unless `szVersionString` is also null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb4c5-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eb4c5-121">Requirements</span></span>  

 <span data-ttu-id="eb4c5-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb4c5-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb4c5-123">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="eb4c5-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eb4c5-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="eb4c5-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb4c5-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb4c5-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb4c5-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb4c5-126">See also</span></span>

- [<span data-ttu-id="eb4c5-127">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eb4c5-127">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="eb4c5-128">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="eb4c5-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="eb4c5-129">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="eb4c5-129">Profiling</span></span>](index.md)
