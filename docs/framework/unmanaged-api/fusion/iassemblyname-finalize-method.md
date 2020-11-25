---
title: IAssemblyName::Finalize Yöntemi
ms.date: 03/30/2017
api_name:
- IAssemblyName.Finalize
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::Finalize
helpviewer_keywords:
- Finalize method [.NET Framework fusion]
- IAssemblyName::Finalize method [.NET Framework fusion]
ms.assetid: 610e792d-98ef-411f-90b0-5b9a3813f547
topic_type:
- apiref
ms.openlocfilehash: 842b878fac1e2590eb6ea0b29ebee0d46e818474
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727932"
---
# <a name="iassemblynamefinalize-method"></a><span data-ttu-id="9b1ca-102">IAssemblyName::Finalize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b1ca-102">IAssemblyName::Finalize Method</span></span>

<span data-ttu-id="9b1ca-103">Bu [IAssemblyName](iassemblyname-interface.md) nesnesinin, yıkıcısı çağrılmadan önce kaynakları serbest bırakma ve diğer temizleme işlemlerini gerçekleştirmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="9b1ca-103">Allows this [IAssemblyName](iassemblyname-interface.md) object to release resources and perform other cleanup operations before its destructor is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b1ca-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="9b1ca-104">Syntax</span></span>  
  
```cpp  
HRESULT Finalize ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="9b1ca-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b1ca-105">Requirements</span></span>  

 <span data-ttu-id="9b1ca-106">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b1ca-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b1ca-107">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="9b1ca-107">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="9b1ca-108">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b1ca-108">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b1ca-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b1ca-109">See also</span></span>

- [<span data-ttu-id="9b1ca-110">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9b1ca-110">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
