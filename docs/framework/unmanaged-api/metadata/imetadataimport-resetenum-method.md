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
ms.openlocfilehash: 04bdd41e884caa5ed39dff4f4f1e027cde1fec53
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568016"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="0e535-102">IMetaDataImport::ResetEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0e535-102">IMetaDataImport::ResetEnum Method</span></span>
<span data-ttu-id="0e535-103">Belirtilen Numaralandırıcı belirtilen konuma sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="0e535-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e535-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e535-104">Syntax</span></span>  
  
```  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,   
   [in] ULONG       ulPos  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0e535-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0e535-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="0e535-106">[in] Sıfırlamak için bir numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="0e535-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="0e535-107">[in] Numaralandırıcı yerleştirileceği en yeni konumu.</span><span class="sxs-lookup"><span data-stu-id="0e535-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e535-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0e535-108">Requirements</span></span>  
 <span data-ttu-id="0e535-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e535-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e535-110">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="0e535-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0e535-111">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="0e535-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0e535-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e535-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e535-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e535-113">See also</span></span>
- [<span data-ttu-id="0e535-114">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0e535-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="0e535-115">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0e535-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
