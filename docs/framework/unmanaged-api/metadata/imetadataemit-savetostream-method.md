---
description: ': Imetadatayayma:: SaveToStream yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 104aa0b0dfcd0f4f9e8b87b4633880f6423f92d0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706662"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="dc8e4-103">IMetaDataEmit::SaveToStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc8e4-103">IMetaDataEmit::SaveToStream Method</span></span>

<span data-ttu-id="dc8e4-104">Geçerli kapsamdaki tüm meta verileri belirtilen öğesine kaydeder `IStream` .</span><span class="sxs-lookup"><span data-stu-id="dc8e4-104">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc8e4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dc8e4-105">Syntax</span></span>  
  
```cpp  
HRESULT SaveToStream (
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc8e4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dc8e4-106">Parameters</span></span>  

 `pIStream`  
 <span data-ttu-id="dc8e4-107">'ndaki Kaydedilecek yazılabilir akış.</span><span class="sxs-lookup"><span data-stu-id="dc8e4-107">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="dc8e4-108">'ndaki Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="dc8e4-108">[in] Reserved.</span></span> <span data-ttu-id="dc8e4-109">Sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dc8e4-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc8e4-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dc8e4-110">Requirements</span></span>  

 <span data-ttu-id="dc8e4-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc8e4-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc8e4-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="dc8e4-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dc8e4-113">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="dc8e4-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dc8e4-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc8e4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc8e4-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc8e4-115">See also</span></span>

- [<span data-ttu-id="dc8e4-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc8e4-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="dc8e4-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc8e4-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
