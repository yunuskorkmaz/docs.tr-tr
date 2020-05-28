---
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
ms.openlocfilehash: 027694cee1b3e4d990796ba31300918f6d859679
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008202"
---
# <a name="imaptokenmap-method"></a><span data-ttu-id="642d1-102">IMapToken::Map Yöntemi</span><span class="sxs-lookup"><span data-stu-id="642d1-102">IMapToken::Map Method</span></span>
<span data-ttu-id="642d1-103">Meta veri imzalarını kullanarak derlemeler arasında bir ilişki eşler.</span><span class="sxs-lookup"><span data-stu-id="642d1-103">Maps a relationship between the assemblies using metadata signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="642d1-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="642d1-104">Syntax</span></span>  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="642d1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="642d1-105">Parameters</span></span>  
 `tkImp`  
 <span data-ttu-id="642d1-106">'ndaki İçeri aktarılan kod nesnesini temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="642d1-106">[in] The metadata token that represents the imported code object.</span></span>  
  
 `tkEmit`  
 <span data-ttu-id="642d1-107">'ndaki Yayınlanan kod nesnesini temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="642d1-107">[in] The metadata token that represents the emitted code object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="642d1-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="642d1-108">Remarks</span></span>  
 <span data-ttu-id="642d1-109">Belirteç yeniden eşlemesi bir birleştirme sırasında gerçekleştiğinde, özgün belirteç içeri aktarılan (kaynak) meta veri kapsamında kapsamlandırılır ve yeni belirteç, yayılan (hedef) meta veri kapsamında kapsamdadır.</span><span class="sxs-lookup"><span data-stu-id="642d1-109">When the token re-map occurs during a merge, the original token is scoped in the imported (source) metadata scope and the new token is scoped in the emitted (target) metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="642d1-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="642d1-110">Requirements</span></span>  
 <span data-ttu-id="642d1-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="642d1-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="642d1-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="642d1-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="642d1-113">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="642d1-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="642d1-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="642d1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="642d1-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="642d1-115">See also</span></span>

- [<span data-ttu-id="642d1-116">IMapToken Arabirimi</span><span class="sxs-lookup"><span data-stu-id="642d1-116">IMapToken Interface</span></span>](imaptoken-interface.md)
