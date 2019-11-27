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
ms.openlocfilehash: c736eccfd5d05ec9b65e6ed26187e7c7b4387c5d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431735"
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="20316-102">IMetaDataEmit::DefineModuleRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="20316-102">IMetaDataEmit::DefineModuleRef Method</span></span>
<span data-ttu-id="20316-103">Belirtilen ada sahip bir modül için meta veri imzası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="20316-103">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20316-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20316-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineModuleRef (     
    [in]  LPCWSTR           szName,   
    [out] mdModuleRef       *pmur   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20316-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="20316-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="20316-106">'ndaki Diğer meta veri dosyasının adı, genellikle DLL.</span><span class="sxs-lookup"><span data-stu-id="20316-106">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="20316-107">Bu yalnızca dosya adıdır.</span><span class="sxs-lookup"><span data-stu-id="20316-107">This is the file name only.</span></span> <span data-ttu-id="20316-108">Tam yol adı kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="20316-108">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="20316-109">dışı Atanan `mdModuleRef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="20316-109">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20316-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="20316-110">Requirements</span></span>  
 <span data-ttu-id="20316-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20316-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20316-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="20316-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="20316-113">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="20316-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20316-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20316-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20316-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20316-115">See also</span></span>

- [<span data-ttu-id="20316-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="20316-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="20316-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="20316-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
