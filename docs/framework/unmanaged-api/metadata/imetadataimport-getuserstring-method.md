---
title: IMetaDataImport::GetUserString Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetUserString
helpviewer_keywords:
- IMetaDataImport::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 0fd3bb47-58b5-4083-b241-b9719df7a285
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 474338ff1780ce9b442208cd06f8b14bc411be5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447755"
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="0590a-102">IMetaDataImport::GetUserString Metodu</span><span class="sxs-lookup"><span data-stu-id="0590a-102">IMetaDataImport::GetUserString Method</span></span>
<span data-ttu-id="0590a-103">Belirtilen meta veri simgesi tarafından temsil edilen sabit değerli bir dize alır.</span><span class="sxs-lookup"><span data-stu-id="0590a-103">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0590a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0590a-104">Syntax</span></span>  
  
```  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0590a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0590a-105">Parameters</span></span>  
 `stk`  
 <span data-ttu-id="0590a-106">[in] İlişkili dizesi döndürülecek dize belirteci.</span><span class="sxs-lookup"><span data-stu-id="0590a-106">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="0590a-107">[out] İstenen dize bir kopyası.</span><span class="sxs-lookup"><span data-stu-id="0590a-107">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="0590a-108">[in] Geniş karakterler istenen en büyük boyutu `szString`.</span><span class="sxs-lookup"><span data-stu-id="0590a-108">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="0590a-109">[out] Geniş karakterler dönen boyutu `szString`.</span><span class="sxs-lookup"><span data-stu-id="0590a-109">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0590a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0590a-110">Requirements</span></span>  
 <span data-ttu-id="0590a-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0590a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0590a-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0590a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0590a-113">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="0590a-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0590a-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0590a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0590a-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0590a-115">See Also</span></span>  
 [<span data-ttu-id="0590a-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0590a-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="0590a-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0590a-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
