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
ms.openlocfilehash: ab2f30c485a755d4788926c13c2608e55a716c5c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704272"
---
# <a name="imetadataemit2savedelta-method"></a><span data-ttu-id="bbf8a-102">IMetaDataEmit2::SaveDelta Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bbf8a-102">IMetaDataEmit2::SaveDelta Method</span></span>

<span data-ttu-id="bbf8a-103">Değişiklikleri geçerli Düzenle ve devam et oturumundan belirtilen dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="bbf8a-103">Saves changes from the current edit-and-continue session to the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbf8a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="bbf8a-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbf8a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bbf8a-105">Parameters</span></span>  

 `szFile`  
 <span data-ttu-id="bbf8a-106">'ndaki Değişikliklerin kaydedileceği dosya adı.</span><span class="sxs-lookup"><span data-stu-id="bbf8a-106">[in] The file name under which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="bbf8a-107">'ndaki Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="bbf8a-107">[in] Reserved.</span></span> <span data-ttu-id="bbf8a-108">Sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bbf8a-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbf8a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bbf8a-109">Requirements</span></span>  

 <span data-ttu-id="bbf8a-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbf8a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbf8a-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="bbf8a-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bbf8a-112">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="bbf8a-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bbf8a-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbf8a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbf8a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbf8a-114">See also</span></span>

- [<span data-ttu-id="bbf8a-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bbf8a-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="bbf8a-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bbf8a-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
