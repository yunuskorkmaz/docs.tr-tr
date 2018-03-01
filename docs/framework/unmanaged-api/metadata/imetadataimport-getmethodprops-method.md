---
title: IMetaDataImport::GetMethodProps Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.GetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodProps
helpviewer_keywords:
- GetMethodProps method [.NET Framework metadata]
- IMetaDataImport::GetMethodProps method [.NET Framework metadata]
ms.assetid: e0667ef7-1d31-4c89-a2d3-d426f023f8d2
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e4e0ae7dfed4b13ea83e16d6380443c9d1b72b06
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetmethodprops-method"></a><span data-ttu-id="feb27-102">IMetaDataImport::GetMethodProps Metodu</span><span class="sxs-lookup"><span data-stu-id="feb27-102">IMetaDataImport::GetMethodProps Method</span></span>
<span data-ttu-id="feb27-103">Belirtilen MethodDef tarafından başvurulan yöntemi ile ilişkili meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="feb27-103">Gets the metadata associated with the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="feb27-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="feb27-104">Syntax</span></span>  
  
```  
HRESULT GetMethodProps (  
    [in]  mdMethodDef         mb,  
    [out] mdTypeDef           *pClass,  
    [out] LPWSTR              szMethod,  
    [in]  ULONG               cchMethod,  
    [out] ULONG               *pchMethod,  
    [out] DWORD               *pdwAttr,  
    [out] PCCOR_SIGNATURE     *ppvSigBlob,  
    [out] ULONG               *pcbSigBlob,  
    [out] ULONG               *pulCodeRVA,  
    [out] DWORD               *pdwImplFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="feb27-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="feb27-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="feb27-106">[in] Meta verileri döndürmek için yöntemini temsil eden MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="feb27-106">[in] The MethodDef token that represents the method to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="feb27-107">[out] Bir işaretçi yöntemi uygulayan türünü temsil eden TypeDef belirteç.</span><span class="sxs-lookup"><span data-stu-id="feb27-107">[out] A Pointer to a TypeDef token that represents the type that implements the method.</span></span>  
  
 `szMethod`  
 <span data-ttu-id="feb27-108">[out] Yöntemin ada sahip bir arabellek için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="feb27-108">[out] A Pointer to a buffer that has the method's name.</span></span>  
  
 `cchMethod`  
 <span data-ttu-id="feb27-109">[in] İstenen boyutu `szMethod`.</span><span class="sxs-lookup"><span data-stu-id="feb27-109">[in] The requested size of `szMethod`.</span></span>  
  
 `pchMethod`  
 <span data-ttu-id="feb27-110">[out] Geniş karakter cinsinden boyutu gösteren bir işaretçi `szMethod`, veya kesme, yöntem adı geniş karakter gerçek sayısını söz konusu olduğunda.</span><span class="sxs-lookup"><span data-stu-id="feb27-110">[out] A Pointer to the size in wide characters of `szMethod`, or in the case of truncation, the actual number of wide characters in the method name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="feb27-111">[out] Yöntemiyle ilişkili herhangi bir bayrağı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="feb27-111">[out] A pointer to any flags associated with the method.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="feb27-112">[out] Yönteminin ikili meta verileri imza için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="feb27-112">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="feb27-113">[out] Bayt cinsinden boyutu gösteren bir işaretçi `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="feb27-113">[out] A Pointer to the size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="feb27-114">[out] Göreli sanal adres yönteminin bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="feb27-114">[out] A pointer to the relative virtual address of the method.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="feb27-115">[out] Herhangi bir uygulama bayrağı yöntemi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="feb27-115">[out] A pointer to any implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="feb27-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="feb27-116">Requirements</span></span>  
 <span data-ttu-id="feb27-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="feb27-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="feb27-118">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="feb27-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="feb27-119">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="feb27-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="feb27-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="feb27-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feb27-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="feb27-121">See Also</span></span>  
 [<span data-ttu-id="feb27-122">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="feb27-122">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="feb27-123">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="feb27-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
