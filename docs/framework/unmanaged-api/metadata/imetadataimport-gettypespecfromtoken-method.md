---
description: ': IMetaDataImport:: GetTypeSpecFromToken yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: b71f8f856da517b3e5046c20d787a555816fb728
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789118"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="661b4-103">IMetaDataImport::GetTypeSpecFromToken Metodu</span><span class="sxs-lookup"><span data-stu-id="661b4-103">IMetaDataImport::GetTypeSpecFromToken Method</span></span>

<span data-ttu-id="661b4-104">Belirtilen belirteçle temsil edilen tür belirtiminin ikili meta veri imzasını alır.</span><span class="sxs-lookup"><span data-stu-id="661b4-104">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="661b4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="661b4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeSpecFromToken (
   [in]  mdTypeSpec            typespec,
   [out] PCCOR_SIGNATURE       *ppvSig,
   [out] ULONG                 *pcbSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="661b4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="661b4-106">Parameters</span></span>  

 `typespec`  
 <span data-ttu-id="661b4-107">'ndaki İstenen meta veri imzasıyla ilişkili TypeSpec belirteci.</span><span class="sxs-lookup"><span data-stu-id="661b4-107">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="661b4-108">dışı İkili meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="661b4-108">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="661b4-109">dışı Meta veri imzasının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="661b4-109">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="661b4-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="661b4-110">Return Value</span></span>  

 <span data-ttu-id="661b4-111">Başarılı veya başarısız olduğunu gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="661b4-111">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="661b4-112">Başarısızlıklar başarısız makroyla test edilebilir.</span><span class="sxs-lookup"><span data-stu-id="661b4-112">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="661b4-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="661b4-113">Requirements</span></span>  

 <span data-ttu-id="661b4-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="661b4-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="661b4-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="661b4-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="661b4-116">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="661b4-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="661b4-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="661b4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="661b4-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="661b4-118">See also</span></span>

- [<span data-ttu-id="661b4-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="661b4-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="661b4-120">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="661b4-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
