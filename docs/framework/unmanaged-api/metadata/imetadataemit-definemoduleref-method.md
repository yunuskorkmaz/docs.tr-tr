---
title: IMetaDataEmit::DefineModuleRef Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineModuleRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineModuleRef
helpviewer_keywords:
- DefineModuleRef method [.NET Framework metadata]
- IMetaDataEmit::DefineModuleRef method [.NET Framework metadata]
ms.assetid: f2833594-d90b-4a71-9a53-34b12470c64a
topic_type:
- apiref
ms.openlocfilehash: efff491d92ac7910f43f76965ef98d1d0e4ba0aa
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004445"
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="e3151-102">IMetaDataEmit::DefineModuleRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e3151-102">IMetaDataEmit::DefineModuleRef Method</span></span>
<span data-ttu-id="e3151-103">Belirtilen ada sahip bir modül için meta veri imzası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e3151-103">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3151-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e3151-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineModuleRef (
    [in]  LPCWSTR           szName,
    [out] mdModuleRef       *pmur
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3151-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e3151-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="e3151-106">'ndaki Diğer meta veri dosyasının adı, genellikle DLL.</span><span class="sxs-lookup"><span data-stu-id="e3151-106">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="e3151-107">Bu yalnızca dosya adıdır.</span><span class="sxs-lookup"><span data-stu-id="e3151-107">This is the file name only.</span></span> <span data-ttu-id="e3151-108">Tam yol adı kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="e3151-108">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="e3151-109">dışı Atanan `mdModuleRef` belirteç.</span><span class="sxs-lookup"><span data-stu-id="e3151-109">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3151-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e3151-110">Requirements</span></span>  
 <span data-ttu-id="e3151-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3151-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3151-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e3151-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e3151-113">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="e3151-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e3151-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3151-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3151-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3151-115">See also</span></span>

- [<span data-ttu-id="e3151-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e3151-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="e3151-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e3151-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
