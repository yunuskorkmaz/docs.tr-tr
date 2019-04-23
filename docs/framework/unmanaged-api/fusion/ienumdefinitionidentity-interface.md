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
ms.openlocfilehash: d19ca92db6f57a004dca54f6e22db10603c9498a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59214851"
---
# <a name="ienumdefinitionidentity-interface"></a><span data-ttu-id="55a93-102">IEnumDefinitionIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="55a93-102">IEnumDefinitionIdentity Interface</span></span>
<span data-ttu-id="55a93-103">Bir koleksiyonu için bir numaralandırıcı görevi gören `IDefinitionIdentity` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="55a93-103">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55a93-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55a93-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="55a93-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="55a93-105">Methods</span></span>  
  
|<span data-ttu-id="55a93-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="55a93-106">Method</span></span>|<span data-ttu-id="55a93-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55a93-107">Description</span></span>|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|<span data-ttu-id="55a93-108">Yeni bir arabirim işaretçisi alır `IEnumDefinitionIdentity` bu aynı üyeleri içeren nesne `IEnumDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="55a93-108">Gets an interface pointer to a new `IEnumDefinitionIdentity` object that contains the same members as this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Next`|<span data-ttu-id="55a93-109">Belirtilen sayıda alır `IDefinitionIdentity` nesneleri, geçerli konumdan başlayarak.</span><span class="sxs-lookup"><span data-stu-id="55a93-109">Gets the specified number of `IDefinitionIdentity` objects, starting at the current position.</span></span>|  
|`IEnumDefinitionIdentity::Reset`|<span data-ttu-id="55a93-110">Yönerge işaretçisini bu başlangıcına taşır `IEnumDefinitionIdentity`.</span><span class="sxs-lookup"><span data-stu-id="55a93-110">Moves the instruction pointer to the beginning of this `IEnumDefinitionIdentity`.</span></span>|  
|`IEnumDefinitionIdentity::Skip`|<span data-ttu-id="55a93-111">Öğe, geçerli konumdan başlayarak belirtilen sayıda yönerge işaretçisini ileriye taşır.</span><span class="sxs-lookup"><span data-stu-id="55a93-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="55a93-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="55a93-112">Requirements</span></span>  
 <span data-ttu-id="55a93-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55a93-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55a93-114">**Üst bilgi:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="55a93-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="55a93-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55a93-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55a93-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55a93-116">See also</span></span>

- [<span data-ttu-id="55a93-117">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="55a93-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="55a93-118">IDefinitionIdentity Arabirimi</span><span class="sxs-lookup"><span data-stu-id="55a93-118">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)
