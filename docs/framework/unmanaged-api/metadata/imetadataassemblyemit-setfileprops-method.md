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
ms.openlocfilehash: 25baa6ffda3d50915cc7898275d6a557c1b3e947
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176038"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a><span data-ttu-id="54259-102">IMetaDataAssemblyEmit::SetFileProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="54259-102">IMetaDataAssemblyEmit::SetFileProps Method</span></span>
<span data-ttu-id="54259-103">Belirtilen `File` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="54259-103">Modifies the specified `File` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54259-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54259-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54259-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="54259-105">Parameters</span></span>  
 `file`  
 <span data-ttu-id="54259-106">[içinde] Değiştirilecek `File` meta veri yapısını belirten meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="54259-106">[in] The metadata token that specifies the `File` metadata structure to be modified.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="54259-107">[içinde] Dosyayla ilişkili karma verilere işaretçi.</span><span class="sxs-lookup"><span data-stu-id="54259-107">[in] A pointer to the hash data associated with the file.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="54259-108">[içinde] `pbHashValue`Baytboyutu.</span><span class="sxs-lookup"><span data-stu-id="54259-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="54259-109">[içinde] Dosyanın çeşitli özniteliklerini belirten [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) değerlerinin bitwise birleşimi.</span><span class="sxs-lookup"><span data-stu-id="54259-109">[in] A bitwise combination of [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values that specify various attributes of the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54259-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="54259-110">Remarks</span></span>  
 <span data-ttu-id="54259-111">Meta `File` veri yapısı oluşturmak için [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="54259-111">To create a `File` metadata structure, use the [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54259-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="54259-112">Requirements</span></span>  
 <span data-ttu-id="54259-113">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54259-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54259-114">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="54259-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="54259-115">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="54259-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="54259-116">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54259-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54259-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="54259-117">See also</span></span>

- [<span data-ttu-id="54259-118">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="54259-118">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
