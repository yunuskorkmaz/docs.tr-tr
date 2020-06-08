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
ms.openlocfilehash: 4521a3f15ec358a4d786a4533efb6b99d0e1c1cc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492388"
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="9b08c-102">IMetaDataImport::CountEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b08c-102">IMetaDataImport::CountEnum Method</span></span>
<span data-ttu-id="9b08c-103">Belirtilen Numaralandırıcı tarafından alınan Numaralandırmadaki öğe sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="9b08c-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b08c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9b08c-104">Syntax</span></span>  
  
```cpp  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b08c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9b08c-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="9b08c-106">'ndaki Numaralandırıcı için tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="9b08c-106">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="9b08c-107">dışı Numaralandırılan öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="9b08c-107">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b08c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9b08c-108">Remarks</span></span>  
 <span data-ttu-id="9b08c-109">Tarafından belirtilen tanıtıcı, `hEnum` önceki bir `Enum` *ad* çağrısından alınır (örneğin, [IMetaDataImport:: EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="9b08c-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b08c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b08c-110">Requirements</span></span>  
 <span data-ttu-id="9b08c-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b08c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b08c-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9b08c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9b08c-113">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="9b08c-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9b08c-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b08c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b08c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b08c-115">See also</span></span>

- [<span data-ttu-id="9b08c-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9b08c-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="9b08c-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9b08c-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
