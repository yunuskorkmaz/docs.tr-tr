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
ms.openlocfilehash: 14bd352099890e4ca36321d550b8e982d4373231
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177896"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="24c9b-102">IMetaDataAssemblyEmit::DefineAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="24c9b-102">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>
<span data-ttu-id="24c9b-103">Belirtilen derleme `Assembly` için meta veri içeren bir yapı oluşturur ve ilişkili meta veri belirteci döndürür.</span><span class="sxs-lookup"><span data-stu-id="24c9b-103">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24c9b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="24c9b-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="24c9b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="24c9b-105">Parameters</span></span>  
 `pbPublicKey`  
 <span data-ttu-id="24c9b-106">[içinde] Derlemenin yayımcısını tanımlayan ortak anahtar veya derleme nin güçlü bir şekilde adlandırılmadıysa NULL.</span><span class="sxs-lookup"><span data-stu-id="24c9b-106">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="24c9b-107">[içinde] `pbPublicKey`Baytboyutu.</span><span class="sxs-lookup"><span data-stu-id="24c9b-107">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="24c9b-108">[içinde] Derlemedeki dosyaları şifrelemek için kullanılacak karma algoritmanın tanımlayıcısı veya SHA-1 algoritmasını belirtmek için NULL.</span><span class="sxs-lookup"><span data-stu-id="24c9b-108">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="24c9b-109">[içinde] Derlemenin insan tarafından okunabilen metin adı.</span><span class="sxs-lookup"><span data-stu-id="24c9b-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="24c9b-110">Bu değer 1024 karakteri geçmemelidir.</span><span class="sxs-lookup"><span data-stu-id="24c9b-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="24c9b-111">[içinde] Derlemenin sürümünü, platformlarını ve yerel bilgilerini içeren bir ASSEMBLYMETADATA örneğine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="24c9b-111">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="24c9b-112">[içinde] Derlemenin özelliklerini açıklayan [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) değerlerinin birleşimi.</span><span class="sxs-lookup"><span data-stu-id="24c9b-112">[in] A combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="24c9b-113">[çıkış] Meta veri belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="24c9b-113">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24c9b-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="24c9b-114">Remarks</span></span>  
 <span data-ttu-id="24c9b-115">Bir `Assembly` bildirim içinde yalnızca bir meta veri yapısı tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="24c9b-115">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24c9b-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="24c9b-116">Requirements</span></span>  
 <span data-ttu-id="24c9b-117">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24c9b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24c9b-118">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="24c9b-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="24c9b-119">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="24c9b-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="24c9b-120">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24c9b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24c9b-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24c9b-121">See also</span></span>

- [<span data-ttu-id="24c9b-122">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="24c9b-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
