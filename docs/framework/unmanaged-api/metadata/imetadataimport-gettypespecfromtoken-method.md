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
ms.openlocfilehash: 62495aa4280bb1799af09fea2e550ae6107e09e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729154"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="c40f9-102">IMetaDataImport::GetTypeSpecFromToken Metodu</span><span class="sxs-lookup"><span data-stu-id="c40f9-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>

<span data-ttu-id="c40f9-103">Belirtilen belirteçle temsil edilen tür belirtiminin ikili meta veri imzasını alır.</span><span class="sxs-lookup"><span data-stu-id="c40f9-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c40f9-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c40f9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeSpecFromToken (
   [in]  mdTypeSpec            typespec,
   [out] PCCOR_SIGNATURE       *ppvSig,
   [out] ULONG                 *pcbSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c40f9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c40f9-105">Parameters</span></span>  

 `typespec`  
 <span data-ttu-id="c40f9-106">'ndaki İstenen meta veri imzasıyla ilişkili TypeSpec belirteci.</span><span class="sxs-lookup"><span data-stu-id="c40f9-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="c40f9-107">dışı İkili meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c40f9-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="c40f9-108">dışı Meta veri imzasının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="c40f9-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c40f9-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c40f9-109">Return Value</span></span>  

 <span data-ttu-id="c40f9-110">Başarılı veya başarısız olduğunu gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="c40f9-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="c40f9-111">Başarısızlıklar başarısız makroyla test edilebilir.</span><span class="sxs-lookup"><span data-stu-id="c40f9-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c40f9-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c40f9-112">Requirements</span></span>  

 <span data-ttu-id="c40f9-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c40f9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c40f9-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c40f9-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c40f9-115">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="c40f9-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c40f9-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c40f9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c40f9-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c40f9-117">See also</span></span>

- [<span data-ttu-id="c40f9-118">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c40f9-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="c40f9-119">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c40f9-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
