---
title: "IMetaDataImport2::EnumMethodSpecs Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.EnumMethodSpecs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: db1968c73d5a1c6e0687bc86f249c70b6c21712c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="d0858-102">IMetaDataImport2::EnumMethodSpecs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d0858-102">IMetaDataImport2::EnumMethodSpecs Method</span></span>
<span data-ttu-id="d0858-103">Bir numaralandırıcı MethodSpec belirteçleri belirtilen MethodDef veya MemberRef ilişkili bir dizi belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="d0858-103">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0858-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0858-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,   
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="d0858-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d0858-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d0858-106">[içinde out] Numaralandırıcı için bir işaretçi `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="d0858-106">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="d0858-107">[in] Numaralandırılacak olan MethodSpec belirteçler olan yöntemi temsil eden MemberRef veya MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="d0858-107">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="d0858-108">Varsa değerini `tk` 0 (sıfır), kapsamdaki tüm MethodSpec belirteçleri numaralandırılır.</span><span class="sxs-lookup"><span data-stu-id="d0858-108">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="d0858-109">[out] Numaralandırılacak MethodSpec belirteçleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="d0858-109">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d0858-110">[in] İstenen sayısı yerleştirmek için belirteçleri `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="d0858-110">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="d0858-111">[out] Sıraya alınan belirteçleri döndürülen sayısıdır `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="d0858-111">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0858-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d0858-112">Return Value</span></span>  
  
|<span data-ttu-id="d0858-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d0858-113">HRESULT</span></span>|<span data-ttu-id="d0858-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d0858-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d0858-115">`EnumMethodSpecs`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d0858-115">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d0858-116">`phEnum`hiç üye öğe yok.</span><span class="sxs-lookup"><span data-stu-id="d0858-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="d0858-117">Bu durumda, `pcMethodSpecs` 0 (sıfır) olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d0858-117">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d0858-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0858-118">Requirements</span></span>  
 <span data-ttu-id="d0858-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0858-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0858-120">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d0858-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d0858-121">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="d0858-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d0858-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0858-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0858-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d0858-123">See Also</span></span>  
 [<span data-ttu-id="d0858-124">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="d0858-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="d0858-125">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="d0858-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
