---
description: ': IMetaDataImport:: GetSigFromToken yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 16b77fe5866319e24b33ec4ce9d2d56797f04514
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789144"
---
# <a name="imetadataimportgetsigfromtoken-method"></a><span data-ttu-id="d1d36-103">IMetaDataImport::GetSigFromToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d1d36-103">IMetaDataImport::GetSigFromToken Method</span></span>

<span data-ttu-id="d1d36-104">Belirtilen belirteçle ilişkili ikili meta veri imzasını alır.</span><span class="sxs-lookup"><span data-stu-id="d1d36-104">Gets the binary metadata signature associated with the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1d36-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d1d36-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSigFromToken (
   [in]   mdSignature        mdSig,
   [out]  PCCOR_SIGNATURE    *ppvSig,
   [out]  ULONG              *pcbSig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1d36-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d1d36-106">Parameters</span></span>  

 `mdSig`  
 <span data-ttu-id="d1d36-107">'ndaki İçin ikili meta veri imzasını döndürecek belirteç.</span><span class="sxs-lookup"><span data-stu-id="d1d36-107">[in] The token to return the binary metadata signature for.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="d1d36-108">dışı Döndürülen meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d1d36-108">[out] A pointer to the returned metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="d1d36-109">dışı İkili meta veri imzasının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="d1d36-109">[out] The size in bytes of the binary metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1d36-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d1d36-110">Requirements</span></span>  

 <span data-ttu-id="d1d36-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1d36-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1d36-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d1d36-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d1d36-113">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d1d36-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d1d36-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1d36-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1d36-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1d36-115">See also</span></span>

- [<span data-ttu-id="d1d36-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d1d36-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="d1d36-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d1d36-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
