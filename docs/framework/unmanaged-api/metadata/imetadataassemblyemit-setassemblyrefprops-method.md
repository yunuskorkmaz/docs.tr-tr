---
title: "IMetaDataAssemblyEmit::SetAssemblyRefProps Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.SetAssemblyRefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::SetAssemblyRefProps
helpviewer_keywords:
- SetAssemblyRefProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 70a32bf3-9051-4f96-ae87-11356d06a073
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 84b6c0d748578b717a128ff3b808977ba902c6dc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a><span data-ttu-id="582de-102">IMetaDataAssemblyEmit::SetAssemblyRefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="582de-102">IMetaDataAssemblyEmit::SetAssemblyRefProps Method</span></span>
<span data-ttu-id="582de-103">Belirtilen değiştirir `AssemblyRef` meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="582de-103">Modifies the specified `AssemblyRef` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="582de-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="582de-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyRefProps (  
    [in] mdAssemblyRef              ar,  
    [in] const void                 *pbPublicKeyOrToken,  
    [in] ULONG                      cbPublicKeyOrToken,  
    [in] LPCWSTR                    szName,   
    [in] const ASSEMBLYMETADATA     *pMetaData,   
    [in] const void                 *pbHashValue,  
    [in] ULONG                      cbHashValue,  
    [in] DWORD                      dwAssemblyRefFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="582de-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="582de-105">Parameters</span></span>  
 `ar`  
 <span data-ttu-id="582de-106">[in] Belirtir meta veri simgesi `AssemblyRef` değiştirilecek meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="582de-106">[in] The metadata token that specifies the `AssemblyRef` metadata structure to be modified.</span></span>  
  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="582de-107">[in] Başvurulan derlemeyi yayımcısı ortak anahtarı.</span><span class="sxs-lookup"><span data-stu-id="582de-107">[in] The public key of the publisher of the referenced assembly.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="582de-108">[in] Bayt cinsinden boyutu `pbPublicKeyOrToken`.</span><span class="sxs-lookup"><span data-stu-id="582de-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="582de-109">[in] Derleme okunabilir metni adı.</span><span class="sxs-lookup"><span data-stu-id="582de-109">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="582de-110">[in] Bir işaretçi ASSEMBLYMETADATA örneğine derleme için sürüm, platform ve yerel ayar bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="582de-110">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="582de-111">[in] Derleme ile ilişkili karma verileri bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="582de-111">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="582de-112">[in] Bayt cinsinden boyutu `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="582de-112">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="582de-113">[in] Bit düzeyinde bileşimini [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) başvurulan derlemeyi özniteliklerini belirten değerleri.</span><span class="sxs-lookup"><span data-stu-id="582de-113">[in] A bitwise combination of [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) values that specify attributes of the referenced assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="582de-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="582de-114">Remarks</span></span>  
 <span data-ttu-id="582de-115">Oluşturmak için bir `AssemblyRef` meta veri yapısı, kullanım [Imetadataassemblyemit::defineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="582de-115">To create an `AssemblyRef` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="582de-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="582de-116">Requirements</span></span>  
 <span data-ttu-id="582de-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="582de-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="582de-118">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="582de-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="582de-119">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="582de-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="582de-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="582de-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="582de-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="582de-121">See Also</span></span>  
 [<span data-ttu-id="582de-122">Imetadataassemblyemit arabirimi</span><span class="sxs-lookup"><span data-stu-id="582de-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
