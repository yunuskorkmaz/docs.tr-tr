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
ms.openlocfilehash: 452104939acf5de7bb151cba00d65fb6631c98d5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124091"
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="20415-102">GetVersionFromProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="20415-102">GetVersionFromProcess Function</span></span>
<span data-ttu-id="20415-103">Belirtilen işlem tanımlayıcısıyla ilişkili olan ortak dil çalışma zamanı (CLR) sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="20415-103">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="20415-104">Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="20415-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20415-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20415-105">Syntax</span></span>  
  
```  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20415-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="20415-106">Parameters</span></span>  
 `hProcess`  
 <span data-ttu-id="20415-107">[in] Bir işlem için bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="20415-107">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="20415-108">[out] Yöntemi başarıyla tamamlanmasından sonra sürüm numarası dizesi içeren bir arabelleği.</span><span class="sxs-lookup"><span data-stu-id="20415-108">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="20415-109">[in] Sürüm arabellek uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="20415-109">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="20415-110">[out] Sürüm numarası dizenin uzunluğu bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="20415-110">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20415-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="20415-111">Return Value</span></span>  
 <span data-ttu-id="20415-112">Bu yöntem standart Bileşen Nesne Modeli (COM) hata kodları, ek olarak aşağıdaki değerleri Wınerror içinde tanımlanan döndürür.</span><span class="sxs-lookup"><span data-stu-id="20415-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="20415-113">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="20415-113">Return code</span></span>|<span data-ttu-id="20415-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20415-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="20415-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="20415-115">S_OK</span></span>|<span data-ttu-id="20415-116">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="20415-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="20415-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="20415-117">E_INVALIDARG</span></span>|<span data-ttu-id="20415-118">`pVersion` NULL ve `cchBuffer` null değil veya bunun tersi de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="20415-118">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="20415-119">-veya-</span><span class="sxs-lookup"><span data-stu-id="20415-119">-or-</span></span><br /><br /> <span data-ttu-id="20415-120">`hProcess` bir işlem için geçerli bir tanıtıcı değil.</span><span class="sxs-lookup"><span data-stu-id="20415-120">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="20415-121">-veya-</span><span class="sxs-lookup"><span data-stu-id="20415-121">-or-</span></span><br /><br /> <span data-ttu-id="20415-122">CLR yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="20415-122">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="20415-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="20415-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="20415-124">`cchBuffer` null veya sürüm dizesinin uzunluğunu değerinden küçük değil.</span><span class="sxs-lookup"><span data-stu-id="20415-124">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="20415-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="20415-125">E_NOTIMPL</span></span>|<span data-ttu-id="20415-126">Bu yöntem, Microsoft Windows 95, Windows 98 Microsoft veya Microsoft Windows Millennium Edition işletim sisteminde kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="20415-126">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="20415-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="20415-127">Requirements</span></span>  
 <span data-ttu-id="20415-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20415-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20415-129">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="20415-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="20415-130">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="20415-130">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20415-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20415-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20415-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20415-132">See also</span></span>

- [<span data-ttu-id="20415-133">GetRequestedRuntimeInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="20415-133">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="20415-134">GetRequestedRuntimeVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="20415-134">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [<span data-ttu-id="20415-135">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="20415-135">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
