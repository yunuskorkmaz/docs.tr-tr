---
description: 'Hakkında daha fazla bilgi edinin: IMapToken:: Map yöntemi'
title: IMapToken::Map Yöntemi
ms.date: 03/30/2017
api_name:
- IMapToken.Map
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMapToken::Map
helpviewer_keywords:
- IMapToken::Map method [.NET Framework metadata]
- Map method [.NET Framework metadata]
ms.assetid: b9b4bf2f-1098-43d6-9619-a99b4bda1940
topic_type:
- apiref
ms.openlocfilehash: da78f22e944a0e4ec25adcd7cdf97b69131a6612
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706743"
---
# <a name="imaptokenmap-method"></a><span data-ttu-id="df8b0-103">IMapToken::Map Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df8b0-103">IMapToken::Map Method</span></span>

<span data-ttu-id="df8b0-104">Meta veri imzalarını kullanarak derlemeler arasında bir ilişki eşler.</span><span class="sxs-lookup"><span data-stu-id="df8b0-104">Maps a relationship between the assemblies using metadata signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df8b0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="df8b0-105">Syntax</span></span>  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df8b0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="df8b0-106">Parameters</span></span>  

 `tkImp`  
 <span data-ttu-id="df8b0-107">'ndaki İçeri aktarılan kod nesnesini temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="df8b0-107">[in] The metadata token that represents the imported code object.</span></span>  
  
 `tkEmit`  
 <span data-ttu-id="df8b0-108">'ndaki Yayınlanan kod nesnesini temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="df8b0-108">[in] The metadata token that represents the emitted code object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df8b0-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="df8b0-109">Remarks</span></span>  

 <span data-ttu-id="df8b0-110">Belirteç yeniden eşlemesi bir birleştirme sırasında gerçekleştiğinde, özgün belirteç içeri aktarılan (kaynak) meta veri kapsamında kapsamlandırılır ve yeni belirteç, yayılan (hedef) meta veri kapsamında kapsamdadır.</span><span class="sxs-lookup"><span data-stu-id="df8b0-110">When the token re-map occurs during a merge, the original token is scoped in the imported (source) metadata scope and the new token is scoped in the emitted (target) metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df8b0-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="df8b0-111">Requirements</span></span>  

 <span data-ttu-id="df8b0-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df8b0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df8b0-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="df8b0-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="df8b0-114">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="df8b0-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="df8b0-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df8b0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df8b0-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df8b0-116">See also</span></span>

- [<span data-ttu-id="df8b0-117">IMapToken Arabirimi</span><span class="sxs-lookup"><span data-stu-id="df8b0-117">IMapToken Interface</span></span>](imaptoken-interface.md)
