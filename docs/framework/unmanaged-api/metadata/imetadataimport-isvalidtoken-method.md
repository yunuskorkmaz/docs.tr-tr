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
ms.openlocfilehash: d752d6dbe8a6b7a23faae498f9118c8d89e92929
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447703"
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="f909a-102">IMetaDataImport::IsValidToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f909a-102">IMetaDataImport::IsValidToken Method</span></span>
<span data-ttu-id="f909a-103">Belirtilen belirteç kodu nesnesi için geçerli bir başvuru tutan olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="f909a-103">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f909a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f909a-104">Syntax</span></span>  
  
```  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f909a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f909a-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="f909a-106">[in] Başvuru geçerliliğini denetlemek için belirteci.</span><span class="sxs-lookup"><span data-stu-id="f909a-106">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f909a-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f909a-107">Return Value</span></span>  
 <span data-ttu-id="f909a-108">`true` varsa `tk` geçerli kapsam içinde geçerli meta veri belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="f909a-108">`true` if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="f909a-109">Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="f909a-109">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f909a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f909a-110">Requirements</span></span>  
 <span data-ttu-id="f909a-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f909a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f909a-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f909a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f909a-113">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f909a-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f909a-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f909a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f909a-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f909a-115">See Also</span></span>  
 [<span data-ttu-id="f909a-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f909a-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="f909a-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f909a-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
