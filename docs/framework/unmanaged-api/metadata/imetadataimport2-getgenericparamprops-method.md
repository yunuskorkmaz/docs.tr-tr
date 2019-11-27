---
title: IMetaDataImport2::GetGenericParamProps Yöntemi
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
ms.openlocfilehash: a8c5dd263401002deaee3d21f1e41b41a29faec2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427302"
---
# <a name="imetadataimport2getgenericparamprops-method"></a><span data-ttu-id="d3a5a-102">IMetaDataImport2::GetGenericParamProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3a5a-102">IMetaDataImport2::GetGenericParamProps Method</span></span>
<span data-ttu-id="d3a5a-103">Belirtilen belirteç tarafından temsil edilen genel parametreyle ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="d3a5a-103">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3a5a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3a5a-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="d3a5a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d3a5a-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="d3a5a-106">'ndaki Meta veri döndürülecek genel parametresini temsil eden belirteç.</span><span class="sxs-lookup"><span data-stu-id="d3a5a-106">[in] The token that represents the generic parameter for which to return metadata.</span></span>  
  
 `pulParamSeq`  
 <span data-ttu-id="d3a5a-107">dışı Üst Oluşturucu veya yöntemde `Type` parametresinin sıra konumu.</span><span class="sxs-lookup"><span data-stu-id="d3a5a-107">[out] The ordinal position of the `Type` parameter in the parent constructor or method.</span></span>  
  
 `pdwParamFlags`  
 <span data-ttu-id="d3a5a-108">dışı Genel parametre için `Type` tanımlayan [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="d3a5a-108">[out] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the `Type` for the generic parameter.</span></span>  
  
 `ptOwner`  
 <span data-ttu-id="d3a5a-109">dışı Parametrenin sahibini temsil eden bir TypeDef veya MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="d3a5a-109">[out] A TypeDef or MethodDef token that represents the owner of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="d3a5a-110">dışı Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="d3a5a-110">[out] Reserved for future extensibility.</span></span>  
  
 `wzName`  
 <span data-ttu-id="d3a5a-111">dışı Genel parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="d3a5a-111">[out] The name of the generic parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="d3a5a-112">'ndaki `wzName` arabelleğinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="d3a5a-112">[in] The size of the `wzName` buffer.</span></span>  
  
 `pchName`  
 <span data-ttu-id="d3a5a-113">dışı Adın, geniş karakter olarak döndürülen boyutu.</span><span class="sxs-lookup"><span data-stu-id="d3a5a-113">[out] The returned size of the name, in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3a5a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3a5a-114">Requirements</span></span>  
 <span data-ttu-id="d3a5a-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3a5a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3a5a-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d3a5a-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d3a5a-117">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="d3a5a-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d3a5a-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3a5a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3a5a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3a5a-119">See also</span></span>

- [<span data-ttu-id="d3a5a-120">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d3a5a-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="d3a5a-121">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d3a5a-121">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
