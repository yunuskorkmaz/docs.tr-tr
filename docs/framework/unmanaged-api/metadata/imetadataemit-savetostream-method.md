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
ms.openlocfilehash: 7db27670b72a5018a03d4614b69486f67bcef155
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175687"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="5fe04-102">IMetaDataEmit::SaveToStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5fe04-102">IMetaDataEmit::SaveToStream Method</span></span>
<span data-ttu-id="5fe04-103">Geçerli kapsamdaki tüm meta verileri belirtilene `IStream`kaydeder.</span><span class="sxs-lookup"><span data-stu-id="5fe04-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fe04-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5fe04-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveToStream (
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fe04-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5fe04-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="5fe04-106">[içinde] Kaydedilen yazılabilir akış.</span><span class="sxs-lookup"><span data-stu-id="5fe04-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="5fe04-107">[içinde] Saklı -dır.</span><span class="sxs-lookup"><span data-stu-id="5fe04-107">[in] Reserved.</span></span> <span data-ttu-id="5fe04-108">Sıfır olmalı.</span><span class="sxs-lookup"><span data-stu-id="5fe04-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fe04-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5fe04-109">Requirements</span></span>  
 <span data-ttu-id="5fe04-110">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fe04-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fe04-111">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5fe04-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5fe04-112">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="5fe04-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5fe04-113">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fe04-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fe04-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5fe04-114">See also</span></span>

- [<span data-ttu-id="5fe04-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5fe04-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="5fe04-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5fe04-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
