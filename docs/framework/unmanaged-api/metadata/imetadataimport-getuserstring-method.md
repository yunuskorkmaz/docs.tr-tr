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
ms.openlocfilehash: 358ca84f32e1b233116605bf5486cc9a01b42e67
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503516"
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="fe7f2-102">IMetaDataImport::GetUserString Metodu</span><span class="sxs-lookup"><span data-stu-id="fe7f2-102">IMetaDataImport::GetUserString Method</span></span>
<span data-ttu-id="fe7f2-103">Belirtilen meta veri belirteci tarafından temsil edilen sabit dizeyi alır.</span><span class="sxs-lookup"><span data-stu-id="fe7f2-103">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe7f2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fe7f2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe7f2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fe7f2-105">Parameters</span></span>  
 `stk`  
 <span data-ttu-id="fe7f2-106">'ndaki İçin ilişkili dizeyi döndürecek dize belirteci.</span><span class="sxs-lookup"><span data-stu-id="fe7f2-106">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="fe7f2-107">dışı İstenen dizenin bir kopyası.</span><span class="sxs-lookup"><span data-stu-id="fe7f2-107">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="fe7f2-108">'ndaki İstenen geniş karakterdeki boyut üst sınırı `szString` .</span><span class="sxs-lookup"><span data-stu-id="fe7f2-108">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="fe7f2-109">dışı Döndürülen geniş karakterdeki boyut `szString` .</span><span class="sxs-lookup"><span data-stu-id="fe7f2-109">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe7f2-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe7f2-110">Requirements</span></span>  
 <span data-ttu-id="fe7f2-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe7f2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe7f2-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="fe7f2-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fe7f2-113">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="fe7f2-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fe7f2-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe7f2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe7f2-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe7f2-115">See also</span></span>

- [<span data-ttu-id="fe7f2-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe7f2-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="fe7f2-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe7f2-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
