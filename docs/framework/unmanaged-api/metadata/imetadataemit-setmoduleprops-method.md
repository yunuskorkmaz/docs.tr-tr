---
title: IMetaDataEmit::SetModuleProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetModuleProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetModuleProps
helpviewer_keywords:
- SetModuleProps method [.NET Framework metadata]
- IMetaDataEmit::SetModuleProps method [.NET Framework metadata]
ms.assetid: b74d7629-5f46-458f-8d67-2456a1e7030c
topic_type:
- apiref
ms.openlocfilehash: 69c3ee366dbb8505e0df744037c480da996bb836
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175622"
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="1b53e-102">IMetaDataEmit::SetModuleProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b53e-102">IMetaDataEmit::SetModuleProps Method</span></span>
<span data-ttu-id="1b53e-103">[Başvuruları IMetaDataEmit::DefineModuleRef'e](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md)önceden yapılan bir çağrıyla tanımlanan bir modüle güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="1b53e-103">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b53e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b53e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetModuleProps (
    [in]  LPCWSTR     szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b53e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1b53e-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="1b53e-106">[içinde] Unicode'daki modül adı.</span><span class="sxs-lookup"><span data-stu-id="1b53e-106">[in] The module name in Unicode.</span></span> <span data-ttu-id="1b53e-107">Bu yalnızca dosya adıdır ve tam yol adı değildir.</span><span class="sxs-lookup"><span data-stu-id="1b53e-107">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b53e-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1b53e-108">Requirements</span></span>  
 <span data-ttu-id="1b53e-109">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b53e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b53e-110">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1b53e-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1b53e-111">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="1b53e-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b53e-112">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b53e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b53e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b53e-113">See also</span></span>

- [<span data-ttu-id="1b53e-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b53e-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="1b53e-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b53e-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
