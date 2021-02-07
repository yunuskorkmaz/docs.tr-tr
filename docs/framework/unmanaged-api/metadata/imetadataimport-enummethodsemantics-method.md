---
description: ': IMetaDataImport:: Enummethodsemantiği yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 9819afb2d7974e9f705c6ff665d3414eade0ab90
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728291"
---
# <a name="imetadataimportenummethodsemantics-method"></a><span data-ttu-id="e646d-103">IMetaDataImport::EnumMethodSemantics Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e646d-103">IMetaDataImport::EnumMethodSemantics Method</span></span>

<span data-ttu-id="e646d-104">Belirtilen yöntemin ilişkili olduğu özellikleri ve özellik değiştirme olaylarını sıralar.</span><span class="sxs-lookup"><span data-stu-id="e646d-104">Enumerates the properties and the property-change events to which the specified method is related.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e646d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e646d-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e646d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e646d-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="e646d-107">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e646d-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="e646d-108">Bu yöntemin ilk çağrısı için bu NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e646d-108">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="e646d-109">'ndaki Sabit listesinin kapsamını sınırlayan bir MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="e646d-109">[in] A MethodDef token that limits the scope of the enumeration.</span></span>  
  
 `rEventProp`  
 <span data-ttu-id="e646d-110">dışı Olayları veya özellikleri depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="e646d-110">[out] The array used to store the events or properties.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e646d-111">'ndaki Dizinin en büyük boyutu `rEventProp` .</span><span class="sxs-lookup"><span data-stu-id="e646d-111">[in] The maximum size of the `rEventProp` array.</span></span>  
  
 `pcEventProp`  
 <span data-ttu-id="e646d-112">dışı İçinde döndürülen olay veya özellik sayısı `rEventProp` .</span><span class="sxs-lookup"><span data-stu-id="e646d-112">[out] The number of events or properties returned in `rEventProp`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e646d-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e646d-113">Return Value</span></span>  
  
|<span data-ttu-id="e646d-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e646d-114">HRESULT</span></span>|<span data-ttu-id="e646d-115">Description</span><span class="sxs-lookup"><span data-stu-id="e646d-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e646d-116">`EnumMethodSemantics` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e646d-116">`EnumMethodSemantics` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e646d-117">Numaralandırılacak hiçbir olay veya özellik yok.</span><span class="sxs-lookup"><span data-stu-id="e646d-117">There are no events or properties to enumerate.</span></span> <span data-ttu-id="e646d-118">Bu durumda, `pcEventProp` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="e646d-118">In that case, `pcEventProp` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e646d-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e646d-119">Remarks</span></span>  

 <span data-ttu-id="e646d-120">Birçok ortak dil çalışma zamanı türü  `Changed` , özellikleriyle ilgili özellik olaylarını ve `On` *özellik* `Changed` yöntemlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e646d-120">Many common language runtime types define *Property*`Changed` events and `On`*Property*`Changed` methods related to their properties.</span></span> <span data-ttu-id="e646d-121">Örneğin, <xref:System.Windows.Forms.Control?displayProperty=nameWithType> türü bir <xref:System.Windows.Forms.Control.Font%2A> özelliği, bir <xref:System.Windows.Forms.Control.FontChanged> olayı ve bir <xref:System.Windows.Forms.Control.OnFontChanged%2A> yöntemini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e646d-121">For example, the <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type defines a <xref:System.Windows.Forms.Control.Font%2A> property, a <xref:System.Windows.Forms.Control.FontChanged> event, and an <xref:System.Windows.Forms.Control.OnFontChanged%2A> method.</span></span> <span data-ttu-id="e646d-122">Özellik çağrıları yönteminin ayarlama erişimcisi yöntemi <xref:System.Windows.Forms.Control.Font%2A> <xref:System.Windows.Forms.Control.OnFontChanged%2A> , bu da <xref:System.Windows.Forms.Control.FontChanged> olayı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e646d-122">The set accessor method of the <xref:System.Windows.Forms.Control.Font%2A> property calls <xref:System.Windows.Forms.Control.OnFontChanged%2A> method, which in turn raises the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span> <span data-ttu-id="e646d-123">`EnumMethodSemantics` <xref:System.Windows.Forms.Control.OnFontChanged%2A> Özelliğine ve olayına başvuru almak için MethodDef kullanarak öğesini çağırın <xref:System.Windows.Forms.Control.Font%2A> <xref:System.Windows.Forms.Control.FontChanged> .</span><span class="sxs-lookup"><span data-stu-id="e646d-123">You would call `EnumMethodSemantics` using the MethodDef for <xref:System.Windows.Forms.Control.OnFontChanged%2A> to get references to the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e646d-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e646d-124">Requirements</span></span>  

 <span data-ttu-id="e646d-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e646d-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e646d-126">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e646d-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e646d-127">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="e646d-127">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e646d-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e646d-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e646d-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e646d-129">See also</span></span>

- [<span data-ttu-id="e646d-130">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e646d-130">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="e646d-131">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e646d-131">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
