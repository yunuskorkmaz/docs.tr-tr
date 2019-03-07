---
title: IMetaDataAssemblyEmit::SetAssemblyRefProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyRefProps
helpviewer_keywords:
- SetAssemblyRefProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 70a32bf3-9051-4f96-ae87-11356d06a073
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b6c29861faa469f03ca5f2d3cb18e95b3e78f52
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489910"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a><span data-ttu-id="4e02b-102">IMetaDataAssemblyEmit::SetAssemblyRefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4e02b-102">IMetaDataAssemblyEmit::SetAssemblyRefProps Method</span></span>
<span data-ttu-id="4e02b-103">Belirtilen değiştirir `AssemblyRef` meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="4e02b-103">Modifies the specified `AssemblyRef` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e02b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4e02b-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="4e02b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4e02b-105">Parameters</span></span>  
 `ar`  
 <span data-ttu-id="4e02b-106">[in] Belirten bir meta veri belirteci `AssemblyRef` değiştirilecek meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="4e02b-106">[in] The metadata token that specifies the `AssemblyRef` metadata structure to be modified.</span></span>  
  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="4e02b-107">[in] Başvurulan derlemenin yayımcı ortak anahtarı.</span><span class="sxs-lookup"><span data-stu-id="4e02b-107">[in] The public key of the publisher of the referenced assembly.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="4e02b-108">[in] Bayt cinsinden boyutu `pbPublicKeyOrToken`.</span><span class="sxs-lookup"><span data-stu-id="4e02b-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="4e02b-109">[in] Derleme kullanıcı tarafından okunabilen metin adı.</span><span class="sxs-lookup"><span data-stu-id="4e02b-109">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="4e02b-110">[in] Derleme sürümü, platforma ve yerel ayar bilgilerini içeren ASSEMBLYMETADATA örneğine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4e02b-110">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="4e02b-111">[in] Bütünleştirilmiş kod ile ilişkili veri karması için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4e02b-111">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="4e02b-112">[in] Bayt cinsinden boyutu `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="4e02b-112">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="4e02b-113">[in] Bitsel bir birleşimi [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) başvurulan derleme özniteliklerini belirten değerleri.</span><span class="sxs-lookup"><span data-stu-id="4e02b-113">[in] A bitwise combination of [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) values that specify attributes of the referenced assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e02b-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4e02b-114">Remarks</span></span>  
 <span data-ttu-id="4e02b-115">Oluşturmak için bir `AssemblyRef` meta veri yapısı, kullanım [Imetadataassemblyemit::defineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4e02b-115">To create an `AssemblyRef` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e02b-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4e02b-116">Requirements</span></span>  
 <span data-ttu-id="4e02b-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e02b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e02b-118">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="4e02b-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4e02b-119">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="4e02b-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4e02b-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e02b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e02b-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e02b-121">See also</span></span>
- [<span data-ttu-id="4e02b-122">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4e02b-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
