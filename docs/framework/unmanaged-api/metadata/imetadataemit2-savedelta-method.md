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
ms.openlocfilehash: 7098bceee6bf60cd7781606ffc889b6af9c3e3cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445341"
---
# <a name="imetadataemit2savedelta-method"></a><span data-ttu-id="76658-102">IMetaDataEmit2::SaveDelta Yöntemi</span><span class="sxs-lookup"><span data-stu-id="76658-102">IMetaDataEmit2::SaveDelta Method</span></span>
<span data-ttu-id="76658-103">Değişiklikleri geçerli Düzenle ve devam et oturumundan belirtilen dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="76658-103">Saves changes from the current edit-and-continue session to the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76658-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="76658-104">Syntax</span></span>  
  
```  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,   
    [in] DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="76658-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="76658-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="76658-106">[in] Altında çalışacağı değişiklikleri kaydetmek dosya adı.</span><span class="sxs-lookup"><span data-stu-id="76658-106">[in] The file name under which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="76658-107">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="76658-107">[in] Reserved.</span></span> <span data-ttu-id="76658-108">Sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="76658-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76658-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="76658-109">Requirements</span></span>  
 <span data-ttu-id="76658-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76658-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76658-111">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="76658-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="76658-112">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="76658-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="76658-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76658-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76658-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="76658-114">See Also</span></span>  
 [<span data-ttu-id="76658-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="76658-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="76658-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="76658-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
