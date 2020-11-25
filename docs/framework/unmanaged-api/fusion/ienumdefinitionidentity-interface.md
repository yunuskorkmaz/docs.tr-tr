---
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
ms.openlocfilehash: f3872a2b03d3b22d695af1c104e9ae8ba8856990
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729011"
---
# <a name="ienumdefinitionidentity-interface"></a><span data-ttu-id="b3136-102">IEnumDefinitionIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b3136-102">IEnumDefinitionIdentity Interface</span></span>

<span data-ttu-id="b3136-103">Bir nesne koleksiyonu için numaralandırıcı görevi görür `IDefinitionIdentity` .</span><span class="sxs-lookup"><span data-stu-id="b3136-103">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3136-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="b3136-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="b3136-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b3136-105">Methods</span></span>  
  
|<span data-ttu-id="b3136-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b3136-106">Method</span></span>|<span data-ttu-id="b3136-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b3136-107">Description</span></span>|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|<span data-ttu-id="b3136-108">`IEnumDefinitionIdentity`Bu, ile aynı üyeleri içeren yeni bir nesne için bir arabirim işaretçisi alır `IEnumDefinitionIdentity` .</span><span class="sxs-lookup"><span data-stu-id="b3136-108">Gets an interface pointer to a new `IEnumDefinitionIdentity` object that contains the same members as this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Next`|<span data-ttu-id="b3136-109">`IDefinitionIdentity`Geçerli konumdan başlayarak belirtilen sayıda nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="b3136-109">Gets the specified number of `IDefinitionIdentity` objects, starting at the current position.</span></span>|  
|`IEnumDefinitionIdentity::Reset`|<span data-ttu-id="b3136-110">Yönerge işaretçisini bunun başlangıcına taşıdır `IEnumDefinitionIdentity` .</span><span class="sxs-lookup"><span data-stu-id="b3136-110">Moves the instruction pointer to the beginning of this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Skip`|<span data-ttu-id="b3136-111">Yönerge işaretçisini, geçerli konumdan başlayarak belirtilen sayıda öğe kadar ileri kaydırır.</span><span class="sxs-lookup"><span data-stu-id="b3136-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b3136-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b3136-112">Requirements</span></span>  

 <span data-ttu-id="b3136-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3136-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3136-114">**Üst bilgi:** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="b3136-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="b3136-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3136-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3136-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3136-116">See also</span></span>

- [<span data-ttu-id="b3136-117">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b3136-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="b3136-118">IDefinitionIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b3136-118">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)
