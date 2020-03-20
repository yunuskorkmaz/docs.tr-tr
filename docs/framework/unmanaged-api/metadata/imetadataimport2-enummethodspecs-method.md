---
title: IMetaDataImport2::EnumMethodSpecs Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumMethodSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type:
- apiref
ms.openlocfilehash: 2df53ba53c64e042abc54a1d2ac043d301acdde9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177180"
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="f7733-102">IMetaDataImport2::EnumMethodSpecs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f7733-102">IMetaDataImport2::EnumMethodSpecs Method</span></span>
<span data-ttu-id="f7733-103">Belirtilen MethodDef veya MemberRef belirteciile ilişkili bir dizi MethodSpec belirteci için bir sayısallaştırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="f7733-103">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7733-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f7733-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="f7733-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f7733-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="f7733-106">[içinde, dışarı] Için sayısallaştırıcıya `rMethodSpecs`bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f7733-106">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="f7733-107">[içinde] MethodSpec belirteçleri numaralandırılacak yöntemi temsil eden MemberRef veya MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="f7733-107">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="f7733-108">Değeri 0 `tk` (sıfır) ise, kapsamdaki tüm MethodSpec belirteçleri numaralandırılır.</span><span class="sxs-lookup"><span data-stu-id="f7733-108">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="f7733-109">[çıkış] Sayısala dizecek MethodSpec belirteçleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="f7733-109">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f7733-110">[içinde] Yerleştirilecek istenen maksimum belirteç `rMethodSpecs`sayısı.</span><span class="sxs-lookup"><span data-stu-id="f7733-110">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="f7733-111">[çıkış] Yerleştirilen belirteçlerin döndürülen `rMethodSpecs`sayısı.</span><span class="sxs-lookup"><span data-stu-id="f7733-111">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7733-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f7733-112">Return Value</span></span>  
  
|<span data-ttu-id="f7733-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f7733-113">HRESULT</span></span>|<span data-ttu-id="f7733-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f7733-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f7733-115">`EnumMethodSpecs`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="f7733-115">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f7733-116">`phEnum`üye öğesi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f7733-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="f7733-117">Bu durumda, `pcMethodSpecs` 0 (sıfır) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f7733-117">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f7733-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f7733-118">Requirements</span></span>  
 <span data-ttu-id="f7733-119">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7733-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7733-120">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f7733-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f7733-121">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="f7733-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f7733-122">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7733-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7733-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7733-123">See also</span></span>

- [<span data-ttu-id="f7733-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f7733-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="f7733-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f7733-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
