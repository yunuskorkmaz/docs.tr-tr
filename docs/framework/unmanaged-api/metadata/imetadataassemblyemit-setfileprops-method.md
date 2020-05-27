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
ms.openlocfilehash: 9990daea1b097532de53684921d3f10c520a3b1a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008072"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a><span data-ttu-id="13401-102">IMetaDataAssemblyEmit::SetFileProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13401-102">IMetaDataAssemblyEmit::SetFileProps Method</span></span>
<span data-ttu-id="13401-103">Belirtilen `File` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="13401-103">Modifies the specified `File` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13401-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="13401-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13401-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="13401-105">Parameters</span></span>  
 `file`  
 <span data-ttu-id="13401-106">'ndaki `File`Değiştirilecek meta veri yapısını belirten meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="13401-106">[in] The metadata token that specifies the `File` metadata structure to be modified.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="13401-107">'ndaki Dosyayla ilişkili karma verilere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="13401-107">[in] A pointer to the hash data associated with the file.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="13401-108">'ndaki Bayt cinsinden boyut `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="13401-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="13401-109">'ndaki Dosyanın çeşitli özniteliklerini belirten [CorFileFlags](corfileflags-enumeration.md) değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="13401-109">[in] A bitwise combination of [CorFileFlags](corfileflags-enumeration.md) values that specify various attributes of the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13401-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13401-110">Remarks</span></span>  
 <span data-ttu-id="13401-111">`File`Meta veri yapısı oluşturmak Için [IMetaDataAssemblyEmit::D efineFile](imetadataassemblyemit-definefile-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="13401-111">To create a `File` metadata structure, use the [IMetaDataAssemblyEmit::DefineFile](imetadataassemblyemit-definefile-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13401-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13401-112">Requirements</span></span>  
 <span data-ttu-id="13401-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13401-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13401-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="13401-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="13401-115">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="13401-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="13401-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13401-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13401-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13401-117">See also</span></span>

- [<span data-ttu-id="13401-118">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13401-118">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
