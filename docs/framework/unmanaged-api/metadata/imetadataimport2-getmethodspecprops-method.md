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
ms.openlocfilehash: 6b5b3b3b5a3613668f4470f48083ae010cc9d336
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445246"
---
# <a name="imetadataimport2getmethodspecprops-method"></a><span data-ttu-id="cb5a8-102">IMetaDataImport2::GetMethodSpecProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb5a8-102">IMetaDataImport2::GetMethodSpecProps Method</span></span>
<span data-ttu-id="cb5a8-103">Belirtilen MethodSpec belirteci tarafından başvurulan metodun meta veri imzasını alır.</span><span class="sxs-lookup"><span data-stu-id="cb5a8-103">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb5a8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb5a8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,   
   [out] ULONG            *pcbSigBlob  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="cb5a8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cb5a8-105">Parameters</span></span>  
 `mi`  
 <span data-ttu-id="cb5a8-106">'ndaki Metodun örneklenmesini temsil eden bir MethodSpec belirteci.</span><span class="sxs-lookup"><span data-stu-id="cb5a8-106">[in] A MethodSpec token that represents the instantiation of the method.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="cb5a8-107">dışı Yöntem tanımını temsil eden MethodDef veya MethodRef belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cb5a8-107">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="cb5a8-108">dışı Metodun ikili meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cb5a8-108">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="cb5a8-109">dışı `ppvSigBlob`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="cb5a8-109">[out] The size, in bytes, of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb5a8-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb5a8-110">Requirements</span></span>  
 <span data-ttu-id="cb5a8-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb5a8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb5a8-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cb5a8-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cb5a8-113">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="cb5a8-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cb5a8-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb5a8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb5a8-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb5a8-115">See also</span></span>

- [<span data-ttu-id="cb5a8-116">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb5a8-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="cb5a8-117">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb5a8-117">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
