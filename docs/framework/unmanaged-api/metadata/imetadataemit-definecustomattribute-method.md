---
description: 'Şu konuda daha fazla bilgi edinin: ımetadatayayma::D efineCustomAttribute yöntemi'
title: IMetaDataEmit::DefineCustomAttribute Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineCustomAttribute
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineCustomAttribute
helpviewer_keywords:
- DefineCustomAttribute method [.NET Framework metadata]
- IMetaDataEmit::DefineCustomAttribute method [.NET Framework metadata]
ms.assetid: 7dd14854-b756-4401-b167-88ca576dc8f0
topic_type:
- apiref
ms.openlocfilehash: 5d802f590525b8b398ac270b1b7f59d122b45b73
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753490"
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="d1353-103">IMetaDataEmit::DefineCustomAttribute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d1353-103">IMetaDataEmit::DefineCustomAttribute Method</span></span>

<span data-ttu-id="d1353-104">Belirtilen nesneye iliştirililmesi için belirtilen meta veri imzasına sahip özel bir öznitelik için bir tanım oluşturur ve bu özel öznitelik tanımına bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="d1353-104">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1353-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d1353-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineCustomAttribute (
    [in]  mdToken     tkObj,
    [in]  mdToken     tkType,
    [in]  void const  *pCustomAttribute,
    [in]  ULONG       cbCustomAttribute,
    [out] mdCustomAttribute *pcv
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1353-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d1353-106">Parameters</span></span>  

 `tkObj`  
 <span data-ttu-id="d1353-107">'ndaki Sahip öğesi için belirteç.</span><span class="sxs-lookup"><span data-stu-id="d1353-107">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="d1353-108">'ndaki Özel özniteliği tanımlayan belirteç.</span><span class="sxs-lookup"><span data-stu-id="d1353-108">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="d1353-109">'ndaki Özel özniteliğe yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d1353-109">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="d1353-110">'ndaki İçindeki bayt sayısı `pCustomAttribute` .</span><span class="sxs-lookup"><span data-stu-id="d1353-110">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="d1353-111">dışı `mdCustomAttribute` Atanan belirteç.</span><span class="sxs-lookup"><span data-stu-id="d1353-111">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1353-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d1353-112">Requirements</span></span>  

 <span data-ttu-id="d1353-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1353-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1353-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d1353-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d1353-115">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="d1353-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d1353-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1353-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1353-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1353-117">See also</span></span>

- [<span data-ttu-id="d1353-118">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d1353-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="d1353-119">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d1353-119">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
