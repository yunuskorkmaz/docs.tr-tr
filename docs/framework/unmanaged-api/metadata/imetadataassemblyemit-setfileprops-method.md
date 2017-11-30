---
title: "IMetaDataAssemblyEmit::SetFileProps Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.SetFileProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::SetFileProps
helpviewer_keywords:
- IMetaDataAssemblyEmit::SetFileProps method [.NET Framework metadata]
- SetFileProps method [.NET Framework metadata]
ms.assetid: 85667d38-611c-45a9-938d-930ac7a7b681
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f179ce3e54a5229423d7267cd52a97edef3b619d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitsetfileprops-method"></a><span data-ttu-id="ccf31-102">IMetaDataAssemblyEmit::SetFileProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ccf31-102">IMetaDataAssemblyEmit::SetFileProps Method</span></span>
<span data-ttu-id="ccf31-103">Belirtilen değiştirir `File` meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="ccf31-103">Modifies the specified `File` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccf31-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ccf31-104">Syntax</span></span>  
  
```  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,   
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ccf31-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ccf31-105">Parameters</span></span>  
 `file`  
 <span data-ttu-id="ccf31-106">[in] Belirtir meta veri simgesi `File` değiştirilecek meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="ccf31-106">[in] The metadata token that specifies the `File` metadata structure to be modified.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="ccf31-107">[in] Dosyayla ilişkili karma verileri bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ccf31-107">[in] A pointer to the hash data associated with the file.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="ccf31-108">[in] Bayt cinsinden boyutu `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="ccf31-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="ccf31-109">[in] Bit düzeyinde bileşimini [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) çeşitli dosyanın özniteliklerini belirten değerleri.</span><span class="sxs-lookup"><span data-stu-id="ccf31-109">[in] A bitwise combination of [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values that specify various attributes of the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ccf31-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ccf31-110">Remarks</span></span>  
 <span data-ttu-id="ccf31-111">Oluşturmak için bir `File` meta veri yapısı, kullanım [Imetadataassemblyemit::definefile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ccf31-111">To create a `File` metadata structure, use the [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccf31-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ccf31-112">Requirements</span></span>  
 <span data-ttu-id="ccf31-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccf31-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccf31-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ccf31-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ccf31-115">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="ccf31-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ccf31-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccf31-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccf31-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ccf31-117">See Also</span></span>  
 [<span data-ttu-id="ccf31-118">Imetadataassemblyemit arabirimi</span><span class="sxs-lookup"><span data-stu-id="ccf31-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
