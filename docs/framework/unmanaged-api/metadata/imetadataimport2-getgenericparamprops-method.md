---
title: IMetaDataImport2::GetGenericParamProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamProps method [.NET Framework metadata]
- GetGenericParamProps method [.NET Framework metadata]
ms.assetid: dbb21e67-712b-49e7-a27c-a1e73ffd46c5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9ded6b4e0ac8f3e70fd0145ab6e2410c3b38e02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448680"
---
# <a name="imetadataimport2getgenericparamprops-method"></a><span data-ttu-id="11287-102">IMetaDataImport2::GetGenericParamProps Metodu</span><span class="sxs-lookup"><span data-stu-id="11287-102">IMetaDataImport2::GetGenericParamProps Method</span></span>
<span data-ttu-id="11287-103">Belirtilen belirteç tarafından temsil edilen genel parametresi ile ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="11287-103">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11287-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="11287-104">Syntax</span></span>  
  
```  
HRESULT GetGenericParamProps (  
   [in]  mdGenericParam  gp,  
   [out] ULONG           *pulParamSeq,  
   [out] DWORD           *pdwParamFlags,  
   [out] mdToken         *ptOwner,  
   [out] DWORD           *reserved,  
   [out] LPWSTR          wzName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="11287-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="11287-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="11287-106">[in] Meta verileri döndürmek üzere genel parametresini temsil eden belirteci.</span><span class="sxs-lookup"><span data-stu-id="11287-106">[in] The token that represents the generic parameter for which to return metadata.</span></span>  
  
 `pulParamSeq`  
 <span data-ttu-id="11287-107">[out] Sıralı konumunu `Type` üst Oluşturucusu veya yöntem parametresinde.</span><span class="sxs-lookup"><span data-stu-id="11287-107">[out] The ordinal position of the `Type` parameter in the parent constructor or method.</span></span>  
  
 `pdwParamFlags`  
 <span data-ttu-id="11287-108">[out] Değerini [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) açıklar numaralandırma `Type` genel parametresi için.</span><span class="sxs-lookup"><span data-stu-id="11287-108">[out] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the `Type` for the generic parameter.</span></span>  
  
 `ptOwner`  
 <span data-ttu-id="11287-109">[out] Parametre sahibi temsil eden bir TypeDef veya MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="11287-109">[out] A TypeDef or MethodDef token that represents the owner of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="11287-110">[out] Gelecekteki genişletilebilirliği için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="11287-110">[out] Reserved for future extensibility.</span></span>  
  
 `wzName`  
 <span data-ttu-id="11287-111">[out] Genel parametre adı.</span><span class="sxs-lookup"><span data-stu-id="11287-111">[out] The name of the generic parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="11287-112">[in] Boyutunu `wzName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="11287-112">[in] The size of the `wzName` buffer.</span></span>  
  
 `pchName`  
 <span data-ttu-id="11287-113">[out] Geniş karakterler adı döndürülen boyutu.</span><span class="sxs-lookup"><span data-stu-id="11287-113">[out] The returned size of the name, in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11287-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="11287-114">Requirements</span></span>  
 <span data-ttu-id="11287-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11287-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11287-116">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="11287-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="11287-117">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="11287-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="11287-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11287-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11287-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="11287-119">See Also</span></span>  
 [<span data-ttu-id="11287-120">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="11287-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="11287-121">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="11287-121">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
