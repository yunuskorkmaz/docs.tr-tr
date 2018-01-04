---
title: "IMetaDataAssemblyEmit::DefineFile Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineFile
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineFile
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineFile method [.NET Framework metadata]
- DefineFile method [.NET Framework metadata]
ms.assetid: c065aadf-c1ca-4981-bde6-597042cb29c4
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 48584822d7a2f31c466401db3a24156a71ad7011
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="c7ae0-102">IMetaDataAssemblyEmit::DefineFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c7ae0-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="c7ae0-103">Oluşturur bir `File` derleme bu derlemesi tarafından başvurulan ve ilişkili meta veri simgesi döndürür için meta verileri içeren meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="c7ae0-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7ae0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7ae0-104">Syntax</span></span>  
  
```  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,   
    [in]  const void     *pbHashValue,   
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c7ae0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c7ae0-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="c7ae0-106">[in] Kullanılacak dosya adı.</span><span class="sxs-lookup"><span data-stu-id="c7ae0-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="c7ae0-107">[in] Derleme ile ilişkili karma verileri bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c7ae0-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="c7ae0-108">[in] Bayt cinsinden boyutu `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="c7ae0-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="c7ae0-109">[in] Bit düzeyinde bileşimini `FileFlags` özellik ayarlarını belirten değerleri.</span><span class="sxs-lookup"><span data-stu-id="c7ae0-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="c7ae0-110">[out] Bir işaretçi döndürülen `File` belirteci.</span><span class="sxs-lookup"><span data-stu-id="c7ae0-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7ae0-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7ae0-111">Remarks</span></span>  
 <span data-ttu-id="c7ae0-112">Bir `File` meta veri yapısı, bu derleme meta verilerini içeren dosyanın hariç olmak üzere bu derlemesi oluşturuldu zaman parçası olan her bir dosya için tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c7ae0-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7ae0-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7ae0-113">Requirements</span></span>  
 <span data-ttu-id="c7ae0-114">**Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7ae0-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7ae0-115">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c7ae0-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c7ae0-116">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="c7ae0-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c7ae0-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7ae0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7ae0-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c7ae0-118">See Also</span></span>  
 [<span data-ttu-id="c7ae0-119">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7ae0-119">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
