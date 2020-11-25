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
ms.openlocfilehash: f9af770f3bdca98f6b3d06d8b0fe6c92745f73e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731635"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="b9955-102">IMetaDataAssemblyImport::EnumFiles Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b9955-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>

<span data-ttu-id="b9955-103">Geçerli derleme bildiriminde başvurulan dosyaları numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="b9955-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9955-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b9955-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,
    [out] mdFile          rFiles[],
    [in]  ULONG           cMax,
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9955-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b9955-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="b9955-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b9955-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="b9955-107">Bu yöntemin ilk çağrısı için bu bir null değer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b9955-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="b9955-108">dışı Meta veri belirteçlerini depolamak için kullanılan dizi `mdFile` .</span><span class="sxs-lookup"><span data-stu-id="b9955-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b9955-109">'ndaki `mdFile` İçine yerleştirilebilecek en fazla belirteç sayısı `rFiles` .</span><span class="sxs-lookup"><span data-stu-id="b9955-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="b9955-110">dışı `mdFile` Gerçekte içine yerleştirilmiş olan belirteçlerin sayısı `rFiles` .</span><span class="sxs-lookup"><span data-stu-id="b9955-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9955-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b9955-111">Return Value</span></span>  
  
|<span data-ttu-id="b9955-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b9955-112">HRESULT</span></span>|<span data-ttu-id="b9955-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b9955-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b9955-114">`EnumFiles` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b9955-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b9955-115">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="b9955-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="b9955-116">Bu durumda, `pcTokens` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="b9955-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b9955-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b9955-117">Requirements</span></span>  

 <span data-ttu-id="b9955-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9955-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9955-119">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b9955-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b9955-120">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="b9955-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b9955-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9955-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9955-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9955-122">See also</span></span>

- [<span data-ttu-id="b9955-123">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b9955-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
