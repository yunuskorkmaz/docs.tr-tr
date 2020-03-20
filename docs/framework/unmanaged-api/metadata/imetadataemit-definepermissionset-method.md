---
title: IMetaDataEmit::DefinePermissionSet Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePermissionSet
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePermissionSet
helpviewer_keywords:
- DefinePermissionSet method [.NET Framework metadata]
- IMetaDataEmit::DefinePermissionSet method [.NET Framework metadata]
ms.assetid: 36cffbf7-82ca-4cf9-bf60-50ab491ac2d9
topic_type:
- apiref
ms.openlocfilehash: a0fd3fdb6dde9fd6b88ea6c64ed907c8a3e9e46d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175804"
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="264a4-102">IMetaDataEmit::DefinePermissionSet Yöntemi</span><span class="sxs-lookup"><span data-stu-id="264a4-102">IMetaDataEmit::DefinePermissionSet Method</span></span>
<span data-ttu-id="264a4-103">Belirtilen meta veri imzasıyla bir izin kümesi için tanım oluşturur ve bu izin kümesi tanımına bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="264a4-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="264a4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="264a4-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,
    [in]  DWORD          dwAction,
    [in]  void const     *pvPermission,
    [in]  ULONG          cbPermission,
    [out] mdPermission   *ppm
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="264a4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="264a4-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="264a4-106">[içinde] Dekore edilecek nesne.</span><span class="sxs-lookup"><span data-stu-id="264a4-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="264a4-107">[içinde] Kullanılacak bildirimsel güvenlik türünü belirten bir [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="264a4-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="264a4-108">[içinde] İzin BLOB.</span><span class="sxs-lookup"><span data-stu-id="264a4-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="264a4-109">[içinde] Boyutu, bayt, ve. `pvPermission`</span><span class="sxs-lookup"><span data-stu-id="264a4-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="264a4-110">[çıkış] İade edilen izin jetonu.</span><span class="sxs-lookup"><span data-stu-id="264a4-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="264a4-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="264a4-111">Requirements</span></span>  
 <span data-ttu-id="264a4-112">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="264a4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="264a4-113">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="264a4-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="264a4-114">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="264a4-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="264a4-115">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="264a4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="264a4-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="264a4-116">See also</span></span>

- [<span data-ttu-id="264a4-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="264a4-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="264a4-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="264a4-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
