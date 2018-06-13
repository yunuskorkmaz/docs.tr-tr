---
title: IMetaDataAssemblyEmit::DefineManifestResource Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineManifestResource
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineManifestResource
helpviewer_keywords:
- DefineManifestResource method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineManifestResource method [.NET Framework metadata]
ms.assetid: 27f6d295-0fe9-4cda-b77e-6e7d5c53df09
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 48d688b64bbe9330a176ef073e96865b719ff2c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446687"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a><span data-ttu-id="8bd44-102">IMetaDataAssemblyEmit::DefineManifestResource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8bd44-102">IMetaDataAssemblyEmit::DefineManifestResource Method</span></span>
<span data-ttu-id="8bd44-103">Oluşturur bir `ManifestResource` belirtilen bildirim kaynağı için meta veriler içeren yapısı ve ilişkili meta veri simgesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="8bd44-103">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bd44-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8bd44-104">Syntax</span></span>  
  
```  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,   
    [in] mdToken                tkImplementation,   
    [in] DWORD                  dwOffset,   
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8bd44-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8bd44-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="8bd44-106">[in] Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="8bd44-106">[in] The name of the resource.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="8bd44-107">[in] Meta veri simgesi türü `mdtFile` veya `mdtAssemblyRef` kaynak sağlayıcıya eşler.</span><span class="sxs-lookup"><span data-stu-id="8bd44-107">[in] A metadata token of type `mdtFile` or `mdtAssemblyRef` that maps to the resource provider.</span></span> <span data-ttu-id="8bd44-108">Bir NULL değer, meta veriler katıştırılmış dosya kaynak sağlayıcısı olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="8bd44-108">A NULL value indicates that the file in which the metadata is embedded is the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="8bd44-109">[in] Dosyası içinde kaynak başına uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="8bd44-109">[in] The offset to the beginning of the resource within the file.</span></span> <span data-ttu-id="8bd44-110">Tek başına dosyalarında kaynaklar için bu her zaman sıfır olacak.</span><span class="sxs-lookup"><span data-stu-id="8bd44-110">For resources in standalone files, this will always be zero.</span></span> <span data-ttu-id="8bd44-111">PE (taşınabilir yürütülebilir) dosyasında katıştırılmış kaynak, kaynak cor.h üstbilgi dosyasında belirtilen konumda başlatır BLOB uzaklığı budur.</span><span class="sxs-lookup"><span data-stu-id="8bd44-111">If the resource is embedded in a PE (portable executable) file, this is an offset of the resource BLOB, which starts at the location specified in the cor.h header file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="8bd44-112">[in] Kaynak tanımı için özellik ayarlarını belirtin bayrağı değerlerin Bitsel bir birleşimi.</span><span class="sxs-lookup"><span data-stu-id="8bd44-112">[in] A bitwise combination of flag values that specify property settings for the resource definition.</span></span>  
  
 `pmdmr`  
 <span data-ttu-id="8bd44-113">[out] Döndürülen meta veri simgesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8bd44-113">[out] A pointer to the returned metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8bd44-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8bd44-114">Remarks</span></span>  
 <span data-ttu-id="8bd44-115">Bir `ManifestResource` meta veri yapısı, her derlemenin dosyaları uygulanan her bir kaynak için tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8bd44-115">One `ManifestResource` metadata structure must be defined for each resource that is implemented in each of the assembly's files.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bd44-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8bd44-116">Requirements</span></span>  
 <span data-ttu-id="8bd44-117">**Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bd44-117">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bd44-118">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8bd44-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8bd44-119">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="8bd44-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8bd44-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bd44-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bd44-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8bd44-121">See Also</span></span>  
 [<span data-ttu-id="8bd44-122">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8bd44-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
