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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88c2513229b6a4183cadbdc78e505910e01e152c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796477"
---
# <a name="ienumdefinitionidentity-interface"></a><span data-ttu-id="b4078-102">IEnumDefinitionIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b4078-102">IEnumDefinitionIdentity Interface</span></span>
<span data-ttu-id="b4078-103">Bir `IDefinitionIdentity` nesne koleksiyonu için numaralandırıcı görevi görür.</span><span class="sxs-lookup"><span data-stu-id="b4078-103">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4078-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b4078-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="b4078-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b4078-105">Methods</span></span>  
  
|<span data-ttu-id="b4078-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b4078-106">Method</span></span>|<span data-ttu-id="b4078-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b4078-107">Description</span></span>|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|<span data-ttu-id="b4078-108">`IEnumDefinitionIdentity` Bu`IEnumDefinitionIdentity`, ile aynı üyeleri içeren yeni bir nesne için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="b4078-108">Gets an interface pointer to a new `IEnumDefinitionIdentity` object that contains the same members as this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Next`|<span data-ttu-id="b4078-109">Geçerli konumdan başlayarak belirtilen sayıda `IDefinitionIdentity` nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="b4078-109">Gets the specified number of `IDefinitionIdentity` objects, starting at the current position.</span></span>|  
|`IEnumDefinitionIdentity::Reset`|<span data-ttu-id="b4078-110">Yönerge işaretçisini bunun `IEnumDefinitionIdentity`başlangıcına taşıdır.</span><span class="sxs-lookup"><span data-stu-id="b4078-110">Moves the instruction pointer to the beginning of this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Skip`|<span data-ttu-id="b4078-111">Yönerge işaretçisini, geçerli konumdan başlayarak belirtilen sayıda öğe kadar ileri kaydırır.</span><span class="sxs-lookup"><span data-stu-id="b4078-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b4078-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b4078-112">Requirements</span></span>  
 <span data-ttu-id="b4078-113">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4078-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4078-114">**Üst bilgi** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="b4078-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="b4078-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4078-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4078-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4078-116">See also</span></span>

- [<span data-ttu-id="b4078-117">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b4078-117">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="b4078-118">IDefinitionIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b4078-118">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)
