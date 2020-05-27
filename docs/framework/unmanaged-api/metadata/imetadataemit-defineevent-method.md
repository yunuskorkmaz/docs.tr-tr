---
title: IMetaDataEmit::DefineEvent Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineEvent
helpviewer_keywords:
- IMetaDataEmit::DefineEvent method [.NET Framework metadata]
- DefineEvent method [.NET Framework metadata]
ms.assetid: cf064bac-9a9f-41c5-9e1d-108ff7af3afe
topic_type:
- apiref
ms.openlocfilehash: 7babd0a90b9882acb03b6360753f55c57a399b9e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005641"
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="c7ae1-102">IMetaDataEmit::DefineEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c7ae1-102">IMetaDataEmit::DefineEvent Method</span></span>
<span data-ttu-id="c7ae1-103">Belirtilen meta veri imzasıyla bir olay tanımı oluşturur ve bu olay tanımına bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="c7ae1-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7ae1-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c7ae1-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineEvent (
    [in]  mdTypeDef    td,
    [in]  LPCWSTR      szEvent,
    [in]  DWORD        dwEventFlags,
    [in]  mdToken      tkEventType,
    [in]  mdMethodDef  mdAddOn,
    [in]  mdMethodDef  mdRemoveOn,
    [in]  mdMethodDef  mdFire,
    [in]  mdMethodDef  rmdOtherMethods[],
    [out] mdEvent      *pmdEvent
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7ae1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c7ae1-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="c7ae1-106">'ndaki Hedef sınıf veya arabirim için belirteç.</span><span class="sxs-lookup"><span data-stu-id="c7ae1-106">[in] The token for the target class or interface.</span></span> <span data-ttu-id="c7ae1-107">Bu bir ya da `mdTypeDef` `mdTypeDefNil` token.</span><span class="sxs-lookup"><span data-stu-id="c7ae1-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="c7ae1-108">'ndaki Etkinliğin adı.</span><span class="sxs-lookup"><span data-stu-id="c7ae1-108">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="c7ae1-109">'ndaki Olay bayrakları.</span><span class="sxs-lookup"><span data-stu-id="c7ae1-109">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="c7ae1-110">'ndaki Olay sınıfı için belirteç.</span><span class="sxs-lookup"><span data-stu-id="c7ae1-110">[in] The token for the event class.</span></span> <span data-ttu-id="c7ae1-111">Bu bir, `mdTypeDef` veya bir `mdTypeRef` `mdTokenNil` belirteçtir.</span><span class="sxs-lookup"><span data-stu-id="c7ae1-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="c7ae1-112">'ndaki Olaya abone olmak için kullanılan yöntem veya null.</span><span class="sxs-lookup"><span data-stu-id="c7ae1-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="c7ae1-113">'ndaki Olayın aboneliğini kaldırmak için kullanılan yöntem veya null.</span><span class="sxs-lookup"><span data-stu-id="c7ae1-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="c7ae1-114">'ndaki Olayı yükseltmek için kullanılan Yöntem (türetilmiş bir sınıf tarafından).</span><span class="sxs-lookup"><span data-stu-id="c7ae1-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="c7ae1-115">'ndaki Olayla ilişkili diğer yöntemler için bir belirteç dizisi.</span><span class="sxs-lookup"><span data-stu-id="c7ae1-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="c7ae1-116">Dizi bir `mdMethodDefNil` belirteçle sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="c7ae1-116">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="c7ae1-117">dışı Olaya atanan meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="c7ae1-117">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7ae1-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7ae1-118">Requirements</span></span>  
 <span data-ttu-id="c7ae1-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7ae1-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7ae1-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c7ae1-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c7ae1-121">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="c7ae1-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c7ae1-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7ae1-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7ae1-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7ae1-123">See also</span></span>

- [<span data-ttu-id="c7ae1-124">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7ae1-124">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="c7ae1-125">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7ae1-125">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
