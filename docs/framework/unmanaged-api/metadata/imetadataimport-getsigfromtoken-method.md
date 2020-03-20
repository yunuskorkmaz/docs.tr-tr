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
ms.openlocfilehash: 5af59e158a34b06d304a98db1dfaa46585b22eb6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177201"
---
# <a name="imetadataimportgetsigfromtoken-method"></a><span data-ttu-id="bd492-102">IMetaDataImport::GetSigFromToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bd492-102">IMetaDataImport::GetSigFromToken Method</span></span>
<span data-ttu-id="bd492-103">Belirtilen belirteçle ilişkili ikili meta veri imzasını alır.</span><span class="sxs-lookup"><span data-stu-id="bd492-103">Gets the binary metadata signature associated with the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd492-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bd492-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSigFromToken (
   [in]   mdSignature        mdSig,
   [out]  PCCOR_SIGNATURE    *ppvSig,
   [out]  ULONG              *pcbSig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd492-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bd492-105">Parameters</span></span>  
 `mdSig`  
 <span data-ttu-id="bd492-106">[içinde] İkili meta veri imzasını döndürmek için belirteç.</span><span class="sxs-lookup"><span data-stu-id="bd492-106">[in] The token to return the binary metadata signature for.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="bd492-107">[çıkış] Döndürülen meta veri imzası için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bd492-107">[out] A pointer to the returned metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="bd492-108">[çıkış] İkili meta veri imzasının baytboyutu.</span><span class="sxs-lookup"><span data-stu-id="bd492-108">[out] The size in bytes of the binary metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd492-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bd492-109">Requirements</span></span>  
 <span data-ttu-id="bd492-110">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd492-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd492-111">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bd492-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bd492-112">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="bd492-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bd492-113">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd492-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd492-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd492-114">See also</span></span>

- [<span data-ttu-id="bd492-115">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bd492-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="bd492-116">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bd492-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
