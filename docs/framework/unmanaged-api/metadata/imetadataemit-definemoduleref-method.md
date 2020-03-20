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
ms.openlocfilehash: 94261b7796166cf482a7de990551890e4722dd3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177732"
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="ab7b2-102">IMetaDataEmit::DefineModuleRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab7b2-102">IMetaDataEmit::DefineModuleRef Method</span></span>
<span data-ttu-id="ab7b2-103">Belirtilen ada sahip bir modül için meta veri imzasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ab7b2-103">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab7b2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ab7b2-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineModuleRef (
    [in]  LPCWSTR           szName,
    [out] mdModuleRef       *pmur
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab7b2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ab7b2-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="ab7b2-106">[içinde] Diğer meta veri dosyasının adı, genellikle bir DLL.</span><span class="sxs-lookup"><span data-stu-id="ab7b2-106">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="ab7b2-107">Bu yalnızca dosya adıdır.</span><span class="sxs-lookup"><span data-stu-id="ab7b2-107">This is the file name only.</span></span> <span data-ttu-id="ab7b2-108">Tam yol adı kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="ab7b2-108">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="ab7b2-109">[çıkış] Atanan `mdModuleRef` belirteç.</span><span class="sxs-lookup"><span data-stu-id="ab7b2-109">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab7b2-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ab7b2-110">Requirements</span></span>  
 <span data-ttu-id="ab7b2-111">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab7b2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab7b2-112">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ab7b2-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ab7b2-113">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="ab7b2-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ab7b2-114">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab7b2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab7b2-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab7b2-115">See also</span></span>

- [<span data-ttu-id="ab7b2-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ab7b2-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ab7b2-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ab7b2-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
