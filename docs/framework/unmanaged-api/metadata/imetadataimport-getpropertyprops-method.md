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
ms.openlocfilehash: 5fc71bf240b89afadbf8f2ba10906322921bdda2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175336"
---
# <a name="imetadataimportgetpropertyprops-method"></a><span data-ttu-id="4ada3-102">IMetaDataImport::GetPropertyProps Metodu</span><span class="sxs-lookup"><span data-stu-id="4ada3-102">IMetaDataImport::GetPropertyProps Method</span></span>
<span data-ttu-id="4ada3-103">Belirtilen belirteç tarafından temsil edilen özelliğin meta verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="4ada3-103">Gets the metadata for the property represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ada3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ada3-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="4ada3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4ada3-105">Parameters</span></span>  
 `prop`  
 <span data-ttu-id="4ada3-106">[içinde] Meta verileri döndürecek özelliği temsil eden bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="4ada3-106">[in] A token that represents the property to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="4ada3-107">[çıkış] Özelliği uygulayan türü temsil eden TypeDef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4ada3-107">[out] A pointer to the TypeDef token that represents the type that implements the property.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="4ada3-108">[çıkış] Özellik adını tutmak için bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="4ada3-108">[out] A buffer to hold the property name.</span></span>  
  
 `cchProperty`  
 <span data-ttu-id="4ada3-109">[içinde] Geniş karakterler boyutu `szProperty`.</span><span class="sxs-lookup"><span data-stu-id="4ada3-109">[in] The size in wide characters of `szProperty`.</span></span>  
  
 `pchProperty`  
 <span data-ttu-id="4ada3-110">[çıkış] Döndürülen geniş karakter `szProperty`sayısı.</span><span class="sxs-lookup"><span data-stu-id="4ada3-110">[out] The number of wide characters returned in `szProperty`.</span></span>  
  
 `pdwPropFlags`  
 <span data-ttu-id="4ada3-111">[çıkış] Özelliğe uygulanan herhangi bir öznitelik bayrakları için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4ada3-111">[out] A pointer to any attribute flags applied to the property.</span></span> <span data-ttu-id="4ada3-112">Bu değer [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) numaralandırmabir bitmask olduğunu.</span><span class="sxs-lookup"><span data-stu-id="4ada3-112">This value is a bitmask from the [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) enumeration.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="4ada3-113">[çıkış] Özelliğin meta veri imzasına işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4ada3-113">[out] A pointer to the metadata signature of the property.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="4ada3-114">[çıkış] Döndürülen bayt `ppvSig`sayısı.</span><span class="sxs-lookup"><span data-stu-id="4ada3-114">[out] The number of bytes returned in `ppvSig`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="4ada3-115">[çıkış] Özelliğin varsayılan değeri olan sabit türünü belirten bir bayrak.</span><span class="sxs-lookup"><span data-stu-id="4ada3-115">[out] A flag specifying the type of the constant that is the default value of the property.</span></span> <span data-ttu-id="4ada3-116">Bu değer CorElementType numaralandırmasından dır.</span><span class="sxs-lookup"><span data-stu-id="4ada3-116">This value is from the CorElementType enumeration.</span></span>  
  
 `ppDefaultValue`  
 <span data-ttu-id="4ada3-117">[çıkış] Bu özellik için varsayılan değeri depolayan baytlar için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4ada3-117">[out] A pointer to the bytes that store the default value for this property.</span></span>  
  
 `pcchDefaultValue`  
 <span data-ttu-id="4ada3-118">[çıkış] Geniş karakterlerdeki boyut `ppDefaultValue`, `pdwCPlusTypeFlag` ELEMENT_TYPE_STRING ise; aksi takdirde, bu değer ilgili değildir.</span><span class="sxs-lookup"><span data-stu-id="4ada3-118">[out] The size in wide characters of `ppDefaultValue`, if `pdwCPlusTypeFlag` is ELEMENT_TYPE_STRING; otherwise, this value is not relevant.</span></span> <span data-ttu-id="4ada3-119">Bu durumda, uzunluk `ppDefaultValue` tarafından belirtilen türden `pdwCPlusTypeFlag`çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="4ada3-119">In that case, the length of `ppDefaultValue` is inferred from the type that is specified by `pdwCPlusTypeFlag`.</span></span>  
  
 `pmdSetter`  
 <span data-ttu-id="4ada3-120">[çıkış] Özelliğin ayarlanan erişimci yöntemini temsil eden MethodDef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4ada3-120">[out] A pointer to the MethodDef token that represents the set accessor method for the property.</span></span>  
  
 `pmdGetter`  
 <span data-ttu-id="4ada3-121">[çıkış] Özelliğin erişime alma yöntemini temsil eden MethodDef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4ada3-121">[out] A pointer to the MethodDef token that represents the get accessor method for the property.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="4ada3-122">[çıkış] Özellik ile ilişkili diğer yöntemleri temsil eden MethodDef belirteçleri bir dizi.</span><span class="sxs-lookup"><span data-stu-id="4ada3-122">[out] An array of MethodDef tokens that represent other methods associated with the property.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4ada3-123">[içinde] `rmdOtherMethod` Dizinin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="4ada3-123">[in] The maximum size of the `rmdOtherMethod` array.</span></span> <span data-ttu-id="4ada3-124">Tüm yöntemleri tutabilecek kadar büyük bir dizi sağlamazsanız, bunlar uyarı yapılmadan atlanır.</span><span class="sxs-lookup"><span data-stu-id="4ada3-124">If you do not provide an array large enough to hold all the methods, they are skipped without warning.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="4ada3-125">[çıkış] MethodDef belirteçlerinin sayısı `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="4ada3-125">[out] The number of MethodDef tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ada3-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4ada3-126">Requirements</span></span>  
 <span data-ttu-id="4ada3-127">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ada3-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ada3-128">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4ada3-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4ada3-129">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="4ada3-129">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4ada3-130">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ada3-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ada3-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ada3-131">See also</span></span>

- [<span data-ttu-id="4ada3-132">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4ada3-132">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="4ada3-133">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4ada3-133">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
