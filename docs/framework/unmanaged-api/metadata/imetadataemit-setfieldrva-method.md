---
description: ': Imetadatayayma:: SetFieldRVA yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataEmit::SetFieldRVA Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldRVA
helpviewer_keywords:
- IMetaDataEmit::SetFieldRVA method [.NET Framework metadata]
- SetFieldRVA method [.NET Framework metadata]
ms.assetid: 6dc37f9d-87ee-4cb3-9216-ced600184ce8
topic_type:
- apiref
ms.openlocfilehash: 5d78880b892dc948337aa1ec1a471a5d380f1e2f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657937"
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="4ddde-103">IMetaDataEmit::SetFieldRVA Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4ddde-103">IMetaDataEmit::SetFieldRVA Method</span></span>

<span data-ttu-id="4ddde-104">Belirtilen belirtecin başvurduğu alanın göreli sanal adresi için genel bir değişken değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4ddde-104">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ddde-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ddde-105">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldRVA (
    [in]  mdFieldDef  fd,
    [in]  ULONG       ulRVA
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ddde-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4ddde-106">Parameters</span></span>  

 `fd`  
 <span data-ttu-id="4ddde-107">'ndaki Hedef alan için belirteç.</span><span class="sxs-lookup"><span data-stu-id="4ddde-107">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="4ddde-108">'ndaki Bir kodun veya veri alanının adresi.</span><span class="sxs-lookup"><span data-stu-id="4ddde-108">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ddde-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4ddde-109">Requirements</span></span>  

 <span data-ttu-id="4ddde-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ddde-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ddde-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4ddde-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4ddde-112">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="4ddde-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4ddde-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ddde-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ddde-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ddde-114">See also</span></span>

- [<span data-ttu-id="4ddde-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4ddde-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="4ddde-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4ddde-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
