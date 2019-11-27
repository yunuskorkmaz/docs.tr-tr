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
ms.openlocfilehash: 0b7ca6f9878ed2fa2d90ea93e5101f0a66ec2d5e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440211"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="b8260-102">IMetaDataAssemblyEmit::DefineFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b8260-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="b8260-103">Bu derleme tarafından başvurulan derleme için meta verileri içeren bir `File` meta veri yapısı oluşturur ve ilişkili meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="b8260-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8260-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b8260-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,   
    [in]  const void     *pbHashValue,   
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8260-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b8260-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="b8260-106">'ndaki Tüketilecek dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="b8260-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="b8260-107">'ndaki Derlemeyle ilişkili karma verileri işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b8260-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="b8260-108">'ndaki `pbHashValue`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="b8260-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="b8260-109">'ndaki Özellik ayarlarını belirten `FileFlags` değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="b8260-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="b8260-110">dışı Döndürülen `File` belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b8260-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8260-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b8260-111">Remarks</span></span>  
 <span data-ttu-id="b8260-112">Bu derlemenin oluşturulduğu zaman, meta verileri içeren dosya hariç olmak üzere, bu derlemenin parçası olan her bir dosya için bir `File` meta veri yapısının tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b8260-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8260-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b8260-113">Requirements</span></span>  
 <span data-ttu-id="b8260-114">**Platform:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8260-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8260-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b8260-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b8260-116">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="b8260-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b8260-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8260-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8260-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8260-118">See also</span></span>

- [<span data-ttu-id="b8260-119">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b8260-119">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
