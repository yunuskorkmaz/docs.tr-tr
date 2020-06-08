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
ms.openlocfilehash: 9b0da8a06259fe99da52497da3011da94289d301
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492336"
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="b2b89-102">IMetaDataImport::EnumCustomAttributes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2b89-102">IMetaDataImport::EnumCustomAttributes Method</span></span>
<span data-ttu-id="b2b89-103">Belirtilen tür veya üyeyle ilişkili özel öznitelik tanımı belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="b2b89-103">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2b89-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b2b89-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b2b89-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b2b89-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b2b89-106">[in, out] Döndürülen Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b2b89-106">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="b2b89-107">'ndaki Numaralandırma kapsamı için bir belirteç veya tüm özel öznitelikler için sıfır.</span><span class="sxs-lookup"><span data-stu-id="b2b89-107">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="b2b89-108">'ndaki Numaralandırılacak özniteliklerin türünün veya `null` tüm türlerin oluşturucusunun belirteci.</span><span class="sxs-lookup"><span data-stu-id="b2b89-108">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="b2b89-109">dışı Özel öznitelik belirteçlerinin dizisi.</span><span class="sxs-lookup"><span data-stu-id="b2b89-109">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b2b89-110">'ndaki Dizinin en büyük boyutu `rCustomAttributes` .</span><span class="sxs-lookup"><span data-stu-id="b2b89-110">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="b2b89-111">[Out, isteğe bağlı] İçinde döndürülen belirteç değerlerinin gerçek sayısı `rCustomAttributes` .</span><span class="sxs-lookup"><span data-stu-id="b2b89-111">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2b89-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b2b89-112">Return Value</span></span>  
  
|<span data-ttu-id="b2b89-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b2b89-113">HRESULT</span></span>|<span data-ttu-id="b2b89-114">Description</span><span class="sxs-lookup"><span data-stu-id="b2b89-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b2b89-115">`EnumCustomAttributes`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b2b89-115">`EnumCustomAttributes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b2b89-116">Numaralandırılacak özel öznitelik yok.</span><span class="sxs-lookup"><span data-stu-id="b2b89-116">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="b2b89-117">Bu durumda, `pcCustomAttributes` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="b2b89-117">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b2b89-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2b89-118">Requirements</span></span>  
 <span data-ttu-id="b2b89-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2b89-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2b89-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b2b89-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b2b89-121">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="b2b89-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b2b89-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2b89-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2b89-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2b89-123">See also</span></span>

- [<span data-ttu-id="b2b89-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2b89-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="b2b89-125">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2b89-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
