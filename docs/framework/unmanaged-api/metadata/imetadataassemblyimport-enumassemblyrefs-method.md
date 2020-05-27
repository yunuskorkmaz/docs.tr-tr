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
ms.openlocfilehash: 1b9700455da82fc7f4a39d4c208ac0b18ef79722
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009125"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="15796-102">IMetaDataAssemblyImport::EnumAssemblyRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="15796-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="15796-103">`mdAssemblyRef`Derleme bildiriminde tanımlanan örnekleri sıralar.</span><span class="sxs-lookup"><span data-stu-id="15796-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15796-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="15796-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,
    [out]     mdAssemblyRef   rAssemblyRefs[],
    [in]      ULONG           cMax,
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15796-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="15796-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="15796-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="15796-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="15796-107">Yöntem ilk kez çağrıldığında bu null bir değer olmalıdır `EnumAssemblyRefs` .</span><span class="sxs-lookup"><span data-stu-id="15796-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="15796-108">dışı `mdAssemblyRef`Meta veri belirteçlerinin numaralandırılması.</span><span class="sxs-lookup"><span data-stu-id="15796-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="15796-109">'ndaki Diziye yerleştirilebilecek en fazla belirteç sayısı `rAssemblyRefs` .</span><span class="sxs-lookup"><span data-stu-id="15796-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="15796-110">dışı Gerçekte içine yerleştirilmiş olan belirteçlerin sayısı `rAssemblyRefs` .</span><span class="sxs-lookup"><span data-stu-id="15796-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="15796-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="15796-111">Return Value</span></span>  
  
|<span data-ttu-id="15796-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="15796-112">HRESULT</span></span>|<span data-ttu-id="15796-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15796-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="15796-114">`EnumAssemblyRefs`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="15796-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="15796-115">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="15796-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="15796-116">Bu durumda, `pcTokens` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="15796-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="15796-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="15796-117">Requirements</span></span>  
 <span data-ttu-id="15796-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15796-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15796-119">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="15796-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="15796-120">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="15796-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="15796-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15796-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15796-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15796-122">See also</span></span>

- [<span data-ttu-id="15796-123">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15796-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
