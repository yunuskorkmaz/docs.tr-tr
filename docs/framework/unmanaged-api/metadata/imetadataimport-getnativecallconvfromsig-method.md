---
title: IMetaDataImport::GetNativeCallConvFromSig Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetNativeCallConvFromSig
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetNativeCallConvFromSig
helpviewer_keywords:
- GetNativeCallConvFromSig method [.NET Framework metadata]
- IMetaDataImport::GetNativeCallConvFromSig method [.NET Framework metadata]
ms.assetid: 50e04026-4d4a-47d9-96c1-f4677d6d938b
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 56c67ad76fb3a4ce5ab2d107ff59da7a932835b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetnativecallconvfromsig-method"></a><span data-ttu-id="3f3ea-102">IMetaDataImport::GetNativeCallConvFromSig Metodu</span><span class="sxs-lookup"><span data-stu-id="3f3ea-102">IMetaDataImport::GetNativeCallConvFromSig Method</span></span>
<span data-ttu-id="3f3ea-103">Yerel bir belirtilen imza işaretçiyi tarafından temsil edilen yöntemi çağırma alır.</span><span class="sxs-lookup"><span data-stu-id="3f3ea-103">Gets the native calling convention for the method that is represented by the specified signature pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f3ea-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f3ea-104">Syntax</span></span>  
  
```  
HRESULT GetNativeCallConvFromSig (  
   [in]  void const  *pvSig,  
   [in]  ULONG       cbSig,  
   [out] ULONG       *pCallConv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3f3ea-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3f3ea-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="3f3ea-106">[in] Meta veri imza için çağırma kuralı döndürmek için yöntemin bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3f3ea-106">[in] A pointer to the metadata signature of the method to return the calling convention for.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="3f3ea-107">[in] Bayt cinsinden boyutu `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="3f3ea-107">[in] The size in bytes of `pvSig`.</span></span>  
  
 `pCallConv`  
 <span data-ttu-id="3f3ea-108">[out] Yerel arama kuralı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3f3ea-108">[out] A pointer to the native calling convention.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f3ea-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f3ea-109">Requirements</span></span>  
 <span data-ttu-id="3f3ea-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f3ea-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f3ea-111">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3f3ea-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3f3ea-112">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3f3ea-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3f3ea-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f3ea-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f3ea-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3f3ea-114">See Also</span></span>  
 <xref:System.Runtime.InteropServices.CallingConvention>  
 [<span data-ttu-id="3f3ea-115">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f3ea-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="3f3ea-116">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f3ea-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
