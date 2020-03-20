---
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
ms.openlocfilehash: 61b5678a546bdbadbcc6d8ee86447cb17ce72b99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175531"
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="43066-102">IMetaDataImport::EnumCustomAttributes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="43066-102">IMetaDataImport::EnumCustomAttributes Method</span></span>
<span data-ttu-id="43066-103">Belirtilen tür veya üyeile ilişkili özel öznitelik tanım belirteçleri güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="43066-103">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43066-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="43066-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="43066-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="43066-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="43066-106">[içinde, dışarı] Döndürülen sayıya işaretçi.</span><span class="sxs-lookup"><span data-stu-id="43066-106">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="43066-107">[içinde] Numaralandırma kapsamı için bir belirteç veya tüm özel öznitelikler için sıfır.</span><span class="sxs-lookup"><span data-stu-id="43066-107">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="43066-108">[içinde] Numaralandırılacak özniteliklerin türünün veya tüm türlerin oluşturucusu `null` için bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="43066-108">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="43066-109">[çıkış] Özel öznitelik belirteçleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="43066-109">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="43066-110">[içinde] `rCustomAttributes` Dizinin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="43066-110">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="43066-111">[çıkış, isteğe bağlı] Döndürülen belirteç değerlerinin `rCustomAttributes`gerçek sayısı.</span><span class="sxs-lookup"><span data-stu-id="43066-111">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43066-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="43066-112">Return Value</span></span>  
  
|<span data-ttu-id="43066-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="43066-113">HRESULT</span></span>|<span data-ttu-id="43066-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43066-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="43066-115">`EnumCustomAttributes`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="43066-115">`EnumCustomAttributes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="43066-116">Sayısala' da özel öznitelikler yoktur.</span><span class="sxs-lookup"><span data-stu-id="43066-116">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="43066-117">Bu durumda, `pcCustomAttributes` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="43066-117">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="43066-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="43066-118">Requirements</span></span>  
 <span data-ttu-id="43066-119">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43066-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43066-120">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="43066-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="43066-121">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="43066-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="43066-122">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43066-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43066-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43066-123">See also</span></span>

- [<span data-ttu-id="43066-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43066-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="43066-125">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43066-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
