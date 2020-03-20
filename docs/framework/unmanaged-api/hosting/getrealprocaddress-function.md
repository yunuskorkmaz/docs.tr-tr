---
title: GetRealProcAddress İşlevi
ms.date: 03/30/2017
api_name:
- GetRealProcAddress
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRealProcAddress
helpviewer_keywords:
- GetRealProcAddress function [.NET Framework hosting]
ms.assetid: f1f2fab1-400b-488f-95f2-d49c4fca3556
topic_type:
- apiref
ms.openlocfilehash: 4c914e00987053b1c1e9e00bf8e54632175e1de8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178168"
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="0cc9e-102">GetRealProcAddress İşlevi</span><span class="sxs-lookup"><span data-stu-id="0cc9e-102">GetRealProcAddress Function</span></span>
<span data-ttu-id="0cc9e-103">Ortak dil çalışma zamanının (CLR) en son yüklenen sürümünden dışa aktarılan belirtilen işlevin adresini alır.</span><span class="sxs-lookup"><span data-stu-id="0cc9e-103">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="0cc9e-104">Bu işlev .NET Framework 4'te amortismana hazırlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0cc9e-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cc9e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0cc9e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,
    [out] VOID  **ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0cc9e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0cc9e-106">Parameters</span></span>  
 `pwszProcName`  
 <span data-ttu-id="0cc9e-107">[içinde] Fonksiyonun adı.</span><span class="sxs-lookup"><span data-stu-id="0cc9e-107">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="0cc9e-108">[çıkış] İşlevin adresine işaretçi alan konum.</span><span class="sxs-lookup"><span data-stu-id="0cc9e-108">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0cc9e-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0cc9e-109">Return Value</span></span>  
 <span data-ttu-id="0cc9e-110">Bu yöntem, WinError.h'de tanımlandığı gibi standart Bileşen Nesne Modeli (COM) hata kodlarını, CorError.h'de tanımlanan aşağıdaki değerlere ek olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="0cc9e-110">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="0cc9e-111">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="0cc9e-111">Return code</span></span>|<span data-ttu-id="0cc9e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0cc9e-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="0cc9e-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="0cc9e-113">S_OK</span></span>|<span data-ttu-id="0cc9e-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="0cc9e-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="0cc9e-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="0cc9e-115">E_POINTER</span></span>|<span data-ttu-id="0cc9e-116">`ppv`geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="0cc9e-116">`ppv` is not valid.</span></span>|  
|<span data-ttu-id="0cc9e-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="0cc9e-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="0cc9e-118">İşlev çalışma zamanından dışa aktarılmaz.</span><span class="sxs-lookup"><span data-stu-id="0cc9e-118">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0cc9e-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0cc9e-119">Requirements</span></span>  
 <span data-ttu-id="0cc9e-120">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cc9e-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cc9e-121">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0cc9e-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0cc9e-122">**Kütüphane:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="0cc9e-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0cc9e-123">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cc9e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cc9e-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cc9e-124">See also</span></span>

- [<span data-ttu-id="0cc9e-125">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="0cc9e-125">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
