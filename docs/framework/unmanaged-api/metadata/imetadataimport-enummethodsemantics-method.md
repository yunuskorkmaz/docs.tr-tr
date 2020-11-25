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
ms.openlocfilehash: 3d14aea92633c944d21d867c8152767ae6f1f291
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720977"
---
# <a name="imetadataimportenummethodsemantics-method"></a><span data-ttu-id="2b28d-102">IMetaDataImport::EnumMethodSemantics Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2b28d-102">IMetaDataImport::EnumMethodSemantics Method</span></span>

<span data-ttu-id="2b28d-103">Belirtilen yöntemin ilişkili olduğu özellikleri ve özellik değiştirme olaylarını sıralar.</span><span class="sxs-lookup"><span data-stu-id="2b28d-103">Enumerates the properties and the property-change events to which the specified method is related.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b28d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2b28d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b28d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2b28d-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="2b28d-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2b28d-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="2b28d-107">Bu yöntemin ilk çağrısı için bu NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b28d-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="2b28d-108">'ndaki Sabit listesinin kapsamını sınırlayan bir MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="2b28d-108">[in] A MethodDef token that limits the scope of the enumeration.</span></span>  
  
 `rEventProp`  
 <span data-ttu-id="2b28d-109">dışı Olayları veya özellikleri depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="2b28d-109">[out] The array used to store the events or properties.</span></span>  
  
 `cMax`  
 <span data-ttu-id="2b28d-110">'ndaki Dizinin en büyük boyutu `rEventProp` .</span><span class="sxs-lookup"><span data-stu-id="2b28d-110">[in] The maximum size of the `rEventProp` array.</span></span>  
  
 `pcEventProp`  
 <span data-ttu-id="2b28d-111">dışı İçinde döndürülen olay veya özellik sayısı `rEventProp` .</span><span class="sxs-lookup"><span data-stu-id="2b28d-111">[out] The number of events or properties returned in `rEventProp`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b28d-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2b28d-112">Return Value</span></span>  
  
|<span data-ttu-id="2b28d-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2b28d-113">HRESULT</span></span>|<span data-ttu-id="2b28d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b28d-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="2b28d-115">`EnumMethodSemantics` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2b28d-115">`EnumMethodSemantics` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="2b28d-116">Numaralandırılacak hiçbir olay veya özellik yok.</span><span class="sxs-lookup"><span data-stu-id="2b28d-116">There are no events or properties to enumerate.</span></span> <span data-ttu-id="2b28d-117">Bu durumda, `pcEventProp` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="2b28d-117">In that case, `pcEventProp` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b28d-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2b28d-118">Remarks</span></span>  

 <span data-ttu-id="2b28d-119">Birçok ortak dil çalışma zamanı türü *Property* `Changed` , özellikleriyle ilgili özellik olaylarını ve `On` *özellik* `Changed` yöntemlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2b28d-119">Many common language runtime types define *Property*`Changed` events and `On`*Property*`Changed` methods related to their properties.</span></span> <span data-ttu-id="2b28d-120">Örneğin, <xref:System.Windows.Forms.Control?displayProperty=nameWithType> türü bir <xref:System.Windows.Forms.Control.Font%2A> özelliği, bir <xref:System.Windows.Forms.Control.FontChanged> olayı ve bir <xref:System.Windows.Forms.Control.OnFontChanged%2A> yöntemini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2b28d-120">For example, the <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type defines a <xref:System.Windows.Forms.Control.Font%2A> property, a <xref:System.Windows.Forms.Control.FontChanged> event, and an <xref:System.Windows.Forms.Control.OnFontChanged%2A> method.</span></span> <span data-ttu-id="2b28d-121">Özellik çağrıları yönteminin ayarlama erişimcisi yöntemi <xref:System.Windows.Forms.Control.Font%2A> <xref:System.Windows.Forms.Control.OnFontChanged%2A> , bu da <xref:System.Windows.Forms.Control.FontChanged> olayı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2b28d-121">The set accessor method of the <xref:System.Windows.Forms.Control.Font%2A> property calls <xref:System.Windows.Forms.Control.OnFontChanged%2A> method, which in turn raises the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span> <span data-ttu-id="2b28d-122">`EnumMethodSemantics` <xref:System.Windows.Forms.Control.OnFontChanged%2A> Özelliğine ve olayına başvuru almak için MethodDef kullanarak öğesini çağırın <xref:System.Windows.Forms.Control.Font%2A> <xref:System.Windows.Forms.Control.FontChanged> .</span><span class="sxs-lookup"><span data-stu-id="2b28d-122">You would call `EnumMethodSemantics` using the MethodDef for <xref:System.Windows.Forms.Control.OnFontChanged%2A> to get references to the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b28d-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2b28d-123">Requirements</span></span>  

 <span data-ttu-id="2b28d-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b28d-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b28d-125">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2b28d-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2b28d-126">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="2b28d-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2b28d-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b28d-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b28d-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b28d-128">See also</span></span>

- [<span data-ttu-id="2b28d-129">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2b28d-129">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="2b28d-130">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2b28d-130">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
