---
title: IMetaDataAssemblyEmit::DefineAssemblyRef Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssemblyRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssemblyRef
helpviewer_keywords:
- DefineAssemblyRef method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineAssemblyRef method [.NET Framework metadata]
ms.assetid: 0b284b18-0084-4b3a-912a-5ebe9f29c88b
topic_type:
- apiref
ms.openlocfilehash: 612463bca18c23fac0b086adde2d208a0fbc5ae5
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008176"
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a><span data-ttu-id="90252-102">IMetaDataAssemblyEmit::DefineAssemblyRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="90252-102">IMetaDataAssemblyEmit::DefineAssemblyRef Method</span></span>
<span data-ttu-id="90252-103">`AssemblyRef`Bu derlemenin başvurduğu derleme için meta veriler içeren bir yapı oluşturur ve ilişkili meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="90252-103">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90252-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="90252-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineAssemblyRef (  
    [in]  void                *pbPublicKeyOrToken,  
    [in]  ULONG               cbPublicKeyOrToken,  
    [in]  LPCWSTR             szName,  
    [in]  ASSEMBLYMETADATA    pMetaData,  
    [in]  void                *pbHashValue,  
    [in]  ULONG               cbHashValue,  
    [in]  DWORD               dwAssemblyRefFlags,  
    [out] mdAssemblyRef       *pmdar  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90252-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="90252-105">Parameters</span></span>  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="90252-106">'ndaki Başvurulan derlemenin yayımcısının ortak anahtarı.</span><span class="sxs-lookup"><span data-stu-id="90252-106">[in] The public key of the publisher of the referenced assembly.</span></span> <span data-ttu-id="90252-107">[StrongNameTokenFromAssembly](../strong-naming/strongnametokenfromassembly-function.md) yardımcı işlevi, bu parametre olarak geçirilecek ortak anahtarın karmasını almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="90252-107">The helper function [StrongNameTokenFromAssembly](../strong-naming/strongnametokenfromassembly-function.md) can be used to get the hash of the public key to pass as this parameter.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="90252-108">'ndaki Bayt cinsinden boyut `pbPublicKeyOrToken` .</span><span class="sxs-lookup"><span data-stu-id="90252-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="90252-109">'ndaki Derlemenin insanların okunabilir metin adı.</span><span class="sxs-lookup"><span data-stu-id="90252-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="90252-110">Bu değerin 1024 karakteri aşmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="90252-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="90252-111">'ndaki Başvurulan derlemenin sürümünü, platformunu ve yerel ayar bilgilerini içeren bir ASSEMBLYMETADATA örneği.</span><span class="sxs-lookup"><span data-stu-id="90252-111">[in] An ASSEMBLYMETADATA instance that contains the version, platform and locale information of the referenced assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="90252-112">'ndaki Başvurulan derlemeyle ilişkili karma verileri.</span><span class="sxs-lookup"><span data-stu-id="90252-112">[in] The hash data associated with the referenced assembly.</span></span> <span data-ttu-id="90252-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="90252-113">Optional.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="90252-114">'ndaki Bayt cinsinden boyut `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="90252-114">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="90252-115">'ndaki Yürütme altyapısının davranışını etkileyen, [CorAssemblyFlags](corassemblyflags-enumeration.md) değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="90252-115">[in] A bitwise combination of [CorAssemblyFlags](corassemblyflags-enumeration.md) values that influence the behavior of the execution engine.</span></span>  
  
 `pmdar`  
 <span data-ttu-id="90252-116">dışı Döndürülen `AssemblyRef` meta veri belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="90252-116">[out] A pointer to the returned `AssemblyRef` metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90252-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="90252-117">Remarks</span></span>  
 <span data-ttu-id="90252-118">`AssemblyRef`Bu derlemenin başvurduğu her derleme için bir meta veri yapısının tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="90252-118">One `AssemblyRef` metadata structure must be defined for each assembly that this assembly references.</span></span>  
  
 <span data-ttu-id="90252-119">Çalışma zamanında, başvurulan bir derlemenin ayrıntıları, derleme çözümleyiciye "yerleşik olarak" bilgi olarak temsil ettikleri bir bildirim ile geçirilir.</span><span class="sxs-lookup"><span data-stu-id="90252-119">At run time, the details of a referenced assembly are passed to the assembly resolver with an indication that they represent the "as built" information.</span></span> <span data-ttu-id="90252-120">Derleme çözümleyici ilke uygular.</span><span class="sxs-lookup"><span data-stu-id="90252-120">The assembly resolver then applies policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90252-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="90252-121">Requirements</span></span>  
 <span data-ttu-id="90252-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90252-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90252-123">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="90252-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="90252-124">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="90252-124">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="90252-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90252-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90252-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90252-126">See also</span></span>

- [<span data-ttu-id="90252-127">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="90252-127">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
