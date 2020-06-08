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
ms.openlocfilehash: 43e9671afa92d36966e51bbdc630db4a9d9083b7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503515"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="0dccd-102">IMetaDataImport::GetTypeSpecFromToken Metodu</span><span class="sxs-lookup"><span data-stu-id="0dccd-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="0dccd-103">Belirtilen belirteçle temsil edilen tür belirtiminin ikili meta veri imzasını alır.</span><span class="sxs-lookup"><span data-stu-id="0dccd-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dccd-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0dccd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeSpecFromToken (
   [in]  mdTypeSpec            typespec,
   [out] PCCOR_SIGNATURE       *ppvSig,
   [out] ULONG                 *pcbSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0dccd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0dccd-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="0dccd-106">'ndaki İstenen meta veri imzasıyla ilişkili TypeSpec belirteci.</span><span class="sxs-lookup"><span data-stu-id="0dccd-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="0dccd-107">dışı İkili meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0dccd-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="0dccd-108">dışı Meta veri imzasının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="0dccd-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0dccd-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0dccd-109">Return Value</span></span>  
 <span data-ttu-id="0dccd-110">Başarılı veya başarısız olduğunu gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="0dccd-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="0dccd-111">Başarısızlıklar başarısız makroyla test edilebilir.</span><span class="sxs-lookup"><span data-stu-id="0dccd-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0dccd-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0dccd-112">Requirements</span></span>  
 <span data-ttu-id="0dccd-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0dccd-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0dccd-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0dccd-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0dccd-115">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="0dccd-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0dccd-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0dccd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dccd-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0dccd-117">See also</span></span>

- [<span data-ttu-id="0dccd-118">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0dccd-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="0dccd-119">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0dccd-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
