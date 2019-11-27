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
ms.openlocfilehash: f79320d5b7d2ad4ad44a79fae063ce6718490a70
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431956"
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a><span data-ttu-id="656a4-102">IMetaDataAssemblyEmit::SetAssemblyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="656a4-102">IMetaDataAssemblyEmit::SetAssemblyProps Method</span></span>
<span data-ttu-id="656a4-103">Belirtilen `Assembly` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="656a4-103">Modifies the specified `Assembly` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="656a4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="656a4-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="656a4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="656a4-105">Parameters</span></span>  
 `pma`  
 <span data-ttu-id="656a4-106">'ndaki Değiştirilecek `Assembly` meta veri yapısını belirten meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="656a4-106">[in] The metadata token that specifies the `Assembly` metadata structure to be modified.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="656a4-107">'ndaki Derlemenin yayımcısının ortak anahtarına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="656a4-107">[in] A pointer to the public key of the publisher of the assembly.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="656a4-108">'ndaki `pbPublicKey`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="656a4-108">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `ulHashAlgId`  
 <span data-ttu-id="656a4-109">'ndaki Derleme dosyalarını karma hale yüklemek için kullanılan karma algoritmanın tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="656a4-109">[in] The identifier for the hash algorithm used to hash the assembly files.</span></span>  
  
 `szName`  
 <span data-ttu-id="656a4-110">'ndaki Derlemenin insanların okunabilir metin adı.</span><span class="sxs-lookup"><span data-stu-id="656a4-110">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="656a4-111">'ndaki Derleme için sürüm, platform ve yerel ayar bilgilerini içeren ASSEMBLYMETADATA işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="656a4-111">[in] A pointer to the ASSEMBLYMETADATA that contains version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="656a4-112">'ndaki Derlemenin çeşitli özniteliklerini belirten, [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="656a4-112">[in] A bitwise combination of [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) values that specify various attributes of the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="656a4-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="656a4-113">Remarks</span></span>  
 <span data-ttu-id="656a4-114">`Assembly` meta veri yapısı oluşturmak için [IMetaDataAssemblyEmit::D efineAssembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="656a4-114">To create an `Assembly` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="656a4-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="656a4-115">Requirements</span></span>  
 <span data-ttu-id="656a4-116">**Platform:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="656a4-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="656a4-117">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="656a4-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="656a4-118">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="656a4-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="656a4-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="656a4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="656a4-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="656a4-120">See also</span></span>

- [<span data-ttu-id="656a4-121">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="656a4-121">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
