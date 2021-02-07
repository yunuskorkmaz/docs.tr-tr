---
description: ': IAssemblyName:: GetVersion yöntemi hakkında daha fazla bilgi'
title: IAssemblyName::GetVersion Metodu
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetVersion
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetVersion
helpviewer_keywords:
- IAssemblyName::GetVersion method [.NET Framework fusion]
- GetVersion method, IAssemblyName interface [.NET Framework fusion]
ms.assetid: 42230928-2c33-41fd-9519-d96efef6c7af
topic_type:
- apiref
ms.openlocfilehash: 3339dda6a0b4f083655ece7bef86b080a8fcf5c8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760725"
---
# <a name="iassemblynamegetversion-method"></a><span data-ttu-id="aaed1-103">IAssemblyName::GetVersion Metodu</span><span class="sxs-lookup"><span data-stu-id="aaed1-103">IAssemblyName::GetVersion Method</span></span>

<span data-ttu-id="aaed1-104">Bu [IAssemblyName](iassemblyname-interface.md) nesnesi tarafından başvurulan derleme için sürüm bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="aaed1-104">Gets the version information for the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaed1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aaed1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion (  
    [out] LPDWORD pdwVersionHi,  
    [out] LPDWORD pdwVersionLow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aaed1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aaed1-106">Parameters</span></span>  

 `pdwVersionHi`  
 <span data-ttu-id="aaed1-107">dışı Sürümün yüksek 32 bitleri.</span><span class="sxs-lookup"><span data-stu-id="aaed1-107">[out] The high 32 bits of the version.</span></span>  
  
 `pdwVersionLow`  
 <span data-ttu-id="aaed1-108">dışı Sürümün düşük 32 bitleri.</span><span class="sxs-lookup"><span data-stu-id="aaed1-108">[out] The low 32 bits of the version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aaed1-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aaed1-109">Requirements</span></span>  

 <span data-ttu-id="aaed1-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aaed1-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aaed1-111">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="aaed1-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="aaed1-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aaed1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaed1-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aaed1-113">See also</span></span>

- [<span data-ttu-id="aaed1-114">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aaed1-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
