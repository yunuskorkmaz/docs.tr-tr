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
ms.openlocfilehash: 3a99ed42f500b83b5109631b21a88029995b43d6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777474"
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="1e120-102">IMetaDataImport::IsValidToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e120-102">IMetaDataImport::IsValidToken Method</span></span>
<span data-ttu-id="1e120-103">Belirtilen belirteç kod nesnesi için geçerli bir başvuru tutan olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="1e120-103">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e120-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1e120-104">Syntax</span></span>  
  
```  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e120-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1e120-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="1e120-106">[in] İçin başvuru geçerliliğini denetlemek için belirteç.</span><span class="sxs-lookup"><span data-stu-id="1e120-106">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e120-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1e120-107">Return Value</span></span>  
 <span data-ttu-id="1e120-108">`true` varsa `tk` geçerli kapsam içinde bir geçerli meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="1e120-108">`true` if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="1e120-109">Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="1e120-109">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e120-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1e120-110">Requirements</span></span>  
 <span data-ttu-id="1e120-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e120-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e120-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="1e120-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1e120-113">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1e120-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1e120-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e120-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e120-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e120-115">See also</span></span>

- [<span data-ttu-id="1e120-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e120-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="1e120-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e120-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
