---
description: 'Şu konuda daha fazla bilgi edinin: ımetadatayayma::D efinePermissionSet yöntemi'
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
ms.openlocfilehash: f5c3f1466217713cb3970c805079d8f65fd429c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784086"
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="763bc-103">IMetaDataEmit::DefinePermissionSet Yöntemi</span><span class="sxs-lookup"><span data-stu-id="763bc-103">IMetaDataEmit::DefinePermissionSet Method</span></span>

<span data-ttu-id="763bc-104">Belirtilen meta veri imzasıyla bir izin kümesi için tanım oluşturur ve bu izin kümesi tanımına bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="763bc-104">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="763bc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="763bc-105">Syntax</span></span>  
  
```cpp  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,
    [in]  DWORD          dwAction,
    [in]  void const     *pvPermission,
    [in]  ULONG          cbPermission,
    [out] mdPermission   *ppm
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="763bc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="763bc-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="763bc-107">'ndaki Tasarlankullanılacak nesne.</span><span class="sxs-lookup"><span data-stu-id="763bc-107">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="763bc-108">'ndaki Kullanılacak bildirime dayalı güvenlik türünü belirten bir [CorDeclSecurity](cordeclsecurity-enumeration.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="763bc-108">[in] A [CorDeclSecurity](cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="763bc-109">'ndaki İzin blobu.</span><span class="sxs-lookup"><span data-stu-id="763bc-109">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="763bc-110">'ndaki Bayt cinsinden boyutu `pvPermission` .</span><span class="sxs-lookup"><span data-stu-id="763bc-110">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="763bc-111">dışı Döndürülen izin belirteci.</span><span class="sxs-lookup"><span data-stu-id="763bc-111">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="763bc-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="763bc-112">Requirements</span></span>  

 <span data-ttu-id="763bc-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="763bc-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="763bc-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="763bc-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="763bc-115">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="763bc-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="763bc-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="763bc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="763bc-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="763bc-117">See also</span></span>

- [<span data-ttu-id="763bc-118">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="763bc-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="763bc-119">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="763bc-119">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
