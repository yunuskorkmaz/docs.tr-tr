---
description: ': Imetadatayayma:: Save yöntemi hakkında daha fazla bilgi'
title: IMetaDataEmit::Save Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Save
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Save
helpviewer_keywords:
- Save method, IMetaDataEmit interface [.NET Framework metadata]
- IMetaDataEmit::Save method [.NET Framework metadata]
ms.assetid: c1de8400-adfe-4a71-b828-a1d0cc1ea505
topic_type:
- apiref
ms.openlocfilehash: bf8675540ae2c851d2b6ed14883c9b75e9631903
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745872"
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="106c8-103">IMetaDataEmit::Save Yöntemi</span><span class="sxs-lookup"><span data-stu-id="106c8-103">IMetaDataEmit::Save Method</span></span>

<span data-ttu-id="106c8-104">Geçerli kapsamdaki tüm meta verileri belirtilen adresteki dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="106c8-104">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="106c8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="106c8-105">Syntax</span></span>  
  
```cpp  
HRESULT Save (
    [in]  LPCWSTR     szFile,
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="106c8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="106c8-106">Parameters</span></span>  

 `wzFile`  
 <span data-ttu-id="106c8-107">'ndaki Kaydedilecek dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="106c8-107">[in] The name of the file to save to.</span></span> <span data-ttu-id="106c8-108">Bu değer null ise, bellek içi kopyalama kullanılan son konuma kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="106c8-108">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="106c8-109">'ndaki Ayrılamadı.</span><span class="sxs-lookup"><span data-stu-id="106c8-109">[in] Reserved.</span></span> <span data-ttu-id="106c8-110">Sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="106c8-110">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="106c8-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="106c8-111">Requirements</span></span>  

 <span data-ttu-id="106c8-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="106c8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="106c8-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="106c8-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="106c8-114">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="106c8-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="106c8-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="106c8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="106c8-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="106c8-116">See also</span></span>

- [<span data-ttu-id="106c8-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="106c8-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="106c8-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="106c8-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
