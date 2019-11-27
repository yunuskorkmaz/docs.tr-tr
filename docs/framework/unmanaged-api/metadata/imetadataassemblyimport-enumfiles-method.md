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
ms.openlocfilehash: e4549789ea1af584c0850a535d9f6bb54f844ce0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443550"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="0f386-102">IMetaDataAssemblyImport::EnumFiles Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f386-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="0f386-103">Geçerli derleme bildiriminde başvurulan dosyaları numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="0f386-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f386-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f386-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,   
    [out] mdFile          rFiles[],   
    [in]  ULONG           cMax,   
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f386-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0f386-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="0f386-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0f386-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="0f386-107">Bu yöntemin ilk çağrısı için bu bir null değer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0f386-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="0f386-108">dışı `mdFile` meta veri belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="0f386-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="0f386-109">'ndaki `rFiles`yerleştirilebilecek en fazla `mdFile` belirteci sayısı.</span><span class="sxs-lookup"><span data-stu-id="0f386-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="0f386-110">dışı Gerçekte `rFiles`yer `mdFile` belirteçlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="0f386-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f386-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0f386-111">Return Value</span></span>  
  
|<span data-ttu-id="0f386-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0f386-112">HRESULT</span></span>|<span data-ttu-id="0f386-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f386-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="0f386-114">`EnumFiles` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0f386-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="0f386-115">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="0f386-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="0f386-116">Bu durumda `pcTokens` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="0f386-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0f386-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f386-117">Requirements</span></span>  
 <span data-ttu-id="0f386-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f386-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f386-119">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0f386-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0f386-120">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="0f386-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0f386-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f386-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f386-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f386-122">See also</span></span>

- [<span data-ttu-id="0f386-123">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f386-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
