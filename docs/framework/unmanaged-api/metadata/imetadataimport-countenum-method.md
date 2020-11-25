---
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
ms.openlocfilehash: f2470cd7112adff35ef49c21a155072fcd4008be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727295"
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="1a812-102">IMetaDataImport::CountEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a812-102">IMetaDataImport::CountEnum Method</span></span>

<span data-ttu-id="1a812-103">Belirtilen Numaralandırıcı tarafından alınan Numaralandırmadaki öğe sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="1a812-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a812-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1a812-104">Syntax</span></span>  
  
```cpp  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a812-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1a812-105">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="1a812-106">'ndaki Numaralandırıcı için tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="1a812-106">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="1a812-107">dışı Numaralandırılan öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="1a812-107">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a812-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1a812-108">Remarks</span></span>  

 <span data-ttu-id="1a812-109">Tarafından belirtilen tanıtıcı, `hEnum` önceki bir `Enum` *ad* çağrısından alınır (örneğin, [IMetaDataImport:: EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="1a812-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a812-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a812-110">Requirements</span></span>  

 <span data-ttu-id="1a812-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a812-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a812-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1a812-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1a812-113">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="1a812-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1a812-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a812-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a812-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a812-115">See also</span></span>

- [<span data-ttu-id="1a812-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a812-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="1a812-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a812-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
