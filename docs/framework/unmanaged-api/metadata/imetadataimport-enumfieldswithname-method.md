---
description: ': IMetaDataImport:: Enumalanadı Withname yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 88096b2b12a9571eb05d4550e6e26a348e28cfd2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799376"
---
# <a name="imetadataimportenumfieldswithname-method"></a><span data-ttu-id="cdbb8-103">IMetaDataImport::EnumFieldsWithName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cdbb8-103">IMetaDataImport::EnumFieldsWithName Method</span></span>

<span data-ttu-id="cdbb8-104">Belirtilen ada sahip belirtilen türdeki FieldDef belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="cdbb8-104">Enumerates FieldDef tokens of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdbb8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cdbb8-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="cdbb8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cdbb8-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="cdbb8-107">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cdbb8-107">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="cdbb8-108">'ndaki Alanları Numaralandırılacak olan türün belirteci.</span><span class="sxs-lookup"><span data-stu-id="cdbb8-108">[in] The token of the type whose fields are to be enumerated.</span></span>  
  
 `szName`  
 <span data-ttu-id="cdbb8-109">'ndaki Sabit listesinin kapsamını sınırlayan alan adı.</span><span class="sxs-lookup"><span data-stu-id="cdbb8-109">[in] The field name that limits the scope of the enumeration.</span></span>  
  
 `rFields`  
 <span data-ttu-id="cdbb8-110">dışı FieldDef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="cdbb8-110">[out] Array used to store the FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="cdbb8-111">'ndaki Dizinin en büyük boyutu `rFields` .</span><span class="sxs-lookup"><span data-stu-id="cdbb8-111">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="cdbb8-112">dışı İçinde döndürülen FieldDef belirteçlerinin gerçek sayısı `rFields` .</span><span class="sxs-lookup"><span data-stu-id="cdbb8-112">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cdbb8-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cdbb8-113">Remarks</span></span>  

 <span data-ttu-id="cdbb8-114">[IMetaDataImport:: EnumFields](imetadataimport-enumfields-method.md)'in aksine, `EnumFieldsWithName` belirtilen ada sahip olmayan tüm alan belirteçlerini atar.</span><span class="sxs-lookup"><span data-stu-id="cdbb8-114">Unlike [IMetaDataImport::EnumFields](imetadataimport-enumfields-method.md), `EnumFieldsWithName` discards all field tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cdbb8-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cdbb8-115">Return Value</span></span>  
  
|<span data-ttu-id="cdbb8-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cdbb8-116">HRESULT</span></span>|<span data-ttu-id="cdbb8-117">Description</span><span class="sxs-lookup"><span data-stu-id="cdbb8-117">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="cdbb8-118">`EnumFieldsWithName` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="cdbb8-118">`EnumFieldsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="cdbb8-119">Numaralandırılacak alan yok.</span><span class="sxs-lookup"><span data-stu-id="cdbb8-119">There are no fields to enumerate.</span></span> <span data-ttu-id="cdbb8-120">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="cdbb8-120">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cdbb8-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cdbb8-121">Requirements</span></span>  

 <span data-ttu-id="cdbb8-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdbb8-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdbb8-123">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cdbb8-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cdbb8-124">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="cdbb8-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cdbb8-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdbb8-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdbb8-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cdbb8-126">See also</span></span>

- [<span data-ttu-id="cdbb8-127">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cdbb8-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="cdbb8-128">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cdbb8-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
