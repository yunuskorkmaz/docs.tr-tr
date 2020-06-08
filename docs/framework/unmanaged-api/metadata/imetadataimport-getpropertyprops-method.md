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
ms.openlocfilehash: cac5aaa7ed13b6a48b36ad550da8b73d0deb2ee7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491049"
---
# <a name="imetadataimportgetpropertyprops-method"></a><span data-ttu-id="1603d-102">IMetaDataImport::GetPropertyProps Metodu</span><span class="sxs-lookup"><span data-stu-id="1603d-102">IMetaDataImport::GetPropertyProps Method</span></span>
<span data-ttu-id="1603d-103">Belirtilen belirteç tarafından temsil edilen özelliğin meta verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="1603d-103">Gets the metadata for the property represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1603d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1603d-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1603d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1603d-105">Parameters</span></span>  
 `prop`  
 <span data-ttu-id="1603d-106">'ndaki Meta verilerini döndürecek özelliği temsil eden bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="1603d-106">[in] A token that represents the property to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="1603d-107">dışı Özelliği uygulayan türü temsil eden TypeDef belirtecinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1603d-107">[out] A pointer to the TypeDef token that represents the type that implements the property.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="1603d-108">dışı Özellik adını tutan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="1603d-108">[out] A buffer to hold the property name.</span></span>  
  
 `cchProperty`  
 <span data-ttu-id="1603d-109">'ndaki Öğesinin geniş karakterdeki boyutu `szProperty` .</span><span class="sxs-lookup"><span data-stu-id="1603d-109">[in] The size in wide characters of `szProperty`.</span></span>  
  
 `pchProperty`  
 <span data-ttu-id="1603d-110">dışı İçinde döndürülen geniş karakter sayısı `szProperty` .</span><span class="sxs-lookup"><span data-stu-id="1603d-110">[out] The number of wide characters returned in `szProperty`.</span></span>  
  
 `pdwPropFlags`  
 <span data-ttu-id="1603d-111">dışı Özelliğe uygulanan öznitelik bayraklarının bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1603d-111">[out] A pointer to any attribute flags applied to the property.</span></span> <span data-ttu-id="1603d-112">Bu değer [CorPropertyAttr](corpropertyattr-enumeration.md) numaralandırmasından bir bit dır.</span><span class="sxs-lookup"><span data-stu-id="1603d-112">This value is a bitmask from the [CorPropertyAttr](corpropertyattr-enumeration.md) enumeration.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="1603d-113">dışı Özelliğin meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1603d-113">[out] A pointer to the metadata signature of the property.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="1603d-114">dışı İçinde döndürülen bayt sayısı `ppvSig` .</span><span class="sxs-lookup"><span data-stu-id="1603d-114">[out] The number of bytes returned in `ppvSig`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="1603d-115">dışı Özelliğin varsayılan değeri olan sabitin türünü belirten bayrak.</span><span class="sxs-lookup"><span data-stu-id="1603d-115">[out] A flag specifying the type of the constant that is the default value of the property.</span></span> <span data-ttu-id="1603d-116">Bu değer CorElementType numaralandırmasından.</span><span class="sxs-lookup"><span data-stu-id="1603d-116">This value is from the CorElementType enumeration.</span></span>  
  
 `ppDefaultValue`  
 <span data-ttu-id="1603d-117">dışı Bu özellik için varsayılan değeri depolayan bayta yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1603d-117">[out] A pointer to the bytes that store the default value for this property.</span></span>  
  
 `pcchDefaultValue`  
 <span data-ttu-id="1603d-118">dışı ' Nin geniş karakterdeki boyutu `ppDefaultValue` , `pdwCPlusTypeFlag` ELEMENT_TYPE_STRING; Aksi takdirde, bu değer ilgili değildir.</span><span class="sxs-lookup"><span data-stu-id="1603d-118">[out] The size in wide characters of `ppDefaultValue`, if `pdwCPlusTypeFlag` is ELEMENT_TYPE_STRING; otherwise, this value is not relevant.</span></span> <span data-ttu-id="1603d-119">Bu durumda, uzunluğu `ppDefaultValue` tarafından belirtilen türden çıkarsanamıyor `pdwCPlusTypeFlag` .</span><span class="sxs-lookup"><span data-stu-id="1603d-119">In that case, the length of `ppDefaultValue` is inferred from the type that is specified by `pdwCPlusTypeFlag`.</span></span>  
  
 `pmdSetter`  
 <span data-ttu-id="1603d-120">dışı Özelliği için set erişimcisi metodunu temsil eden MethodDef belirtecinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1603d-120">[out] A pointer to the MethodDef token that represents the set accessor method for the property.</span></span>  
  
 `pmdGetter`  
 <span data-ttu-id="1603d-121">dışı Özelliği için get erişimcisi metodunu temsil eden MethodDef belirtecinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1603d-121">[out] A pointer to the MethodDef token that represents the get accessor method for the property.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="1603d-122">dışı Özelliği ile ilişkili diğer yöntemleri temsil eden bir MethodDef belirteçleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="1603d-122">[out] An array of MethodDef tokens that represent other methods associated with the property.</span></span>  
  
 `cMax`  
 <span data-ttu-id="1603d-123">'ndaki Dizinin en büyük boyutu `rmdOtherMethod` .</span><span class="sxs-lookup"><span data-stu-id="1603d-123">[in] The maximum size of the `rmdOtherMethod` array.</span></span> <span data-ttu-id="1603d-124">Tüm yöntemleri tutacak büyüklükte bir dizi sağlamazsanız, bunlar uyarı vermeden atlanır.</span><span class="sxs-lookup"><span data-stu-id="1603d-124">If you do not provide an array large enough to hold all the methods, they are skipped without warning.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="1603d-125">dışı İçinde döndürülen MethodDef belirteçleri sayısı `rmdOtherMethod` .</span><span class="sxs-lookup"><span data-stu-id="1603d-125">[out] The number of MethodDef tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1603d-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1603d-126">Requirements</span></span>  
 <span data-ttu-id="1603d-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1603d-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1603d-128">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1603d-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1603d-129">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="1603d-129">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1603d-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1603d-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1603d-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1603d-131">See also</span></span>

- [<span data-ttu-id="1603d-132">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1603d-132">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="1603d-133">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1603d-133">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
