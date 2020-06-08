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
ms.openlocfilehash: d795f90c458b7fcf1a191b2763ac5f5bb55fb438
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490907"
---
# <a name="imetadataimportgetsigfromtoken-method"></a><span data-ttu-id="be7aa-102">IMetaDataImport::GetSigFromToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="be7aa-102">IMetaDataImport::GetSigFromToken Method</span></span>
<span data-ttu-id="be7aa-103">Belirtilen belirteçle ilişkili ikili meta veri imzasını alır.</span><span class="sxs-lookup"><span data-stu-id="be7aa-103">Gets the binary metadata signature associated with the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be7aa-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="be7aa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSigFromToken (
   [in]   mdSignature        mdSig,
   [out]  PCCOR_SIGNATURE    *ppvSig,
   [out]  ULONG              *pcbSig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be7aa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="be7aa-105">Parameters</span></span>  
 `mdSig`  
 <span data-ttu-id="be7aa-106">'ndaki İçin ikili meta veri imzasını döndürecek belirteç.</span><span class="sxs-lookup"><span data-stu-id="be7aa-106">[in] The token to return the binary metadata signature for.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="be7aa-107">dışı Döndürülen meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="be7aa-107">[out] A pointer to the returned metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="be7aa-108">dışı İkili meta veri imzasının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="be7aa-108">[out] The size in bytes of the binary metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be7aa-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be7aa-109">Requirements</span></span>  
 <span data-ttu-id="be7aa-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be7aa-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be7aa-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="be7aa-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="be7aa-112">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="be7aa-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="be7aa-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be7aa-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be7aa-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be7aa-114">See also</span></span>

- [<span data-ttu-id="be7aa-115">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="be7aa-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="be7aa-116">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="be7aa-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
