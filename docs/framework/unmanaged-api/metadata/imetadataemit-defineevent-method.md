---
description: 'Şu konuda daha fazla bilgi edinin: ımetadatayayma::D efineEvent yöntemi'
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
ms.openlocfilehash: f96f3a5b2ed16ba83223312af82cac7688cebfa0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753477"
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="6a86c-103">IMetaDataEmit::DefineEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a86c-103">IMetaDataEmit::DefineEvent Method</span></span>

<span data-ttu-id="6a86c-104">Belirtilen meta veri imzasıyla bir olay tanımı oluşturur ve bu olay tanımına bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="6a86c-104">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a86c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a86c-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6a86c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6a86c-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="6a86c-107">'ndaki Hedef sınıf veya arabirim için belirteç.</span><span class="sxs-lookup"><span data-stu-id="6a86c-107">[in] The token for the target class or interface.</span></span> <span data-ttu-id="6a86c-108">Bu bir ya da `mdTypeDef` `mdTypeDefNil` token.</span><span class="sxs-lookup"><span data-stu-id="6a86c-108">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="6a86c-109">'ndaki Etkinliğin adı.</span><span class="sxs-lookup"><span data-stu-id="6a86c-109">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="6a86c-110">'ndaki Olay bayrakları.</span><span class="sxs-lookup"><span data-stu-id="6a86c-110">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="6a86c-111">'ndaki Olay sınıfı için belirteç.</span><span class="sxs-lookup"><span data-stu-id="6a86c-111">[in] The token for the event class.</span></span> <span data-ttu-id="6a86c-112">Bu bir, `mdTypeDef` veya bir `mdTypeRef` `mdTokenNil` belirteçtir.</span><span class="sxs-lookup"><span data-stu-id="6a86c-112">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="6a86c-113">'ndaki Olaya abone olmak için kullanılan yöntem veya null.</span><span class="sxs-lookup"><span data-stu-id="6a86c-113">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="6a86c-114">'ndaki Olayın aboneliğini kaldırmak için kullanılan yöntem veya null.</span><span class="sxs-lookup"><span data-stu-id="6a86c-114">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="6a86c-115">'ndaki Olayı yükseltmek için kullanılan Yöntem (türetilmiş bir sınıf tarafından).</span><span class="sxs-lookup"><span data-stu-id="6a86c-115">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="6a86c-116">'ndaki Olayla ilişkili diğer yöntemler için bir belirteç dizisi.</span><span class="sxs-lookup"><span data-stu-id="6a86c-116">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="6a86c-117">Dizi bir `mdMethodDefNil` belirteçle sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="6a86c-117">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="6a86c-118">dışı Olaya atanan meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="6a86c-118">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a86c-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a86c-119">Requirements</span></span>  

 <span data-ttu-id="6a86c-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a86c-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a86c-121">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6a86c-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6a86c-122">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="6a86c-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6a86c-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a86c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a86c-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a86c-124">See also</span></span>

- [<span data-ttu-id="6a86c-125">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a86c-125">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="6a86c-126">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a86c-126">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
