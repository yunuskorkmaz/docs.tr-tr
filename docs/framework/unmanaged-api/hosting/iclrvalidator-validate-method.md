---
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
ms.openlocfilehash: 18492f3e95947a3a11da9d5d303651c04d764a8f
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762636"
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="11ec2-102">ICLRValidator::Validate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="11ec2-102">ICLRValidator::Validate Method</span></span>
<span data-ttu-id="11ec2-103">Belirtilen dosyadaki taşınabilir yürütülebilir (PE) veya Microsoft ara dili 'ni (MSIL) doğrular.</span><span class="sxs-lookup"><span data-stu-id="11ec2-103">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11ec2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="11ec2-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="11ec2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="11ec2-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="11ec2-106">'ndaki `IVEHandler`Doğrulama hatalarını işleyen bir örneğe yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="11ec2-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="11ec2-107">'ndaki Geçerli için tanımlayıcı <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="11ec2-107">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="11ec2-108">'ndaki Gerçekleştirilmesi gereken doğrulamanın türünü belirten [ValidatorFlags](validatorflags-enumeration.md) değerlerinin birleşimi.</span><span class="sxs-lookup"><span data-stu-id="11ec2-108">[in] A combination of [ValidatorFlags](validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="11ec2-109">'ndaki Doğrulamadan çıkmadan önce izin verilen en fazla hata sayısı.</span><span class="sxs-lookup"><span data-stu-id="11ec2-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="11ec2-110">'ndaki Kullanılmayan.</span><span class="sxs-lookup"><span data-stu-id="11ec2-110">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="11ec2-111">'ndaki Doğrulanacak dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="11ec2-111">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="11ec2-112">'ndaki Dosya arabelleği işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="11ec2-112">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="11ec2-113">'ndaki Doğrulanacak dosyanın bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="11ec2-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11ec2-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="11ec2-114">Return Value</span></span>  
  
|<span data-ttu-id="11ec2-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="11ec2-115">HRESULT</span></span>|<span data-ttu-id="11ec2-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="11ec2-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="11ec2-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="11ec2-117">S_OK</span></span>|<span data-ttu-id="11ec2-118">`Validate`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="11ec2-118">`Validate` returned successfully.</span></span>|  
|<span data-ttu-id="11ec2-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="11ec2-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="11ec2-120">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="11ec2-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="11ec2-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="11ec2-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="11ec2-122">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="11ec2-122">The call timed out.</span></span>|  
|<span data-ttu-id="11ec2-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="11ec2-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="11ec2-124">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="11ec2-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="11ec2-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="11ec2-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="11ec2-126">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="11ec2-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="11ec2-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="11ec2-127">E_FAIL</span></span>|<span data-ttu-id="11ec2-128">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="11ec2-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="11ec2-129">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="11ec2-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="11ec2-130">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="11ec2-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="11ec2-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="11ec2-131">Requirements</span></span>  
 <span data-ttu-id="11ec2-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11ec2-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11ec2-133">**Üst bilgi:** IValidator. IDL, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="11ec2-133">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="11ec2-134">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="11ec2-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11ec2-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11ec2-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11ec2-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11ec2-136">See also</span></span>

- [<span data-ttu-id="11ec2-137">ICLRValidator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="11ec2-137">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)
