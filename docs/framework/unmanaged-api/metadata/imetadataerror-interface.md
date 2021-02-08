---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataError arabirimi'
title: IMetaDataError Arabirimi
ms.date: 03/30/2017
api_name:
- IMetaDataError
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataError
helpviewer_keywords:
- IMetaDataError interface [.NET Framework metadata]
ms.assetid: 0020b62c-ea88-40c7-a9ee-16b064f81624
topic_type:
- apiref
ms.openlocfilehash: f32c8abc3cccce770b86ce47016d9b7e18acad23
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771697"
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="af0cf-103">IMetaDataError Arabirimi</span><span class="sxs-lookup"><span data-stu-id="af0cf-103">IMetaDataError Interface</span></span>

<span data-ttu-id="af0cf-104">Meta veri birleştirme sırasında hataları raporlamak için bir geri çağırma mekanizması sağlar.</span><span class="sxs-lookup"><span data-stu-id="af0cf-104">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="af0cf-105">`IMetaDataError`Arabirimin istemci tarafından uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="af0cf-105">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="af0cf-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="af0cf-106">Methods</span></span>  
  
|<span data-ttu-id="af0cf-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="af0cf-107">Method</span></span>|<span data-ttu-id="af0cf-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="af0cf-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="af0cf-109">OnError Yöntemi</span><span class="sxs-lookup"><span data-stu-id="af0cf-109">OnError Method</span></span>](imetadataerror-onerror-method.md)|<span data-ttu-id="af0cf-110">Meta veri birleştirme sırasında oluşan hataların bildirimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="af0cf-110">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="af0cf-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="af0cf-111">Requirements</span></span>  

 <span data-ttu-id="af0cf-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af0cf-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af0cf-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="af0cf-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="af0cf-114">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="af0cf-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="af0cf-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af0cf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af0cf-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af0cf-116">See also</span></span>

- [<span data-ttu-id="af0cf-117">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="af0cf-117">Metadata Interfaces</span></span>](metadata-interfaces.md)
