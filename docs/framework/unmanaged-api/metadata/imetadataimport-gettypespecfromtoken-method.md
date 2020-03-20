---
title: IMetaDataImport::GetTypeSpecFromToken Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeSpecFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeSpecFromToken
helpviewer_keywords:
- GetTypeSpecFromToken method [.NET Framework metadata]
- IMetaDataImport::GetTypeSpecFromToken method [.NET Framework metadata]
ms.assetid: ee518bda-3296-482e-a7b7-e9d51dd1a181
topic_type:
- apiref
ms.openlocfilehash: 34b7cebfa063a3ad077b74a753fd37ba67ff53a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175323"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="c1b92-102">IMetaDataImport::GetTypeSpecFromToken Metodu</span><span class="sxs-lookup"><span data-stu-id="c1b92-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="c1b92-103">Belirtilen belirteç tarafından temsil edilen tür belirtiminin ikili meta veri imzasını alır.</span><span class="sxs-lookup"><span data-stu-id="c1b92-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1b92-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1b92-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeSpecFromToken (
   [in]  mdTypeSpec            typespec,
   [out] PCCOR_SIGNATURE       *ppvSig,
   [out] ULONG                 *pcbSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1b92-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c1b92-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="c1b92-106">[içinde] İstenen meta veri imzasıyla ilişkili TypeSpec belirteci.</span><span class="sxs-lookup"><span data-stu-id="c1b92-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="c1b92-107">[çıkış] İkili meta veri imzası için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c1b92-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="c1b92-108">[çıkış] Meta veri imzasının baytboyutu.</span><span class="sxs-lookup"><span data-stu-id="c1b92-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1b92-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c1b92-109">Return Value</span></span>  
 <span data-ttu-id="c1b92-110">Başarı veya başarısızlığı gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="c1b92-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="c1b92-111">Hatalar FAILED makrosu ile test edilebilir.</span><span class="sxs-lookup"><span data-stu-id="c1b92-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1b92-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c1b92-112">Requirements</span></span>  
 <span data-ttu-id="c1b92-113">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1b92-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1b92-114">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c1b92-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c1b92-115">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="c1b92-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c1b92-116">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1b92-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1b92-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1b92-117">See also</span></span>

- [<span data-ttu-id="c1b92-118">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1b92-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c1b92-119">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1b92-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
