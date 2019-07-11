---
title: IMetaDataAssemblyEmit::DefineFile Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineFile
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineFile method [.NET Framework metadata]
- DefineFile method [.NET Framework metadata]
ms.assetid: c065aadf-c1ca-4981-bde6-597042cb29c4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 54d5a233da2bf033d960fd02961ac89eb57151d2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776290"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="6738b-102">IMetaDataAssemblyEmit::DefineFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6738b-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="6738b-103">Oluşturur bir `File` derleme bu derlemesi tarafından başvurulan ve ilişkili meta veri belirteci döndürür meta verilerini içeren meta veri yapısı.</span><span class="sxs-lookup"><span data-stu-id="6738b-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6738b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6738b-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,   
    [in]  const void     *pbHashValue,   
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6738b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6738b-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="6738b-106">[in] Kullanılacak dosya adı.</span><span class="sxs-lookup"><span data-stu-id="6738b-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="6738b-107">[in] Bütünleştirilmiş kod ile ilişkili veri karması için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6738b-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="6738b-108">[in] Bayt cinsinden boyutu `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="6738b-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="6738b-109">[in] Bitsel bir birleşimi `FileFlags` özellik ayarlarını belirten değerleri.</span><span class="sxs-lookup"><span data-stu-id="6738b-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="6738b-110">[out] Döndürülen işaretçi `File` belirteci.</span><span class="sxs-lookup"><span data-stu-id="6738b-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6738b-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6738b-111">Remarks</span></span>  
 <span data-ttu-id="6738b-112">Bir `File` meta veri yapısı, meta veriler içeren dosya hariç olmak üzere bu bütünleştirilmiş kod oluşturulmuş zaman bu derlemenin parçası olan her bir dosya için tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6738b-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6738b-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6738b-113">Requirements</span></span>  
 <span data-ttu-id="6738b-114">**Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6738b-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6738b-115">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="6738b-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6738b-116">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="6738b-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6738b-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6738b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6738b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6738b-118">See also</span></span>

- [<span data-ttu-id="6738b-119">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6738b-119">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
