---
title: "IMetaDataAssemblyEmit::DefineManifestResource Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineManifestResource
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineManifestResource
helpviewer_keywords:
- DefineManifestResource method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineManifestResource method [.NET Framework metadata]
ms.assetid: 27f6d295-0fe9-4cda-b77e-6e7d5c53df09
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 516099f0735e83982fcbab62936bb398c4f7b02d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a><span data-ttu-id="57011-102">IMetaDataAssemblyEmit::DefineManifestResource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="57011-102">IMetaDataAssemblyEmit::DefineManifestResource Method</span></span>
<span data-ttu-id="57011-103">Oluşturur bir `ManifestResource` belirtilen bildirim kaynağı için meta veriler içeren yapısı ve ilişkili meta veri simgesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="57011-103">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57011-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="57011-104">Syntax</span></span>  
  
```  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,   
    [in] mdToken                tkImplementation,   
    [in] DWORD                  dwOffset,   
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57011-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="57011-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="57011-106">[in] Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="57011-106">[in] The name of the resource.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="57011-107">[in] Meta veri simgesi türü `mdtFile` veya `mdtAssemblyRef` kaynak sağlayıcıya eşler.</span><span class="sxs-lookup"><span data-stu-id="57011-107">[in] A metadata token of type `mdtFile` or `mdtAssemblyRef` that maps to the resource provider.</span></span> <span data-ttu-id="57011-108">Bir NULL değer, meta veriler katıştırılmış dosya kaynak sağlayıcısı olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="57011-108">A NULL value indicates that the file in which the metadata is embedded is the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="57011-109">[in] Dosyası içinde kaynak başına uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="57011-109">[in] The offset to the beginning of the resource within the file.</span></span> <span data-ttu-id="57011-110">Tek başına dosyalarında kaynaklar için bu her zaman sıfır olacak.</span><span class="sxs-lookup"><span data-stu-id="57011-110">For resources in standalone files, this will always be zero.</span></span> <span data-ttu-id="57011-111">PE (taşınabilir yürütülebilir) dosyasında katıştırılmış kaynak, kaynak cor.h üstbilgi dosyasında belirtilen konumda başlatır BLOB uzaklığı budur.</span><span class="sxs-lookup"><span data-stu-id="57011-111">If the resource is embedded in a PE (portable executable) file, this is an offset of the resource BLOB, which starts at the location specified in the cor.h header file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="57011-112">[in] Kaynak tanımı için özellik ayarlarını belirtin bayrağı değerlerin Bitsel bir birleşimi.</span><span class="sxs-lookup"><span data-stu-id="57011-112">[in] A bitwise combination of flag values that specify property settings for the resource definition.</span></span>  
  
 `pmdmr`  
 <span data-ttu-id="57011-113">[out] Döndürülen meta veri simgesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="57011-113">[out] A pointer to the returned metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57011-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="57011-114">Remarks</span></span>  
 <span data-ttu-id="57011-115">Bir `ManifestResource` meta veri yapısı, her derlemenin dosyaları uygulanan her bir kaynak için tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="57011-115">One `ManifestResource` metadata structure must be defined for each resource that is implemented in each of the assembly's files.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57011-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="57011-116">Requirements</span></span>  
 <span data-ttu-id="57011-117">**Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57011-117">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57011-118">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="57011-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="57011-119">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="57011-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="57011-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57011-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57011-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="57011-121">See Also</span></span>  
 [<span data-ttu-id="57011-122">Imetadataassemblyemit arabirimi</span><span class="sxs-lookup"><span data-stu-id="57011-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
