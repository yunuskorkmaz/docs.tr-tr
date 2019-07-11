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
ms.openlocfilehash: b8cd086a86d104fdfebf1a8298a22b795cb2389b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782640"
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="129c4-102">IMetaDataImport2::EnumMethodSpecs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="129c4-102">IMetaDataImport2::EnumMethodSpecs Method</span></span>
<span data-ttu-id="129c4-103">Bir numaralandırıcı MethodSpec Neobsahuje belirteçleri belirtilen MethodDef veya MemberRef ilişkili bir dizisi için belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="129c4-103">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="129c4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="129c4-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,   
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="129c4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="129c4-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="129c4-106">[out içinde] Numaralandırıcı için bir işaretçiye `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="129c4-106">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="129c4-107">[in] Numaralandırılacak olan MethodSpec Neobsahuje belirteçler, yöntemi temsil eden MemberRef veya MethodDef belirteç.</span><span class="sxs-lookup"><span data-stu-id="129c4-107">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="129c4-108">Varsa değerini `tk` 0 (sıfır), kapsamdaki tüm MethodSpec Neobsahuje belirteçleri numaralandırılır.</span><span class="sxs-lookup"><span data-stu-id="129c4-108">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="129c4-109">[out] Numaralandırılacak MethodSpec Neobsahuje belirteçleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="129c4-109">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="129c4-110">[in] İstenen sayısı yerleştirmek için belirteçleri `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="129c4-110">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="129c4-111">[out] Döndürülen belirteç sayısı yerleştirilen `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="129c4-111">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="129c4-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="129c4-112">Return Value</span></span>  
  
|<span data-ttu-id="129c4-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="129c4-113">HRESULT</span></span>|<span data-ttu-id="129c4-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="129c4-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="129c4-115">`EnumMethodSpecs` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="129c4-115">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="129c4-116">`phEnum` üye öğe yok.</span><span class="sxs-lookup"><span data-stu-id="129c4-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="129c4-117">Bu durumda, `pcMethodSpecs` 0 (sıfır) olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="129c4-117">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="129c4-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="129c4-118">Requirements</span></span>  
 <span data-ttu-id="129c4-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="129c4-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="129c4-120">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="129c4-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="129c4-121">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="129c4-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="129c4-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="129c4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="129c4-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="129c4-123">See also</span></span>

- [<span data-ttu-id="129c4-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="129c4-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="129c4-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="129c4-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
