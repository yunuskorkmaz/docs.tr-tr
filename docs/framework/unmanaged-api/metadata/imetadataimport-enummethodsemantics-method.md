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
ms.openlocfilehash: 16cfa6df6251cd67860155cb8092e77a835eaaef
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223276"
---
# <a name="imetadataimportenummethodsemantics-method"></a><span data-ttu-id="a5554-102">IMetaDataImport::EnumMethodSemantics Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a5554-102">IMetaDataImport::EnumMethodSemantics Method</span></span>
<span data-ttu-id="a5554-103">Özellikler ve belirtilen yöntem ilgili olduğu özellik değiştirme olayları numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="a5554-103">Enumerates the properties and the property-change events to which the specified method is related.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5554-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a5554-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,   
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5554-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a5554-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="a5554-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a5554-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="a5554-107">Bu, bu yöntemin ilk çağrı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a5554-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="a5554-108">[in] Numaralandırma kapsamını sınırlar MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="a5554-108">[in] A MethodDef token that limits the scope of the enumeration.</span></span>  
  
 `rEventProp`  
 <span data-ttu-id="a5554-109">[out] Özellikleri ve olayları depolamak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="a5554-109">[out] The array used to store the events or properties.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a5554-110">[in] En büyük boyutunu `rEventProp` dizisi.</span><span class="sxs-lookup"><span data-stu-id="a5554-110">[in] The maximum size of the `rEventProp` array.</span></span>  
  
 `pcEventProp`  
 <span data-ttu-id="a5554-111">[out] Olaylar veya özellikler döndürülen sayısını `rEventProp`.</span><span class="sxs-lookup"><span data-stu-id="a5554-111">[out] The number of events or properties returned in `rEventProp`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a5554-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a5554-112">Return Value</span></span>  
  
|<span data-ttu-id="a5554-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a5554-113">HRESULT</span></span>|<span data-ttu-id="a5554-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a5554-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSemantics` <span data-ttu-id="a5554-115">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a5554-115">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a5554-116">Olay veya listelemek için özellikler vardır.</span><span class="sxs-lookup"><span data-stu-id="a5554-116">There are no events or properties to enumerate.</span></span> <span data-ttu-id="a5554-117">Bu durumda, `pcEventProp` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="a5554-117">In that case, `pcEventProp` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5554-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a5554-118">Remarks</span></span>  
 <span data-ttu-id="a5554-119">Birçok ortak dil çalışma zamanı tür tanımlama *özelliği* `Changed` olayları ve `On` *özelliği* `Changed` ilgili özellikleri için yöntemler.</span><span class="sxs-lookup"><span data-stu-id="a5554-119">Many common language runtime types define *Property*`Changed` events and `On`*Property*`Changed` methods related to their properties.</span></span> <span data-ttu-id="a5554-120">Örneğin, <xref:System.Windows.Forms.Control?displayProperty=nameWithType> türünü tanımlayan bir <xref:System.Windows.Forms.Control.Font%2A> özelliği, bir <xref:System.Windows.Forms.Control.FontChanged> olayı ve bir <xref:System.Windows.Forms.Control.OnFontChanged%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a5554-120">For example, the <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type defines a <xref:System.Windows.Forms.Control.Font%2A> property, a <xref:System.Windows.Forms.Control.FontChanged> event, and an <xref:System.Windows.Forms.Control.OnFontChanged%2A> method.</span></span> <span data-ttu-id="a5554-121">Ayarlama erişimcisi yöntemi <xref:System.Windows.Forms.Control.Font%2A> özellik çağrılarında <xref:System.Windows.Forms.Control.OnFontChanged%2A> sırayla başlatır yöntemi <xref:System.Windows.Forms.Control.FontChanged> olay.</span><span class="sxs-lookup"><span data-stu-id="a5554-121">The set accessor method of the <xref:System.Windows.Forms.Control.Font%2A> property calls <xref:System.Windows.Forms.Control.OnFontChanged%2A> method, which in turn raises the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span> <span data-ttu-id="a5554-122">Çağrı yapıyordu `EnumMethodSemantics` için MethodDef kullanarak <xref:System.Windows.Forms.Control.OnFontChanged%2A> başvurularını almak için <xref:System.Windows.Forms.Control.Font%2A> özelliği ve <xref:System.Windows.Forms.Control.FontChanged> olay.</span><span class="sxs-lookup"><span data-stu-id="a5554-122">You would call `EnumMethodSemantics` using the MethodDef for <xref:System.Windows.Forms.Control.OnFontChanged%2A> to get references to the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5554-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a5554-123">Requirements</span></span>  
 <span data-ttu-id="a5554-124">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5554-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5554-125">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="a5554-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a5554-126">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="a5554-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="a5554-127">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="a5554-127">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a5554-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5554-128">See also</span></span>

- [<span data-ttu-id="a5554-129">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a5554-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="a5554-130">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a5554-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
