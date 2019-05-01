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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b80bb7b62d3a4ffee61cc6756b7d7d02f2b074bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049953"
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="716bb-102">IMetaDataImport::EnumCustomAttributes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="716bb-102">IMetaDataImport::EnumCustomAttributes Method</span></span>
<span data-ttu-id="716bb-103">Belirtilen tür veya üye ile ilişkili özel öznitelik tanımı belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="716bb-103">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="716bb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="716bb-104">Syntax</span></span>  
  
```  
HRESULT EnumCustomAttributes (   
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,   
   [in]  mdToken            tkType,   
   [out] mdCustomAttribute  rCustomAttributes[],   
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="716bb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="716bb-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="716bb-106">[out içinde] Döndürülen Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="716bb-106">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="716bb-107">[in] Numaralandırma veya tüm özel öznitelikleri için sıfır kapsamı için bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="716bb-107">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="716bb-108">[in] Numaralandırılacak, öznitelik türünün oluşturucusu için bir belirteç veya `null` tüm türleri.</span><span class="sxs-lookup"><span data-stu-id="716bb-108">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="716bb-109">[out] Özel öznitelik belirteçleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="716bb-109">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="716bb-110">[in] En büyük boyutunu `rCustomAttributes` dizisi.</span><span class="sxs-lookup"><span data-stu-id="716bb-110">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="716bb-111">[out, isteğe bağlı] Gerçek sayı, döndürülen belirteç değerlerinin `rCustomAttributes`.</span><span class="sxs-lookup"><span data-stu-id="716bb-111">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="716bb-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="716bb-112">Return Value</span></span>  
  
|<span data-ttu-id="716bb-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="716bb-113">HRESULT</span></span>|<span data-ttu-id="716bb-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="716bb-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="716bb-115">`EnumCustomAttributes` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="716bb-115">`EnumCustomAttributes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="716bb-116">Numaralandırılacak özel öznitelik vardır.</span><span class="sxs-lookup"><span data-stu-id="716bb-116">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="716bb-117">Bu durumda, `pcCustomAttributes` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="716bb-117">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="716bb-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="716bb-118">Requirements</span></span>  
 <span data-ttu-id="716bb-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="716bb-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="716bb-120">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="716bb-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="716bb-121">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="716bb-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="716bb-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="716bb-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="716bb-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="716bb-123">See also</span></span>

- [<span data-ttu-id="716bb-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="716bb-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="716bb-125">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="716bb-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
