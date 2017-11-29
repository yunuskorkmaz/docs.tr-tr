---
title: IMetaDataImport::GetNameFromToken Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetNameFromToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetNameFromToken
helpviewer_keywords:
- GetNameFromToken method [.NET Framework metadata]
- IMetaDataImport::GetNameFromToken method [.NET Framework metadata]
ms.assetid: 32114ecf-8916-4ab2-a201-179c017344f1
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e77954d5730417a005c6c1ac07fa171bd0f1b13a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetnamefromtoken-method"></a><span data-ttu-id="1623f-102">IMetaDataImport::GetNameFromToken Metodu</span><span class="sxs-lookup"><span data-stu-id="1623f-102">IMetaDataImport::GetNameFromToken Method</span></span>
<span data-ttu-id="1623f-103">Belirtilen meta veri simgesi tarafından başvurulan nesne UTF-8 adını alır.</span><span class="sxs-lookup"><span data-stu-id="1623f-103">Gets the UTF-8 name of the object referenced by the specified metadata token.</span></span> <span data-ttu-id="1623f-104">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="1623f-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1623f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1623f-105">Syntax</span></span>  
  
```  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1623f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1623f-106">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="1623f-107">[in] Adını döndürmek için nesneyi gösteren belirteci.</span><span class="sxs-lookup"><span data-stu-id="1623f-107">[in] The token representing the object to return the name for.</span></span>  
  
 `pszUtf8NamePtr`  
 <span data-ttu-id="1623f-108">[out] Bir işaretçi yığınındaki UTF-8 nesne adı.</span><span class="sxs-lookup"><span data-stu-id="1623f-108">[out] A pointer to the UTF-8 object name in the heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1623f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1623f-109">Remarks</span></span>  
 <span data-ttu-id="1623f-110">`GetNameFromToken`Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="1623f-110">`GetNameFromToken` is obsolete.</span></span> <span data-ttu-id="1623f-111">Alternatif olarak, belirtecin gerekli, gibi belirli türü özelliklerini almak için bir yöntem çağrısı `GetFieldProps` bir alan için veya `GetMethodProps` bir yöntem için.</span><span class="sxs-lookup"><span data-stu-id="1623f-111">As an alternative, call a method to get the properties of the particular type of token required, such as `GetFieldProps` for a field or `GetMethodProps` for a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1623f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1623f-112">Requirements</span></span>  
 <span data-ttu-id="1623f-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1623f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1623f-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1623f-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1623f-115">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1623f-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1623f-116">**.NET framework sürümleri:** 1.0</span><span class="sxs-lookup"><span data-stu-id="1623f-116">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1623f-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1623f-117">See Also</span></span>  
 [<span data-ttu-id="1623f-118">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="1623f-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="1623f-119">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="1623f-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
