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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 48055103b49b4c61bb7561f2d4aa6c8daae07ae2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62044219"
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="cfa34-102">IMetaDataEmit::DefineEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cfa34-102">IMetaDataEmit::DefineEvent Method</span></span>
<span data-ttu-id="cfa34-103">Belirtilen meta verileri imza ile bir olay için bir tanım oluşturur ve bu olay tanımı için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="cfa34-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfa34-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cfa34-104">Syntax</span></span>  
  
```  
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
  
## <a name="parameters"></a><span data-ttu-id="cfa34-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cfa34-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="cfa34-106">[in] Hedef sınıf veya arabirim için belirteç.</span><span class="sxs-lookup"><span data-stu-id="cfa34-106">[in] The token for the target class or interface.</span></span> <span data-ttu-id="cfa34-107">Bu bir `mdTypeDef` veya `mdTypeDefNil` belirteci.</span><span class="sxs-lookup"><span data-stu-id="cfa34-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="cfa34-108">[in] Olayın adı.</span><span class="sxs-lookup"><span data-stu-id="cfa34-108">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="cfa34-109">[in] Olay bayrakları.</span><span class="sxs-lookup"><span data-stu-id="cfa34-109">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="cfa34-110">[in] Olay sınıfı için belirteci.</span><span class="sxs-lookup"><span data-stu-id="cfa34-110">[in] The token for the event class.</span></span> <span data-ttu-id="cfa34-111">Bu bir `mdTypeDef`, `mdTypeRef`, veya `mdTokenNil` belirteci.</span><span class="sxs-lookup"><span data-stu-id="cfa34-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="cfa34-112">[in] Olay ya da null için abone olmak için kullanılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="cfa34-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="cfa34-113">[in] Olay ya da null için aboneliğinizi iptal etmek için kullanılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="cfa34-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="cfa34-114">[in] (Bir türetilmiş sınıf tarafından) olay oluşturmak için kullanılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="cfa34-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="cfa34-115">[in] Olay ile ilişkili diğer yöntemleri için belirteçleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="cfa34-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="cfa34-116">Dizi ile sonlandırılmış bir `mdMethodDefNil` belirteci.</span><span class="sxs-lookup"><span data-stu-id="cfa34-116">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="cfa34-117">[out] Olaya atanan meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="cfa34-117">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfa34-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cfa34-118">Requirements</span></span>  
 <span data-ttu-id="cfa34-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfa34-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfa34-120">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="cfa34-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cfa34-121">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="cfa34-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cfa34-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfa34-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfa34-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfa34-123">See also</span></span>

- [<span data-ttu-id="cfa34-124">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cfa34-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="cfa34-125">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cfa34-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
