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
ms.openlocfilehash: 56fc0273fb2c1b77c74d7a1d853886f47170497e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447934"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="f6d0e-102">IMetaDataImport::ResetEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f6d0e-102">IMetaDataImport::ResetEnum Method</span></span>
<span data-ttu-id="f6d0e-103">Belirtilen Numaralandırıcı belirtilen konuma sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="f6d0e-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6d0e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f6d0e-104">Syntax</span></span>  
  
```  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,   
   [in] ULONG       ulPos  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f6d0e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f6d0e-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="f6d0e-106">[in] Sıfırlama Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="f6d0e-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="f6d0e-107">[in] Numaralayıcı yerleştirmek için en yeni konumu.</span><span class="sxs-lookup"><span data-stu-id="f6d0e-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6d0e-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f6d0e-108">Requirements</span></span>  
 <span data-ttu-id="f6d0e-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6d0e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6d0e-110">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f6d0e-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f6d0e-111">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f6d0e-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f6d0e-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6d0e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6d0e-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f6d0e-113">See Also</span></span>  
 [<span data-ttu-id="f6d0e-114">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f6d0e-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="f6d0e-115">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f6d0e-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
