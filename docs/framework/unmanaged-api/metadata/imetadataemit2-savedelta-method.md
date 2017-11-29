---
title: "IMetaDataEmit2::SaveDelta Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2.SaveDelta
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2::SaveDelta
helpviewer_keywords:
- IMetaDataEmit2::SaveDelta method [.NET Framework metadata]
- SaveDelta method [.NET Framework metadata]
ms.assetid: b95739fe-d2fa-4776-ae0d-31d9707ef799
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7f2e16d994c648f3c88a23488df75f04dbdaa47a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemit2savedelta-method"></a><span data-ttu-id="e7763-102">IMetaDataEmit2::SaveDelta Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e7763-102">IMetaDataEmit2::SaveDelta Method</span></span>
<span data-ttu-id="e7763-103">Değişiklikleri geçerli Düzenle ve devam et oturumundan belirtilen dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e7763-103">Saves changes from the current edit-and-continue session to the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7763-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e7763-104">Syntax</span></span>  
  
```  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,   
    [in] DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e7763-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e7763-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="e7763-106">[in] Altında çalışacağı değişiklikleri kaydetmek dosya adı.</span><span class="sxs-lookup"><span data-stu-id="e7763-106">[in] The file name under which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="e7763-107">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="e7763-107">[in] Reserved.</span></span> <span data-ttu-id="e7763-108">Sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e7763-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7763-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e7763-109">Requirements</span></span>  
 <span data-ttu-id="e7763-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7763-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7763-111">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e7763-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e7763-112">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="e7763-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e7763-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7763-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7763-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e7763-114">See Also</span></span>  
 [<span data-ttu-id="e7763-115">Imetadataemit2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7763-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="e7763-116">Imetadataemit arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7763-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
