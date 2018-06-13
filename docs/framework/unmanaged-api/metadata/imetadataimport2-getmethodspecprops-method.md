---
title: IMetaDataImport2::GetMethodSpecProps Metodu
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3249ad76c428752c91540e135bc978d3fe835de1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448139"
---
# <a name="imetadataimport2getmethodspecprops-method"></a><span data-ttu-id="9503c-102">IMetaDataImport2::GetMethodSpecProps Metodu</span><span class="sxs-lookup"><span data-stu-id="9503c-102">IMetaDataImport2::GetMethodSpecProps Method</span></span>
<span data-ttu-id="9503c-103">Belirtilen MethodSpec tarafından başvurulan meta veri imzası belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="9503c-103">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9503c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9503c-104">Syntax</span></span>  
  
```  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,   
   [out] ULONG            *pcbSigBlob  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="9503c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9503c-105">Parameters</span></span>  
 `mi`  
 <span data-ttu-id="9503c-106">[in] Örnek oluşturma yönteminin temsil eden bir MethodSpec belirteci.</span><span class="sxs-lookup"><span data-stu-id="9503c-106">[in] A MethodSpec token that represents the instantiation of the method.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="9503c-107">[out] Yöntem tanımını temsil eden MethodDef veya MethodRef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9503c-107">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="9503c-108">[out] Yönteminin ikili meta verileri imza için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9503c-108">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="9503c-109">[out] Bayt olarak boyutu, `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="9503c-109">[out] The size, in bytes, of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9503c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9503c-110">Requirements</span></span>  
 <span data-ttu-id="9503c-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9503c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9503c-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9503c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9503c-113">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="9503c-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9503c-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9503c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9503c-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9503c-115">See Also</span></span>  
 [<span data-ttu-id="9503c-116">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9503c-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="9503c-117">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9503c-117">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
