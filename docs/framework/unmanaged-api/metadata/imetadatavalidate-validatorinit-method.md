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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 177bd67e9f177296cf436e3c2537b95b30e34e87
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766887"
---
# <a name="imetadatavalidatevalidatorinit-method"></a><span data-ttu-id="2803c-102">IMetaDataValidate::ValidatorInit Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2803c-102">IMetaDataValidate::ValidatorInit Method</span></span>
<span data-ttu-id="2803c-103">Geçerli meta veri kapsamda modül türünü belirtir ve doğrulama hataları için belirtilen geri çağırma yöntemi kaydeder bir bayrak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2803c-103">Sets a flag that specifies the type of the module in the current metadata scope, and registers the specified callback method for validation errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2803c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2803c-104">Syntax</span></span>  
  
```cpp  
HRESULT ValidatorInit (  
   [in] DWORD       dwModuleType,  
   [in] IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2803c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2803c-105">Parameters</span></span>  
 `dwModule`  
 <span data-ttu-id="2803c-106">[in] Değerini [CorValidatorModuleType](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md) modül türü geçerli meta veri kapsamda belirten sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="2803c-106">[in] A value of the [CorValidatorModuleType](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md) enumeration that specifies the type of the module in the current metadata scope.</span></span>  
  
 `pUnk`  
 <span data-ttu-id="2803c-107">[in] Bir işaretçi bir [IUnknown](/cpp/atl/iunknown) doğrulama hataları için bir işlev geri çağırma işlevi görür örneği.</span><span class="sxs-lookup"><span data-stu-id="2803c-107">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) instance that serves as a function callback for validation errors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2803c-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2803c-108">Requirements</span></span>  
 <span data-ttu-id="2803c-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2803c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2803c-110">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="2803c-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2803c-111">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="2803c-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2803c-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2803c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2803c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2803c-113">See also</span></span>

- [<span data-ttu-id="2803c-114">IMetaDataValidate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2803c-114">IMetaDataValidate Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)
