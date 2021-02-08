---
description: ': IMetaDataImport:: GetUserString metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 074d196c74be30f5879410ad44b9bb5c096eb153
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789105"
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="a190f-103">IMetaDataImport::GetUserString Metodu</span><span class="sxs-lookup"><span data-stu-id="a190f-103">IMetaDataImport::GetUserString Method</span></span>

<span data-ttu-id="a190f-104">Belirtilen meta veri belirteci tarafından temsil edilen sabit dizeyi alır.</span><span class="sxs-lookup"><span data-stu-id="a190f-104">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a190f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a190f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a190f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a190f-106">Parameters</span></span>  

 `stk`  
 <span data-ttu-id="a190f-107">'ndaki İçin ilişkili dizeyi döndürecek dize belirteci.</span><span class="sxs-lookup"><span data-stu-id="a190f-107">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="a190f-108">dışı İstenen dizenin bir kopyası.</span><span class="sxs-lookup"><span data-stu-id="a190f-108">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="a190f-109">'ndaki İstenen geniş karakterdeki boyut üst sınırı `szString` .</span><span class="sxs-lookup"><span data-stu-id="a190f-109">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="a190f-110">dışı Döndürülen geniş karakterdeki boyut `szString` .</span><span class="sxs-lookup"><span data-stu-id="a190f-110">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a190f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a190f-111">Requirements</span></span>  

 <span data-ttu-id="a190f-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a190f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a190f-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a190f-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a190f-114">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="a190f-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a190f-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a190f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a190f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a190f-116">See also</span></span>

- [<span data-ttu-id="a190f-117">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a190f-117">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="a190f-118">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a190f-118">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
