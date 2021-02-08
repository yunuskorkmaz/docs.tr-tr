---
description: ': Imetadatayayma:: SetPermissionSetProps Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 1e2786a21a1024f32328e36878a1a2427af54f51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771892"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="2bfaf-103">IMetaDataEmit::SetPermissionSetProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2bfaf-103">IMetaDataEmit::SetPermissionSetProps Method</span></span>

<span data-ttu-id="2bfaf-104">[Imetadatayayma::D efinePermissionSet](imetadataemit-definepermissionset-method.md)için önceki bir çağrı tarafından tanımlanan izin kümesinin meta veri imzasının özelliklerini ayarlar veya güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="2bfaf-104">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bfaf-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2bfaf-105">Syntax</span></span>  
  
```cpp  
HRESULT SetPermissionSetProps (
    [in]  mdToken         tk,
    [in]  DWORD           dwAction,
    [in]  void const      *pvPermission,
    [in]  ULONG           cbPermission,
    [out] mdPermission    *ppm
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2bfaf-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2bfaf-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="2bfaf-107">'ndaki Tasarlankullanılacak nesneyi temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="2bfaf-107">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="2bfaf-108">'ndaki Kullanılacak bildirime dayalı güvenlik türünü belirten bir [CorDeclSecurity](cordeclsecurity-enumeration.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="2bfaf-108">[in] A [CorDeclSecurity](cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="2bfaf-109">'ndaki İzin blobu.</span><span class="sxs-lookup"><span data-stu-id="2bfaf-109">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="2bfaf-110">'ndaki Bayt cinsinden boyutu `pvPermission` .</span><span class="sxs-lookup"><span data-stu-id="2bfaf-110">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="2bfaf-111">dışı `mdPermission` Güncelleştirilmiş izinleri temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="2bfaf-111">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bfaf-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2bfaf-112">Requirements</span></span>  

 <span data-ttu-id="2bfaf-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bfaf-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bfaf-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2bfaf-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2bfaf-115">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="2bfaf-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2bfaf-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bfaf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bfaf-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2bfaf-117">See also</span></span>

- [<span data-ttu-id="2bfaf-118">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2bfaf-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="2bfaf-119">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2bfaf-119">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
