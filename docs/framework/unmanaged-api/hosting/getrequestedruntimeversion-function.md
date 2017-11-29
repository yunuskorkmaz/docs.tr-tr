---
title: "GetRequestedRuntimeVersion İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: GetRequestedRuntimeVersion
helpviewer_keywords: GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bfac4e32841b8a8332a1f4124c1326f1ef7da1f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="9be9c-102">GetRequestedRuntimeVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="9be9c-102">GetRequestedRuntimeVersion Function</span></span>
<span data-ttu-id="9be9c-103">Belirtilen uygulama tarafından istenen ortak dil çalışma zamanı (CLR) sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="9be9c-103">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="9be9c-104">Bu sürümü yüklü değilse, önce istenen sürümü yüklü en son sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="9be9c-104">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="9be9c-105">Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9be9c-105">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9be9c-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9be9c-106">Syntax</span></span>  
  
```  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *pdwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9be9c-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9be9c-107">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="9be9c-108">[in] Uygulamanın adı.</span><span class="sxs-lookup"><span data-stu-id="9be9c-108">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="9be9c-109">[out] Başarıyla tamamlandıktan sonra sürüm numarası dizesi içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="9be9c-109">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="9be9c-110">[in] Sürüm arabellek uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="9be9c-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="9be9c-111">[out] Sürüm numarası dize uzunluğu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9be9c-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9be9c-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9be9c-112">Return Value</span></span>  
 <span data-ttu-id="9be9c-113">Bu yöntem standart Bileşen Nesne Modeli (COM) hata kodları, ek olarak aşağıdaki değerleri Winerror.h'de içinde tanımlandığı şekilde döndürür.</span><span class="sxs-lookup"><span data-stu-id="9be9c-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="9be9c-114">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="9be9c-114">Return code</span></span>|<span data-ttu-id="9be9c-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9be9c-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="9be9c-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="9be9c-116">S_OK</span></span>|<span data-ttu-id="9be9c-117">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="9be9c-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="9be9c-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="9be9c-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="9be9c-119">Sürüm arabellek sürüm dizesi depolamak için yeterli büyüklükte değil.</span><span class="sxs-lookup"><span data-stu-id="9be9c-119">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="9be9c-120">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="9be9c-120">E_POINTER</span></span>|<span data-ttu-id="9be9c-121">`pdwLength`null şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="9be9c-121">`pdwLength` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9be9c-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9be9c-122">Requirements</span></span>  
 <span data-ttu-id="9be9c-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9be9c-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9be9c-124">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9be9c-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9be9c-125">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9be9c-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9be9c-126">**.NET framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9be9c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9be9c-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9be9c-127">See Also</span></span>  
 [<span data-ttu-id="9be9c-128">Getrequestedruntimeınfo işlevi</span><span class="sxs-lookup"><span data-stu-id="9be9c-128">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 [<span data-ttu-id="9be9c-129">GetVersionFromProcess işlevi</span><span class="sxs-lookup"><span data-stu-id="9be9c-129">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 [<span data-ttu-id="9be9c-130">Kullanım dışı CLR barındırma işlevleri</span><span class="sxs-lookup"><span data-stu-id="9be9c-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
