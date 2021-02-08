---
description: ': GetVersionFromProcess Işlevi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: ab665d2984f79baf049009690b36782528094937
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785256"
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="44f6c-103">GetVersionFromProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="44f6c-103">GetVersionFromProcess Function</span></span>

<span data-ttu-id="44f6c-104">Belirtilen işlem tanıtıcısıyla ilişkili ortak dil çalışma zamanının (CLR) sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="44f6c-104">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="44f6c-105">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="44f6c-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44f6c-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="44f6c-106">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44f6c-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="44f6c-107">Parameters</span></span>  

 `hProcess`  
 <span data-ttu-id="44f6c-108">'ndaki Bir işleme yönelik bir tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="44f6c-108">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="44f6c-109">dışı Yöntemi başarıyla tamamlandıktan sonra sürüm numarası dizesini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="44f6c-109">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="44f6c-110">'ndaki Sürüm arabelleğinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="44f6c-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="44f6c-111">dışı Sürüm numarası dizesinin uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="44f6c-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44f6c-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="44f6c-112">Return Value</span></span>  

 <span data-ttu-id="44f6c-113">Bu yöntem, aşağıdaki değerlere ek olarak, WinError. h içinde tanımlanan standart bileşen nesne modeli (COM) hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="44f6c-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="44f6c-114">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="44f6c-114">Return code</span></span>|<span data-ttu-id="44f6c-115">Description</span><span class="sxs-lookup"><span data-stu-id="44f6c-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="44f6c-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="44f6c-116">S_OK</span></span>|<span data-ttu-id="44f6c-117">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="44f6c-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="44f6c-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="44f6c-118">E_INVALIDARG</span></span>|<span data-ttu-id="44f6c-119">`pVersion` null ve `cchBuffer` null ya da tam tersi.</span><span class="sxs-lookup"><span data-stu-id="44f6c-119">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="44f6c-120">-veya-</span><span class="sxs-lookup"><span data-stu-id="44f6c-120">-or-</span></span><br /><br /> <span data-ttu-id="44f6c-121">`hProcess` bir işleme geçerli bir tanıtıcı değil.</span><span class="sxs-lookup"><span data-stu-id="44f6c-121">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="44f6c-122">-veya-</span><span class="sxs-lookup"><span data-stu-id="44f6c-122">-or-</span></span><br /><br /> <span data-ttu-id="44f6c-123">CLR yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="44f6c-123">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="44f6c-124">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="44f6c-124">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="44f6c-125">`cchBuffer` null veya sürüm dizesinin uzunluğundan daha küçük.</span><span class="sxs-lookup"><span data-stu-id="44f6c-125">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="44f6c-126">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="44f6c-126">E_NOTIMPL</span></span>|<span data-ttu-id="44f6c-127">Bu yöntem Microsoft Windows 95, Microsoft Windows 98 veya Microsoft Windows Millennium Edition işletim sisteminde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="44f6c-127">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="44f6c-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="44f6c-128">Requirements</span></span>  

 <span data-ttu-id="44f6c-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44f6c-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44f6c-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="44f6c-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="44f6c-131">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="44f6c-131">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44f6c-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44f6c-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44f6c-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44f6c-133">See also</span></span>

- [<span data-ttu-id="44f6c-134">GetRequestedRuntimeInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="44f6c-134">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="44f6c-135">GetRequestedRuntimeVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="44f6c-135">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)
- [<span data-ttu-id="44f6c-136">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="44f6c-136">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
