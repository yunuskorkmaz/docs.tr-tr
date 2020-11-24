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
ms.openlocfilehash: 4c3e0953d71020ba62ee4ab68aa9e21ea3f0f521
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675041"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="29026-102">IMetaDataEmit::SetPermissionSetProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="29026-102">IMetaDataEmit::SetPermissionSetProps Method</span></span>

<span data-ttu-id="29026-103">[Imetadatayayma::D efinePermissionSet](imetadataemit-definepermissionset-method.md)için önceki bir çağrı tarafından tanımlanan izin kümesinin meta veri imzasının özelliklerini ayarlar veya güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="29026-103">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29026-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="29026-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPermissionSetProps (
    [in]  mdToken         tk,
    [in]  DWORD           dwAction,
    [in]  void const      *pvPermission,
    [in]  ULONG           cbPermission,
    [out] mdPermission    *ppm
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29026-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="29026-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="29026-106">'ndaki Tasarlankullanılacak nesneyi temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="29026-106">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="29026-107">'ndaki Kullanılacak bildirime dayalı güvenlik türünü belirten bir [CorDeclSecurity](cordeclsecurity-enumeration.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="29026-107">[in] A [CorDeclSecurity](cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="29026-108">'ndaki İzin blobu.</span><span class="sxs-lookup"><span data-stu-id="29026-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="29026-109">'ndaki Bayt cinsinden boyutu `pvPermission` .</span><span class="sxs-lookup"><span data-stu-id="29026-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="29026-110">dışı `mdPermission` Güncelleştirilmiş izinleri temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="29026-110">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29026-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="29026-111">Requirements</span></span>  

 <span data-ttu-id="29026-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29026-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29026-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="29026-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="29026-114">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="29026-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="29026-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29026-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29026-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29026-116">See also</span></span>

- [<span data-ttu-id="29026-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="29026-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="29026-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="29026-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
