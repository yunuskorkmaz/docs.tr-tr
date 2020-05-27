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
ms.openlocfilehash: 87e00a69643b6bc403188fb0fdb6f9e3f3d82115
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003886"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="af25b-102">IMetaDataEmit::SaveToStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="af25b-102">IMetaDataEmit::SaveToStream Method</span></span>
<span data-ttu-id="af25b-103">Geçerli kapsamdaki tüm meta verileri belirtilen öğesine kaydeder `IStream` .</span><span class="sxs-lookup"><span data-stu-id="af25b-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af25b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="af25b-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveToStream (
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af25b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="af25b-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="af25b-106">'ndaki Kaydedilecek yazılabilir akış.</span><span class="sxs-lookup"><span data-stu-id="af25b-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="af25b-107">'ndaki Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="af25b-107">[in] Reserved.</span></span> <span data-ttu-id="af25b-108">Sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="af25b-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af25b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="af25b-109">Requirements</span></span>  
 <span data-ttu-id="af25b-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af25b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af25b-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="af25b-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="af25b-112">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="af25b-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="af25b-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af25b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af25b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af25b-114">See also</span></span>

- [<span data-ttu-id="af25b-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="af25b-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="af25b-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="af25b-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
