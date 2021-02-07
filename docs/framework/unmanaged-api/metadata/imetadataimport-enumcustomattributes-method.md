---
description: ': IMetaDataImport:: EnumCustomAttributes yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataImport::EnumCustomAttributes Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumCustomAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type:
- apiref
ms.openlocfilehash: 1c55ea4b72483e5dc30425172b95be7f77e8a62a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677593"
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="6d2c9-103">IMetaDataImport::EnumCustomAttributes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d2c9-103">IMetaDataImport::EnumCustomAttributes Method</span></span>

<span data-ttu-id="6d2c9-104">Belirtilen tür veya üyeyle ilişkili özel öznitelik tanımı belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="6d2c9-104">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d2c9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6d2c9-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes (
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,
   [in]  mdToken            tkType,
   [out] mdCustomAttribute  rCustomAttributes[],
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d2c9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6d2c9-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="6d2c9-107">[in, out] Döndürülen Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6d2c9-107">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="6d2c9-108">'ndaki Numaralandırma kapsamı için bir belirteç veya tüm özel öznitelikler için sıfır.</span><span class="sxs-lookup"><span data-stu-id="6d2c9-108">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="6d2c9-109">'ndaki Numaralandırılacak özniteliklerin türünün veya `null` tüm türlerin oluşturucusunun belirteci.</span><span class="sxs-lookup"><span data-stu-id="6d2c9-109">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="6d2c9-110">dışı Özel öznitelik belirteçlerinin dizisi.</span><span class="sxs-lookup"><span data-stu-id="6d2c9-110">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="6d2c9-111">'ndaki Dizinin en büyük boyutu `rCustomAttributes` .</span><span class="sxs-lookup"><span data-stu-id="6d2c9-111">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="6d2c9-112">[Out, isteğe bağlı] İçinde döndürülen belirteç değerlerinin gerçek sayısı `rCustomAttributes` .</span><span class="sxs-lookup"><span data-stu-id="6d2c9-112">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d2c9-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6d2c9-113">Return Value</span></span>  
  
|<span data-ttu-id="6d2c9-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6d2c9-114">HRESULT</span></span>|<span data-ttu-id="6d2c9-115">Description</span><span class="sxs-lookup"><span data-stu-id="6d2c9-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6d2c9-116">`EnumCustomAttributes` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="6d2c9-116">`EnumCustomAttributes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="6d2c9-117">Numaralandırılacak özel öznitelik yok.</span><span class="sxs-lookup"><span data-stu-id="6d2c9-117">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="6d2c9-118">Bu durumda, `pcCustomAttributes` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="6d2c9-118">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6d2c9-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6d2c9-119">Requirements</span></span>  

 <span data-ttu-id="6d2c9-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d2c9-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d2c9-121">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6d2c9-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6d2c9-122">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="6d2c9-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6d2c9-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d2c9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d2c9-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d2c9-124">See also</span></span>

- [<span data-ttu-id="6d2c9-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d2c9-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="6d2c9-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d2c9-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
