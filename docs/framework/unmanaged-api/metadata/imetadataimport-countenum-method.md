---
description: ': IMetaDataImport:: CountEnum yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataImport::CountEnum Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CountEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CountEnum
helpviewer_keywords:
- CountEnum method [.NET Framework metadata]
- IMetaDataImport::CountEnum method [.NET Framework metadata]
ms.assetid: d1de53ad-9435-4b5f-9df7-07f21210e5b5
topic_type:
- apiref
ms.openlocfilehash: c579ef7ce440e3552ab28572fc6c96ad12d66400
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677697"
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="07736-103">IMetaDataImport::CountEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="07736-103">IMetaDataImport::CountEnum Method</span></span>

<span data-ttu-id="07736-104">Belirtilen Numaralandırıcı tarafından alınan Numaralandırmadaki öğe sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="07736-104">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07736-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07736-105">Syntax</span></span>  
  
```cpp  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07736-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="07736-106">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="07736-107">'ndaki Numaralandırıcı için tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="07736-107">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="07736-108">dışı Numaralandırılan öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="07736-108">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07736-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07736-109">Remarks</span></span>  

 <span data-ttu-id="07736-110">Tarafından belirtilen tanıtıcı, `hEnum` önceki bir `Enum` *ad* çağrısından alınır (örneğin, [IMetaDataImport:: EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="07736-110">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07736-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07736-111">Requirements</span></span>  

 <span data-ttu-id="07736-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07736-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07736-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="07736-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="07736-114">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="07736-114">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="07736-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07736-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07736-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07736-116">See also</span></span>

- [<span data-ttu-id="07736-117">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="07736-117">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="07736-118">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="07736-118">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
