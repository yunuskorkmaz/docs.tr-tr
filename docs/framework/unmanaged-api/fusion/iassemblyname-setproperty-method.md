---
description: ': IAssemblyName:: SetProperty yöntemi hakkında daha fazla bilgi'
title: IAssemblyName::SetProperty Yöntemi
ms.date: 03/30/2017
api_name:
- IAssemblyName.SetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::SetProperty
helpviewer_keywords:
- IAssemblyName::SetProperty method [.NET Framework fusion]
- SetProperty method [.NET Framework fusion]
ms.assetid: 496c3add-f60b-4073-943f-d1bcf33330cb
topic_type:
- apiref
ms.openlocfilehash: cab132c2cd8a0744a2a946a1d8b21f49012c6eac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760698"
---
# <a name="iassemblynamesetproperty-method"></a><span data-ttu-id="4d1c3-103">IAssemblyName::SetProperty Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4d1c3-103">IAssemblyName::SetProperty Method</span></span>

<span data-ttu-id="4d1c3-104">Belirtilen özellik tanımlayıcısı tarafından başvurulan özelliğin değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4d1c3-104">Sets the value of the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d1c3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4d1c3-105">Syntax</span></span>  
  
```cpp  
HRESULT SetProperty (  
    [in] DWORD  PropertyId,  
    [in] LPVOID pvProperty,  
    [in] DWORD  cbProperty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d1c3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4d1c3-106">Parameters</span></span>  

 `PropertyId`  
 <span data-ttu-id="4d1c3-107">'ndaki Değeri ayarlanacak özelliğin benzersiz tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="4d1c3-107">[in] The unique identifier of the property whose value will be set.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="4d1c3-108">'ndaki Tarafından başvurulan özelliğin ayarlanacağı değer `PropertyId` .</span><span class="sxs-lookup"><span data-stu-id="4d1c3-108">[in] The value to which to set the property referenced by `PropertyId`.</span></span>  
  
 `cbProperty`  
 <span data-ttu-id="4d1c3-109">'ndaki Bayt cinsinden boyutu `pvProperty` .</span><span class="sxs-lookup"><span data-stu-id="4d1c3-109">[in] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d1c3-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4d1c3-110">Requirements</span></span>  

 <span data-ttu-id="4d1c3-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d1c3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d1c3-112">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="4d1c3-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="4d1c3-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d1c3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d1c3-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d1c3-114">See also</span></span>

- [<span data-ttu-id="4d1c3-115">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d1c3-115">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
