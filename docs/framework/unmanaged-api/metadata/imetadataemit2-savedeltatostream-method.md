---
title: IMetaDataEmit2::SaveDeltaToStream Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToStream
helpviewer_keywords:
- IMetaDataEmit2::SaveDeltaToStream method [.NET Framework metadata]
- SaveDeltaToStream method [.NET Framework metadata]
ms.assetid: ecd786e8-f9a4-4190-a6ef-af18e8c6d654
topic_type:
- apiref
ms.openlocfilehash: 7e8376f3a029b0e3ec51a1e7587dd14b3e7530ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177420"
---
# <a name="imetadataemit2savedeltatostream-method"></a><span data-ttu-id="0d455-102">IMetaDataEmit2::SaveDeltaToStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0d455-102">IMetaDataEmit2::SaveDeltaToStream Method</span></span>
<span data-ttu-id="0d455-103">Değişiklikleri geçerli düzenle ve devam oturumundan belirtilen akışa kaydeder.</span><span class="sxs-lookup"><span data-stu-id="0d455-103">Saves changes from the current edit-and-continue session to the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d455-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0d455-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDeltaToStream (  
    [in] IStream     *pIStream,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d455-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0d455-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="0d455-106">[içinde] Değişiklikleri kaydetmek için yazılabilir akış için bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0d455-106">[in] An interface pointer to the writable stream to which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="0d455-107">[içinde] Saklı -dır.</span><span class="sxs-lookup"><span data-stu-id="0d455-107">[in] Reserved.</span></span> <span data-ttu-id="0d455-108">Bu değer sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0d455-108">This value must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d455-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0d455-109">Requirements</span></span>  
 <span data-ttu-id="0d455-110">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d455-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d455-111">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0d455-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0d455-112">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="0d455-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0d455-113">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d455-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d455-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d455-114">See also</span></span>

- [<span data-ttu-id="0d455-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0d455-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="0d455-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0d455-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
