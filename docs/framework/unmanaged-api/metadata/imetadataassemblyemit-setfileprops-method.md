---
description: ': IMetaDataAssemblyEmit:: SetFileProps yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 482aa11b85eaf05d126c4fcc0d5a1aced85002d4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789313"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a><span data-ttu-id="a8592-103">IMetaDataAssemblyEmit::SetFileProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a8592-103">IMetaDataAssemblyEmit::SetFileProps Method</span></span>

<span data-ttu-id="a8592-104">Belirtilen `File` meta veri yapısını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="a8592-104">Modifies the specified `File` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8592-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a8592-105">Syntax</span></span>  
  
```cpp  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8592-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a8592-106">Parameters</span></span>  

 `file`  
 <span data-ttu-id="a8592-107">'ndaki `File` Değiştirilecek meta veri yapısını belirten meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="a8592-107">[in] The metadata token that specifies the `File` metadata structure to be modified.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="a8592-108">'ndaki Dosyayla ilişkili karma verilere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a8592-108">[in] A pointer to the hash data associated with the file.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="a8592-109">'ndaki Bayt cinsinden boyut `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="a8592-109">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="a8592-110">'ndaki Dosyanın çeşitli özniteliklerini belirten [CorFileFlags](corfileflags-enumeration.md) değerlerinin bit düzeyinde birleşimi.</span><span class="sxs-lookup"><span data-stu-id="a8592-110">[in] A bitwise combination of [CorFileFlags](corfileflags-enumeration.md) values that specify various attributes of the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8592-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a8592-111">Remarks</span></span>  

 <span data-ttu-id="a8592-112">`File`Meta veri yapısı oluşturmak Için [IMetaDataAssemblyEmit::D efineFile](imetadataassemblyemit-definefile-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="a8592-112">To create a `File` metadata structure, use the [IMetaDataAssemblyEmit::DefineFile](imetadataassemblyemit-definefile-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8592-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a8592-113">Requirements</span></span>  

 <span data-ttu-id="a8592-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8592-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8592-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a8592-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a8592-116">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="a8592-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a8592-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8592-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8592-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8592-118">See also</span></span>

- [<span data-ttu-id="a8592-119">IMetaDataAssemblyEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a8592-119">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
