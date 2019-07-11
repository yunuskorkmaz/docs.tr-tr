---
title: IMetaDataImport::EnumMethodSemantics Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodSemantics
helpviewer_keywords:
- EnumMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::EnumMethodSemantics method [.NET Framework metadata]
ms.assetid: e7e3c630-9691-46d6-94df-b5593a7bb08a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 715e53ae04532214d4011d4a40503b2ade5a014d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782067"
---
# <a name="imetadataimportenummethodsemantics-method"></a><span data-ttu-id="89529-102">IMetaDataImport::EnumMethodSemantics Yöntemi</span><span class="sxs-lookup"><span data-stu-id="89529-102">IMetaDataImport::EnumMethodSemantics Method</span></span>
<span data-ttu-id="89529-103">Özellikler ve belirtilen yöntem ilgili olduğu özellik değiştirme olayları numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="89529-103">Enumerates the properties and the property-change events to which the specified method is related.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89529-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89529-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,   
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89529-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="89529-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="89529-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="89529-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="89529-107">Bu, bu yöntemin ilk çağrı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="89529-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="89529-108">[in] Numaralandırma kapsamını sınırlar MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="89529-108">[in] A MethodDef token that limits the scope of the enumeration.</span></span>  
  
 `rEventProp`  
 <span data-ttu-id="89529-109">[out] Özellikleri ve olayları depolamak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="89529-109">[out] The array used to store the events or properties.</span></span>  
  
 `cMax`  
 <span data-ttu-id="89529-110">[in] En büyük boyutunu `rEventProp` dizisi.</span><span class="sxs-lookup"><span data-stu-id="89529-110">[in] The maximum size of the `rEventProp` array.</span></span>  
  
 `pcEventProp`  
 <span data-ttu-id="89529-111">[out] Olaylar veya özellikler döndürülen sayısını `rEventProp`.</span><span class="sxs-lookup"><span data-stu-id="89529-111">[out] The number of events or properties returned in `rEventProp`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89529-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="89529-112">Return Value</span></span>  
  
|<span data-ttu-id="89529-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="89529-113">HRESULT</span></span>|<span data-ttu-id="89529-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89529-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="89529-115">`EnumMethodSemantics` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="89529-115">`EnumMethodSemantics` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="89529-116">Olay veya listelemek için özellikler vardır.</span><span class="sxs-lookup"><span data-stu-id="89529-116">There are no events or properties to enumerate.</span></span> <span data-ttu-id="89529-117">Bu durumda, `pcEventProp` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="89529-117">In that case, `pcEventProp` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89529-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="89529-118">Remarks</span></span>  
 <span data-ttu-id="89529-119">Birçok ortak dil çalışma zamanı tür tanımlama *özelliği* `Changed` olayları ve `On` *özelliği* `Changed` ilgili özellikleri için yöntemler.</span><span class="sxs-lookup"><span data-stu-id="89529-119">Many common language runtime types define *Property*`Changed` events and `On`*Property*`Changed` methods related to their properties.</span></span> <span data-ttu-id="89529-120">Örneğin, <xref:System.Windows.Forms.Control?displayProperty=nameWithType> türünü tanımlayan bir <xref:System.Windows.Forms.Control.Font%2A> özelliği, bir <xref:System.Windows.Forms.Control.FontChanged> olayı ve bir <xref:System.Windows.Forms.Control.OnFontChanged%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="89529-120">For example, the <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type defines a <xref:System.Windows.Forms.Control.Font%2A> property, a <xref:System.Windows.Forms.Control.FontChanged> event, and an <xref:System.Windows.Forms.Control.OnFontChanged%2A> method.</span></span> <span data-ttu-id="89529-121">Ayarlama erişimcisi yöntemi <xref:System.Windows.Forms.Control.Font%2A> özellik çağrılarında <xref:System.Windows.Forms.Control.OnFontChanged%2A> sırayla başlatır yöntemi <xref:System.Windows.Forms.Control.FontChanged> olay.</span><span class="sxs-lookup"><span data-stu-id="89529-121">The set accessor method of the <xref:System.Windows.Forms.Control.Font%2A> property calls <xref:System.Windows.Forms.Control.OnFontChanged%2A> method, which in turn raises the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span> <span data-ttu-id="89529-122">Çağrı yapıyordu `EnumMethodSemantics` için MethodDef kullanarak <xref:System.Windows.Forms.Control.OnFontChanged%2A> başvurularını almak için <xref:System.Windows.Forms.Control.Font%2A> özelliği ve <xref:System.Windows.Forms.Control.FontChanged> olay.</span><span class="sxs-lookup"><span data-stu-id="89529-122">You would call `EnumMethodSemantics` using the MethodDef for <xref:System.Windows.Forms.Control.OnFontChanged%2A> to get references to the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89529-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="89529-123">Requirements</span></span>  
 <span data-ttu-id="89529-124">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89529-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89529-125">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="89529-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="89529-126">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="89529-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="89529-127">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89529-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89529-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89529-128">See also</span></span>

- [<span data-ttu-id="89529-129">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="89529-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="89529-130">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="89529-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
