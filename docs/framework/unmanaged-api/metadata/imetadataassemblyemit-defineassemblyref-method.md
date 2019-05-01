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
ms.openlocfilehash: e480c408c10eb9e135f260426750f7747e5d8ce5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62044778"
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a><span data-ttu-id="33f67-102">IMetaDataAssemblyEmit::DefineAssemblyRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="33f67-102">IMetaDataAssemblyEmit::DefineAssemblyRef Method</span></span>
<span data-ttu-id="33f67-103">Oluşturur bir `AssemblyRef` yapısı bu derlemeye başvuran bir derleme için meta verileri içeren ve ilişkili meta veri belirteci döndürür.</span><span class="sxs-lookup"><span data-stu-id="33f67-103">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33f67-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="33f67-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="33f67-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="33f67-105">Parameters</span></span>  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="33f67-106">[in] Başvurulan derlemenin yayımcı ortak anahtarı.</span><span class="sxs-lookup"><span data-stu-id="33f67-106">[in] The public key of the publisher of the referenced assembly.</span></span> <span data-ttu-id="33f67-107">Yardımcı işlevini [StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) Bu parametre olarak geçirmek için ortak anahtar karması almak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="33f67-107">The helper function [StrongNameTokenFromAssembly](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md) can be used to get the hash of the public key to pass as this parameter.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="33f67-108">[in] Bayt cinsinden boyutu `pbPublicKeyOrToken`.</span><span class="sxs-lookup"><span data-stu-id="33f67-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="33f67-109">[in] Derleme kullanıcı tarafından okunabilen metin adı.</span><span class="sxs-lookup"><span data-stu-id="33f67-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="33f67-110">Bu değer, 1024 karakteri aşmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="33f67-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="33f67-111">[in] Başvurulan derlemenin sürümü, platforma ve yerel ayar bilgilerini içeren ASSEMBLYMETADATA örneği.</span><span class="sxs-lookup"><span data-stu-id="33f67-111">[in] An ASSEMBLYMETADATA instance that contains the version, platform and locale information of the referenced assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="33f67-112">[in] Başvurulan bütünleştirilmiş kod ile ilişkili veri karması.</span><span class="sxs-lookup"><span data-stu-id="33f67-112">[in] The hash data associated with the referenced assembly.</span></span> <span data-ttu-id="33f67-113">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="33f67-113">Optional.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="33f67-114">[in] Bayt cinsinden boyutu `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="33f67-114">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="33f67-115">[in] Bitsel bir birleşimi [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) yürütme altyapısı davranışını etkileyen değerleri.</span><span class="sxs-lookup"><span data-stu-id="33f67-115">[in] A bitwise combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that influence the behavior of the execution engine.</span></span>  
  
 `pmdar`  
 <span data-ttu-id="33f67-116">[out] Döndürülen işaretçi `AssemblyRef` meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="33f67-116">[out] A pointer to the returned `AssemblyRef` metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33f67-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="33f67-117">Remarks</span></span>  
 <span data-ttu-id="33f67-118">Bir `AssemblyRef` meta veri yapısı, bu derlemenin başvurduğu her derleme için tanımlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="33f67-118">One `AssemblyRef` metadata structure must be defined for each assembly that this assembly references.</span></span>  
  
 <span data-ttu-id="33f67-119">Çalışma zamanında derleme çözümleyiciye bilgileri "yerleşik olarak" temsil ettikleri bir gösterge ile başvurulan bir derlemenin ayrıntılarını geçirilir.</span><span class="sxs-lookup"><span data-stu-id="33f67-119">At run time, the details of a referenced assembly are passed to the assembly resolver with an indication that they represent the "as built" information.</span></span> <span data-ttu-id="33f67-120">Derleme Çözücü sonra ilke uygulanır.</span><span class="sxs-lookup"><span data-stu-id="33f67-120">The assembly resolver then applies policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33f67-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="33f67-121">Requirements</span></span>  
 <span data-ttu-id="33f67-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33f67-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33f67-123">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="33f67-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="33f67-124">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="33f67-124">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="33f67-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33f67-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33f67-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33f67-126">See also</span></span>

- [<span data-ttu-id="33f67-127">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="33f67-127">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
