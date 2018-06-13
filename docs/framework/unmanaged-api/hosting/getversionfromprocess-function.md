---
title: GetVersionFromProcess İşlevi
ms.date: 03/30/2017
api_name:
- GetVersionFromProcess
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetVersionFromProcess
helpviewer_keywords:
- GetVersionFromProcess function [.NET Framework hosting]
ms.assetid: a9f7f824-64a1-408d-8607-91c7f19d21fe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b57d04a8a49371872c679a331b5ae9c45dce797
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433079"
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="a9ef4-102">GetVersionFromProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="a9ef4-102">GetVersionFromProcess Function</span></span>
<span data-ttu-id="a9ef4-103">Belirtilen işlem tanıtıcı ile ilişkili ortak dil çalışma zamanı (CLR) sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="a9ef4-103">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="a9ef4-104">Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9ef4-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9ef4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a9ef4-105">Syntax</span></span>  
  
```  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *dwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a9ef4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a9ef4-106">Parameters</span></span>  
 `hProcess`  
 <span data-ttu-id="a9ef4-107">[in] Bir işlem için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="a9ef4-107">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="a9ef4-108">[out] Yöntem başarılı tamamlanmasından sonra sürüm numarası dizesi içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="a9ef4-108">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="a9ef4-109">[in] Sürüm arabellek uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="a9ef4-109">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="a9ef4-110">[out] Sürüm numarası dize uzunluğu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a9ef4-110">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9ef4-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a9ef4-111">Return Value</span></span>  
 <span data-ttu-id="a9ef4-112">Bu yöntem standart Bileşen Nesne Modeli (COM) hata kodları, ek olarak aşağıdaki değerleri Winerror.h'de içinde tanımlandığı şekilde döndürür.</span><span class="sxs-lookup"><span data-stu-id="a9ef4-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="a9ef4-113">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="a9ef4-113">Return code</span></span>|<span data-ttu-id="a9ef4-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9ef4-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="a9ef4-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="a9ef4-115">S_OK</span></span>|<span data-ttu-id="a9ef4-116">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="a9ef4-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="a9ef4-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a9ef4-117">E_INVALIDARG</span></span>|<span data-ttu-id="a9ef4-118">`pVersion` NULL ve `cchBuffer` null değil veya tam tersi.</span><span class="sxs-lookup"><span data-stu-id="a9ef4-118">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="a9ef4-119">-veya-</span><span class="sxs-lookup"><span data-stu-id="a9ef4-119">-or-</span></span><br /><br /> <span data-ttu-id="a9ef4-120">`hProcess` bir işlem için geçerli bir tanıtıcı değil.</span><span class="sxs-lookup"><span data-stu-id="a9ef4-120">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="a9ef4-121">-veya-</span><span class="sxs-lookup"><span data-stu-id="a9ef4-121">-or-</span></span><br /><br /> <span data-ttu-id="a9ef4-122">CLR yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="a9ef4-122">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="a9ef4-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="a9ef4-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="a9ef4-124">`cchBuffer` null veya sürüm dizesi uzunluğundan daha az olabilir.</span><span class="sxs-lookup"><span data-stu-id="a9ef4-124">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="a9ef4-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="a9ef4-125">E_NOTIMPL</span></span>|<span data-ttu-id="a9ef4-126">Bu yöntem Microsoft Windows 95, Microsoft Windows 98 veya Microsoft Windows Millennium Edition işletim sisteminde kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="a9ef4-126">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a9ef4-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a9ef4-127">Requirements</span></span>  
 <span data-ttu-id="a9ef4-128">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9ef4-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9ef4-129">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a9ef4-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a9ef4-130">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a9ef4-130">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a9ef4-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9ef4-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9ef4-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a9ef4-132">See Also</span></span>  
 [<span data-ttu-id="a9ef4-133">GetRequestedRuntimeInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="a9ef4-133">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 [<span data-ttu-id="a9ef4-134">GetRequestedRuntimeVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="a9ef4-134">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 [<span data-ttu-id="a9ef4-135">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="a9ef4-135">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
