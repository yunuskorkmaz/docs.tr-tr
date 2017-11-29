---
title: "GetRealProcAddress İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetRealProcAddress
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetRealProcAddress
helpviewer_keywords: GetRealProcAddress function [.NET Framework hosting]
ms.assetid: f1f2fab1-400b-488f-95f2-d49c4fca3556
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 53e51bcf72f1a59f5c471564022d0d8c415381a6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="9b950-102">GetRealProcAddress İşlevi</span><span class="sxs-lookup"><span data-stu-id="9b950-102">GetRealProcAddress Function</span></span>
<span data-ttu-id="9b950-103">Son yüklenen sürümünden ortak dil çalışma zamanı (CLR) dışarı belirtilen işlev adresi alır.</span><span class="sxs-lookup"><span data-stu-id="9b950-103">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="9b950-104">Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9b950-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b950-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9b950-105">Syntax</span></span>  
  
```  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,   
    [out] VOID  **ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b950-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9b950-106">Parameters</span></span>  
 `pwszProcName`  
 <span data-ttu-id="9b950-107">[in] İşlevin adı.</span><span class="sxs-lookup"><span data-stu-id="9b950-107">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="9b950-108">[out] İşlevin adresini gösteren bir işaretçi aldığı konumu.</span><span class="sxs-lookup"><span data-stu-id="9b950-108">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b950-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9b950-109">Return Value</span></span>  
 <span data-ttu-id="9b950-110">Bu yöntem standart Bileşen Nesne Modeli (COM) hata kodları, CorError.h içinde tanımlanan aşağıdaki değerleri yanı sıra Winerror.h'de içinde tanımlandığı şekilde döndürür.</span><span class="sxs-lookup"><span data-stu-id="9b950-110">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="9b950-111">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="9b950-111">Return code</span></span>|<span data-ttu-id="9b950-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9b950-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="9b950-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="9b950-113">S_OK</span></span>|<span data-ttu-id="9b950-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="9b950-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="9b950-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="9b950-115">E_POINTER</span></span>|<span data-ttu-id="9b950-116">`ppv`geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="9b950-116">`ppv` is not valid.</span></span>|  
|<span data-ttu-id="9b950-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="9b950-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="9b950-118">İşlev çalışma zamanını şuradan verilmez.</span><span class="sxs-lookup"><span data-stu-id="9b950-118">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9b950-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b950-119">Requirements</span></span>  
 <span data-ttu-id="9b950-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b950-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b950-121">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9b950-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9b950-122">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9b950-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9b950-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b950-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b950-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9b950-124">See Also</span></span>  
 [<span data-ttu-id="9b950-125">Kullanım dışı CLR barındırma işlevleri</span><span class="sxs-lookup"><span data-stu-id="9b950-125">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
