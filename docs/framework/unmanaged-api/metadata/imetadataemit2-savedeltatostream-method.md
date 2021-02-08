---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataEmit2:: SaveDeltaToStream yöntemi'
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
ms.openlocfilehash: ce2e7822a5220a8ab1264a6e18337ba0f7828e3b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771710"
---
# <a name="imetadataemit2savedeltatostream-method"></a><span data-ttu-id="2c85b-103">IMetaDataEmit2::SaveDeltaToStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c85b-103">IMetaDataEmit2::SaveDeltaToStream Method</span></span>

<span data-ttu-id="2c85b-104">Değişiklikleri geçerli Düzenle ve devam et oturumundan belirtilen akışa kaydeder.</span><span class="sxs-lookup"><span data-stu-id="2c85b-104">Saves changes from the current edit-and-continue session to the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c85b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c85b-105">Syntax</span></span>  
  
```cpp  
HRESULT SaveDeltaToStream (  
    [in] IStream     *pIStream,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c85b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2c85b-106">Parameters</span></span>  

 `pIStream`  
 <span data-ttu-id="2c85b-107">'ndaki Değişikliklerin kaydedileceği yazılabilir akışa yönelik bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="2c85b-107">[in] An interface pointer to the writable stream to which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="2c85b-108">'ndaki Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="2c85b-108">[in] Reserved.</span></span> <span data-ttu-id="2c85b-109">Bu değer sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c85b-109">This value must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c85b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c85b-110">Requirements</span></span>  

 <span data-ttu-id="2c85b-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c85b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c85b-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2c85b-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2c85b-113">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="2c85b-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2c85b-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c85b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c85b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c85b-115">See also</span></span>

- [<span data-ttu-id="2c85b-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c85b-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="2c85b-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c85b-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
