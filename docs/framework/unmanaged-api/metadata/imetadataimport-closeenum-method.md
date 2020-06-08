---
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
ms.openlocfilehash: 5de62db4180a6a9160193053fe42e39cebc34d0e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492505"
---
# <a name="imetadataimportcloseenum-method"></a><span data-ttu-id="08de9-102">IMetaDataImport::CloseEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08de9-102">IMetaDataImport::CloseEnum Method</span></span>
<span data-ttu-id="08de9-103">Belirtilen tanıtıcı tarafından tanımlanan numaralandırıcısı kapatır.</span><span class="sxs-lookup"><span data-stu-id="08de9-103">Closes the enumerator that is identified by the specified handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08de9-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="08de9-104">Syntax</span></span>  
  
```cpp  
void CloseEnum (  
   [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08de9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="08de9-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="08de9-106">'ndaki Numaralandırıcının kapanmak için tanıtıcı.</span><span class="sxs-lookup"><span data-stu-id="08de9-106">[in] The handle for the enumerator to close.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08de9-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08de9-107">Remarks</span></span>  
 <span data-ttu-id="08de9-108">Tarafından belirtilen tanıtıcı, `hEnum` önceki bir `Enum` *ad* çağrısından alınır (örneğin, [IMetaDataImport:: EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="08de9-108">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08de9-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08de9-109">Requirements</span></span>  
 <span data-ttu-id="08de9-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08de9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08de9-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="08de9-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="08de9-112">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="08de9-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="08de9-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08de9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08de9-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08de9-114">See also</span></span>

- [<span data-ttu-id="08de9-115">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08de9-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="08de9-116">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08de9-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
