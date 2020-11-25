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
ms.openlocfilehash: 26b345567699c5780827ed835cff13069ea8f609
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702751"
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="a555f-102">IMetaDataImport2::EnumMethodSpecs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a555f-102">IMetaDataImport2::EnumMethodSpecs Method</span></span>

<span data-ttu-id="a555f-103">Belirtilen MethodDef veya MemberRef belirteciyle ilişkili bir MethodSpec belirteçleri dizisi için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="a555f-103">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a555f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a555f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="a555f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a555f-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="a555f-106">[in, out] İçin numaralandırıcı işaretçisi `rMethodSpecs` .</span><span class="sxs-lookup"><span data-stu-id="a555f-106">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="a555f-107">'ndaki MethodSpec belirteçleri numaralandırılmış olan yöntemi temsil eden MemberRef veya MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="a555f-107">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="a555f-108">Değeri `tk` 0 (sıfır) ise, kapsamdaki tüm MethodSpec belirteçleri numaralandırılır.</span><span class="sxs-lookup"><span data-stu-id="a555f-108">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="a555f-109">dışı Numaralandırılacak MethodSpec belirteçlerinin dizisi.</span><span class="sxs-lookup"><span data-stu-id="a555f-109">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a555f-110">'ndaki İstenen en fazla belirteç sayısı, içine yerleştirilecek `rMethodSpecs` .</span><span class="sxs-lookup"><span data-stu-id="a555f-110">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="a555f-111">dışı Döndürülen belirteç sayısı döndürüldü `rMethodSpecs` .</span><span class="sxs-lookup"><span data-stu-id="a555f-111">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a555f-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a555f-112">Return Value</span></span>  
  
|<span data-ttu-id="a555f-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a555f-113">HRESULT</span></span>|<span data-ttu-id="a555f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a555f-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a555f-115">`EnumMethodSpecs` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a555f-115">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a555f-116">`phEnum` Üye öğesi yok.</span><span class="sxs-lookup"><span data-stu-id="a555f-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="a555f-117">Bu durumda, `pcMethodSpecs` 0 (sıfır) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a555f-117">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a555f-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a555f-118">Requirements</span></span>  

 <span data-ttu-id="a555f-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a555f-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a555f-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a555f-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a555f-121">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="a555f-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a555f-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a555f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a555f-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a555f-123">See also</span></span>

- [<span data-ttu-id="a555f-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a555f-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="a555f-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a555f-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
