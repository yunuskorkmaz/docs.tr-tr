---
title: IMetaDataAssemblyImport::EnumFiles Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumFiles
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumFiles
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumFiles method [.NET Framework metadata]
- EnumFiles method [.NET Framework metadata]
ms.assetid: f0d721e2-b946-426d-8e20-9124bd04e4cb
topic_type:
- apiref
ms.openlocfilehash: 70f76318f51047cb81262f744a6fbed5fe401692
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177811"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="0ff68-102">IMetaDataAssemblyImport::EnumFiles Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0ff68-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="0ff68-103">Geçerli derleme bildiriminde başvurulan dosyaları güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="0ff68-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ff68-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0ff68-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,
    [out] mdFile          rFiles[],
    [in]  ULONG           cMax,
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ff68-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0ff68-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="0ff68-106">[içinde, dışarı] Sayıya işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0ff68-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="0ff68-107">Bu yöntemin ilk araması için null bir değer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0ff68-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="0ff68-108">[çıkış] `mdFile` Meta veri belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="0ff68-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="0ff68-109">[içinde] Yerleştirilebilen `mdFile` en fazla belirteç `rFiles`sayısı.</span><span class="sxs-lookup"><span data-stu-id="0ff68-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="0ff68-110">[çıkış] Yerleştirilen belirteçlerin `mdFile` `rFiles`sayısı.</span><span class="sxs-lookup"><span data-stu-id="0ff68-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ff68-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0ff68-111">Return Value</span></span>  
  
|<span data-ttu-id="0ff68-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0ff68-112">HRESULT</span></span>|<span data-ttu-id="0ff68-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ff68-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="0ff68-114">`EnumFiles`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0ff68-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="0ff68-115">Sayısala rendelemek için hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="0ff68-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="0ff68-116">Bu durumda, `pcTokens` sıfıra ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="0ff68-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0ff68-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0ff68-117">Requirements</span></span>  
 <span data-ttu-id="0ff68-118">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ff68-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ff68-119">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0ff68-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0ff68-120">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="0ff68-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0ff68-121">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ff68-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ff68-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ff68-122">See also</span></span>

- [<span data-ttu-id="0ff68-123">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ff68-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
