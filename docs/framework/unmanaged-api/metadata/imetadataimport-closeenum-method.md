---
description: ': IMetaDataImport:: CloseEnum Yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataImport::CloseEnum Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CloseEnum
helpviewer_keywords:
- IMetaDataImport::CloseEnum method [.NET Framework metadata]
- CloseEnum method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 727819d5-1dab-4ebb-ac25-950b4111dc72
topic_type:
- apiref
ms.openlocfilehash: b18b484cab0d9f4c0ecea21da78535c9a872bb1d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677749"
---
# <a name="imetadataimportcloseenum-method"></a><span data-ttu-id="d9911-103">IMetaDataImport::CloseEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d9911-103">IMetaDataImport::CloseEnum Method</span></span>

<span data-ttu-id="d9911-104">Belirtilen tanıtıcı tarafından tanımlanan numaralandırıcısı kapatır.</span><span class="sxs-lookup"><span data-stu-id="d9911-104">Closes the enumerator that is identified by the specified handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9911-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9911-105">Syntax</span></span>  
  
```cpp  
void CloseEnum (  
   [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9911-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d9911-106">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="d9911-107">'ndaki Numaralandırıcının kapanmak için tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="d9911-107">[in] The handle for the enumerator to close.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9911-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d9911-108">Remarks</span></span>  

 <span data-ttu-id="d9911-109">Tarafından belirtilen tanıtıcı, `hEnum` önceki bir `Enum` *ad* çağrısından alınır (örneğin, [IMetaDataImport:: EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="d9911-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9911-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d9911-110">Requirements</span></span>  

 <span data-ttu-id="d9911-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9911-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9911-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d9911-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d9911-113">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d9911-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d9911-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9911-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9911-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9911-115">See also</span></span>

- [<span data-ttu-id="d9911-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9911-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="d9911-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9911-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
