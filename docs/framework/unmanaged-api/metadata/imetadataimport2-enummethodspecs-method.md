---
title: "IMetaDataImport2::EnumMethodSpecs Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6e134d19eb6699f39e6d538f93f989b87ed8f37d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="6594a-102">IMetaDataImport2::EnumMethodSpecs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6594a-102">IMetaDataImport2::EnumMethodSpecs Method</span></span>
<span data-ttu-id="6594a-103">Bir numaralandırıcı MethodSpec belirteçleri belirtilen MethodDef veya MemberRef ilişkili bir dizi belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="6594a-103">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6594a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6594a-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,   
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="6594a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6594a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="6594a-106">[içinde out] Numaralandırıcı için bir işaretçi `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="6594a-106">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="6594a-107">[in] Numaralandırılacak olan MethodSpec belirteçler olan yöntemi temsil eden MemberRef veya MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="6594a-107">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="6594a-108">Varsa değerini `tk` 0 (sıfır), kapsamdaki tüm MethodSpec belirteçleri numaralandırılır.</span><span class="sxs-lookup"><span data-stu-id="6594a-108">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="6594a-109">[out] Numaralandırılacak MethodSpec belirteçleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="6594a-109">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="6594a-110">[in] İstenen sayısı yerleştirmek için belirteçleri `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="6594a-110">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="6594a-111">[out] Sıraya alınan belirteçleri döndürülen sayısıdır `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="6594a-111">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6594a-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6594a-112">Return Value</span></span>  
  
|<span data-ttu-id="6594a-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6594a-113">HRESULT</span></span>|<span data-ttu-id="6594a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6594a-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6594a-115">`EnumMethodSpecs`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="6594a-115">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="6594a-116">`phEnum`hiç üye öğe yok.</span><span class="sxs-lookup"><span data-stu-id="6594a-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="6594a-117">Bu durumda, `pcMethodSpecs` 0 (sıfır) olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6594a-117">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6594a-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6594a-118">Requirements</span></span>  
 <span data-ttu-id="6594a-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6594a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6594a-120">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6594a-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6594a-121">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="6594a-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6594a-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6594a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6594a-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6594a-123">See Also</span></span>  
 [<span data-ttu-id="6594a-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6594a-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="6594a-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6594a-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
