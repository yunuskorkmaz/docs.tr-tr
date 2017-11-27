---
title: IMetaDataImport2::GetMethodSpecProps Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.GetMethodSpecProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::GetMethodSpecProps
helpviewer_keywords:
- GetMethodSpecProps method [.NET Framework metadata]
- IMetaDataImport2::GetMethodSpecProps method [.NET Framework metadata]
ms.assetid: 9544b711-e669-4eaf-8630-ee862e5e4489
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b07e79f3990782e18ffdc57e9bd75a0b62765ba6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2getmethodspecprops-method"></a><span data-ttu-id="81dff-102">IMetaDataImport2::GetMethodSpecProps Metodu</span><span class="sxs-lookup"><span data-stu-id="81dff-102">IMetaDataImport2::GetMethodSpecProps Method</span></span>
<span data-ttu-id="81dff-103">Belirtilen MethodSpec tarafından başvurulan meta veri imzası belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="81dff-103">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81dff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="81dff-104">Syntax</span></span>  
  
```  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,   
   [out] ULONG            *pcbSigBlob  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="81dff-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="81dff-105">Parameters</span></span>  
 `mi`  
 <span data-ttu-id="81dff-106">[in] Örnek oluşturma yönteminin temsil eden bir MethodSpec belirteci.</span><span class="sxs-lookup"><span data-stu-id="81dff-106">[in] A MethodSpec token that represents the instantiation of the method.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="81dff-107">[out] Yöntem tanımını temsil eden MethodDef veya MethodRef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="81dff-107">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="81dff-108">[out] Yönteminin ikili meta verileri imza için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="81dff-108">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="81dff-109">[out] Bayt olarak boyutu, `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="81dff-109">[out] The size, in bytes, of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81dff-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="81dff-110">Requirements</span></span>  
 <span data-ttu-id="81dff-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81dff-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81dff-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="81dff-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="81dff-113">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="81dff-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="81dff-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81dff-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81dff-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="81dff-115">See Also</span></span>  
 [<span data-ttu-id="81dff-116">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="81dff-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="81dff-117">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="81dff-117">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
