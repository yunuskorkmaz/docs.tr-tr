---
title: IMetaDataAssemblyEmit::SetFileProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetFileProps
helpviewer_keywords:
- IMetaDataAssemblyEmit::SetFileProps method [.NET Framework metadata]
- SetFileProps method [.NET Framework metadata]
ms.assetid: 85667d38-611c-45a9-938d-930ac7a7b681
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 203c31129218be585960e771b1d7e669defd8cde
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743302"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a><span data-ttu-id="67adb-102">IMetaDataAssemblyEmit::SetFileProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="67adb-102">IMetaDataAssemblyEmit::SetFileProps Method</span></span>
<span data-ttu-id="67adb-103">Belirtilen değiştirir `File` meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="67adb-103">Modifies the specified `File` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67adb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67adb-104">Syntax</span></span>  
  
```  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,   
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="67adb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="67adb-105">Parameters</span></span>  
 `file`  
 <span data-ttu-id="67adb-106">[in] Belirten bir meta veri belirteci `File` değiştirilecek meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="67adb-106">[in] The metadata token that specifies the `File` metadata structure to be modified.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="67adb-107">[in] Bir dosyayla ilişkili veri karması işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="67adb-107">[in] A pointer to the hash data associated with the file.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="67adb-108">[in] Bayt cinsinden boyutu `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="67adb-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="67adb-109">[in] Bitsel bir birleşimi [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) dosyanın çeşitli özniteliklerini belirten değerleri.</span><span class="sxs-lookup"><span data-stu-id="67adb-109">[in] A bitwise combination of [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values that specify various attributes of the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67adb-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="67adb-110">Remarks</span></span>  
 <span data-ttu-id="67adb-111">Oluşturmak için bir `File` meta veri yapısı, kullanım [Imetadataassemblyemit::definefile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="67adb-111">To create a `File` metadata structure, use the [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67adb-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="67adb-112">Requirements</span></span>  
 <span data-ttu-id="67adb-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67adb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67adb-114">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="67adb-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="67adb-115">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="67adb-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="67adb-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67adb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67adb-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67adb-117">See also</span></span>
- [<span data-ttu-id="67adb-118">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="67adb-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
