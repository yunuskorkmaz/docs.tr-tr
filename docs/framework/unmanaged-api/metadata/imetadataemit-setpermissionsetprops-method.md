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
ms.openlocfilehash: 53a75b8e7edd15cd233577e0a3714fb5d981495f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432332"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="d5e8e-102">IMetaDataEmit::SetPermissionSetProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5e8e-102">IMetaDataEmit::SetPermissionSetProps Method</span></span>
<span data-ttu-id="d5e8e-103">[Imetadatayayma::D efinePermissionSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md)için önceki bir çağrı tarafından tanımlanan izin kümesinin meta veri imzasının özelliklerini ayarlar veya güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="d5e8e-103">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5e8e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5e8e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPermissionSetProps (   
    [in]  mdToken         tk,   
    [in]  DWORD           dwAction,   
    [in]  void const      *pvPermission,   
    [in]  ULONG           cbPermission,   
    [out] mdPermission    *ppm   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5e8e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d5e8e-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="d5e8e-106">'ndaki Tasarlankullanılacak nesneyi temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="d5e8e-106">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="d5e8e-107">'ndaki Kullanılacak bildirime dayalı güvenlik türünü belirten bir [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="d5e8e-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="d5e8e-108">'ndaki İzin blobu.</span><span class="sxs-lookup"><span data-stu-id="d5e8e-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="d5e8e-109">'ndaki `pvPermission`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="d5e8e-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="d5e8e-110">dışı Güncelleştirilmiş izinleri temsil eden bir `mdPermission` meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="d5e8e-110">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5e8e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5e8e-111">Requirements</span></span>  
 <span data-ttu-id="d5e8e-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5e8e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5e8e-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d5e8e-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d5e8e-114">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="d5e8e-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5e8e-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5e8e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5e8e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5e8e-116">See also</span></span>

- [<span data-ttu-id="d5e8e-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5e8e-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="d5e8e-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5e8e-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
