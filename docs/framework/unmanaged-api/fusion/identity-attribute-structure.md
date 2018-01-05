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
ms.workload: dotnet
ms.openlocfilehash: 2c0d09bf4c24f977a490f946cbc35b2b3f53dfc3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="identityattribute-structure"></a><span data-ttu-id="e3ced-102">IDENTITY_ATTRIBUTE Yapısı</span><span class="sxs-lookup"><span data-stu-id="e3ced-102">IDENTITY_ATTRIBUTE Structure</span></span>
<span data-ttu-id="e3ced-103">İlgili meta verileri öznitelik bilgileri içeren bir [Idefinitionıdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="e3ced-103">Contains metadata attribute information about an [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3ced-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e3ced-104">Syntax</span></span>  
  
```  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="e3ced-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e3ced-105">Members</span></span>  
  
|<span data-ttu-id="e3ced-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e3ced-106">Member</span></span>|<span data-ttu-id="e3ced-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3ced-107">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="e3ced-108">Ad alanı içeren bir null olarak sonlandırılan bir karakter dizesi için bir işaretçi özniteliği kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="e3ced-108">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="e3ced-109">Özniteliğin adını içeren bir null olarak sonlandırılan bir karakter dizesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e3ced-109">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="e3ced-110">Öznitelik değerini içeren bir null olarak sonlandırılan bir karakter dizesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e3ced-110">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3ced-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e3ced-111">Remarks</span></span>  
 <span data-ttu-id="e3ced-112">`IDENTITY_ATTRIBUTE` Yapısı null olarak sonlandırılan bir karakter dizeleri üç işaretçiler içerir.</span><span class="sxs-lookup"><span data-stu-id="e3ced-112">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="e3ced-113">Bu üç dizeleri bir öznitelik açıklar.</span><span class="sxs-lookup"><span data-stu-id="e3ced-113">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="e3ced-114">Örneği bir `IDENTITY_ATTRIBUTE` yapısı örneği ile ilişkili bir [ıdentıty_attrıbute_blob](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="e3ced-114">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="e3ced-115">`IDENTITY_ATTRIBUTE` Yapısı içeren gerçek dizeler ve karşılık gelen `IDENTITY_ATTRIBUTE_BLOB` yapısı listeler listelenen üç dizelere uzaklıkları `IDENTITY_ATTRIBUTE` yapısı.</span><span class="sxs-lookup"><span data-stu-id="e3ced-115">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3ced-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e3ced-116">Requirements</span></span>  
 <span data-ttu-id="e3ced-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3ced-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3ced-118">**Başlık:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="e3ced-118">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="e3ced-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3ced-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3ced-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e3ced-120">See Also</span></span>  
 [<span data-ttu-id="e3ced-121">IDefinitionIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e3ced-121">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)  
 [<span data-ttu-id="e3ced-122">IDENTITY_ATTRIBUTE_BLOB Yapısı</span><span class="sxs-lookup"><span data-stu-id="e3ced-122">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)  
 [<span data-ttu-id="e3ced-123">Fusion Yapıları</span><span class="sxs-lookup"><span data-stu-id="e3ced-123">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
