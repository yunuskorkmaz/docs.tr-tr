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
ms.openlocfilehash: 6ad6bbb8a4c69f575bbeba3a297c46e049a97325
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176051"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a><span data-ttu-id="c5694-102">IMetaDataAssemblyEmit::SetAssemblyRefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c5694-102">IMetaDataAssemblyEmit::SetAssemblyRefProps Method</span></span>
<span data-ttu-id="c5694-103">Belirtilen `AssemblyRef` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="c5694-103">Modifies the specified `AssemblyRef` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5694-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5694-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="c5694-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c5694-105">Parameters</span></span>  
 `ar`  
 <span data-ttu-id="c5694-106">[içinde] Değiştirilecek `AssemblyRef` meta veri yapısını belirten meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="c5694-106">[in] The metadata token that specifies the `AssemblyRef` metadata structure to be modified.</span></span>  
  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="c5694-107">[içinde] Başvurulan derlemenin yayımcısının ortak anahtarı.</span><span class="sxs-lookup"><span data-stu-id="c5694-107">[in] The public key of the publisher of the referenced assembly.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="c5694-108">[içinde] `pbPublicKeyOrToken`Baytboyutu.</span><span class="sxs-lookup"><span data-stu-id="c5694-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="c5694-109">[içinde] Derlemenin insan tarafından okunabilen metin adı.</span><span class="sxs-lookup"><span data-stu-id="c5694-109">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="c5694-110">[içinde] Derlemenin sürümünü, platformlarını ve yerel bilgilerini içeren bir ASSEMBLYMETADATA örneğine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c5694-110">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="c5694-111">[içinde] Derleme ile ilişkili karma verilere işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c5694-111">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="c5694-112">[içinde] `pbHashValue`Baytboyutu.</span><span class="sxs-lookup"><span data-stu-id="c5694-112">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="c5694-113">[içinde] Başvurulan derlemenin özniteliklerini belirten [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) değerlerinin bityişli bir birleşimi.</span><span class="sxs-lookup"><span data-stu-id="c5694-113">[in] A bitwise combination of [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) values that specify attributes of the referenced assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5694-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5694-114">Remarks</span></span>  
 <span data-ttu-id="c5694-115">Meta `AssemblyRef` veri yapısı oluşturmak için [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c5694-115">To create an `AssemblyRef` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5694-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c5694-116">Requirements</span></span>  
 <span data-ttu-id="c5694-117">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5694-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5694-118">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c5694-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c5694-119">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="c5694-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c5694-120">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5694-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5694-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5694-121">See also</span></span>

- [<span data-ttu-id="c5694-122">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5694-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
