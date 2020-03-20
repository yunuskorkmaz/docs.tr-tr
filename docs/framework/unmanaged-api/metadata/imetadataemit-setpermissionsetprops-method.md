---
title: IMetaDataEmit::SetPermissionSetProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPermissionSetProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPermissionSetProps
helpviewer_keywords:
- SetPermissionSetProps method [.NET Framework metadata]
- IMetaDataEmit::SetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 8eaee971-40bf-45e2-a3d8-6e57674213b6
topic_type:
- apiref
ms.openlocfilehash: de4cfdf2a9353eebdebaf4df9e481d06d776ff04
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177483"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="898f5-102">IMetaDataEmit::SetPermissionSetProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="898f5-102">IMetaDataEmit::SetPermissionSetProps Method</span></span>
<span data-ttu-id="898f5-103">[IMetaDataEmit::DefinePermissionSet'e](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md)yapılan bir önceki çağrı yla tanımlanan bir izin kümesinin meta veri imzasının özelliklerini ayarlar veya güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="898f5-103">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="898f5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="898f5-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPermissionSetProps (
    [in]  mdToken         tk,
    [in]  DWORD           dwAction,
    [in]  void const      *pvPermission,
    [in]  ULONG           cbPermission,
    [out] mdPermission    *ppm
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="898f5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="898f5-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="898f5-106">[içinde] Dekore edilecek nesneyi temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="898f5-106">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="898f5-107">[içinde] Kullanılacak bildirimsel güvenlik türünü belirten bir [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="898f5-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="898f5-108">[içinde] İzin BLOB.</span><span class="sxs-lookup"><span data-stu-id="898f5-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="898f5-109">[içinde] Boyutu, bayt, ve. `pvPermission`</span><span class="sxs-lookup"><span data-stu-id="898f5-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="898f5-110">[çıkış] Güncelleştirilmiş izinleri temsil eden `mdPermission` bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="898f5-110">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="898f5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="898f5-111">Requirements</span></span>  
 <span data-ttu-id="898f5-112">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="898f5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="898f5-113">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="898f5-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="898f5-114">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="898f5-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="898f5-115">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="898f5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="898f5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="898f5-116">See also</span></span>

- [<span data-ttu-id="898f5-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="898f5-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="898f5-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="898f5-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
