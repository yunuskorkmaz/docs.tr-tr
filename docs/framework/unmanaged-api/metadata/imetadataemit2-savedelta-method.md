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
ms.openlocfilehash: d3e25f271fc434785e25e7b226ad98f86b5f8dfc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492791"
---
# <a name="imetadataemit2savedelta-method"></a><span data-ttu-id="c885e-102">IMetaDataEmit2::SaveDelta Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c885e-102">IMetaDataEmit2::SaveDelta Method</span></span>
<span data-ttu-id="c885e-103">Değişiklikleri geçerli Düzenle ve devam et oturumundan belirtilen dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="c885e-103">Saves changes from the current edit-and-continue session to the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c885e-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c885e-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c885e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c885e-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="c885e-106">'ndaki Değişikliklerin kaydedileceği dosya adı.</span><span class="sxs-lookup"><span data-stu-id="c885e-106">[in] The file name under which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="c885e-107">'ndaki Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="c885e-107">[in] Reserved.</span></span> <span data-ttu-id="c885e-108">Sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c885e-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c885e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c885e-109">Requirements</span></span>  
 <span data-ttu-id="c885e-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c885e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c885e-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c885e-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c885e-112">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="c885e-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c885e-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c885e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c885e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c885e-114">See also</span></span>

- [<span data-ttu-id="c885e-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c885e-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="c885e-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c885e-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
