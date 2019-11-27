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
ms.openlocfilehash: 5434aa2d12bd9a29a8c2fc784421442469ceb1ce
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440552"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a><span data-ttu-id="6558b-102">IMetaDataAssemblyEmit::SetAssemblyRefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6558b-102">IMetaDataAssemblyEmit::SetAssemblyRefProps Method</span></span>
<span data-ttu-id="6558b-103">Belirtilen `AssemblyRef` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="6558b-103">Modifies the specified `AssemblyRef` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6558b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6558b-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="6558b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6558b-105">Parameters</span></span>  
 `ar`  
 <span data-ttu-id="6558b-106">'ndaki Değiştirilecek `AssemblyRef` meta veri yapısını belirten meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="6558b-106">[in] The metadata token that specifies the `AssemblyRef` metadata structure to be modified.</span></span>  
  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="6558b-107">'ndaki Başvurulan derlemenin yayımcısının ortak anahtarı.</span><span class="sxs-lookup"><span data-stu-id="6558b-107">[in] The public key of the publisher of the referenced assembly.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="6558b-108">'ndaki `pbPublicKeyOrToken`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="6558b-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="6558b-109">'ndaki Derlemenin insanların okunabilir metin adı.</span><span class="sxs-lookup"><span data-stu-id="6558b-109">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="6558b-110">'ndaki Derleme için sürüm, platform ve yerel ayar bilgilerini içeren bir ASSEMBLYMETADATA örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6558b-110">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="6558b-111">'ndaki Derlemeyle ilişkili karma verileri işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="6558b-111">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="6558b-112">'ndaki `pbHashValue`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="6558b-112">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="6558b-113">'ndaki Başvurulan derlemenin özniteliklerini belirten, [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="6558b-113">[in] A bitwise combination of [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) values that specify attributes of the referenced assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6558b-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6558b-114">Remarks</span></span>  
 <span data-ttu-id="6558b-115">`AssemblyRef` meta veri yapısı oluşturmak için [IMetaDataAssemblyEmit::D efineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="6558b-115">To create an `AssemblyRef` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6558b-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6558b-116">Requirements</span></span>  
 <span data-ttu-id="6558b-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6558b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6558b-118">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6558b-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6558b-119">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="6558b-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6558b-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6558b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6558b-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6558b-121">See also</span></span>

- [<span data-ttu-id="6558b-122">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6558b-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
