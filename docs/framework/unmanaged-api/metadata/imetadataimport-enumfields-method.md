---
description: ': IMetaDataImport:: EnumFields metodu hakkında daha fazla bilgi'
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
ms.openlocfilehash: 5cb9b3a47dc4c51b9eba24b9519e4b97846c1a6d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799388"
---
# <a name="imetadataimportenumfields-method"></a><span data-ttu-id="b3964-103">IMetaDataImport::EnumFields Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b3964-103">IMetaDataImport::EnumFields Method</span></span>

<span data-ttu-id="b3964-104">Belirtilen TypeDef belirtecinin başvurduğu tür için FieldDef belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="b3964-104">Enumerates FieldDef tokens for the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3964-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b3964-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumFields (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   cl,
   [out]     mdFieldDef  rFields[],
   [in]      ULONG       cMax,
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3964-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b3964-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="b3964-107">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b3964-107">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="b3964-108">'ndaki Alanları Numaralandırılacak olan sınıfın TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="b3964-108">[in] The TypeDef token of the class whose fields are to be enumerated.</span></span>  
  
 `rFields`  
 <span data-ttu-id="b3964-109">dışı FieldDef belirteçlerinin listesi.</span><span class="sxs-lookup"><span data-stu-id="b3964-109">[out] The list of FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b3964-110">'ndaki Dizinin en büyük boyutu `rFields` .</span><span class="sxs-lookup"><span data-stu-id="b3964-110">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="b3964-111">dışı İçinde döndürülen FieldDef belirteçlerinin gerçek sayısı `rFields` .</span><span class="sxs-lookup"><span data-stu-id="b3964-111">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3964-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b3964-112">Return Value</span></span>  
  
|<span data-ttu-id="b3964-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b3964-113">HRESULT</span></span>|<span data-ttu-id="b3964-114">Description</span><span class="sxs-lookup"><span data-stu-id="b3964-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b3964-115">`EnumFields` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b3964-115">`EnumFields` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b3964-116">Numaralandırılacak alan yok.</span><span class="sxs-lookup"><span data-stu-id="b3964-116">There are no fields to enumerate.</span></span> <span data-ttu-id="b3964-117">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="b3964-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b3964-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b3964-118">Requirements</span></span>  

 <span data-ttu-id="b3964-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3964-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3964-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b3964-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b3964-121">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="b3964-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b3964-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3964-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3964-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3964-123">See also</span></span>

- [<span data-ttu-id="b3964-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b3964-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="b3964-125">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b3964-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
