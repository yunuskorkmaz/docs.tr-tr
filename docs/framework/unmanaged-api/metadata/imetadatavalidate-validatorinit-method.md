---
title: IMetaDataValidate::ValidatorInit Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataValidate.ValidatorInit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataValidate::ValidatorInit
helpviewer_keywords:
- IMetaDataValidate::ValidatorInit method [.NET Framework metadata]
- ValidatorInit method [.NET Framework metadata]
ms.assetid: 6bafd75a-e2d0-4aea-aed1-074374d5dff6
topic_type:
- apiref
ms.openlocfilehash: e2f54e11906cd4ba1440e220530f2ca5b9de769f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708562"
---
# <a name="imetadatavalidatevalidatorinit-method"></a><span data-ttu-id="3836e-102">IMetaDataValidate::ValidatorInit Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3836e-102">IMetaDataValidate::ValidatorInit Method</span></span>

<span data-ttu-id="3836e-103">Geçerli meta veri kapsamındaki modülün türünü belirten bir bayrak ayarlar ve doğrulama hataları için belirtilen geri çağırma yöntemini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="3836e-103">Sets a flag that specifies the type of the module in the current metadata scope, and registers the specified callback method for validation errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3836e-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3836e-104">Syntax</span></span>  
  
```cpp  
HRESULT ValidatorInit (  
   [in] DWORD       dwModuleType,  
   [in] IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3836e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3836e-105">Parameters</span></span>  

 `dwModule`  
 <span data-ttu-id="3836e-106">'ndaki Geçerli meta veri kapsamındaki modülün türünü belirten [CorValidatorModuleType](corvalidatormoduletype-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="3836e-106">[in] A value of the [CorValidatorModuleType](corvalidatormoduletype-enumeration.md) enumeration that specifies the type of the module in the current metadata scope.</span></span>  
  
 `pUnk`  
 <span data-ttu-id="3836e-107">'ndaki Doğrulama hataları için işlev geri çağırması görevi gören bir [IUnknown](/cpp/atl/iunknown) örneği işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="3836e-107">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) instance that serves as a function callback for validation errors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3836e-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3836e-108">Requirements</span></span>  

 <span data-ttu-id="3836e-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3836e-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3836e-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3836e-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3836e-111">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="3836e-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3836e-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3836e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3836e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3836e-113">See also</span></span>

- [<span data-ttu-id="3836e-114">IMetaDataValidate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3836e-114">IMetaDataValidate Interface</span></span>](imetadatavalidate-interface.md)
