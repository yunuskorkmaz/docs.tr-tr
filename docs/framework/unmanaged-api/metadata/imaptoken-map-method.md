---
title: "IMapToken::Map Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMapToken.Map
api_location: mscoree.dll
api_type: COM
f1_keywords: IMapToken::Map
helpviewer_keywords:
- IMapToken::Map method [.NET Framework metadata]
- Map method [.NET Framework metadata]
ms.assetid: b9b4bf2f-1098-43d6-9619-a99b4bda1940
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2e3a9701bab27764803442a3cd0c24c4e412deaf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="imaptokenmap-method"></a><span data-ttu-id="283b8-102">IMapToken::Map Yöntemi</span><span class="sxs-lookup"><span data-stu-id="283b8-102">IMapToken::Map Method</span></span>
<span data-ttu-id="283b8-103">Meta veri imzaları kullanarak derlemeler arasında bir ilişki eşler.</span><span class="sxs-lookup"><span data-stu-id="283b8-103">Maps a relationship between the assemblies using metadata signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="283b8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="283b8-104">Syntax</span></span>  
  
```  
HRESULT Map (  
    [in]  mdToken tkImp,   
    [in]  mdToken tkEmit  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="283b8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="283b8-105">Parameters</span></span>  
 `tkImp`  
 <span data-ttu-id="283b8-106">[in] İçeri aktarılan kod nesnesini temsil eden meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="283b8-106">[in] The metadata token that represents the imported code object.</span></span>  
  
 `tkEmit`  
 <span data-ttu-id="283b8-107">[in] Verilmiş kod nesnesini temsil eden meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="283b8-107">[in] The metadata token that represents the emitted code object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="283b8-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="283b8-108">Remarks</span></span>  
 <span data-ttu-id="283b8-109">Belirteç eşleme yeniden birleştirme sırasında ortaya çıktığında, özgün belirteç alınan (kaynak) meta veri kapsamda kapsamlıdır ve yeni belirteci verilmiş (hedef) meta veri kapsamda kapsamlıdır.</span><span class="sxs-lookup"><span data-stu-id="283b8-109">When the token re-map occurs during a merge, the original token is scoped in the imported (source) metadata scope and the new token is scoped in the emitted (target) metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="283b8-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="283b8-110">Requirements</span></span>  
 <span data-ttu-id="283b8-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="283b8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="283b8-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="283b8-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="283b8-113">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="283b8-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="283b8-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="283b8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="283b8-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="283b8-115">See Also</span></span>  
 [<span data-ttu-id="283b8-116">Imaptoken arabirimi</span><span class="sxs-lookup"><span data-stu-id="283b8-116">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
