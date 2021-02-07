---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataAssemblyEmit::D efineFile yöntemi'
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
ms.openlocfilehash: 825ef44c2b0a5f312b4c5f9c851d62e75709c7ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671059"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="4f867-103">IMetaDataAssemblyEmit::DefineFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f867-103">IMetaDataAssemblyEmit::DefineFile Method</span></span>

<span data-ttu-id="4f867-104">`File`Bu derleme tarafından başvurulan derleme için meta verileri içeren bir meta veri yapısı oluşturur ve ilişkili meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="4f867-104">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f867-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4f867-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,
    [in]  const void     *pbHashValue,
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f867-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4f867-106">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="4f867-107">'ndaki Tüketilecek dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="4f867-107">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="4f867-108">'ndaki Derlemeyle ilişkili karma verileri işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="4f867-108">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="4f867-109">'ndaki Bayt cinsinden boyut `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="4f867-109">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="4f867-110">'ndaki `FileFlags` Özellik ayarlarını belirten değerlerin bit tabanlı birleşimi.</span><span class="sxs-lookup"><span data-stu-id="4f867-110">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="4f867-111">dışı Döndürülen belirtece yönelik bir işaretçi `File` .</span><span class="sxs-lookup"><span data-stu-id="4f867-111">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f867-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4f867-112">Remarks</span></span>  

 <span data-ttu-id="4f867-113">Bu `File` derlemenin oluşturulduğu zaman, meta verileri içeren dosya hariç olmak üzere, bu derlemenin parçası olan her bir dosya için bir meta veri yapısının tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4f867-113">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f867-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4f867-114">Requirements</span></span>  

 <span data-ttu-id="4f867-115">**Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f867-115">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f867-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4f867-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4f867-117">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="4f867-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4f867-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f867-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f867-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f867-119">See also</span></span>

- [<span data-ttu-id="4f867-120">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4f867-120">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
