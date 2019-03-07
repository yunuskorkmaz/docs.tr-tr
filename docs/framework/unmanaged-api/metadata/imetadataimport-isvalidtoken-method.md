---
title: IMetaDataImport::IsValidToken Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsValidToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsValidToken
helpviewer_keywords:
- IMetaDataImport::IsValidToken method [.NET Framework metadata]
- IsValidToken method [.NET Framework metadata]
ms.assetid: aeb0fc63-9eff-4384-9284-cb9900572d74
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6e887fb5f4f9667bed7eef4a84899f82cada0fcd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489585"
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="c51c5-102">IMetaDataImport::IsValidToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c51c5-102">IMetaDataImport::IsValidToken Method</span></span>
<span data-ttu-id="c51c5-103">Belirtilen belirteç kod nesnesi için geçerli bir başvuru tutan olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="c51c5-103">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c51c5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c51c5-104">Syntax</span></span>  
  
```  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c51c5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c51c5-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="c51c5-106">[in] İçin başvuru geçerliliğini denetlemek için belirteç.</span><span class="sxs-lookup"><span data-stu-id="c51c5-106">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c51c5-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c51c5-107">Return Value</span></span>  
 <span data-ttu-id="c51c5-108">`true` varsa `tk` geçerli kapsam içinde bir geçerli meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="c51c5-108">`true` if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="c51c5-109">Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="c51c5-109">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c51c5-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c51c5-110">Requirements</span></span>  
 <span data-ttu-id="c51c5-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c51c5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c51c5-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="c51c5-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c51c5-113">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c51c5-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c51c5-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c51c5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c51c5-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c51c5-115">See also</span></span>
- [<span data-ttu-id="c51c5-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c51c5-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c51c5-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c51c5-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
