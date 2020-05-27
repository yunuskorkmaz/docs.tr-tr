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
ms.openlocfilehash: 61d81c94e3a9c092b5d45791962635c761e8da8a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008150"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="64328-102">IMetaDataAssemblyEmit::DefineFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="64328-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="64328-103">`File`Bu derleme tarafından başvurulan derleme için meta verileri içeren bir meta veri yapısı oluşturur ve ilişkili meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="64328-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64328-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="64328-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,
    [in]  const void     *pbHashValue,
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64328-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="64328-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="64328-106">'ndaki Tüketilecek dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="64328-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="64328-107">'ndaki Derlemeyle ilişkili karma verileri işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="64328-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="64328-108">'ndaki Bayt cinsinden boyut `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="64328-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="64328-109">'ndaki `FileFlags`Özellik ayarlarını belirten değerlerin bit tabanlı birleşimi.</span><span class="sxs-lookup"><span data-stu-id="64328-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="64328-110">dışı Döndürülen belirtece yönelik bir işaretçi `File` .</span><span class="sxs-lookup"><span data-stu-id="64328-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64328-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="64328-111">Remarks</span></span>  
 <span data-ttu-id="64328-112">Bu `File` derlemenin oluşturulduğu zaman, meta verileri içeren dosya hariç olmak üzere, bu derlemenin parçası olan her bir dosya için bir meta veri yapısının tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="64328-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64328-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="64328-113">Requirements</span></span>  
 <span data-ttu-id="64328-114">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64328-114">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64328-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="64328-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="64328-116">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="64328-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="64328-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64328-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64328-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64328-118">See also</span></span>

- [<span data-ttu-id="64328-119">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64328-119">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
