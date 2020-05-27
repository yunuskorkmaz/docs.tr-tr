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
ms.openlocfilehash: 17c91200730431c4c6e230b8c1561ce7c4863868
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008189"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="8e5d2-102">IMetaDataAssemblyEmit::DefineAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8e5d2-102">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>
<span data-ttu-id="8e5d2-103">`Assembly`Belirtilen derleme için meta veriler içeren bir yapı oluşturur ve ilişkili meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="8e5d2-103">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e5d2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8e5d2-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="8e5d2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8e5d2-105">Parameters</span></span>  
 `pbPublicKey`  
 <span data-ttu-id="8e5d2-106">'ndaki Derlemenin yayımcısını tanımlayan ortak anahtar veya derleme kesin olarak adlandırılmamışsa NULL.</span><span class="sxs-lookup"><span data-stu-id="8e5d2-106">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="8e5d2-107">'ndaki Bayt cinsinden boyut `pbPublicKey` .</span><span class="sxs-lookup"><span data-stu-id="8e5d2-107">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="8e5d2-108">'ndaki Derlemedeki dosyaları şifrelemek için kullanılan karma algoritmanın tanımlayıcısı ya da SHA-1 algoritmasını belirtmek için NULL.</span><span class="sxs-lookup"><span data-stu-id="8e5d2-108">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="8e5d2-109">'ndaki Derlemenin insanların okunabilir metin adı.</span><span class="sxs-lookup"><span data-stu-id="8e5d2-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="8e5d2-110">Bu değerin 1024 karakteri aşmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8e5d2-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="8e5d2-111">'ndaki Derleme için sürüm, platform ve yerel ayar bilgilerini içeren bir ASSEMBLYMETADATA örneğine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8e5d2-111">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="8e5d2-112">'ndaki Derlemenin özelliklerini tanımlayan [CorAssemblyFlags](corassemblyflags-enumeration.md) değerlerinin birleşimi.</span><span class="sxs-lookup"><span data-stu-id="8e5d2-112">[in] A combination of [CorAssemblyFlags](corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="8e5d2-113">dışı Meta veri belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8e5d2-113">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e5d2-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8e5d2-114">Remarks</span></span>  
 <span data-ttu-id="8e5d2-115">`Assembly`Bir bildirim içinde yalnızca bir meta veri yapısı tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="8e5d2-115">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e5d2-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8e5d2-116">Requirements</span></span>  
 <span data-ttu-id="8e5d2-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e5d2-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e5d2-118">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8e5d2-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8e5d2-119">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="8e5d2-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8e5d2-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e5d2-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e5d2-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e5d2-121">See also</span></span>

- [<span data-ttu-id="8e5d2-122">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8e5d2-122">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
