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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fa5a446ba7bfd70330601c7cbc129800761cdb7c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782615"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="b7915-102">IMetaDataImport::ResetEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b7915-102">IMetaDataImport::ResetEnum Method</span></span>
<span data-ttu-id="b7915-103">Belirtilen Numaralandırıcı belirtilen konuma sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="b7915-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7915-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b7915-104">Syntax</span></span>  
  
```cpp  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,   
   [in] ULONG       ulPos  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7915-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b7915-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="b7915-106">[in] Sıfırlamak için bir numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="b7915-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="b7915-107">[in] Numaralandırıcı yerleştirileceği en yeni konumu.</span><span class="sxs-lookup"><span data-stu-id="b7915-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7915-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b7915-108">Requirements</span></span>  
 <span data-ttu-id="b7915-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7915-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7915-110">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="b7915-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b7915-111">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b7915-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b7915-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7915-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7915-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7915-113">See also</span></span>

- [<span data-ttu-id="b7915-114">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b7915-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b7915-115">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b7915-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
