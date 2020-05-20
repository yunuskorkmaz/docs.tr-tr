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
ms.openlocfilehash: fbaf45da0902ded8a2f7bf0d470aaed3b5f531aa
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617132"
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="d5035-102">GetVersionFromProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="d5035-102">GetVersionFromProcess Function</span></span>
<span data-ttu-id="d5035-103">Belirtilen işlem tanıtıcısıyla ilişkili ortak dil çalışma zamanının (CLR) sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="d5035-103">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="d5035-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="d5035-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5035-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d5035-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5035-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d5035-106">Parameters</span></span>  
 `hProcess`  
 <span data-ttu-id="d5035-107">'ndaki Bir işleme yönelik bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="d5035-107">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="d5035-108">dışı Yöntemi başarıyla tamamlandıktan sonra sürüm numarası dizesini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="d5035-108">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="d5035-109">'ndaki Sürüm arabelleğinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="d5035-109">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="d5035-110">dışı Sürüm numarası dizesinin uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d5035-110">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5035-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d5035-111">Return Value</span></span>  
 <span data-ttu-id="d5035-112">Bu yöntem, aşağıdaki değerlere ek olarak, WinError. h içinde tanımlanan standart bileşen nesne modeli (COM) hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="d5035-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="d5035-113">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="d5035-113">Return code</span></span>|<span data-ttu-id="d5035-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d5035-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="d5035-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="d5035-115">S_OK</span></span>|<span data-ttu-id="d5035-116">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="d5035-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="d5035-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d5035-117">E_INVALIDARG</span></span>|<span data-ttu-id="d5035-118">`pVersion`null ve `cchBuffer` null ya da tam tersi.</span><span class="sxs-lookup"><span data-stu-id="d5035-118">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="d5035-119">-veya-</span><span class="sxs-lookup"><span data-stu-id="d5035-119">-or-</span></span><br /><br /> <span data-ttu-id="d5035-120">`hProcess`bir işleme geçerli bir tanıtıcı değil.</span><span class="sxs-lookup"><span data-stu-id="d5035-120">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="d5035-121">-veya-</span><span class="sxs-lookup"><span data-stu-id="d5035-121">-or-</span></span><br /><br /> <span data-ttu-id="d5035-122">CLR yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="d5035-122">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="d5035-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="d5035-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="d5035-124">`cchBuffer`null veya sürüm dizesinin uzunluğundan daha küçük.</span><span class="sxs-lookup"><span data-stu-id="d5035-124">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="d5035-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="d5035-125">E_NOTIMPL</span></span>|<span data-ttu-id="d5035-126">Bu yöntem Microsoft Windows 95, Microsoft Windows 98 veya Microsoft Windows Millennium Edition işletim sisteminde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d5035-126">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d5035-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5035-127">Requirements</span></span>  
 <span data-ttu-id="d5035-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5035-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5035-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d5035-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d5035-130">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d5035-130">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5035-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5035-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5035-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5035-132">See also</span></span>

- [<span data-ttu-id="d5035-133">GetRequestedRuntimeInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="d5035-133">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="d5035-134">GetRequestedRuntimeVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="d5035-134">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)
- [<span data-ttu-id="d5035-135">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d5035-135">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
