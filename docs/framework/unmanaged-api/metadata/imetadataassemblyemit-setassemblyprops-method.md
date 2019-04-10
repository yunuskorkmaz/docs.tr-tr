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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3361212f9a7f7ff0739e8544419a2b67abc8f457
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214656"
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a><span data-ttu-id="145ae-102">IMetaDataAssemblyEmit::SetAssemblyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="145ae-102">IMetaDataAssemblyEmit::SetAssemblyProps Method</span></span>
<span data-ttu-id="145ae-103">Belirtilen değiştirir `Assembly` meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="145ae-103">Modifies the specified `Assembly` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="145ae-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="145ae-104">Syntax</span></span>  
  
```  
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
  
## <a name="parameters"></a><span data-ttu-id="145ae-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="145ae-105">Parameters</span></span>  
 `pma`  
 <span data-ttu-id="145ae-106">[in] Belirten bir meta veri belirteci `Assembly` değiştirilecek meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="145ae-106">[in] The metadata token that specifies the `Assembly` metadata structure to be modified.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="145ae-107">[in] Derlemenin yayımcı ortak anahtarı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="145ae-107">[in] A pointer to the public key of the publisher of the assembly.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="145ae-108">[in] Bayt cinsinden boyutu `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="145ae-108">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `ulHashAlgId`  
 <span data-ttu-id="145ae-109">[in] Derleme dosyalarını karması için kullanılan karma algoritması için tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="145ae-109">[in] The identifier for the hash algorithm used to hash the assembly files.</span></span>  
  
 `szName`  
 <span data-ttu-id="145ae-110">[in] Derleme kullanıcı tarafından okunabilen metin adı.</span><span class="sxs-lookup"><span data-stu-id="145ae-110">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="145ae-111">[in] Derleme sürümü, platforma ve yerel ayar bilgilerini içeren ASSEMBLYMETADATA işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="145ae-111">[in] A pointer to the ASSEMBLYMETADATA that contains version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="145ae-112">[in] Bitsel bir birleşimi [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) derleme çeşitli özniteliklerini belirten değerleri.</span><span class="sxs-lookup"><span data-stu-id="145ae-112">[in] A bitwise combination of [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) values that specify various attributes of the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="145ae-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="145ae-113">Remarks</span></span>  
 <span data-ttu-id="145ae-114">Oluşturmak için bir `Assembly` meta veri yapısı, kullanım [Imetadataassemblyemit::defineassembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="145ae-114">To create an `Assembly` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="145ae-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="145ae-115">Requirements</span></span>  
 <span data-ttu-id="145ae-116">**Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="145ae-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="145ae-117">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="145ae-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="145ae-118">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="145ae-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="145ae-119">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="145ae-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="145ae-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="145ae-120">See also</span></span>

- [<span data-ttu-id="145ae-121">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="145ae-121">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
