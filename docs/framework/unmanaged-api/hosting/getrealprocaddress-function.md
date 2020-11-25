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
ms.openlocfilehash: d48106fca6008955409581ad9ac202aebe785cb4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733236"
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="bda85-102">GetRealProcAddress İşlevi</span><span class="sxs-lookup"><span data-stu-id="bda85-102">GetRealProcAddress Function</span></span>

<span data-ttu-id="bda85-103">Ortak dil çalışma zamanının (CLR) en son yüklenen sürümünden aktarılmış olan belirtilen işlevin adresini alır.</span><span class="sxs-lookup"><span data-stu-id="bda85-103">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="bda85-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="bda85-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bda85-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="bda85-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,
    [out] VOID  **ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bda85-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bda85-106">Parameters</span></span>  

 `pwszProcName`  
 <span data-ttu-id="bda85-107">'ndaki İşlevin adı.</span><span class="sxs-lookup"><span data-stu-id="bda85-107">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="bda85-108">dışı İşlevin adresine bir işaretçi alan konum.</span><span class="sxs-lookup"><span data-stu-id="bda85-108">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bda85-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bda85-109">Return Value</span></span>  

 <span data-ttu-id="bda85-110">Bu yöntem, CorError. h içinde tanımlanan aşağıdaki değerlere ek olarak, WinError. h içinde tanımlanan standart bileşen nesne modeli (COM) hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="bda85-110">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="bda85-111">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="bda85-111">Return code</span></span>|<span data-ttu-id="bda85-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bda85-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="bda85-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="bda85-113">S_OK</span></span>|<span data-ttu-id="bda85-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="bda85-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="bda85-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="bda85-115">E_POINTER</span></span>|<span data-ttu-id="bda85-116">`ppv` geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="bda85-116">`ppv` is not valid.</span></span>|  
|<span data-ttu-id="bda85-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="bda85-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="bda85-118">İşlev çalışma zamanından dışarıya aktarılmamış.</span><span class="sxs-lookup"><span data-stu-id="bda85-118">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bda85-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bda85-119">Requirements</span></span>  

 <span data-ttu-id="bda85-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bda85-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bda85-121">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bda85-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bda85-122">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bda85-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bda85-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bda85-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bda85-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bda85-124">See also</span></span>

- [<span data-ttu-id="bda85-125">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="bda85-125">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
