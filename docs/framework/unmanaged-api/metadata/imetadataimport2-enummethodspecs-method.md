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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a3641fcda33a497293dbf87b419c8606847dc296
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130955"
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="bad7a-102">IMetaDataImport2::EnumMethodSpecs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bad7a-102">IMetaDataImport2::EnumMethodSpecs Method</span></span>
<span data-ttu-id="bad7a-103">Bir numaralandırıcı MethodSpec Neobsahuje belirteçleri belirtilen MethodDef veya MemberRef ilişkili bir dizisi için belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="bad7a-103">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bad7a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bad7a-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,   
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="bad7a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bad7a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="bad7a-106">[out içinde] Numaralandırıcı için bir işaretçiye `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="bad7a-106">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="bad7a-107">[in] Numaralandırılacak olan MethodSpec Neobsahuje belirteçler, yöntemi temsil eden MemberRef veya MethodDef belirteç.</span><span class="sxs-lookup"><span data-stu-id="bad7a-107">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="bad7a-108">Varsa değerini `tk` 0 (sıfır), kapsamdaki tüm MethodSpec Neobsahuje belirteçleri numaralandırılır.</span><span class="sxs-lookup"><span data-stu-id="bad7a-108">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="bad7a-109">[out] Numaralandırılacak MethodSpec Neobsahuje belirteçleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="bad7a-109">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="bad7a-110">[in] İstenen sayısı yerleştirmek için belirteçleri `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="bad7a-110">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="bad7a-111">[out] Döndürülen belirteç sayısı yerleştirilen `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="bad7a-111">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bad7a-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bad7a-112">Return Value</span></span>  
  
|<span data-ttu-id="bad7a-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bad7a-113">HRESULT</span></span>|<span data-ttu-id="bad7a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bad7a-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSpecs` <span data-ttu-id="bad7a-115">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="bad7a-115">returned successfully.</span></span>|  
|`S_FALSE`|`phEnum` <span data-ttu-id="bad7a-116">üye öğe yok.</span><span class="sxs-lookup"><span data-stu-id="bad7a-116">has no member elements.</span></span> <span data-ttu-id="bad7a-117">Bu durumda, `pcMethodSpecs` 0 (sıfır) olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bad7a-117">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bad7a-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bad7a-118">Requirements</span></span>  
 <span data-ttu-id="bad7a-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bad7a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bad7a-120">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="bad7a-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bad7a-121">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="bad7a-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="bad7a-122">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="bad7a-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bad7a-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bad7a-123">See also</span></span>

- [<span data-ttu-id="bad7a-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bad7a-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="bad7a-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bad7a-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
