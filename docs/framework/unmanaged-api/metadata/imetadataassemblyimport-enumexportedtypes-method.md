---
title: IMetaDataAssemblyImport::EnumExportedTypes Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumExportedTypes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumExportedTypes
helpviewer_keywords:
- EnumExportedTypes method [.NET Framework metadata]
- IMetaDataAssemblyImport::EnumExportedTypes method [.NET Framework metadata]
ms.assetid: e5912ed8-e4ce-438b-8ea3-d9e4c288d109
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1beb76012d5f0351ee644c8dea89cabdbe2c8970
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555030"
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a><span data-ttu-id="51bf7-102">IMetaDataAssemblyImport::EnumExportedTypes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51bf7-102">IMetaDataAssemblyImport::EnumExportedTypes Method</span></span>
<span data-ttu-id="51bf7-103">Başvurulan derleme bildiriminde geçerli meta veri kapsamda dışarı aktarılan türlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="51bf7-103">Enumerates the exported types referenced in the assembly manifest in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51bf7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="51bf7-104">Syntax</span></span>  
  
```  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,   
    [out] mdExportedType   rExportedTypes[],   
    [in]  ULONG            cMax,   
    [out] ULONG            *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="51bf7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="51bf7-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="51bf7-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="51bf7-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="51bf7-107">Bu boş olmalıdır ne zaman değer `EnumExportedTypes` yöntemi ilk kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="51bf7-107">This must be a null value when the `EnumExportedTypes` method is called for the first time.</span></span>  
  
 `rExportedTypes`  
 <span data-ttu-id="51bf7-108">[out] Numaralandırmasını `mdExportedType` meta veri belirteçleri.</span><span class="sxs-lookup"><span data-stu-id="51bf7-108">[out] The enumeration of `mdExportedType` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="51bf7-109">[in] En fazla `mdExportedType` yerleştirilebilir belirteçleri `rExportedTypes` dizisi.</span><span class="sxs-lookup"><span data-stu-id="51bf7-109">[in] The maximum number of `mdExportedType` tokens that can be placed in the `rExportedTypes` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="51bf7-110">[out] Sayısını `mdExportedType` belirteçleri gerçekten yerleştirilen `rExportedTypes`.</span><span class="sxs-lookup"><span data-stu-id="51bf7-110">[out] The number of `mdExportedType` tokens actually placed in `rExportedTypes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51bf7-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="51bf7-111">Return Value</span></span>  
  
|<span data-ttu-id="51bf7-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="51bf7-112">HRESULT</span></span>|<span data-ttu-id="51bf7-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="51bf7-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="51bf7-114">`EnumExportedTypes` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="51bf7-114">`EnumExportedTypes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="51bf7-115">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="51bf7-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="51bf7-116">Bu durumda, `pcTokens` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="51bf7-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="51bf7-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="51bf7-117">Requirements</span></span>  
 <span data-ttu-id="51bf7-118">**Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51bf7-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51bf7-119">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="51bf7-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="51bf7-120">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="51bf7-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="51bf7-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51bf7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51bf7-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51bf7-122">See also</span></span>
- [<span data-ttu-id="51bf7-123">IMetaDataAssemblyImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="51bf7-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
