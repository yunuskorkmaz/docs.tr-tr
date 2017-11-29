---
title: "IDENTITY_ATTRIBUTE Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDENTITY_ATTRIBUTE
api_location: fusion.dll
api_type: COM
f1_keywords: IDENTITY_ATTRIBUTE
helpviewer_keywords: IDENTITY_ATTRIBUTE structure [.NET Framework fusion]
ms.assetid: 1ee7c434-9681-4fa8-badd-652cb1a9742b
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3fc4d9f7a95a3283d87f036163592f43e87dd053
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="identityattribute-structure"></a><span data-ttu-id="d4802-102">IDENTITY_ATTRIBUTE Yapısı</span><span class="sxs-lookup"><span data-stu-id="d4802-102">IDENTITY_ATTRIBUTE Structure</span></span>
<span data-ttu-id="d4802-103">İlgili meta verileri öznitelik bilgileri içeren bir [Idefinitionıdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="d4802-103">Contains metadata attribute information about an [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4802-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4802-104">Syntax</span></span>  
  
```  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="d4802-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d4802-105">Members</span></span>  
  
|<span data-ttu-id="d4802-106">Üye</span><span class="sxs-lookup"><span data-stu-id="d4802-106">Member</span></span>|<span data-ttu-id="d4802-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4802-107">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="d4802-108">Ad alanı içeren bir null olarak sonlandırılan bir karakter dizesi için bir işaretçi özniteliği kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="d4802-108">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="d4802-109">Özniteliğin adını içeren bir null olarak sonlandırılan bir karakter dizesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d4802-109">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="d4802-110">Öznitelik değerini içeren bir null olarak sonlandırılan bir karakter dizesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d4802-110">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4802-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d4802-111">Remarks</span></span>  
 <span data-ttu-id="d4802-112">`IDENTITY_ATTRIBUTE` Yapısı null olarak sonlandırılan bir karakter dizeleri üç işaretçiler içerir.</span><span class="sxs-lookup"><span data-stu-id="d4802-112">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="d4802-113">Bu üç dizeleri bir öznitelik açıklar.</span><span class="sxs-lookup"><span data-stu-id="d4802-113">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="d4802-114">Örneği bir `IDENTITY_ATTRIBUTE` yapısı örneği ile ilişkili bir [ıdentıty_attrıbute_blob](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="d4802-114">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="d4802-115">`IDENTITY_ATTRIBUTE` Yapısı içeren gerçek dizeler ve karşılık gelen `IDENTITY_ATTRIBUTE_BLOB` yapısı listeler listelenen üç dizelere uzaklıkları `IDENTITY_ATTRIBUTE` yapısı.</span><span class="sxs-lookup"><span data-stu-id="d4802-115">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4802-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4802-116">Requirements</span></span>  
 <span data-ttu-id="d4802-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4802-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4802-118">**Başlık:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="d4802-118">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="d4802-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4802-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4802-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d4802-120">See Also</span></span>  
 [<span data-ttu-id="d4802-121">Idefinitionıdentity arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4802-121">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)  
 [<span data-ttu-id="d4802-122">Identıty_attrıbute_blob yapısı</span><span class="sxs-lookup"><span data-stu-id="d4802-122">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)  
 [<span data-ttu-id="d4802-123">Fusion yapıları</span><span class="sxs-lookup"><span data-stu-id="d4802-123">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
