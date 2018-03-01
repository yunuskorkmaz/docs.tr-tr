---
title: "GetRequestedRuntimeVersion İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersion
helpviewer_keywords:
- GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 13309a7362f468d3711176db2adc7a82e3b949d3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="08675-102">GetRequestedRuntimeVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="08675-102">GetRequestedRuntimeVersion Function</span></span>
<span data-ttu-id="08675-103">Belirtilen uygulama tarafından istenen ortak dil çalışma zamanı (CLR) sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="08675-103">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="08675-104">Bu sürümü yüklü değilse, önce istenen sürümü yüklü en son sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="08675-104">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="08675-105">Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="08675-105">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08675-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08675-106">Syntax</span></span>  
  
```  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *pdwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="08675-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="08675-107">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="08675-108">[in] Uygulamanın adı.</span><span class="sxs-lookup"><span data-stu-id="08675-108">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="08675-109">[out] Başarıyla tamamlandıktan sonra sürüm numarası dizesi içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="08675-109">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="08675-110">[in] Sürüm arabellek uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="08675-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="08675-111">[out] Sürüm numarası dize uzunluğu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="08675-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08675-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="08675-112">Return Value</span></span>  
 <span data-ttu-id="08675-113">Bu yöntem standart Bileşen Nesne Modeli (COM) hata kodları, ek olarak aşağıdaki değerleri Winerror.h'de içinde tanımlandığı şekilde döndürür.</span><span class="sxs-lookup"><span data-stu-id="08675-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="08675-114">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="08675-114">Return code</span></span>|<span data-ttu-id="08675-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08675-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="08675-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="08675-116">S_OK</span></span>|<span data-ttu-id="08675-117">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="08675-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="08675-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="08675-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="08675-119">Sürüm arabellek sürüm dizesi depolamak için yeterli büyüklükte değil.</span><span class="sxs-lookup"><span data-stu-id="08675-119">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="08675-120">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="08675-120">E_POINTER</span></span>|<span data-ttu-id="08675-121">`pdwLength`null şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="08675-121">`pdwLength` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="08675-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08675-122">Requirements</span></span>  
 <span data-ttu-id="08675-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08675-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08675-124">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="08675-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="08675-125">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="08675-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08675-126">**.NET framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08675-126">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08675-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="08675-127">See Also</span></span>  
 [<span data-ttu-id="08675-128">GetRequestedRuntimeInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="08675-128">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 [<span data-ttu-id="08675-129">GetVersionFromProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="08675-129">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 [<span data-ttu-id="08675-130">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="08675-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
