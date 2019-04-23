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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d4723fbf2311316184cb77c90754d7e037badcd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089599"
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="16289-102">GetRealProcAddress İşlevi</span><span class="sxs-lookup"><span data-stu-id="16289-102">GetRealProcAddress Function</span></span>
<span data-ttu-id="16289-103">En son yüklenen sürümünden ortak dil çalışma zamanı (CLR) dışarı aktarılan belirtilen işlevin adresini alır.</span><span class="sxs-lookup"><span data-stu-id="16289-103">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="16289-104">Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="16289-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16289-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16289-105">Syntax</span></span>  
  
```  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,   
    [out] VOID  **ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16289-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="16289-106">Parameters</span></span>  
 `pwszProcName`  
 <span data-ttu-id="16289-107">[in] İşlevin adı.</span><span class="sxs-lookup"><span data-stu-id="16289-107">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="16289-108">[out] İşlevin adresini bir işaretçiye alan konumu.</span><span class="sxs-lookup"><span data-stu-id="16289-108">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="16289-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="16289-109">Return Value</span></span>  
 <span data-ttu-id="16289-110">Bu yöntem standart Bileşen Nesne Modeli (COM) hata kodları CorError.h içinde tanımlanan aşağıdaki değerlere ek olarak Wınerror içinde tanımlanan döndürür.</span><span class="sxs-lookup"><span data-stu-id="16289-110">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="16289-111">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="16289-111">Return code</span></span>|<span data-ttu-id="16289-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16289-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="16289-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="16289-113">S_OK</span></span>|<span data-ttu-id="16289-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="16289-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="16289-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="16289-115">E_POINTER</span></span>|<span data-ttu-id="16289-116">`ppv` geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="16289-116">`ppv` is not valid.</span></span>|  
|<span data-ttu-id="16289-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="16289-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="16289-118">İşlev, çalışma zamanını şuradan verilmez.</span><span class="sxs-lookup"><span data-stu-id="16289-118">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="16289-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="16289-119">Requirements</span></span>  
 <span data-ttu-id="16289-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16289-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16289-121">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="16289-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="16289-122">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="16289-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="16289-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16289-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16289-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16289-124">See also</span></span>

- [<span data-ttu-id="16289-125">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="16289-125">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
