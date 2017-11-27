---
title: "GetVersionFromProcess İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetVersionFromProcess
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: GetVersionFromProcess
helpviewer_keywords: GetVersionFromProcess function [.NET Framework hosting]
ms.assetid: a9f7f824-64a1-408d-8607-91c7f19d21fe
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3c73d12731a5c72b8c0e724f74ee0aa9ebddeee9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="1c393-102">GetVersionFromProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="1c393-102">GetVersionFromProcess Function</span></span>
<span data-ttu-id="1c393-103">Belirtilen işlem tanıtıcı ile ilişkili ortak dil çalışma zamanı (CLR) sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="1c393-103">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="1c393-104">Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1c393-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c393-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1c393-105">Syntax</span></span>  
  
```  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *dwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1c393-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1c393-106">Parameters</span></span>  
 `hProcess`  
 <span data-ttu-id="1c393-107">[in] Bir işlem için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="1c393-107">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="1c393-108">[out] Yöntem başarılı tamamlanmasından sonra sürüm numarası dizesi içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="1c393-108">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="1c393-109">[in] Sürüm arabellek uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="1c393-109">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="1c393-110">[out] Sürüm numarası dize uzunluğu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1c393-110">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1c393-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1c393-111">Return Value</span></span>  
 <span data-ttu-id="1c393-112">Bu yöntem standart Bileşen Nesne Modeli (COM) hata kodları, ek olarak aşağıdaki değerleri Winerror.h'de içinde tanımlandığı şekilde döndürür.</span><span class="sxs-lookup"><span data-stu-id="1c393-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="1c393-113">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="1c393-113">Return code</span></span>|<span data-ttu-id="1c393-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c393-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="1c393-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="1c393-115">S_OK</span></span>|<span data-ttu-id="1c393-116">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="1c393-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="1c393-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="1c393-117">E_INVALIDARG</span></span>|<span data-ttu-id="1c393-118">`pVersion`NULL ve `cchBuffer` null değil veya tam tersi.</span><span class="sxs-lookup"><span data-stu-id="1c393-118">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="1c393-119">veya</span><span class="sxs-lookup"><span data-stu-id="1c393-119">-or-</span></span><br /><br /> <span data-ttu-id="1c393-120">`hProcess`bir işlem için geçerli bir tanıtıcı değil.</span><span class="sxs-lookup"><span data-stu-id="1c393-120">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="1c393-121">veya</span><span class="sxs-lookup"><span data-stu-id="1c393-121">-or-</span></span><br /><br /> <span data-ttu-id="1c393-122">CLR yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="1c393-122">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="1c393-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="1c393-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="1c393-124">`cchBuffer`null veya sürüm dizesi uzunluğundan daha az olabilir.</span><span class="sxs-lookup"><span data-stu-id="1c393-124">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="1c393-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="1c393-125">E_NOTIMPL</span></span>|<span data-ttu-id="1c393-126">Bu yöntem Microsoft Windows 95, Microsoft Windows 98 veya Microsoft Windows Millennium Edition işletim sisteminde kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="1c393-126">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1c393-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1c393-127">Requirements</span></span>  
 <span data-ttu-id="1c393-128">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c393-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c393-129">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1c393-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1c393-130">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1c393-130">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1c393-131">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c393-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c393-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1c393-132">See Also</span></span>  
 [<span data-ttu-id="1c393-133">Getrequestedruntimeınfo işlevi</span><span class="sxs-lookup"><span data-stu-id="1c393-133">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 [<span data-ttu-id="1c393-134">GetRequestedRuntimeVersion işlevi</span><span class="sxs-lookup"><span data-stu-id="1c393-134">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 [<span data-ttu-id="1c393-135">Kullanım dışı CLR barındırma işlevleri</span><span class="sxs-lookup"><span data-stu-id="1c393-135">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
