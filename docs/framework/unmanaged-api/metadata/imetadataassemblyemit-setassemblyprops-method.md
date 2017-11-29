---
title: "IMetaDataAssemblyEmit::SetAssemblyProps Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.SetAssemblyProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyProps method [.NET Framework metadata]
ms.assetid: 91b633d7-9e75-43c3-a8d2-2144984e5f9e
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d2c9336855d706a9861d4e832e5f0234cdf04db7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a><span data-ttu-id="497ce-102">IMetaDataAssemblyEmit::SetAssemblyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="497ce-102">IMetaDataAssemblyEmit::SetAssemblyProps Method</span></span>
<span data-ttu-id="497ce-103">Belirtilen değiştirir `Assembly` meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="497ce-103">Modifies the specified `Assembly` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="497ce-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="497ce-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyProps (  
    [in] mdAssembly               pma,  
    [in] const void               *pbPublicKey,  
    [in] ULONG                    cbPublicKey,  
    [in] ULONG                    ulHashAlgId,  
    [in] LPCWSTR                  szName,  
    [in] const ASSEMBLYMETADATA   *pMetaData,  
    [in] DWORD                    dwAssemblyFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="497ce-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="497ce-105">Parameters</span></span>  
 `pma`  
 <span data-ttu-id="497ce-106">[in] Belirtir meta veri simgesi `Assembly` değiştirilecek meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="497ce-106">[in] The metadata token that specifies the `Assembly` metadata structure to be modified.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="497ce-107">[in] Derleme publisher'ın ortak anahtar için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="497ce-107">[in] A pointer to the public key of the publisher of the assembly.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="497ce-108">[in] Bayt cinsinden boyutu `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="497ce-108">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `ulHashAlgId`  
 <span data-ttu-id="497ce-109">[in] Derleme dosyalarını karması için kullanılan karma algoritma tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="497ce-109">[in] The identifier for the hash algorithm used to hash the assembly files.</span></span>  
  
 `szName`  
 <span data-ttu-id="497ce-110">[in] Derleme okunabilir metni adı.</span><span class="sxs-lookup"><span data-stu-id="497ce-110">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="497ce-111">[in] Derleme sürümü, platform ve yerel ayar bilgilerini içeren ASSEMBLYMETADATA gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="497ce-111">[in] A pointer to the ASSEMBLYMETADATA that contains version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="497ce-112">[in] Bit düzeyinde bileşimini [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) derlemenin çeşitli öznitelikler belirten değerleri.</span><span class="sxs-lookup"><span data-stu-id="497ce-112">[in] A bitwise combination of [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) values that specify various attributes of the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="497ce-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="497ce-113">Remarks</span></span>  
 <span data-ttu-id="497ce-114">Oluşturmak için bir `Assembly` meta veri yapısı, kullanım [Imetadataassemblyemit::defineassembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="497ce-114">To create an `Assembly` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="497ce-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="497ce-115">Requirements</span></span>  
 <span data-ttu-id="497ce-116">**Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="497ce-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="497ce-117">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="497ce-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="497ce-118">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="497ce-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="497ce-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="497ce-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="497ce-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="497ce-120">See Also</span></span>  
 [<span data-ttu-id="497ce-121">Imetadataassemblyemit arabirimi</span><span class="sxs-lookup"><span data-stu-id="497ce-121">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
