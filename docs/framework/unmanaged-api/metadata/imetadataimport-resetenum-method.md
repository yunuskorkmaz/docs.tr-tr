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
ms.openlocfilehash: 3dd82588cf2dbf92fdda66fd7674c17ddc8b7306
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177184"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="bad15-102">IMetaDataImport::ResetEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bad15-102">IMetaDataImport::ResetEnum Method</span></span>
<span data-ttu-id="bad15-103">Belirtilen sayısallaştırıcıyı belirtilen konuma sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="bad15-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bad15-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bad15-104">Syntax</span></span>  
  
```cpp  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,
   [in] ULONG       ulPos  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bad15-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bad15-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="bad15-106">[içinde] Sıfırlamak için enumerator.</span><span class="sxs-lookup"><span data-stu-id="bad15-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="bad15-107">[içinde] Enumerator yerleştirmek için yeni pozisyon.</span><span class="sxs-lookup"><span data-stu-id="bad15-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bad15-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bad15-108">Requirements</span></span>  
 <span data-ttu-id="bad15-109">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bad15-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bad15-110">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bad15-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bad15-111">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="bad15-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bad15-112">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bad15-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bad15-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bad15-113">See also</span></span>

- [<span data-ttu-id="bad15-114">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bad15-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="bad15-115">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bad15-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
