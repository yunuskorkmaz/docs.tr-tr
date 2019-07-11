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
ms.openlocfilehash: edeaefd0792a5cc03ae6d4385ff669a343ffdfc9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778812"
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="89de5-102">IMetaDataImport::GetUserString Metodu</span><span class="sxs-lookup"><span data-stu-id="89de5-102">IMetaDataImport::GetUserString Method</span></span>
<span data-ttu-id="89de5-103">Belirtilen meta veri belirteci tarafından temsil edilen sabit dizesini alır.</span><span class="sxs-lookup"><span data-stu-id="89de5-103">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89de5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89de5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89de5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="89de5-105">Parameters</span></span>  
 `stk`  
 <span data-ttu-id="89de5-106">[in] İlişkili dize için döndürülecek dize belirteci.</span><span class="sxs-lookup"><span data-stu-id="89de5-106">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="89de5-107">[out] İstenen dizenin bir kopyası.</span><span class="sxs-lookup"><span data-stu-id="89de5-107">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="89de5-108">[in] Geniş karakter istenen cinsinden en büyük boyutu `szString`.</span><span class="sxs-lookup"><span data-stu-id="89de5-108">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="89de5-109">[out] Geniş karakterler döndürülen boyutu `szString`.</span><span class="sxs-lookup"><span data-stu-id="89de5-109">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89de5-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="89de5-110">Requirements</span></span>  
 <span data-ttu-id="89de5-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89de5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89de5-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="89de5-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="89de5-113">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="89de5-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="89de5-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89de5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89de5-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89de5-115">See also</span></span>

- [<span data-ttu-id="89de5-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="89de5-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="89de5-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="89de5-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
