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
ms.openlocfilehash: f20652a7f86576e64646a1f63c3e2c48b55cf811
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175466"
---
# <a name="imetadataimportenummethodsemantics-method"></a><span data-ttu-id="9a447-102">IMetaDataImport::EnumMethodSemantics Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9a447-102">IMetaDataImport::EnumMethodSemantics Method</span></span>
<span data-ttu-id="9a447-103">Belirtilen yöntemin ilişkili olduğu özellikleri ve özellik değiştirme olaylarını günceller.</span><span class="sxs-lookup"><span data-stu-id="9a447-103">Enumerates the properties and the property-change events to which the specified method is related.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a447-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a447-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a447-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9a447-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="9a447-106">[içinde, dışarı] Sayıya işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="9a447-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="9a447-107">Bu yöntemin ilk araması için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9a447-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="9a447-108">[içinde] Numaralandırmakapsamını sınırlayan bir MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="9a447-108">[in] A MethodDef token that limits the scope of the enumeration.</span></span>  
  
 `rEventProp`  
 <span data-ttu-id="9a447-109">[çıkış] Olayları veya özellikleri depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="9a447-109">[out] The array used to store the events or properties.</span></span>  
  
 `cMax`  
 <span data-ttu-id="9a447-110">[içinde] `rEventProp` Dizinin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="9a447-110">[in] The maximum size of the `rEventProp` array.</span></span>  
  
 `pcEventProp`  
 <span data-ttu-id="9a447-111">[çıkış] Döndürülen olay veya özellik `rEventProp`sayısı.</span><span class="sxs-lookup"><span data-stu-id="9a447-111">[out] The number of events or properties returned in `rEventProp`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a447-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9a447-112">Return Value</span></span>  
  
|<span data-ttu-id="9a447-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9a447-113">HRESULT</span></span>|<span data-ttu-id="9a447-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a447-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="9a447-115">`EnumMethodSemantics`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="9a447-115">`EnumMethodSemantics` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="9a447-116">Sayısala'da olay veya özellik yoktur.</span><span class="sxs-lookup"><span data-stu-id="9a447-116">There are no events or properties to enumerate.</span></span> <span data-ttu-id="9a447-117">Bu durumda, `pcEventProp` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="9a447-117">In that case, `pcEventProp` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a447-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a447-118">Remarks</span></span>  
 <span data-ttu-id="9a447-119">Birçok yaygın dil çalışma *Property* `Changed` zamanı `On`türleri, özellikleriyle ilgili Özellik olayları ve *Özellik* `Changed` yöntemlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9a447-119">Many common language runtime types define *Property*`Changed` events and `On`*Property*`Changed` methods related to their properties.</span></span> <span data-ttu-id="9a447-120">Örneğin, <xref:System.Windows.Forms.Control?displayProperty=nameWithType> tür bir <xref:System.Windows.Forms.Control.Font%2A> özellik, bir <xref:System.Windows.Forms.Control.FontChanged> olay ve <xref:System.Windows.Forms.Control.OnFontChanged%2A> bir yöntem tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9a447-120">For example, the <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type defines a <xref:System.Windows.Forms.Control.Font%2A> property, a <xref:System.Windows.Forms.Control.FontChanged> event, and an <xref:System.Windows.Forms.Control.OnFontChanged%2A> method.</span></span> <span data-ttu-id="9a447-121">Özellik arama <xref:System.Windows.Forms.Control.Font%2A> <xref:System.Windows.Forms.Control.OnFontChanged%2A> yönteminin ayarlı erişimci yöntemi, <xref:System.Windows.Forms.Control.FontChanged> sırayla olayı yükseltir.</span><span class="sxs-lookup"><span data-stu-id="9a447-121">The set accessor method of the <xref:System.Windows.Forms.Control.Font%2A> property calls <xref:System.Windows.Forms.Control.OnFontChanged%2A> method, which in turn raises the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span> <span data-ttu-id="9a447-122">Özellik ve `EnumMethodSemantics` <xref:System.Windows.Forms.Control.FontChanged> olay başvuruları <xref:System.Windows.Forms.Control.OnFontChanged%2A> almak için MethodDef kullanarak aramak istiyorsunuz. <xref:System.Windows.Forms.Control.Font%2A></span><span class="sxs-lookup"><span data-stu-id="9a447-122">You would call `EnumMethodSemantics` using the MethodDef for <xref:System.Windows.Forms.Control.OnFontChanged%2A> to get references to the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a447-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9a447-123">Requirements</span></span>  
 <span data-ttu-id="9a447-124">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a447-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a447-125">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9a447-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9a447-126">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="9a447-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9a447-127">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a447-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a447-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a447-128">See also</span></span>

- [<span data-ttu-id="9a447-129">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9a447-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="9a447-130">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9a447-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
