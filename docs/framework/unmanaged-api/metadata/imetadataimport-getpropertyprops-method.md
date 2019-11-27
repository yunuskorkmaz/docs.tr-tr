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
ms.openlocfilehash: 247a2793bf3806f5ee38585d50b4535820dfcb69
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437064"
---
# <a name="imetadataimportgetpropertyprops-method"></a><span data-ttu-id="e2738-102">IMetaDataImport::GetPropertyProps Metodu</span><span class="sxs-lookup"><span data-stu-id="e2738-102">IMetaDataImport::GetPropertyProps Method</span></span>
<span data-ttu-id="e2738-103">Belirtilen belirteç tarafından temsil edilen özelliğin meta verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="e2738-103">Gets the metadata for the property represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2738-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2738-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="e2738-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e2738-105">Parameters</span></span>  
 `prop`  
 <span data-ttu-id="e2738-106">'ndaki Meta verilerini döndürecek özelliği temsil eden bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="e2738-106">[in] A token that represents the property to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="e2738-107">dışı Özelliği uygulayan türü temsil eden TypeDef belirtecinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e2738-107">[out] A pointer to the TypeDef token that represents the type that implements the property.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="e2738-108">dışı Özellik adını tutan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="e2738-108">[out] A buffer to hold the property name.</span></span>  
  
 `cchProperty`  
 <span data-ttu-id="e2738-109">'ndaki `szProperty`geniş karakterdeki boyut.</span><span class="sxs-lookup"><span data-stu-id="e2738-109">[in] The size in wide characters of `szProperty`.</span></span>  
  
 `pchProperty`  
 <span data-ttu-id="e2738-110">dışı `szProperty`' de döndürülen geniş karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="e2738-110">[out] The number of wide characters returned in `szProperty`.</span></span>  
  
 `pdwPropFlags`  
 <span data-ttu-id="e2738-111">dışı Özelliğe uygulanan öznitelik bayraklarının bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e2738-111">[out] A pointer to any attribute flags applied to the property.</span></span> <span data-ttu-id="e2738-112">Bu değer [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) numaralandırmasından bir bit dır.</span><span class="sxs-lookup"><span data-stu-id="e2738-112">This value is a bitmask from the [CorPropertyAttr](../../../../docs/framework/unmanaged-api/metadata/corpropertyattr-enumeration.md) enumeration.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="e2738-113">dışı Özelliğin meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e2738-113">[out] A pointer to the metadata signature of the property.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="e2738-114">dışı `ppvSig`döndürülen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="e2738-114">[out] The number of bytes returned in `ppvSig`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="e2738-115">dışı Özelliğin varsayılan değeri olan sabitin türünü belirten bayrak.</span><span class="sxs-lookup"><span data-stu-id="e2738-115">[out] A flag specifying the type of the constant that is the default value of the property.</span></span> <span data-ttu-id="e2738-116">Bu değer CorElementType numaralandırmasından.</span><span class="sxs-lookup"><span data-stu-id="e2738-116">This value is from the CorElementType enumeration.</span></span>  
  
 `ppDefaultValue`  
 <span data-ttu-id="e2738-117">dışı Bu özellik için varsayılan değeri depolayan bayta yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e2738-117">[out] A pointer to the bytes that store the default value for this property.</span></span>  
  
 `pcchDefaultValue`  
 <span data-ttu-id="e2738-118">dışı `pdwCPlusTypeFlag` ELEMENT_TYPE_STRING `ppDefaultValue`geniş karakterdeki boyut. Aksi takdirde, bu değer ilgili değildir.</span><span class="sxs-lookup"><span data-stu-id="e2738-118">[out] The size in wide characters of `ppDefaultValue`, if `pdwCPlusTypeFlag` is ELEMENT_TYPE_STRING; otherwise, this value is not relevant.</span></span> <span data-ttu-id="e2738-119">Bu durumda, `ppDefaultValue` uzunluğu `pdwCPlusTypeFlag`tarafından belirtilen türden algılanır.</span><span class="sxs-lookup"><span data-stu-id="e2738-119">In that case, the length of `ppDefaultValue` is inferred from the type that is specified by `pdwCPlusTypeFlag`.</span></span>  
  
 `pmdSetter`  
 <span data-ttu-id="e2738-120">dışı Özelliği için set erişimcisi metodunu temsil eden MethodDef belirtecinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e2738-120">[out] A pointer to the MethodDef token that represents the set accessor method for the property.</span></span>  
  
 `pmdGetter`  
 <span data-ttu-id="e2738-121">dışı Özelliği için get erişimcisi metodunu temsil eden MethodDef belirtecinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e2738-121">[out] A pointer to the MethodDef token that represents the get accessor method for the property.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="e2738-122">dışı Özelliği ile ilişkili diğer yöntemleri temsil eden bir MethodDef belirteçleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="e2738-122">[out] An array of MethodDef tokens that represent other methods associated with the property.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e2738-123">'ndaki `rmdOtherMethod` dizisinin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="e2738-123">[in] The maximum size of the `rmdOtherMethod` array.</span></span> <span data-ttu-id="e2738-124">Tüm yöntemleri tutacak büyüklükte bir dizi sağlamazsanız, bunlar uyarı vermeden atlanır.</span><span class="sxs-lookup"><span data-stu-id="e2738-124">If you do not provide an array large enough to hold all the methods, they are skipped without warning.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="e2738-125">dışı `rmdOtherMethod`döndürülen MethodDef belirteçleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="e2738-125">[out] The number of MethodDef tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2738-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2738-126">Requirements</span></span>  
 <span data-ttu-id="e2738-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2738-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2738-128">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e2738-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e2738-129">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="e2738-129">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e2738-130">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2738-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2738-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2738-131">See also</span></span>

- [<span data-ttu-id="e2738-132">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2738-132">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="e2738-133">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2738-133">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
