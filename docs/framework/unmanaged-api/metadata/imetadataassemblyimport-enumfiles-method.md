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
ms.openlocfilehash: ed8bafd67b5d55a5116111b7721fbdc31c52aca6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009105"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="fc325-102">IMetaDataAssemblyImport::EnumFiles Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fc325-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="fc325-103">Geçerli derleme bildiriminde başvurulan dosyaları numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="fc325-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc325-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fc325-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,
    [out] mdFile          rFiles[],
    [in]  ULONG           cMax,
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc325-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fc325-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="fc325-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fc325-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="fc325-107">Bu yöntemin ilk çağrısı için bu bir null değer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fc325-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="fc325-108">dışı Meta veri belirteçlerini depolamak için kullanılan dizi `mdFile` .</span><span class="sxs-lookup"><span data-stu-id="fc325-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="fc325-109">'ndaki `mdFile`İçine yerleştirilebilecek en fazla belirteç sayısı `rFiles` .</span><span class="sxs-lookup"><span data-stu-id="fc325-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="fc325-110">dışı `mdFile`Gerçekte içine yerleştirilmiş olan belirteçlerin sayısı `rFiles` .</span><span class="sxs-lookup"><span data-stu-id="fc325-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc325-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fc325-111">Return Value</span></span>  
  
|<span data-ttu-id="fc325-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fc325-112">HRESULT</span></span>|<span data-ttu-id="fc325-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc325-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="fc325-114">`EnumFiles`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="fc325-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="fc325-115">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="fc325-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="fc325-116">Bu durumda, `pcTokens` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="fc325-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fc325-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fc325-117">Requirements</span></span>  
 <span data-ttu-id="fc325-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc325-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc325-119">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="fc325-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fc325-120">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="fc325-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fc325-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc325-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc325-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc325-122">See also</span></span>

- [<span data-ttu-id="fc325-123">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fc325-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
