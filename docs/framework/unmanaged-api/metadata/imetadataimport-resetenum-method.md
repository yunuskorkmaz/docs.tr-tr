---
title: IMetaDataImport::ResetEnum Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResetEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResetEnum
helpviewer_keywords:
- ResetEnum method [.NET Framework metadata]
- IMetaDataImport::ResetEnum method [.NET Framework metadata]
ms.assetid: dda867b5-1050-49ba-b01c-fcc83b7a5617
topic_type:
- apiref
ms.openlocfilehash: bc7f1740d666211b63cd93e6f1c0e6955f61ec5d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503464"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="133a8-102">IMetaDataImport::ResetEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="133a8-102">IMetaDataImport::ResetEnum Method</span></span>
<span data-ttu-id="133a8-103">Belirtilen numaralandırıcısı belirtilen konuma sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="133a8-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="133a8-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="133a8-104">Syntax</span></span>  
  
```cpp  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,
   [in] ULONG       ulPos  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="133a8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="133a8-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="133a8-106">'ndaki Sıfırlanacak Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="133a8-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="133a8-107">'ndaki Numaralandırıcının yerleştirileceği yeni konum.</span><span class="sxs-lookup"><span data-stu-id="133a8-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="133a8-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="133a8-108">Requirements</span></span>  
 <span data-ttu-id="133a8-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="133a8-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="133a8-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="133a8-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="133a8-111">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="133a8-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="133a8-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="133a8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="133a8-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="133a8-113">See also</span></span>

- [<span data-ttu-id="133a8-114">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="133a8-114">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="133a8-115">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="133a8-115">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
