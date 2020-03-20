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
ms.openlocfilehash: a9598be850604f16ee8cc62187e1fed7ecf3a7e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175856"
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="6f147-102">IMetaDataEmit::DefineEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f147-102">IMetaDataEmit::DefineEvent Method</span></span>
<span data-ttu-id="6f147-103">Belirtilen meta veri imzasına sahip bir olay için tanım oluşturur ve bu olay tanımına bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="6f147-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f147-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f147-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6f147-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6f147-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="6f147-106">[içinde] Hedef sınıf veya arabirim için belirteç.</span><span class="sxs-lookup"><span data-stu-id="6f147-106">[in] The token for the target class or interface.</span></span> <span data-ttu-id="6f147-107">Bu ya `mdTypeDef` bir `mdTypeDefNil` ya da bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="6f147-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="6f147-108">[içinde] Olayın adı.</span><span class="sxs-lookup"><span data-stu-id="6f147-108">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="6f147-109">[içinde] Olay bayrakları.</span><span class="sxs-lookup"><span data-stu-id="6f147-109">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="6f147-110">[içinde] Olay sınıfının belirteci.</span><span class="sxs-lookup"><span data-stu-id="6f147-110">[in] The token for the event class.</span></span> <span data-ttu-id="6f147-111">Bu bir `mdTypeDef`, `mdTypeRef`a `mdTokenNil` , ya da bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="6f147-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="6f147-112">[içinde] Olaya abone olmak için kullanılan yöntem veya null.</span><span class="sxs-lookup"><span data-stu-id="6f147-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="6f147-113">[içinde] Olaya aboneliğini iptal etmek veya geçersiz kılmak için kullanılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="6f147-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="6f147-114">[içinde] Olayı yükseltmek için (türetilmiş bir sınıf tarafından) kullanılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="6f147-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="6f147-115">[içinde] Olayla ilişkili diğer yöntemler için bir dizi belirteç.</span><span class="sxs-lookup"><span data-stu-id="6f147-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="6f147-116">Dizi bir `mdMethodDefNil` belirteç ile sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="6f147-116">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="6f147-117">[çıkış] Olaya atanan meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="6f147-117">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f147-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f147-118">Requirements</span></span>  
 <span data-ttu-id="6f147-119">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f147-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f147-120">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6f147-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6f147-121">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="6f147-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f147-122">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f147-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f147-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f147-123">See also</span></span>

- [<span data-ttu-id="6f147-124">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6f147-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="6f147-125">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6f147-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
