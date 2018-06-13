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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b6675d50d3222a43abc8838c3c86cb825d2dad16
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445728"
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a><span data-ttu-id="66456-102">IMetaDataAssemblyEmit::DefineAssemblyRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66456-102">IMetaDataAssemblyEmit::DefineAssemblyRef Method</span></span>
<span data-ttu-id="66456-103">Oluşturur bir `AssemblyRef` Bu bütünleştirilmiş koduna başvuruyor, derleme için meta verileri içeren yapısını ve ilişkili meta veri simgesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="66456-103">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66456-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="66456-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="66456-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="66456-105">Parameters</span></span>  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="66456-106">[in] Başvurulan derlemeyi yayımcısı ortak anahtarı.</span><span class="sxs-lookup"><span data-stu-id="66456-106">[in] The public key of the publisher of the referenced assembly.</span></span> <span data-ttu-id="66456-107">Yardımcı işlevini [StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) Bu parametre olarak geçirmek için ortak anahtar karma almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66456-107">The helper function [StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) can be used to get the hash of the public key to pass as this parameter.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="66456-108">[in] Bayt cinsinden boyutu `pbPublicKeyOrToken`.</span><span class="sxs-lookup"><span data-stu-id="66456-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="66456-109">[in] Derleme okunabilir metni adı.</span><span class="sxs-lookup"><span data-stu-id="66456-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="66456-110">Bu değer 1024 karakterden uzun olamaz.</span><span class="sxs-lookup"><span data-stu-id="66456-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="66456-111">[in] Başvurulan derlemeyi sürümü, platform ve yerel ayar bilgileri içeren bir ASSEMBLYMETADATA örneği.</span><span class="sxs-lookup"><span data-stu-id="66456-111">[in] An ASSEMBLYMETADATA instance that contains the version, platform and locale information of the referenced assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="66456-112">[in] Başvurulan derlemesiyle ilişkilendirilmiş veri karması.</span><span class="sxs-lookup"><span data-stu-id="66456-112">[in] The hash data associated with the referenced assembly.</span></span> <span data-ttu-id="66456-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="66456-113">Optional.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="66456-114">[in] Bayt cinsinden boyutu `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="66456-114">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="66456-115">[in] Bit düzeyinde bileşimini [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) yürütme altyapısı davranışını etkilemek değerleri.</span><span class="sxs-lookup"><span data-stu-id="66456-115">[in] A bitwise combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that influence the behavior of the execution engine.</span></span>  
  
 `pmdar`  
 <span data-ttu-id="66456-116">[out] Bir işaretçi döndürülen `AssemblyRef` meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="66456-116">[out] A pointer to the returned `AssemblyRef` metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66456-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="66456-117">Remarks</span></span>  
 <span data-ttu-id="66456-118">Bir `AssemblyRef` meta veri yapısı bu derlemeye başvuran her derlemesi için tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="66456-118">One `AssemblyRef` metadata structure must be defined for each assembly that this assembly references.</span></span>  
  
 <span data-ttu-id="66456-119">Çalışma zamanında "yerleşik haliyle" bilgi temsil ettiğini bir göstergesi ile derleme çözümleyiciye başvurulan bir derleme ayrıntılarını geçirilir.</span><span class="sxs-lookup"><span data-stu-id="66456-119">At run time, the details of a referenced assembly are passed to the assembly resolver with an indication that they represent the "as built" information.</span></span> <span data-ttu-id="66456-120">Derleme Çözümleyicisi sonra ilke uygulanır.</span><span class="sxs-lookup"><span data-stu-id="66456-120">The assembly resolver then applies policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66456-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="66456-121">Requirements</span></span>  
 <span data-ttu-id="66456-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66456-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66456-123">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="66456-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="66456-124">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="66456-124">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="66456-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66456-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66456-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="66456-126">See Also</span></span>  
 [<span data-ttu-id="66456-127">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="66456-127">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
