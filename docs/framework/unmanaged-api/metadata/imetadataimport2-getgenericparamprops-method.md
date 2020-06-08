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
ms.openlocfilehash: 7e97b2d4ad1fec4675d1484959b115a4d4b87e90
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490620"
---
# <a name="imetadataimport2getgenericparamprops-method"></a><span data-ttu-id="f9f4e-102">IMetaDataImport2::GetGenericParamProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f9f4e-102">IMetaDataImport2::GetGenericParamProps Method</span></span>
<span data-ttu-id="f9f4e-103">Belirtilen belirteç tarafından temsil edilen genel parametreyle ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="f9f4e-103">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9f4e-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f9f4e-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f9f4e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f9f4e-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="f9f4e-106">'ndaki Meta veri döndürülecek genel parametresini temsil eden belirteç.</span><span class="sxs-lookup"><span data-stu-id="f9f4e-106">[in] The token that represents the generic parameter for which to return metadata.</span></span>  
  
 `pulParamSeq`  
 <span data-ttu-id="f9f4e-107">dışı `Type`Parametrenin üst Oluşturucu veya yöntemdeki sıra konumu.</span><span class="sxs-lookup"><span data-stu-id="f9f4e-107">[out] The ordinal position of the `Type` parameter in the parent constructor or method.</span></span>  
  
 `pdwParamFlags`  
 <span data-ttu-id="f9f4e-108">dışı Genel parametresi için tanımlayan [CorGenericParamAttr](corgenericparamattr-enumeration.md) numaralandırması değeri `Type` .</span><span class="sxs-lookup"><span data-stu-id="f9f4e-108">[out] A value of the [CorGenericParamAttr](corgenericparamattr-enumeration.md) enumeration that describes the `Type` for the generic parameter.</span></span>  
  
 `ptOwner`  
 <span data-ttu-id="f9f4e-109">dışı Parametrenin sahibini temsil eden bir TypeDef veya MethodDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="f9f4e-109">[out] A TypeDef or MethodDef token that represents the owner of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="f9f4e-110">dışı Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="f9f4e-110">[out] Reserved for future extensibility.</span></span>  
  
 `wzName`  
 <span data-ttu-id="f9f4e-111">dışı Genel parametrenin adı.</span><span class="sxs-lookup"><span data-stu-id="f9f4e-111">[out] The name of the generic parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="f9f4e-112">'ndaki `wzName`Arabelleğin boyutu.</span><span class="sxs-lookup"><span data-stu-id="f9f4e-112">[in] The size of the `wzName` buffer.</span></span>  
  
 `pchName`  
 <span data-ttu-id="f9f4e-113">dışı Adın, geniş karakter olarak döndürülen boyutu.</span><span class="sxs-lookup"><span data-stu-id="f9f4e-113">[out] The returned size of the name, in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9f4e-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9f4e-114">Requirements</span></span>  
 <span data-ttu-id="f9f4e-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9f4e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9f4e-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f9f4e-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f9f4e-117">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="f9f4e-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f9f4e-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9f4e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9f4e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9f4e-119">See also</span></span>

- [<span data-ttu-id="f9f4e-120">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f9f4e-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="f9f4e-121">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f9f4e-121">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
