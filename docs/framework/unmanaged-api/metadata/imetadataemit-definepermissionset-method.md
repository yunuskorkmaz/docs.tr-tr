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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 33eadccf691b14289a46ff460f3cef8ae636b129
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074852"
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="a4b15-102">IMetaDataEmit::DefinePermissionSet Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a4b15-102">IMetaDataEmit::DefinePermissionSet Method</span></span>
<span data-ttu-id="a4b15-103">Bir izin kümesi ile belirtilen meta veri imzası için bir tanım oluşturur ve bu izin kümesi tanımı için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="a4b15-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4b15-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a4b15-104">Syntax</span></span>  
  
```  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,   
    [in]  DWORD          dwAction,   
    [in]  void const     *pvPermission,   
    [in]  ULONG          cbPermission,   
    [out] mdPermission   *ppm   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4b15-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a4b15-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="a4b15-106">[in] Donatılmış olmalıdır nesne.</span><span class="sxs-lookup"><span data-stu-id="a4b15-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="a4b15-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) kullanılacak bildirim temelli güvenlik türünü belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="a4b15-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="a4b15-108">[in] BLOB izni.</span><span class="sxs-lookup"><span data-stu-id="a4b15-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="a4b15-109">[in] Bayt cinsinden boyutu, `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="a4b15-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="a4b15-110">[out] İzin verilen belirteç.</span><span class="sxs-lookup"><span data-stu-id="a4b15-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4b15-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a4b15-111">Requirements</span></span>  
 <span data-ttu-id="a4b15-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4b15-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4b15-113">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="a4b15-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a4b15-114">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="a4b15-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a4b15-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4b15-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4b15-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4b15-116">See also</span></span>

- [<span data-ttu-id="a4b15-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a4b15-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a4b15-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a4b15-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
