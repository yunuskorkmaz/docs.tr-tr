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
ms.workload: dotnet
ms.openlocfilehash: baa0c0e78f7912561b432effd2bf5503e0f06ae7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetnamefromtoken-method"></a><span data-ttu-id="66d46-102">IMetaDataImport::GetNameFromToken Metodu</span><span class="sxs-lookup"><span data-stu-id="66d46-102">IMetaDataImport::GetNameFromToken Method</span></span>
<span data-ttu-id="66d46-103">Belirtilen meta veri simgesi tarafından başvurulan nesne UTF-8 adını alır.</span><span class="sxs-lookup"><span data-stu-id="66d46-103">Gets the UTF-8 name of the object referenced by the specified metadata token.</span></span> <span data-ttu-id="66d46-104">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="66d46-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66d46-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="66d46-105">Syntax</span></span>  
  
```  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="66d46-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="66d46-106">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="66d46-107">[in] Adını döndürmek için nesneyi gösteren belirteci.</span><span class="sxs-lookup"><span data-stu-id="66d46-107">[in] The token representing the object to return the name for.</span></span>  
  
 `pszUtf8NamePtr`  
 <span data-ttu-id="66d46-108">[out] Bir işaretçi yığınındaki UTF-8 nesne adı.</span><span class="sxs-lookup"><span data-stu-id="66d46-108">[out] A pointer to the UTF-8 object name in the heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66d46-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="66d46-109">Remarks</span></span>  
 <span data-ttu-id="66d46-110">`GetNameFromToken`Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="66d46-110">`GetNameFromToken` is obsolete.</span></span> <span data-ttu-id="66d46-111">Alternatif olarak, belirtecin gerekli, gibi belirli türü özelliklerini almak için bir yöntem çağrısı `GetFieldProps` bir alan için veya `GetMethodProps` bir yöntem için.</span><span class="sxs-lookup"><span data-stu-id="66d46-111">As an alternative, call a method to get the properties of the particular type of token required, such as `GetFieldProps` for a field or `GetMethodProps` for a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66d46-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="66d46-112">Requirements</span></span>  
 <span data-ttu-id="66d46-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66d46-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66d46-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="66d46-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="66d46-115">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="66d46-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="66d46-116">**.NET framework sürümleri:** 1.0</span><span class="sxs-lookup"><span data-stu-id="66d46-116">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66d46-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="66d46-117">See Also</span></span>  
 [<span data-ttu-id="66d46-118">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="66d46-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="66d46-119">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="66d46-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
