---
title: IMetaDataImport::GetPropertyProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPropertyProps
helpviewer_keywords:
- GetPropertyProps method [.NET Framework metadata]
- IMetaDataImport::GetPropertyProps method [.NET Framework metadata]
ms.assetid: dc0ff3e6-7e7d-4f6c-948d-52b28f5cb78c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a08bd5beeb9fab1cd5b703c3afc4e82aaf71dbbc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122609"
---
# <a name="imetadataimportgetpropertyprops-method"></a><span data-ttu-id="0882e-102">IMetaDataImport::GetPropertyProps Metodu</span><span class="sxs-lookup"><span data-stu-id="0882e-102">IMetaDataImport::GetPropertyProps Method</span></span>
<span data-ttu-id="0882e-103">Belirtilen belirteç tarafından temsil edilen bir özellik için meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="0882e-103">Gets the metadata for the property represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0882e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0882e-104">Syntax</span></span>  
  
```  
HRESULT GetPropertyProps (  
   [in]  mdProperty        prop,  
   [out] mdTypeDef         *pClass,   
   [out] LPCWSTR           szProperty,   
   [in]  ULONG             cchProperty,   
   [out] ULONG             *pchProperty,   
   [out] DWORD             *pdwPropFlags,   
   [out] PCCOR_SIGNATURE   *ppvSig,   
   [out] ULONG             *pbSig,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppDefaultValue,  
   [out] ULONG             *pcchDefaultValue,  
   [out] mdMethodDef       *pmdSetter,   
   [out] mdMethodDef       *pmdGetter,   
   [out] mdMethodDef       rmdOtherMethod[],  
   [in]  ULONG             cMax,   
   [out] ULONG             *pcOtherMethod   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0882e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0882e-105">Parameters</span></span>  
 `prop`  
 <span data-ttu-id="0882e-106">[in] Özellik için meta verileri döndürmek için temsil eden bir belirteci.</span><span class="sxs-lookup"><span data-stu-id="0882e-106">[in] A token that represents the property to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="0882e-107">[out] Özelliği uygulayan türü temsil eden TypeDef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0882e-107">[out] A pointer to the TypeDef token that represents the type that implements the property.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="0882e-108">[out] Özellik adını tutan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="0882e-108">[out] A buffer to hold the property name.</span></span>  
  
 `cchProperty`  
 <span data-ttu-id="0882e-109">[in] Geniş karakter cinsinden boyutu `szProperty`.</span><span class="sxs-lookup"><span data-stu-id="0882e-109">[in] The size in wide characters of `szProperty`.</span></span>  
  
 `pchProperty`  
 <span data-ttu-id="0882e-110">[out] Döndürülen geniş karakter sayısını `szProperty`.</span><span class="sxs-lookup"><span data-stu-id="0882e-110">[out] The number of wide characters returned in `szProperty`.</span></span>  
  
 `pdwPropFlags`  
 <span data-ttu-id="0882e-111">[out] Özelliğine uygulanan herhangi bir öznitelik bayrakları için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0882e-111">[out] A pointer to any attribute flags applied to the property.</span></span> <span data-ttu-id="0882e-112">Gelen bir bit maskesi değerdir [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="0882e-112">This value is a bitmask from the [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) enumeration.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="0882e-113">[out] Özelliğin meta veri imzası bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0882e-113">[out] A pointer to the metadata signature of the property.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="0882e-114">[out] Döndürülen bayt sayısı `ppvSig`.</span><span class="sxs-lookup"><span data-stu-id="0882e-114">[out] The number of bytes returned in `ppvSig`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="0882e-115">[out] Özelliğin varsayılan değeri sabiti türünü belirten bir bayrak.</span><span class="sxs-lookup"><span data-stu-id="0882e-115">[out] A flag specifying the type of the constant that is the default value of the property.</span></span> <span data-ttu-id="0882e-116">CorElementType numaralandırması değerdir.</span><span class="sxs-lookup"><span data-stu-id="0882e-116">This value is from the CorElementType enumeration.</span></span>  
  
 `ppDefaultValue`  
 <span data-ttu-id="0882e-117">[out] Bu özellik için varsayılan değeri depolamak bayt için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0882e-117">[out] A pointer to the bytes that store the default value for this property.</span></span>  
  
 `pcchDefaultValue`  
 <span data-ttu-id="0882e-118">[out] Geniş karakter cinsinden boyutu `ppDefaultValue`, `pdwCPlusTypeFlag` olduğu ELEMENT_TYPE_STRING; Aksi takdirde, bu değeri uygun değil.</span><span class="sxs-lookup"><span data-stu-id="0882e-118">[out] The size in wide characters of `ppDefaultValue`, if `pdwCPlusTypeFlag` is ELEMENT_TYPE_STRING; otherwise, this value is not relevant.</span></span> <span data-ttu-id="0882e-119">Bu durumda, uzunluğunu `ppDefaultValue` tarafından belirtilen türden çıkarılan `pdwCPlusTypeFlag`.</span><span class="sxs-lookup"><span data-stu-id="0882e-119">In that case, the length of `ppDefaultValue` is inferred from the type that is specified by `pdwCPlusTypeFlag`.</span></span>  
  
 `pmdSetter`  
 <span data-ttu-id="0882e-120">[out] Özelliği için set erişimcisi yöntemi temsil eden MethodDef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0882e-120">[out] A pointer to the MethodDef token that represents the set accessor method for the property.</span></span>  
  
 `pmdGetter`  
 <span data-ttu-id="0882e-121">[out] Özellik get erişimci yöntemi temsil eden MethodDef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0882e-121">[out] A pointer to the MethodDef token that represents the get accessor method for the property.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="0882e-122">[out] Özellikle ilişkili diğer yöntemleri temsil eden MethodDef belirteçleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="0882e-122">[out] An array of MethodDef tokens that represent other methods associated with the property.</span></span>  
  
 `cMax`  
 <span data-ttu-id="0882e-123">[in] En büyük boyutunu `rmdOtherMethod` dizisi.</span><span class="sxs-lookup"><span data-stu-id="0882e-123">[in] The maximum size of the `rmdOtherMethod` array.</span></span> <span data-ttu-id="0882e-124">Tüm yöntemleri tutabilecek kadar büyük bir dizi belirtmezseniz, bunlar uyarı vermeden atlanır.</span><span class="sxs-lookup"><span data-stu-id="0882e-124">If you do not provide an array large enough to hold all the methods, they are skipped without warning.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="0882e-125">[out] Döndürülen MethodDef belirteçleri sayısı `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="0882e-125">[out] The number of MethodDef tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0882e-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0882e-126">Requirements</span></span>  
 <span data-ttu-id="0882e-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0882e-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0882e-128">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="0882e-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0882e-129">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="0882e-129">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="0882e-130">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="0882e-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0882e-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0882e-131">See also</span></span>

- [<span data-ttu-id="0882e-132">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0882e-132">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="0882e-133">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0882e-133">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
