---
title: IMetaDataImport2::GetMethodSpecProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetMethodSpecProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetMethodSpecProps
helpviewer_keywords:
- GetMethodSpecProps method [.NET Framework metadata]
- IMetaDataImport2::GetMethodSpecProps method [.NET Framework metadata]
ms.assetid: 9544b711-e669-4eaf-8630-ee862e5e4489
topic_type:
- apiref
ms.openlocfilehash: 0bfbfec930c193ea05a01bd5bd9f46d2ec6714b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175297"
---
# <a name="imetadataimport2getmethodspecprops-method"></a><span data-ttu-id="22b40-102">IMetaDataImport2::GetMethodSpecProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="22b40-102">IMetaDataImport2::GetMethodSpecProps Method</span></span>
<span data-ttu-id="22b40-103">Belirtilen MethodSpec belirteci tarafından başvurulan yöntemin meta veri imzasını alır.</span><span class="sxs-lookup"><span data-stu-id="22b40-103">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22b40-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="22b40-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,
   [out] ULONG            *pcbSigBlob  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="22b40-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="22b40-105">Parameters</span></span>  
 `mi`  
 <span data-ttu-id="22b40-106">[içinde] Yöntemin anlık durumunu temsil eden bir MethodSpec belirteci.</span><span class="sxs-lookup"><span data-stu-id="22b40-106">[in] A MethodSpec token that represents the instantiation of the method.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="22b40-107">[çıkış] Yöntem tanımını temsil eden MethodDef veya MethodRef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="22b40-107">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="22b40-108">[çıkış] Yöntemin ikili meta veri imzasına işaretçi.</span><span class="sxs-lookup"><span data-stu-id="22b40-108">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="22b40-109">[çıkış] Boyutu, bayt, ve. `ppvSigBlob`</span><span class="sxs-lookup"><span data-stu-id="22b40-109">[out] The size, in bytes, of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22b40-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="22b40-110">Requirements</span></span>  
 <span data-ttu-id="22b40-111">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22b40-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22b40-112">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="22b40-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="22b40-113">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="22b40-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="22b40-114">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22b40-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22b40-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22b40-115">See also</span></span>

- [<span data-ttu-id="22b40-116">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="22b40-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="22b40-117">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="22b40-117">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
