---
title: IMetaDataImport::EnumFields Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFields
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFields
helpviewer_keywords:
- EnumFields method [.NET Framework metadata]
- IMetaDataImport::EnumFields method [.NET Framework metadata]
ms.assetid: 1d23247e-c58c-45db-afd8-83aa89cde18e
topic_type:
- apiref
ms.openlocfilehash: 74035e9551cb1d622b326e511c3884e1eadf057f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711604"
---
# <a name="imetadataimportenumfields-method"></a><span data-ttu-id="024ba-102">IMetaDataImport::EnumFields Yöntemi</span><span class="sxs-lookup"><span data-stu-id="024ba-102">IMetaDataImport::EnumFields Method</span></span>

<span data-ttu-id="024ba-103">Belirtilen TypeDef belirtecinin başvurduğu tür için FieldDef belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="024ba-103">Enumerates FieldDef tokens for the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="024ba-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="024ba-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFields (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   cl,
   [out]     mdFieldDef  rFields[],
   [in]      ULONG       cMax,
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="024ba-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="024ba-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="024ba-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="024ba-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="024ba-107">'ndaki Alanları Numaralandırılacak olan sınıfın TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="024ba-107">[in] The TypeDef token of the class whose fields are to be enumerated.</span></span>  
  
 `rFields`  
 <span data-ttu-id="024ba-108">dışı FieldDef belirteçlerinin listesi.</span><span class="sxs-lookup"><span data-stu-id="024ba-108">[out] The list of FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="024ba-109">'ndaki Dizinin en büyük boyutu `rFields` .</span><span class="sxs-lookup"><span data-stu-id="024ba-109">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="024ba-110">dışı İçinde döndürülen FieldDef belirteçlerinin gerçek sayısı `rFields` .</span><span class="sxs-lookup"><span data-stu-id="024ba-110">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="024ba-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="024ba-111">Return Value</span></span>  
  
|<span data-ttu-id="024ba-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="024ba-112">HRESULT</span></span>|<span data-ttu-id="024ba-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="024ba-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="024ba-114">`EnumFields` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="024ba-114">`EnumFields` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="024ba-115">Numaralandırılacak alan yok.</span><span class="sxs-lookup"><span data-stu-id="024ba-115">There are no fields to enumerate.</span></span> <span data-ttu-id="024ba-116">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="024ba-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="024ba-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="024ba-117">Requirements</span></span>  

 <span data-ttu-id="024ba-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="024ba-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="024ba-119">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="024ba-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="024ba-120">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="024ba-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="024ba-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="024ba-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="024ba-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="024ba-122">See also</span></span>

- [<span data-ttu-id="024ba-123">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="024ba-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="024ba-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="024ba-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
