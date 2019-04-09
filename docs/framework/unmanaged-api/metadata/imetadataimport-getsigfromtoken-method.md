---
title: IMetaDataImport::GetSigFromToken Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetSigFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetSigFromToken
helpviewer_keywords:
- IMetaDataImport::GetSigFromToken method [.NET Framework metadata]
- GetSigFromToken method [.NET Framework metadata]
ms.assetid: ab894dc4-f7b6-4afc-bfcb-582a4b7e53a2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 823a172c05d2ce76fef790966f54d7216f579fde
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59152990"
---
# <a name="imetadataimportgetsigfromtoken-method"></a><span data-ttu-id="85f7c-102">IMetaDataImport::GetSigFromToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85f7c-102">IMetaDataImport::GetSigFromToken Method</span></span>
<span data-ttu-id="85f7c-103">Belirtilen belirteçle ilişkili ikili meta veri imzası alır.</span><span class="sxs-lookup"><span data-stu-id="85f7c-103">Gets the binary metadata signature associated with the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85f7c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="85f7c-104">Syntax</span></span>  
  
```  
HRESULT GetSigFromToken (   
   [in]   mdSignature        mdSig,   
   [out]  PCCOR_SIGNATURE    *ppvSig,   
   [out]  ULONG              *pcbSig   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85f7c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="85f7c-105">Parameters</span></span>  
 `mdSig`  
 <span data-ttu-id="85f7c-106">[in] İkili meta veri imzası döndürmek için belirteç.</span><span class="sxs-lookup"><span data-stu-id="85f7c-106">[in] The token to return the binary metadata signature for.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="85f7c-107">[out] Döndürülen meta veri imzası bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="85f7c-107">[out] A pointer to the returned metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="85f7c-108">[out] İkili meta verileri imza bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="85f7c-108">[out] The size in bytes of the binary metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85f7c-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="85f7c-109">Requirements</span></span>  
 <span data-ttu-id="85f7c-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85f7c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85f7c-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="85f7c-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="85f7c-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="85f7c-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="85f7c-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="85f7c-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="85f7c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85f7c-114">See also</span></span>

- [<span data-ttu-id="85f7c-115">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85f7c-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="85f7c-116">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85f7c-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
