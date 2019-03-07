---
title: IMetaDataImport::GetNativeCallConvFromSig Yöntemi
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
ms.openlocfilehash: 1002aa9e01fedaacf80622952bbba82caa7081c1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498022"
---
# <a name="imetadataimportgetnativecallconvfromsig-method"></a><span data-ttu-id="13501-102">IMetaDataImport::GetNativeCallConvFromSig Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13501-102">IMetaDataImport::GetNativeCallConvFromSig Method</span></span>
<span data-ttu-id="13501-103">Yerel bir belirtilen imza işaretçi tarafından temsil edilen yöntem için çağırma alır.</span><span class="sxs-lookup"><span data-stu-id="13501-103">Gets the native calling convention for the method that is represented by the specified signature pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13501-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13501-104">Syntax</span></span>  
  
```  
HRESULT GetNativeCallConvFromSig (  
   [in]  void const  *pvSig,  
   [in]  ULONG       cbSig,  
   [out] ULONG       *pCallConv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13501-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="13501-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="13501-106">[in] Çağırma kuralının döndürmek için yöntemin meta veri imzası bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="13501-106">[in] A pointer to the metadata signature of the method to return the calling convention for.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="13501-107">[in] Bayt cinsinden boyutu `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="13501-107">[in] The size in bytes of `pvSig`.</span></span>  
  
 `pCallConv`  
 <span data-ttu-id="13501-108">[out] Yerel çağrı kuralı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="13501-108">[out] A pointer to the native calling convention.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13501-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13501-109">Requirements</span></span>  
 <span data-ttu-id="13501-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13501-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13501-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="13501-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="13501-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="13501-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="13501-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13501-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13501-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13501-114">See also</span></span>
- <xref:System.Runtime.InteropServices.CallingConvention>
- [<span data-ttu-id="13501-115">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13501-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="13501-116">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13501-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
