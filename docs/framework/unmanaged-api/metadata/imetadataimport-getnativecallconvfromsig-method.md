---
title: IMetaDataImport::GetNativeCallConvFromSig Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNativeCallConvFromSig
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNativeCallConvFromSig
helpviewer_keywords:
- GetNativeCallConvFromSig method [.NET Framework metadata]
- IMetaDataImport::GetNativeCallConvFromSig method [.NET Framework metadata]
ms.assetid: 50e04026-4d4a-47d9-96c1-f4677d6d938b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 963d46aea4ab31e770cb845fe699208f6c8f9ac7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447246"
---
# <a name="imetadataimportgetnativecallconvfromsig-method"></a><span data-ttu-id="e2a07-102">IMetaDataImport::GetNativeCallConvFromSig Metodu</span><span class="sxs-lookup"><span data-stu-id="e2a07-102">IMetaDataImport::GetNativeCallConvFromSig Method</span></span>
<span data-ttu-id="e2a07-103">Yerel bir belirtilen imza işaretçiyi tarafından temsil edilen yöntemi çağırma alır.</span><span class="sxs-lookup"><span data-stu-id="e2a07-103">Gets the native calling convention for the method that is represented by the specified signature pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2a07-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2a07-104">Syntax</span></span>  
  
```  
HRESULT GetNativeCallConvFromSig (  
   [in]  void const  *pvSig,  
   [in]  ULONG       cbSig,  
   [out] ULONG       *pCallConv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2a07-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e2a07-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="e2a07-106">[in] Meta veri imza için çağırma kuralı döndürmek için yöntemin bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e2a07-106">[in] A pointer to the metadata signature of the method to return the calling convention for.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="e2a07-107">[in] Bayt cinsinden boyutu `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="e2a07-107">[in] The size in bytes of `pvSig`.</span></span>  
  
 `pCallConv`  
 <span data-ttu-id="e2a07-108">[out] Yerel arama kuralı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e2a07-108">[out] A pointer to the native calling convention.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2a07-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2a07-109">Requirements</span></span>  
 <span data-ttu-id="e2a07-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2a07-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2a07-111">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e2a07-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e2a07-112">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e2a07-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e2a07-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2a07-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2a07-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e2a07-114">See Also</span></span>  
 <xref:System.Runtime.InteropServices.CallingConvention>  
 [<span data-ttu-id="e2a07-115">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2a07-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="e2a07-116">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2a07-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
