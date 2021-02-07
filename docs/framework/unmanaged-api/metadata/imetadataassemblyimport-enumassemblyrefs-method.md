---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataAssemblyImport:: Trmassemblyrefs yöntemi'
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
ms.openlocfilehash: fc1d74d79edc21c6d3d13c80510440333d083801
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671067"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="c4698-103">IMetaDataAssemblyImport::EnumAssemblyRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4698-103">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>

<span data-ttu-id="c4698-104">`mdAssemblyRef`Derleme bildiriminde tanımlanan örnekleri sıralar.</span><span class="sxs-lookup"><span data-stu-id="c4698-104">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4698-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c4698-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,
    [out]     mdAssemblyRef   rAssemblyRefs[],
    [in]      ULONG           cMax,
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4698-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c4698-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="c4698-107">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c4698-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="c4698-108">Yöntem ilk kez çağrıldığında bu null bir değer olmalıdır `EnumAssemblyRefs` .</span><span class="sxs-lookup"><span data-stu-id="c4698-108">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="c4698-109">dışı `mdAssemblyRef` Meta veri belirteçlerinin numaralandırılması.</span><span class="sxs-lookup"><span data-stu-id="c4698-109">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c4698-110">'ndaki Diziye yerleştirilebilecek en fazla belirteç sayısı `rAssemblyRefs` .</span><span class="sxs-lookup"><span data-stu-id="c4698-110">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="c4698-111">dışı Gerçekte içine yerleştirilmiş olan belirteçlerin sayısı `rAssemblyRefs` .</span><span class="sxs-lookup"><span data-stu-id="c4698-111">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4698-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c4698-112">Return Value</span></span>  
  
|<span data-ttu-id="c4698-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c4698-113">HRESULT</span></span>|<span data-ttu-id="c4698-114">Description</span><span class="sxs-lookup"><span data-stu-id="c4698-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c4698-115">`EnumAssemblyRefs` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c4698-115">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c4698-116">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="c4698-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="c4698-117">Bu durumda, `pcTokens` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c4698-117">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c4698-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c4698-118">Requirements</span></span>  

 <span data-ttu-id="c4698-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4698-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4698-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c4698-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c4698-121">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="c4698-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c4698-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4698-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4698-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4698-123">See also</span></span>

- [<span data-ttu-id="c4698-124">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c4698-124">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
