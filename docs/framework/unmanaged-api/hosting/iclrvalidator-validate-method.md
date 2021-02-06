---
description: ': ICLRValidator:: Validate yöntemi hakkında daha fazla bilgi edinin'
title: ICLRValidator::Validate Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::Validate
helpviewer_keywords:
- Validate method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::Validate method [.NET Framework hosting]
ms.assetid: 0b1b432a-d234-4002-839b-81366c3a8bdc
topic_type:
- apiref
ms.openlocfilehash: a188315d44021fc8bf40be9bb9aecac436351467
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636751"
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="ecdc6-103">ICLRValidator::Validate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ecdc6-103">ICLRValidator::Validate Method</span></span>

<span data-ttu-id="ecdc6-104">Belirtilen dosyadaki taşınabilir yürütülebilir (PE) veya Microsoft ara dili 'ni (MSIL) doğrular.</span><span class="sxs-lookup"><span data-stu-id="ecdc6-104">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecdc6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ecdc6-105">Syntax</span></span>  
  
```cpp  
HRESULT Validate (  
    [in] IVEHandler        *veh,  
    [in] unsigned long      ulAppDomainId,  
    [in] unsigned long      ulFlags,  
    [in] unsigned long      ulMaxError,  
    [in] unsigned long      token,  
    [in] LPWSTR             fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long      ulSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="ecdc6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ecdc6-106">Parameters</span></span>  

 `veh`  
 <span data-ttu-id="ecdc6-107">'ndaki `IVEHandler` Doğrulama hatalarını işleyen bir örneğe yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ecdc6-107">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="ecdc6-108">'ndaki Geçerli için tanımlayıcı <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="ecdc6-108">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="ecdc6-109">'ndaki Gerçekleştirilmesi gereken doğrulamanın türünü belirten [ValidatorFlags](validatorflags-enumeration.md) değerlerinin birleşimi.</span><span class="sxs-lookup"><span data-stu-id="ecdc6-109">[in] A combination of [ValidatorFlags](validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="ecdc6-110">'ndaki Doğrulamadan çıkmadan önce izin verilen en fazla hata sayısı.</span><span class="sxs-lookup"><span data-stu-id="ecdc6-110">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="ecdc6-111">'ndaki Kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="ecdc6-111">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="ecdc6-112">'ndaki Doğrulanacak dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="ecdc6-112">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="ecdc6-113">'ndaki Dosya arabelleği işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ecdc6-113">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="ecdc6-114">'ndaki Doğrulanacak dosyanın bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="ecdc6-114">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ecdc6-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ecdc6-115">Return Value</span></span>  
  
|<span data-ttu-id="ecdc6-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ecdc6-116">HRESULT</span></span>|<span data-ttu-id="ecdc6-117">Description</span><span class="sxs-lookup"><span data-stu-id="ecdc6-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ecdc6-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="ecdc6-118">S_OK</span></span>|<span data-ttu-id="ecdc6-119">`Validate` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ecdc6-119">`Validate` returned successfully.</span></span>|  
|<span data-ttu-id="ecdc6-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ecdc6-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ecdc6-121">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="ecdc6-121">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ecdc6-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ecdc6-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ecdc6-123">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="ecdc6-123">The call timed out.</span></span>|  
|<span data-ttu-id="ecdc6-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ecdc6-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ecdc6-125">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ecdc6-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ecdc6-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ecdc6-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ecdc6-127">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="ecdc6-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ecdc6-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ecdc6-128">E_FAIL</span></span>|<span data-ttu-id="ecdc6-129">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ecdc6-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ecdc6-130">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ecdc6-130">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ecdc6-131">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ecdc6-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ecdc6-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ecdc6-132">Requirements</span></span>  

 <span data-ttu-id="ecdc6-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecdc6-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecdc6-134">**Üst bilgi:** IValidator. IDL, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="ecdc6-134">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="ecdc6-135">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="ecdc6-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ecdc6-136">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecdc6-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecdc6-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ecdc6-137">See also</span></span>

- [<span data-ttu-id="ecdc6-138">ICLRValidator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ecdc6-138">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)
