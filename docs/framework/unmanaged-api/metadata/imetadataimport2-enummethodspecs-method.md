---
description: 'Daha fazla bilgi edinin: IMetaDataImport2:: Enummethodspec yöntemi'
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
ms.openlocfilehash: 19fff1d78599d968bb1fd0ab27b0f71e41fae20b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677528"
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="79cd2-103">IMetaDataImport2::EnumMethodSpecs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79cd2-103">IMetaDataImport2::EnumMethodSpecs Method</span></span>

<span data-ttu-id="79cd2-104">Belirtilen MethodDef veya MemberRef belirteciyle ilişkili bir MethodSpec belirteçleri dizisi için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="79cd2-104">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79cd2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79cd2-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="79cd2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="79cd2-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="79cd2-107">[in, out] İçin numaralandırıcı işaretçisi `rMethodSpecs` .</span><span class="sxs-lookup"><span data-stu-id="79cd2-107">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="79cd2-108">'ndaki MethodSpec belirteçleri numaralandırılmış olan yöntemi temsil eden MemberRef veya MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="79cd2-108">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="79cd2-109">Değeri `tk` 0 (sıfır) ise, kapsamdaki tüm MethodSpec belirteçleri numaralandırılır.</span><span class="sxs-lookup"><span data-stu-id="79cd2-109">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="79cd2-110">dışı Numaralandırılacak MethodSpec belirteçlerinin dizisi.</span><span class="sxs-lookup"><span data-stu-id="79cd2-110">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="79cd2-111">'ndaki İstenen en fazla belirteç sayısı, içine yerleştirilecek `rMethodSpecs` .</span><span class="sxs-lookup"><span data-stu-id="79cd2-111">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="79cd2-112">dışı Döndürülen belirteç sayısı döndürüldü `rMethodSpecs` .</span><span class="sxs-lookup"><span data-stu-id="79cd2-112">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79cd2-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="79cd2-113">Return Value</span></span>  
  
|<span data-ttu-id="79cd2-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="79cd2-114">HRESULT</span></span>|<span data-ttu-id="79cd2-115">Description</span><span class="sxs-lookup"><span data-stu-id="79cd2-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="79cd2-116">`EnumMethodSpecs` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="79cd2-116">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="79cd2-117">`phEnum` Üye öğesi yok.</span><span class="sxs-lookup"><span data-stu-id="79cd2-117">`phEnum` has no member elements.</span></span> <span data-ttu-id="79cd2-118">Bu durumda, `pcMethodSpecs` 0 (sıfır) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="79cd2-118">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="79cd2-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="79cd2-119">Requirements</span></span>  

 <span data-ttu-id="79cd2-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79cd2-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79cd2-121">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="79cd2-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="79cd2-122">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="79cd2-122">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="79cd2-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79cd2-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79cd2-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79cd2-124">See also</span></span>

- [<span data-ttu-id="79cd2-125">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="79cd2-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="79cd2-126">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="79cd2-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
