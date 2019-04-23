---
title: IMetaDataAssemblyEmit::DefineAssembly Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b95a583aec87e3ba3e247d1ef800302b62657837
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59176013"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="ea89f-102">IMetaDataAssemblyEmit::DefineAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ea89f-102">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>
<span data-ttu-id="ea89f-103">Oluşturur bir `Assembly` belirtilen derleme için meta veriler içeren yapı ve ilişkili meta veri belirteci döndürür.</span><span class="sxs-lookup"><span data-stu-id="ea89f-103">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea89f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ea89f-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ea89f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ea89f-105">Parameters</span></span>  
 `pbPublicKey`  
 <span data-ttu-id="ea89f-106">[in] Derleme verilemiş, derleme veya NULL bir yayıncıyı ortak anahtarı.</span><span class="sxs-lookup"><span data-stu-id="ea89f-106">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="ea89f-107">[in] Bayt cinsinden boyutu `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="ea89f-107">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="ea89f-108">[in] Derleme ya da NULL SHA-1 algoritmasını belirtmek için dosyaları şifrelemek için kullanılacak karma algoritması tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="ea89f-108">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="ea89f-109">[in] Derleme kullanıcı tarafından okunabilen metin adı.</span><span class="sxs-lookup"><span data-stu-id="ea89f-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="ea89f-110">Bu değer, 1024 karakteri aşmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ea89f-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="ea89f-111">[in] Derleme sürümü, platforma ve yerel ayar bilgilerini içeren ASSEMBLYMETADATA örneğine bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ea89f-111">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="ea89f-112">[in] Bir birleşimi [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) değerleri derleme özellikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ea89f-112">[in] A combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="ea89f-113">[out] Meta veri belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ea89f-113">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea89f-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ea89f-114">Remarks</span></span>  
 <span data-ttu-id="ea89f-115">Yalnızca bir `Assembly` meta veri yapısı bir bildirimi içinde tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="ea89f-115">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea89f-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ea89f-116">Requirements</span></span>  
 <span data-ttu-id="ea89f-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea89f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea89f-118">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="ea89f-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ea89f-119">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ea89f-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ea89f-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea89f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea89f-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea89f-121">See also</span></span>

- [<span data-ttu-id="ea89f-122">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ea89f-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
