---
description: ': IMetaDataImport:: ResetEnum yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 7b1572be2e2b905e6db5cf6e422643dbb76ca9be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99670586"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="099cb-103">IMetaDataImport::ResetEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="099cb-103">IMetaDataImport::ResetEnum Method</span></span>

<span data-ttu-id="099cb-104">Belirtilen numaralandırıcısı belirtilen konuma sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="099cb-104">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="099cb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="099cb-105">Syntax</span></span>  
  
```cpp  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,
   [in] ULONG       ulPos  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="099cb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="099cb-106">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="099cb-107">'ndaki Sıfırlanacak Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="099cb-107">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="099cb-108">'ndaki Numaralandırıcının yerleştirileceği yeni konum.</span><span class="sxs-lookup"><span data-stu-id="099cb-108">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="099cb-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="099cb-109">Requirements</span></span>  

 <span data-ttu-id="099cb-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="099cb-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="099cb-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="099cb-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="099cb-112">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="099cb-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="099cb-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="099cb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="099cb-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="099cb-114">See also</span></span>

- [<span data-ttu-id="099cb-115">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="099cb-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="099cb-116">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="099cb-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
