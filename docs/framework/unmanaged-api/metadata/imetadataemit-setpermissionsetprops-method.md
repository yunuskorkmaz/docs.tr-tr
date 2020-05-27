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
ms.openlocfilehash: 1e6ee1f2f497ef30a5390e7afac55c54705248ed
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007812"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="084c1-102">IMetaDataEmit::SetPermissionSetProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="084c1-102">IMetaDataEmit::SetPermissionSetProps Method</span></span>
<span data-ttu-id="084c1-103">[Imetadatayayma::D efinePermissionSet](imetadataemit-definepermissionset-method.md)için önceki bir çağrı tarafından tanımlanan izin kümesinin meta veri imzasının özelliklerini ayarlar veya güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="084c1-103">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="084c1-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="084c1-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPermissionSetProps (
    [in]  mdToken         tk,
    [in]  DWORD           dwAction,
    [in]  void const      *pvPermission,
    [in]  ULONG           cbPermission,
    [out] mdPermission    *ppm
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="084c1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="084c1-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="084c1-106">'ndaki Tasarlankullanılacak nesneyi temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="084c1-106">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="084c1-107">'ndaki Kullanılacak bildirime dayalı güvenlik türünü belirten bir [CorDeclSecurity](cordeclsecurity-enumeration.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="084c1-107">[in] A [CorDeclSecurity](cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="084c1-108">'ndaki İzin blobu.</span><span class="sxs-lookup"><span data-stu-id="084c1-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="084c1-109">'ndaki Bayt cinsinden boyutu `pvPermission` .</span><span class="sxs-lookup"><span data-stu-id="084c1-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="084c1-110">dışı `mdPermission`Güncelleştirilmiş izinleri temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="084c1-110">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="084c1-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="084c1-111">Requirements</span></span>  
 <span data-ttu-id="084c1-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="084c1-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="084c1-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="084c1-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="084c1-114">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="084c1-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="084c1-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="084c1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="084c1-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="084c1-116">See also</span></span>

- [<span data-ttu-id="084c1-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="084c1-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="084c1-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="084c1-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
