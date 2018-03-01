---
title: "BlessIWbemServicesObject işlevi (yönetilmeyen API Başvurusu)"
description: "BlessIWbemServicesObject işlevi kullanıcı kimlik bilgilerini IWbemServices nesneyi erişime olup olmadığını gösterir"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- BlessIWbemServicesObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServicesObject
helpviewer_keywords:
- BlessIWbemServicesObject function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2430358e5ea21468c2e975c2a26f20fe801ee546
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="blessiwbemservicesobject-function"></a><span data-ttu-id="5b462-103">BlessIWbemServicesObject işlevi</span><span class="sxs-lookup"><span data-stu-id="5b462-103">BlessIWbemServicesObject function</span></span>
<span data-ttu-id="5b462-104">Kullanıcı kimlik bilgilerinin belirtilen erişime olup olmadığını gösteren [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="5b462-104">Indicates whether the user credentials permit access to a specified [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="5b462-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5b462-105">Syntax</span></span>  
  
```  
HRESULT BlessIWbemServicesObject (
   [in] IUnknown* pIUnknown,
   [in] BSTR strUser, 
   [in] BSTR strPassword, 
   [in] BSTR strAuthority, 
   [in] DWORD impLevel, 
   [in] DWORD authnLevel
);
```  

## <a name="parameters"></a><span data-ttu-id="5b462-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5b462-106">Parameters</span></span>

`pIWbemServices`  
<span data-ttu-id="5b462-107">[in] WMI hizmeti nesnesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5b462-107">[in] A pointer to a WMI service object.</span></span>

`strUser`  
<span data-ttu-id="5b462-108">[in] Kullanıcı adı.</span><span class="sxs-lookup"><span data-stu-id="5b462-108">[in] The user name.</span></span>

`strPassword`  
<span data-ttu-id="5b462-109">[in] İlişkili parolayı `strUser`.</span><span class="sxs-lookup"><span data-stu-id="5b462-109">[in] The password associated with `strUser`.</span></span>

<span data-ttu-id="5b462-110">`strAuthority`[in] Kullanıcının etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="5b462-110">`strAuthority` [in] The domain name of the user.</span></span> <span data-ttu-id="5b462-111">Bkz: [ConnectServerWmi](connectserverwmi.md) daha fazla bilgi için işlevi.</span><span class="sxs-lookup"><span data-stu-id="5b462-111">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

<span data-ttu-id="5b462-112">`impLevel`[in] Kimliğe bürünme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="5b462-112">`impLevel` [in] The impersonation level.</span></span>

<span data-ttu-id="5b462-113">`authnLevel`[in] Kimlik doğrulama düzeyi.</span><span class="sxs-lookup"><span data-stu-id="5b462-113">`authnLevel` [in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="5b462-114">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="5b462-114">Return value</span></span>

<span data-ttu-id="5b462-115">Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *Winerror.h'de* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:</span><span class="sxs-lookup"><span data-stu-id="5b462-115">The following values returned by this function are defined in the *WinError.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5b462-116">Sabit</span><span class="sxs-lookup"><span data-stu-id="5b462-116">Constant</span></span>  |<span data-ttu-id="5b462-117">Değer</span><span class="sxs-lookup"><span data-stu-id="5b462-117">Value</span></span>  |<span data-ttu-id="5b462-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b462-118">Description</span></span>  |
|---------|---------|---------|
| `E_INVALIDARG` | <span data-ttu-id="5b462-119">0x80070057</span><span class="sxs-lookup"><span data-stu-id="5b462-119">0x80070057</span></span> | <span data-ttu-id="5b462-120">Bir veya daha fazla bağımsız değişken geçersiz.</span><span class="sxs-lookup"><span data-stu-id="5b462-120">One or more arguments are invalid.</span></span> |
| `E_POINTER` | <span data-ttu-id="5b462-121">0x80004003</span><span class="sxs-lookup"><span data-stu-id="5b462-121">0x80004003</span></span> | <span data-ttu-id="5b462-122">`pIWbemServices`olan `null`.</span><span class="sxs-lookup"><span data-stu-id="5b462-122">`pIWbemServices` is `null`.</span></span> | 
| `E_FAIL` | <span data-ttu-id="5b462-123">0x80000008</span><span class="sxs-lookup"><span data-stu-id="5b462-123">0x80000008</span></span> | <span data-ttu-id="5b462-124">Belirlenemeyen bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="5b462-124">An unspecified error has occurred.</span></span> |
| `E_OUTOFMEMORY` | <span data-ttu-id="5b462-125">0x80000002</span><span class="sxs-lookup"><span data-stu-id="5b462-125">0x80000002</span></span> | <span data-ttu-id="5b462-126">İşlemi gerçekleştirmek yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="5b462-126">Insufficient memory is available to perform the operation.</span></span> | 
| `S_OK` | <span data-ttu-id="5b462-127">0</span><span class="sxs-lookup"><span data-stu-id="5b462-127">0</span></span> | <span data-ttu-id="5b462-128">İşlev çağrısı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="5b462-128">The function call was successful.</span></span> | 

## <a name="requirements"></a><span data-ttu-id="5b462-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5b462-129">Requirements</span></span>  
 <span data-ttu-id="5b462-130">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b462-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b462-131">**Başlık:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5b462-131">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5b462-132">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5b462-132">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b462-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b462-133">See also</span></span>  
[<span data-ttu-id="5b462-134">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5b462-134">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
