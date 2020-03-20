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
ms.openlocfilehash: a04a0c5e6865c3664d2cb5fb341c3625e35d4d7c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178123"
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="c6b93-102">GetVersionFromProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="c6b93-102">GetVersionFromProcess Function</span></span>
<span data-ttu-id="c6b93-103">Belirtilen işlem tanıtıcısıyla ilişkili ortak dil çalışma zamanının (CLR) sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="c6b93-103">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="c6b93-104">Bu işlev .NET Framework 4'te amortismana hazırlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c6b93-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6b93-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6b93-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6b93-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c6b93-106">Parameters</span></span>  
 `hProcess`  
 <span data-ttu-id="c6b93-107">[içinde] Bir işlemin sapı.</span><span class="sxs-lookup"><span data-stu-id="c6b93-107">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="c6b93-108">[çıkış] Yöntemin başarıyla tamamlanmasından sonra sürüm numarası dizesini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="c6b93-108">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="c6b93-109">[içinde] Sürüm arabelleği uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="c6b93-109">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="c6b93-110">[çıkış] Sürüm numarası dizesinin uzunluğuna işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c6b93-110">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6b93-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c6b93-111">Return Value</span></span>  
 <span data-ttu-id="c6b93-112">Bu yöntem, aşağıdaki değerlere ek olarak WinError.h'de tanımlandığı şekilde standart Bileşen Nesne Modeli (COM) hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="c6b93-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="c6b93-113">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="c6b93-113">Return code</span></span>|<span data-ttu-id="c6b93-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6b93-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="c6b93-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="c6b93-115">S_OK</span></span>|<span data-ttu-id="c6b93-116">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="c6b93-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="c6b93-117">E_ınvalıdarg</span><span class="sxs-lookup"><span data-stu-id="c6b93-117">E_INVALIDARG</span></span>|<span data-ttu-id="c6b93-118">`pVersion`null ve `cchBuffer` null değildir, ya da tersi.</span><span class="sxs-lookup"><span data-stu-id="c6b93-118">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="c6b93-119">-veya-</span><span class="sxs-lookup"><span data-stu-id="c6b93-119">-or-</span></span><br /><br /> <span data-ttu-id="c6b93-120">`hProcess`bir işlem için geçerli bir tutamaç değildir.</span><span class="sxs-lookup"><span data-stu-id="c6b93-120">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="c6b93-121">-veya-</span><span class="sxs-lookup"><span data-stu-id="c6b93-121">-or-</span></span><br /><br /> <span data-ttu-id="c6b93-122">CLR dolu değil.</span><span class="sxs-lookup"><span data-stu-id="c6b93-122">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="c6b93-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="c6b93-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="c6b93-124">`cchBuffer`null veya sürüm dize uzunluğu daha azdır.</span><span class="sxs-lookup"><span data-stu-id="c6b93-124">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="c6b93-125">E_notımpl</span><span class="sxs-lookup"><span data-stu-id="c6b93-125">E_NOTIMPL</span></span>|<span data-ttu-id="c6b93-126">Bu yöntem Microsoft Windows 95, Microsoft Windows 98 veya Microsoft Windows Millennium Edition işletim sisteminde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c6b93-126">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c6b93-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c6b93-127">Requirements</span></span>  
 <span data-ttu-id="c6b93-128">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6b93-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6b93-129">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c6b93-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c6b93-130">**Kütüphane:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="c6b93-130">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c6b93-131">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6b93-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6b93-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6b93-132">See also</span></span>

- [<span data-ttu-id="c6b93-133">GetRequestedRuntimeInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="c6b93-133">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="c6b93-134">GetRequestedRuntimeVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="c6b93-134">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [<span data-ttu-id="c6b93-135">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="c6b93-135">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
