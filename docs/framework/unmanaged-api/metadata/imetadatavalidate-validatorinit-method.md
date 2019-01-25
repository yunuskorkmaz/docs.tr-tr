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
ms.openlocfilehash: eb5f0514cad852367365b9c8b24ef006e275f749
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54696457"
---
# <a name="imetadatavalidatevalidatorinit-method"></a><span data-ttu-id="82390-102">IMetaDataValidate::ValidatorInit Yöntemi</span><span class="sxs-lookup"><span data-stu-id="82390-102">IMetaDataValidate::ValidatorInit Method</span></span>
<span data-ttu-id="82390-103">Geçerli meta veri kapsamda modül türünü belirtir ve doğrulama hataları için belirtilen geri çağırma yöntemi kaydeder bir bayrak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="82390-103">Sets a flag that specifies the type of the module in the current metadata scope, and registers the specified callback method for validation errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82390-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82390-104">Syntax</span></span>  
  
```  
HRESULT ValidatorInit (  
   [in] DWORD       dwModuleType,  
   [in] IUnknown    *pUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="82390-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="82390-105">Parameters</span></span>  
 `dwModule`  
 <span data-ttu-id="82390-106">[in] Değerini [CorValidatorModuleType](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md) modül türü geçerli meta veri kapsamda belirten sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="82390-106">[in] A value of the [CorValidatorModuleType](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md) enumeration that specifies the type of the module in the current metadata scope.</span></span>  
  
 `pUnk`  
 <span data-ttu-id="82390-107">[in] Bir işaretçi bir [IUnknown](/cpp/atl/iunknown) doğrulama hataları için bir işlev geri çağırma işlevi görür örneği.</span><span class="sxs-lookup"><span data-stu-id="82390-107">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) instance that serves as a function callback for validation errors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82390-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="82390-108">Requirements</span></span>  
 <span data-ttu-id="82390-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82390-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82390-110">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="82390-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="82390-111">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="82390-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="82390-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82390-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82390-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82390-113">See also</span></span>
- [<span data-ttu-id="82390-114">IMetaDataValidate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="82390-114">IMetaDataValidate Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)
