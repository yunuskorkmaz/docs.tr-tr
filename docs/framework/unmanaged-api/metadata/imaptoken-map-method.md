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
ms.openlocfilehash: 428b022ed560648f59798154d5987d382938c280
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176077"
---
# <a name="imaptokenmap-method"></a><span data-ttu-id="31638-102">IMapToken::Map Yöntemi</span><span class="sxs-lookup"><span data-stu-id="31638-102">IMapToken::Map Method</span></span>
<span data-ttu-id="31638-103">Meta veri imzalarını kullanarak derlemeler arasındaki ilişkiyi eşler.</span><span class="sxs-lookup"><span data-stu-id="31638-103">Maps a relationship between the assemblies using metadata signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31638-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="31638-104">Syntax</span></span>  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31638-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="31638-105">Parameters</span></span>  
 `tkImp`  
 <span data-ttu-id="31638-106">[içinde] İçe aktarılan kod nesnesini temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="31638-106">[in] The metadata token that represents the imported code object.</span></span>  
  
 `tkEmit`  
 <span data-ttu-id="31638-107">[içinde] Yayılan kod nesnesini temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="31638-107">[in] The metadata token that represents the emitted code object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31638-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="31638-108">Remarks</span></span>  
 <span data-ttu-id="31638-109">Belirteç yeniden eşlemi birleştirme sırasında gerçekleştiğinde, özgün belirteç içe aktarılan (kaynak) meta veri kapsamında ve yeni belirteç yayılan (hedef) meta veri kapsamında kapsamlıdır.</span><span class="sxs-lookup"><span data-stu-id="31638-109">When the token re-map occurs during a merge, the original token is scoped in the imported (source) metadata scope and the new token is scoped in the emitted (target) metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31638-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="31638-110">Requirements</span></span>  
 <span data-ttu-id="31638-111">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31638-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31638-112">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="31638-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="31638-113">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="31638-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="31638-114">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31638-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31638-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31638-115">See also</span></span>

- [<span data-ttu-id="31638-116">IMapToken Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31638-116">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
