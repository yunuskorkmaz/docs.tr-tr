---
description: 'Daha fazla bilgi edinin: IEnumDefinitionIdentity Interface'
title: IEnumDefinitionIdentity Arabirimi
ms.date: 03/30/2017
api_name:
- IEnumDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumDefinitionIdentity
helpviewer_keywords:
- IEnumDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: 8263e75d-251b-4abc-8a1a-c62884142232
topic_type:
- apiref
ms.openlocfilehash: 1055031c064115410334bbe4b20b48deee7ec4c4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800168"
---
# <a name="ienumdefinitionidentity-interface"></a><span data-ttu-id="dae14-103">IEnumDefinitionIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dae14-103">IEnumDefinitionIdentity Interface</span></span>

<span data-ttu-id="dae14-104">Bir nesne koleksiyonu için numaralandırıcı görevi görür `IDefinitionIdentity` .</span><span class="sxs-lookup"><span data-stu-id="dae14-104">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dae14-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="dae14-105">Syntax</span></span>  
  
```cpp  
IEnumDefinitionIdentity : IUnknown {  
  
    HRESULT Clone (  
        [out] IEnumDefinitionIdentity **ppIEnumDefinitionIdentity  
    );  
  
    HRESULT Next (  
        [in]  ULONG               celt,  
        [out, length_is(celt), size_is(*pceltWritten)]  
              IDefinitionIdentity *rgpIDefinitionIdentity[],  
        [out] ULONG               *pceltWritten  
    );  
  
    HRESULT Reset ();  
  
    HRESULT Skip (  
        [in] ULONG celt  
    );  
  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="dae14-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="dae14-106">Methods</span></span>  
  
|<span data-ttu-id="dae14-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="dae14-107">Method</span></span>|<span data-ttu-id="dae14-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dae14-108">Description</span></span>|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|<span data-ttu-id="dae14-109">`IEnumDefinitionIdentity`Bu, ile aynı üyeleri içeren yeni bir nesne için bir arabirim işaretçisi alır `IEnumDefinitionIdentity` .</span><span class="sxs-lookup"><span data-stu-id="dae14-109">Gets an interface pointer to a new `IEnumDefinitionIdentity` object that contains the same members as this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Next`|<span data-ttu-id="dae14-110">`IDefinitionIdentity`Geçerli konumdan başlayarak belirtilen sayıda nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="dae14-110">Gets the specified number of `IDefinitionIdentity` objects, starting at the current position.</span></span>|  
|`IEnumDefinitionIdentity::Reset`|<span data-ttu-id="dae14-111">Yönerge işaretçisini bunun başlangıcına taşıdır `IEnumDefinitionIdentity` .</span><span class="sxs-lookup"><span data-stu-id="dae14-111">Moves the instruction pointer to the beginning of this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Skip`|<span data-ttu-id="dae14-112">Yönerge işaretçisini, geçerli konumdan başlayarak belirtilen sayıda öğe kadar ileri kaydırır.</span><span class="sxs-lookup"><span data-stu-id="dae14-112">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dae14-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dae14-113">Requirements</span></span>  

 <span data-ttu-id="dae14-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dae14-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dae14-115">**Üst bilgi:** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="dae14-115">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="dae14-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dae14-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dae14-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dae14-117">See also</span></span>

- [<span data-ttu-id="dae14-118">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="dae14-118">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="dae14-119">IDefinitionIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dae14-119">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)
