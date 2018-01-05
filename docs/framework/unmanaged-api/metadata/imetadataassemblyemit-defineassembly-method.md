---
title: "IMetaDataAssemblyEmit::DefineAssembly Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineAssembly
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 35bc85cdc4380ee112b7095866c05e5d7639200b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="ad99d-102">IMetaDataAssemblyEmit::DefineAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad99d-102">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>
<span data-ttu-id="ad99d-103">Oluşturur bir `Assembly` için belirtilen derlemeyi meta veriler içeren yapısı ve ilişkili meta veri simgesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="ad99d-103">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad99d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ad99d-104">Syntax</span></span>  
  
```  
HRESULT DefineAssembly (  
    [in]  void                 *pbPublicKey,  
    [in]  ULONG                cbPublicKey,  
    [in]  ULONG                uHashAlgId,  
    [in]  LPCWSTR              szName,   
    [in]  ASSEMBLYMETADATA     *pMetaData,  
    [in]  DWORD                dwAssemblyFlags,  
    [out] mdAssembly           *pmda  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad99d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ad99d-105">Parameters</span></span>  
 `pbPublicKey`  
 <span data-ttu-id="ad99d-106">[in] Derleme güçlü olarak adlandırılmamış, derleme ya da NULL yayımcıyı tanımlayan ortak anahtarı.</span><span class="sxs-lookup"><span data-stu-id="ad99d-106">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="ad99d-107">[in] Bayt cinsinden boyutu `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="ad99d-107">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="ad99d-108">[in] Derleme veya NULL SHA-1 algoritmasını belirtmek için dosyaları şifrelemek için kullanılacak karma algoritma tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="ad99d-108">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="ad99d-109">[in] Derleme okunabilir metni adı.</span><span class="sxs-lookup"><span data-stu-id="ad99d-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="ad99d-110">Bu değer 1024 karakterden uzun olamaz.</span><span class="sxs-lookup"><span data-stu-id="ad99d-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="ad99d-111">[in] Bir işaretçi ASSEMBLYMETADATA örneğine derleme için sürüm, platform ve yerel ayar bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="ad99d-111">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="ad99d-112">[in] Bir birleşimini [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) derleme özelliklerini açıklayan değerleri.</span><span class="sxs-lookup"><span data-stu-id="ad99d-112">[in] A combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="ad99d-113">[out] Meta veri simgesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ad99d-113">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad99d-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ad99d-114">Remarks</span></span>  
 <span data-ttu-id="ad99d-115">Yalnızca bir `Assembly` meta veri yapısı içinde bir bildirim tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="ad99d-115">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad99d-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad99d-116">Requirements</span></span>  
 <span data-ttu-id="ad99d-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad99d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad99d-118">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ad99d-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ad99d-119">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ad99d-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ad99d-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad99d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad99d-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ad99d-121">See Also</span></span>  
 [<span data-ttu-id="ad99d-122">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad99d-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
