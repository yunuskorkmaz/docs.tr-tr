---
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 277b93267f0537c8e499a8d8f3b456c4396a975c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966347"
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="e912f-102">IMetaDataError Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e912f-102">IMetaDataError Interface</span></span>
<span data-ttu-id="e912f-103">Meta veri birleştirme sırasında hataları raporlamak için bir geri çağırma mekanizması sağlar.</span><span class="sxs-lookup"><span data-stu-id="e912f-103">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e912f-104">`IMetaDataError` Arabirimin istemci tarafından uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e912f-104">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e912f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e912f-105">Methods</span></span>  
  
|<span data-ttu-id="e912f-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e912f-106">Method</span></span>|<span data-ttu-id="e912f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e912f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e912f-108">OnError Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e912f-108">OnError Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-onerror-method.md)|<span data-ttu-id="e912f-109">Meta veri birleştirme sırasında oluşan hataların bildirimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e912f-109">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e912f-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e912f-110">Requirements</span></span>  
 <span data-ttu-id="e912f-111">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e912f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e912f-112">**Üst bilgi** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e912f-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e912f-113">**Kitaplığı** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="e912f-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e912f-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e912f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e912f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e912f-115">See also</span></span>

- [<span data-ttu-id="e912f-116">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e912f-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
