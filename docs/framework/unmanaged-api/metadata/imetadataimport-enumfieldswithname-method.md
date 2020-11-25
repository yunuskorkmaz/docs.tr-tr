---
title: IMetaDataImport::EnumFieldsWithName Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFieldsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFieldsWithName
helpviewer_keywords:
- IMetaDataImport::EnumFieldsWithName method [.NET Framework metadata]
- EnumFieldsWithName method [.NET Framework metadata]
ms.assetid: 42145e8d-000f-4d0b-ae43-c08201190fa2
topic_type:
- apiref
ms.openlocfilehash: 0a254587282dea43a3507fbbeca35bd7aa9604f3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711578"
---
# <a name="imetadataimportenumfieldswithname-method"></a><span data-ttu-id="323ad-102">IMetaDataImport::EnumFieldsWithName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="323ad-102">IMetaDataImport::EnumFieldsWithName Method</span></span>

<span data-ttu-id="323ad-103">Belirtilen ada sahip belirtilen türdeki FieldDef belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="323ad-103">Enumerates FieldDef tokens of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="323ad-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="323ad-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFieldsWithName (  
   [in, out] HCORENUM    *phEnum,
   [in]  mdTypeDef       cl,
   [in]  LPCWSTR         szName,
   [out] mdFieldDef      rFields[],
   [in]  ULONG           cMax,
   [out] ULONG           *pcTokens
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="323ad-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="323ad-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="323ad-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="323ad-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="323ad-107">'ndaki Alanları Numaralandırılacak olan türün belirteci.</span><span class="sxs-lookup"><span data-stu-id="323ad-107">[in] The token of the type whose fields are to be enumerated.</span></span>  
  
 `szName`  
 <span data-ttu-id="323ad-108">'ndaki Sabit listesinin kapsamını sınırlayan alan adı.</span><span class="sxs-lookup"><span data-stu-id="323ad-108">[in] The field name that limits the scope of the enumeration.</span></span>  
  
 `rFields`  
 <span data-ttu-id="323ad-109">dışı FieldDef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="323ad-109">[out] Array used to store the FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="323ad-110">'ndaki Dizinin en büyük boyutu `rFields` .</span><span class="sxs-lookup"><span data-stu-id="323ad-110">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="323ad-111">dışı İçinde döndürülen FieldDef belirteçlerinin gerçek sayısı `rFields` .</span><span class="sxs-lookup"><span data-stu-id="323ad-111">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="323ad-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="323ad-112">Remarks</span></span>  

 <span data-ttu-id="323ad-113">[IMetaDataImport:: EnumFields](imetadataimport-enumfields-method.md)'in aksine, `EnumFieldsWithName` belirtilen ada sahip olmayan tüm alan belirteçlerini atar.</span><span class="sxs-lookup"><span data-stu-id="323ad-113">Unlike [IMetaDataImport::EnumFields](imetadataimport-enumfields-method.md), `EnumFieldsWithName` discards all field tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="323ad-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="323ad-114">Return Value</span></span>  
  
|<span data-ttu-id="323ad-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="323ad-115">HRESULT</span></span>|<span data-ttu-id="323ad-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="323ad-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="323ad-117">`EnumFieldsWithName` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="323ad-117">`EnumFieldsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="323ad-118">Numaralandırılacak alan yok.</span><span class="sxs-lookup"><span data-stu-id="323ad-118">There are no fields to enumerate.</span></span> <span data-ttu-id="323ad-119">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="323ad-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="323ad-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="323ad-120">Requirements</span></span>  

 <span data-ttu-id="323ad-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="323ad-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="323ad-122">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="323ad-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="323ad-123">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="323ad-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="323ad-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="323ad-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="323ad-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="323ad-125">See also</span></span>

- [<span data-ttu-id="323ad-126">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="323ad-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="323ad-127">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="323ad-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
