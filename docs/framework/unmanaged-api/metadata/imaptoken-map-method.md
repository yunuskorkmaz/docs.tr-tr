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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a85dc586b0c08fabdd34c018e82314c9003eeded
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62044908"
---
# <a name="imaptokenmap-method"></a><span data-ttu-id="eaa6e-102">IMapToken::Map Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eaa6e-102">IMapToken::Map Method</span></span>
<span data-ttu-id="eaa6e-103">Meta verileri imza kullanma derlemeler arasında bir ilişki eşler.</span><span class="sxs-lookup"><span data-stu-id="eaa6e-103">Maps a relationship between the assemblies using metadata signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaa6e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eaa6e-104">Syntax</span></span>  
  
```  
HRESULT Map (  
    [in]  mdToken tkImp,   
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eaa6e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eaa6e-105">Parameters</span></span>  
 `tkImp`  
 <span data-ttu-id="eaa6e-106">[in] Alınan kod nesnesini temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="eaa6e-106">[in] The metadata token that represents the imported code object.</span></span>  
  
 `tkEmit`  
 <span data-ttu-id="eaa6e-107">[in] Gösterilen kod nesneyi temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="eaa6e-107">[in] The metadata token that represents the emitted code object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eaa6e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eaa6e-108">Remarks</span></span>  
 <span data-ttu-id="eaa6e-109">Belirteci yeniden eşlemeniz birleştirme sırasında ortaya çıktığında, özgün belirteç içeri aktarılan (kaynak) meta verileri kapsamda kapsama alınır ve yeni belirteç yayılan (hedef) meta verileri kapsamda kapsamlıdır.</span><span class="sxs-lookup"><span data-stu-id="eaa6e-109">When the token re-map occurs during a merge, the original token is scoped in the imported (source) metadata scope and the new token is scoped in the emitted (target) metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eaa6e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eaa6e-110">Requirements</span></span>  
 <span data-ttu-id="eaa6e-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eaa6e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eaa6e-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="eaa6e-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="eaa6e-113">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="eaa6e-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="eaa6e-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eaa6e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaa6e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eaa6e-115">See also</span></span>

- [<span data-ttu-id="eaa6e-116">IMapToken Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eaa6e-116">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
