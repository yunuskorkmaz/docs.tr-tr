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
ms.openlocfilehash: 3ab24ab869e1f2cff9beafe50e6982ba2e7cf0aa
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436698"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="baa1c-102">IMetaDataImport::GetTypeSpecFromToken Metodu</span><span class="sxs-lookup"><span data-stu-id="baa1c-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="baa1c-103">Gets the binary metadata signature of the type specification represented by the specified token.</span><span class="sxs-lookup"><span data-stu-id="baa1c-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baa1c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="baa1c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeSpecFromToken (   
   [in]  mdTypeSpec            typespec,   
   [out] PCCOR_SIGNATURE       *ppvSig,   
   [out] ULONG                 *pcbSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="baa1c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="baa1c-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="baa1c-106">[in] The TypeSpec token associated with the requested metadata signature.</span><span class="sxs-lookup"><span data-stu-id="baa1c-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="baa1c-107">[out] A pointer to the binary metadata signature.</span><span class="sxs-lookup"><span data-stu-id="baa1c-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="baa1c-108">[out] The size, in bytes, of the metadata signature.</span><span class="sxs-lookup"><span data-stu-id="baa1c-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="baa1c-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="baa1c-109">Return Value</span></span>  
 <span data-ttu-id="baa1c-110">An HRESULT that indicates success or failure.</span><span class="sxs-lookup"><span data-stu-id="baa1c-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="baa1c-111">Failures can be tested with the FAILED macro.</span><span class="sxs-lookup"><span data-stu-id="baa1c-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="baa1c-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="baa1c-112">Requirements</span></span>  
 <span data-ttu-id="baa1c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="baa1c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="baa1c-114">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="baa1c-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="baa1c-115">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="baa1c-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="baa1c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="baa1c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baa1c-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="baa1c-117">See also</span></span>

- [<span data-ttu-id="baa1c-118">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="baa1c-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="baa1c-119">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="baa1c-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
