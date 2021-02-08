---
description: 'Daha fazla bilgi edinin: GetRealProcAddress Işlevi'
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
ms.openlocfilehash: b8b3db77d6aef7fae3045a7aa2310c1fadc70e91
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785321"
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="cc11a-103">GetRealProcAddress İşlevi</span><span class="sxs-lookup"><span data-stu-id="cc11a-103">GetRealProcAddress Function</span></span>

<span data-ttu-id="cc11a-104">Ortak dil çalışma zamanının (CLR) en son yüklenen sürümünden aktarılmış olan belirtilen işlevin adresini alır.</span><span class="sxs-lookup"><span data-stu-id="cc11a-104">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="cc11a-105">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="cc11a-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc11a-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc11a-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,
    [out] VOID  **ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc11a-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cc11a-107">Parameters</span></span>  

 `pwszProcName`  
 <span data-ttu-id="cc11a-108">'ndaki İşlevin adı.</span><span class="sxs-lookup"><span data-stu-id="cc11a-108">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="cc11a-109">dışı İşlevin adresine bir işaretçi alan konum.</span><span class="sxs-lookup"><span data-stu-id="cc11a-109">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cc11a-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cc11a-110">Return Value</span></span>  

 <span data-ttu-id="cc11a-111">Bu yöntem, CorError. h içinde tanımlanan aşağıdaki değerlere ek olarak, WinError. h içinde tanımlanan standart bileşen nesne modeli (COM) hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="cc11a-111">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="cc11a-112">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="cc11a-112">Return code</span></span>|<span data-ttu-id="cc11a-113">Description</span><span class="sxs-lookup"><span data-stu-id="cc11a-113">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="cc11a-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="cc11a-114">S_OK</span></span>|<span data-ttu-id="cc11a-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="cc11a-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="cc11a-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="cc11a-116">E_POINTER</span></span>|<span data-ttu-id="cc11a-117">`ppv` geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="cc11a-117">`ppv` is not valid.</span></span>|  
|<span data-ttu-id="cc11a-118">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="cc11a-118">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="cc11a-119">İşlev çalışma zamanından dışarıya aktarılmamış.</span><span class="sxs-lookup"><span data-stu-id="cc11a-119">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cc11a-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cc11a-120">Requirements</span></span>  

 <span data-ttu-id="cc11a-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc11a-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc11a-122">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cc11a-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cc11a-123">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cc11a-123">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cc11a-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc11a-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc11a-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc11a-125">See also</span></span>

- [<span data-ttu-id="cc11a-126">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="cc11a-126">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
