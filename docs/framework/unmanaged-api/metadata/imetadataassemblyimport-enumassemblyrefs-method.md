---
title: IMetaDataAssemblyImport::EnumAssemblyRefs Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumAssemblyRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs method [.NET Framework metadata]
- EnumAssemblyRefs method [.NET Framework metadata]
ms.assetid: 8844d0dd-730e-4592-8a7b-c1462d312c70
topic_type:
- apiref
ms.openlocfilehash: 6a4489d094974eb872b39824ceb185b0cbe48625
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177822"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="86db0-102">IMetaDataAssemblyImport::EnumAssemblyRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="86db0-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="86db0-103">Derleme bildiriminde `mdAssemblyRef` tanımlanan örnekleri oyalar.</span><span class="sxs-lookup"><span data-stu-id="86db0-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86db0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86db0-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,
    [out]     mdAssemblyRef   rAssemblyRefs[],
    [in]      ULONG           cMax,
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86db0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="86db0-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="86db0-106">[içinde, dışarı] Sayıya işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="86db0-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="86db0-107">`EnumAssemblyRefs` Yöntem ilk kez çağrıldığında bu null bir değer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="86db0-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="86db0-108">[çıkış] `mdAssemblyRef` Meta veri belirteçlerinin numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="86db0-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="86db0-109">[içinde] `rAssemblyRefs` Diziye yerleştirilebilir belirteçleri maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="86db0-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="86db0-110">[çıkış] Yerleştirilen belirteçlerin `rAssemblyRefs`sayısı.</span><span class="sxs-lookup"><span data-stu-id="86db0-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86db0-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="86db0-111">Return Value</span></span>  
  
|<span data-ttu-id="86db0-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="86db0-112">HRESULT</span></span>|<span data-ttu-id="86db0-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86db0-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="86db0-114">`EnumAssemblyRefs`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="86db0-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="86db0-115">Sayısala rendelemek için hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="86db0-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="86db0-116">Bu durumda, `pcTokens` sıfıra ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="86db0-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="86db0-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86db0-117">Requirements</span></span>  
 <span data-ttu-id="86db0-118">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86db0-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86db0-119">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="86db0-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="86db0-120">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="86db0-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="86db0-121">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86db0-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86db0-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86db0-122">See also</span></span>

- [<span data-ttu-id="86db0-123">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86db0-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
