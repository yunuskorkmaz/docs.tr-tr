---
title: IMetaDataEmit2::SaveDelta Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDelta
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDelta
helpviewer_keywords:
- IMetaDataEmit2::SaveDelta method [.NET Framework metadata]
- SaveDelta method [.NET Framework metadata]
ms.assetid: b95739fe-d2fa-4776-ae0d-31d9707ef799
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 212625fd460e88201dd4799754297861826d3aa7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777149"
---
# <a name="imetadataemit2savedelta-method"></a><span data-ttu-id="8d588-102">IMetaDataEmit2::SaveDelta Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d588-102">IMetaDataEmit2::SaveDelta Method</span></span>
<span data-ttu-id="8d588-103">Değişiklikleri geçerli Düzenle ve devam et oturumdan belirtilen dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="8d588-103">Saves changes from the current edit-and-continue session to the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d588-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8d588-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,   
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d588-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8d588-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="8d588-106">[in] Dosya adı altında kaydetmek için değiştirir.</span><span class="sxs-lookup"><span data-stu-id="8d588-106">[in] The file name under which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="8d588-107">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="8d588-107">[in] Reserved.</span></span> <span data-ttu-id="8d588-108">Sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8d588-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d588-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8d588-109">Requirements</span></span>  
 <span data-ttu-id="8d588-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d588-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d588-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="8d588-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8d588-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="8d588-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8d588-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d588-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d588-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d588-114">See also</span></span>

- [<span data-ttu-id="8d588-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8d588-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="8d588-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8d588-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
