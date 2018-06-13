---
title: IMetaDataAssemblyEmit::SetAssemblyProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyProps method [.NET Framework metadata]
ms.assetid: 91b633d7-9e75-43c3-a8d2-2144984e5f9e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6f8132296035e9ddcdcad76d93ed05358beb0b81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448239"
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a><span data-ttu-id="d6e53-102">IMetaDataAssemblyEmit::SetAssemblyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d6e53-102">IMetaDataAssemblyEmit::SetAssemblyProps Method</span></span>
<span data-ttu-id="d6e53-103">Belirtilen değiştirir `Assembly` meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="d6e53-103">Modifies the specified `Assembly` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6e53-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6e53-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="d6e53-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d6e53-105">Parameters</span></span>  
 `pma`  
 <span data-ttu-id="d6e53-106">[in] Belirtir meta veri simgesi `Assembly` değiştirilecek meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="d6e53-106">[in] The metadata token that specifies the `Assembly` metadata structure to be modified.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="d6e53-107">[in] Derleme publisher'ın ortak anahtar için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d6e53-107">[in] A pointer to the public key of the publisher of the assembly.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="d6e53-108">[in] Bayt cinsinden boyutu `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="d6e53-108">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `ulHashAlgId`  
 <span data-ttu-id="d6e53-109">[in] Derleme dosyalarını karması için kullanılan karma algoritma tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="d6e53-109">[in] The identifier for the hash algorithm used to hash the assembly files.</span></span>  
  
 `szName`  
 <span data-ttu-id="d6e53-110">[in] Derleme okunabilir metni adı.</span><span class="sxs-lookup"><span data-stu-id="d6e53-110">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="d6e53-111">[in] Derleme sürümü, platform ve yerel ayar bilgilerini içeren ASSEMBLYMETADATA gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d6e53-111">[in] A pointer to the ASSEMBLYMETADATA that contains version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="d6e53-112">[in] Bit düzeyinde bileşimini [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) derlemenin çeşitli öznitelikler belirten değerleri.</span><span class="sxs-lookup"><span data-stu-id="d6e53-112">[in] A bitwise combination of [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) values that specify various attributes of the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6e53-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d6e53-113">Remarks</span></span>  
 <span data-ttu-id="d6e53-114">Oluşturmak için bir `Assembly` meta veri yapısı, kullanım [Imetadataassemblyemit::defineassembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d6e53-114">To create an `Assembly` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6e53-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d6e53-115">Requirements</span></span>  
 <span data-ttu-id="d6e53-116">**Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6e53-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6e53-117">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d6e53-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d6e53-118">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="d6e53-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d6e53-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6e53-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6e53-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d6e53-120">See Also</span></span>  
 [<span data-ttu-id="d6e53-121">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6e53-121">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
