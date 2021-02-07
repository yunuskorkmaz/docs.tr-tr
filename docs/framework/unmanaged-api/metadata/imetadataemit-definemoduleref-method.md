---
description: 'Şu konuda daha fazla bilgi edinin: ımetadatayayma::D efineModuleRef yöntemi'
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
ms.openlocfilehash: b5af5e458f749d2315612bbe9419f037331f8c46
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753399"
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="fb875-103">IMetaDataEmit::DefineModuleRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fb875-103">IMetaDataEmit::DefineModuleRef Method</span></span>

<span data-ttu-id="fb875-104">Belirtilen ada sahip bir modül için meta veri imzası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fb875-104">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb875-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb875-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineModuleRef (
    [in]  LPCWSTR           szName,
    [out] mdModuleRef       *pmur
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb875-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fb875-106">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="fb875-107">'ndaki Diğer meta veri dosyasının adı, genellikle DLL.</span><span class="sxs-lookup"><span data-stu-id="fb875-107">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="fb875-108">Bu yalnızca dosya adıdır.</span><span class="sxs-lookup"><span data-stu-id="fb875-108">This is the file name only.</span></span> <span data-ttu-id="fb875-109">Tam yol adı kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="fb875-109">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="fb875-110">dışı Atanan `mdModuleRef` belirteç.</span><span class="sxs-lookup"><span data-stu-id="fb875-110">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb875-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fb875-111">Requirements</span></span>  

 <span data-ttu-id="fb875-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb875-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb875-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="fb875-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fb875-114">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="fb875-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fb875-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb875-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb875-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb875-116">See also</span></span>

- [<span data-ttu-id="fb875-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb875-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="fb875-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb875-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
