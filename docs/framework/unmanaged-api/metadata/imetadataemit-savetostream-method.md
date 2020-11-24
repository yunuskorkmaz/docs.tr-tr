---
title: IMetaDataEmit::SaveToStream Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToStream
helpviewer_keywords:
- IMetaDataEmit::SaveToStream method [.NET Framework metadata]
- SaveToStream method [.NET Framework metadata]
ms.assetid: e0290a49-3818-4a43-ad46-3014faa34f97
topic_type:
- apiref
ms.openlocfilehash: 3f8da08b96c47c90ecccae28dd1662a7abffaf1d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688568"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="9f447-102">IMetaDataEmit::SaveToStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f447-102">IMetaDataEmit::SaveToStream Method</span></span>

<span data-ttu-id="9f447-103">Geçerli kapsamdaki tüm meta verileri belirtilen öğesine kaydeder `IStream` .</span><span class="sxs-lookup"><span data-stu-id="9f447-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f447-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9f447-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveToStream (
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f447-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9f447-105">Parameters</span></span>  

 `pIStream`  
 <span data-ttu-id="9f447-106">'ndaki Kaydedilecek yazılabilir akış.</span><span class="sxs-lookup"><span data-stu-id="9f447-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="9f447-107">'ndaki Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="9f447-107">[in] Reserved.</span></span> <span data-ttu-id="9f447-108">Sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9f447-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f447-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9f447-109">Requirements</span></span>  

 <span data-ttu-id="9f447-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f447-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f447-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9f447-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9f447-112">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="9f447-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9f447-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f447-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f447-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f447-114">See also</span></span>

- [<span data-ttu-id="9f447-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f447-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="9f447-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f447-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
