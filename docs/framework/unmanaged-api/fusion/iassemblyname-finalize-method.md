---
description: 'Şu konuda daha fazla bilgi edinin: IAssemblyName:: Finalize yöntemi'
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
ms.openlocfilehash: d6277fdbc15f6f907d5e758dac4a3670570d585d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760777"
---
# <a name="iassemblynamefinalize-method"></a><span data-ttu-id="ca363-103">IAssemblyName::Finalize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ca363-103">IAssemblyName::Finalize Method</span></span>

<span data-ttu-id="ca363-104">Bu [IAssemblyName](iassemblyname-interface.md) nesnesinin, yıkıcısı çağrılmadan önce kaynakları serbest bırakma ve diğer temizleme işlemlerini gerçekleştirmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="ca363-104">Allows this [IAssemblyName](iassemblyname-interface.md) object to release resources and perform other cleanup operations before its destructor is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca363-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ca363-105">Syntax</span></span>  
  
```cpp  
HRESULT Finalize ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="ca363-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ca363-106">Requirements</span></span>  

 <span data-ttu-id="ca363-107">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca363-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca363-108">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="ca363-108">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ca363-109">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca363-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca363-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca363-110">See also</span></span>

- [<span data-ttu-id="ca363-111">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ca363-111">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
