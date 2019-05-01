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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c35212e7d261a5b385823fdaa345f6fbd638571c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959593"
---
# <a name="imetadataimport2getmethodspecprops-method"></a><span data-ttu-id="ead03-102">IMetaDataImport2::GetMethodSpecProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ead03-102">IMetaDataImport2::GetMethodSpecProps Method</span></span>
<span data-ttu-id="ead03-103">Belirtilen MethodSpec tarafından başvurulan meta veri imzası belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="ead03-103">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ead03-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ead03-104">Syntax</span></span>  
  
```  
HRESULT GetMethodSpecProps (  
   [in]  mdMethodSpec     mi,  
   [out] mdToken          *tkParent,  
   [out] PCCOR_SIGNATURE  *ppvSigBlob,   
   [out] ULONG            *pcbSigBlob  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="ead03-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ead03-105">Parameters</span></span>  
 `mi`  
 <span data-ttu-id="ead03-106">[in] Örnekleme yönteminin temsil eden bir MethodSpec Neobsahuje belirteci.</span><span class="sxs-lookup"><span data-stu-id="ead03-106">[in] A MethodSpec token that represents the instantiation of the method.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="ead03-107">[out] Yöntem tanımını temsil eden MethodDef veya MethodRef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ead03-107">[out] A pointer to the MethodDef or MethodRef token that represents the method definition.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="ead03-108">[out] İkili meta veri imzası yöntem bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ead03-108">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="ead03-109">[out] Bayt cinsinden boyutu, `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="ead03-109">[out] The size, in bytes, of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ead03-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ead03-110">Requirements</span></span>  
 <span data-ttu-id="ead03-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ead03-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ead03-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="ead03-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ead03-113">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="ead03-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ead03-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ead03-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ead03-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ead03-115">See also</span></span>

- [<span data-ttu-id="ead03-116">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ead03-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="ead03-117">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ead03-117">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
