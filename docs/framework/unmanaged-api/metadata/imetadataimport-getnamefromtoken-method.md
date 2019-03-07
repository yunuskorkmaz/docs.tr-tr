---
title: IMetaDataImport::GetNameFromToken Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNameFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNameFromToken
helpviewer_keywords:
- GetNameFromToken method [.NET Framework metadata]
- IMetaDataImport::GetNameFromToken method [.NET Framework metadata]
ms.assetid: 32114ecf-8916-4ab2-a201-179c017344f1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1f45c89572362f380997e7d8247b93c0f8629655
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478888"
---
# <a name="imetadataimportgetnamefromtoken-method"></a><span data-ttu-id="f2997-102">IMetaDataImport::GetNameFromToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2997-102">IMetaDataImport::GetNameFromToken Method</span></span>
<span data-ttu-id="f2997-103">Belirtilen meta veri belirteci tarafından başvurulan nesne UTF-8 adını alır.</span><span class="sxs-lookup"><span data-stu-id="f2997-103">Gets the UTF-8 name of the object referenced by the specified metadata token.</span></span> <span data-ttu-id="f2997-104">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="f2997-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2997-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2997-105">Syntax</span></span>  
  
```  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2997-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f2997-106">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="f2997-107">[in] Adı döndürülecek nesne temsil eden belirteç.</span><span class="sxs-lookup"><span data-stu-id="f2997-107">[in] The token representing the object to return the name for.</span></span>  
  
 `pszUtf8NamePtr`  
 <span data-ttu-id="f2997-108">[out] Yığın UTF-8 nesnenin adına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f2997-108">[out] A pointer to the UTF-8 object name in the heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2997-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f2997-109">Remarks</span></span>  
 <span data-ttu-id="f2997-110">`GetNameFromToken` artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="f2997-110">`GetNameFromToken` is obsolete.</span></span> <span data-ttu-id="f2997-111">Alternatif olarak, belirteç gereklidir, gibi belirli türünü özelliklerini almak için bir yöntemi çağırmak `GetFieldProps` bir alanın veya `GetMethodProps` için bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="f2997-111">As an alternative, call a method to get the properties of the particular type of token required, such as `GetFieldProps` for a field or `GetMethodProps` for a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2997-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f2997-112">Requirements</span></span>  
 <span data-ttu-id="f2997-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2997-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2997-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="f2997-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f2997-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f2997-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f2997-116">**.NET framework sürümleri:** 1.0</span><span class="sxs-lookup"><span data-stu-id="f2997-116">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2997-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2997-117">See also</span></span>
- [<span data-ttu-id="f2997-118">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f2997-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="f2997-119">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f2997-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
