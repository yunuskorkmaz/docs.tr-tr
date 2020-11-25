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
ms.openlocfilehash: 3698525c139ed52b59ca577c598e675b6c26eef4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719521"
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="d2249-102">IMetaDataEmit::DefinePermissionSet Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2249-102">IMetaDataEmit::DefinePermissionSet Method</span></span>

<span data-ttu-id="d2249-103">Belirtilen meta veri imzasıyla bir izin kümesi için tanım oluşturur ve bu izin kümesi tanımına bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="d2249-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2249-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d2249-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,
    [in]  DWORD          dwAction,
    [in]  void const     *pvPermission,
    [in]  ULONG          cbPermission,
    [out] mdPermission   *ppm
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2249-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d2249-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="d2249-106">'ndaki Tasarlankullanılacak nesne.</span><span class="sxs-lookup"><span data-stu-id="d2249-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="d2249-107">'ndaki Kullanılacak bildirime dayalı güvenlik türünü belirten bir [CorDeclSecurity](cordeclsecurity-enumeration.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="d2249-107">[in] A [CorDeclSecurity](cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="d2249-108">'ndaki İzin blobu.</span><span class="sxs-lookup"><span data-stu-id="d2249-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="d2249-109">'ndaki Bayt cinsinden boyutu `pvPermission` .</span><span class="sxs-lookup"><span data-stu-id="d2249-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="d2249-110">dışı Döndürülen izin belirteci.</span><span class="sxs-lookup"><span data-stu-id="d2249-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2249-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d2249-111">Requirements</span></span>  

 <span data-ttu-id="d2249-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2249-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2249-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d2249-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d2249-114">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="d2249-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d2249-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2249-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2249-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2249-116">See also</span></span>

- [<span data-ttu-id="d2249-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d2249-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="d2249-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d2249-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
