---
description: ': IAssemblyName:: GetName metodu hakkında daha fazla bilgi'
title: IAssemblyName::GetName Yöntemi
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetName
helpviewer_keywords:
- GetName method, IAssemblyName interface [.NET Framework debugging]
- IAssemblyName::GetName method [.NET Framework fusion]
ms.assetid: 1dee9781-1cf3-48a9-a376-d18ea1f73280
topic_type:
- apiref
ms.openlocfilehash: 04cd6258c2fc60c9fc40e1e4b731e5c04a8d3112
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760751"
---
# <a name="iassemblynamegetname-method"></a><span data-ttu-id="b3d24-103">IAssemblyName::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b3d24-103">IAssemblyName::GetName Method</span></span>

<span data-ttu-id="b3d24-104">Bu [IAssemblyName](iassemblyname-interface.md) nesnesinin başvurduğu derlemenin basit, şifrelenmemiş adını alır.</span><span class="sxs-lookup"><span data-stu-id="b3d24-104">Gets the simple, unencrypted name of the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3d24-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b3d24-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in, out] LPDWORD lpcwBuffer,  
    [out]     WCHAR *pwzName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3d24-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b3d24-106">Parameters</span></span>  

 `lpcwBuffer`  
 <span data-ttu-id="b3d24-107">[in, out] `pwzName` Null Sonlandırıcı karakteri de dahil olmak üzere geniş karakter cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="b3d24-107">[in, out] The size of `pwzName` in wide characters, including the null terminator character.</span></span>  
  
 `pwzName`  
 <span data-ttu-id="b3d24-108">dışı Başvurulan derlemenin adını tutan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="b3d24-108">[out] A buffer to hold the name of the referenced assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3d24-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b3d24-109">Requirements</span></span>  

 <span data-ttu-id="b3d24-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3d24-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3d24-111">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="b3d24-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b3d24-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3d24-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3d24-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3d24-113">See also</span></span>

- [<span data-ttu-id="b3d24-114">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b3d24-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
