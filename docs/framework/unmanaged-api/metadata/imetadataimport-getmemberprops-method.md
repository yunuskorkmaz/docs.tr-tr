---
title: IMetaDataImport::GetMemberProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberProps
helpviewer_keywords:
- IMetaDataImport::GetMemberProps method [.NET Framework metadata]
- GetMemberProps method [.NET Framework metadata]
ms.assetid: 42790918-4142-4938-b8f4-a56979a55846
topic_type:
- apiref
ms.openlocfilehash: bc5bbba2fa4a95955e52a2e083a2097178b5d96a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437511"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="cc830-102">IMetaDataImport::GetMemberProps Metodu</span><span class="sxs-lookup"><span data-stu-id="cc830-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="cc830-103">Belirtilen meta veri belirtecinin başvurduğu <xref:System.Type> üyesinin adı, ikili imzası ve göreli sanal adresi de dahil olmak üzere, belirtilen üye tanımı için meta verilerde depolanan bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="cc830-103">Gets information stored in the metadata for a specified member definition, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span> <span data-ttu-id="cc830-104">Bu basit bir yardımcı yöntemdir: *MB* bir MethodDef Ise **GetMethodProps** çağrılır; *MB* bir fieldDef Ise, **GetFieldProps** çağırılır.</span><span class="sxs-lookup"><span data-stu-id="cc830-104">This is a simple helper method: if *mb* is a MethodDef, then **GetMethodProps** is called; if *mb* is a FieldDef, then **GetFieldProps** is called.</span></span> <span data-ttu-id="cc830-105">Ayrıntılar için diğer yöntemlere bakın.</span><span class="sxs-lookup"><span data-stu-id="cc830-105">See these other methods for details.</span></span> 
  
## <a name="syntax"></a><span data-ttu-id="cc830-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc830-106">Syntax</span></span>  
  
```cpp  
HRESULT GetMemberProps (  
   [in]  mdToken           mb,   
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szMember,   
   [in]  ULONG             cchMember,   
   [out] ULONG             *pchMember,   
   [out] DWORD             *pdwAttr,  
   [out] PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pcbSigBlob,   
   [out] ULONG             *pulCodeRVA,   
   [out] DWORD             *pdwImplFlags,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc830-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cc830-107">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="cc830-108">'ndaki İlişkili meta verileri almak için üyeye başvuran belirteç.</span><span class="sxs-lookup"><span data-stu-id="cc830-108">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="cc830-109">dışı Üyenin sınıfını temsil eden meta veri belirtecinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="cc830-109">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="cc830-110">dışı Üyenin adı.</span><span class="sxs-lookup"><span data-stu-id="cc830-110">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="cc830-111">'ndaki `szMember` arabelleğinin geniş karakterdeki boyutu.</span><span class="sxs-lookup"><span data-stu-id="cc830-111">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="cc830-112">dışı Döndürülen adın geniş karakterdeki boyutu.</span><span class="sxs-lookup"><span data-stu-id="cc830-112">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="cc830-113">dışı Üyeye uygulanan bayrak değerleri.</span><span class="sxs-lookup"><span data-stu-id="cc830-113">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="cc830-114">dışı Üyenin ikili meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cc830-114">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="cc830-115">dışı `ppvSigBlob`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="cc830-115">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="cc830-116">dışı Üyenin göreli sanal adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cc830-116">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="cc830-117">dışı Üyeyle ilişkili herhangi bir yöntem uygulama bayrağı.</span><span class="sxs-lookup"><span data-stu-id="cc830-117">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="cc830-118">dışı Bir <xref:System.ValueType>işaretleyen bayrak.</span><span class="sxs-lookup"><span data-stu-id="cc830-118">[out] A flag that marks a <xref:System.ValueType>.</span></span> <span data-ttu-id="cc830-119">`ELEMENT_TYPE_*` değerlerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="cc830-119">It is one of the `ELEMENT_TYPE_*` values.</span></span>
  
 `ppValue`  
 <span data-ttu-id="cc830-120">dışı Bu üye tarafından döndürülen sabit dize değeri.</span><span class="sxs-lookup"><span data-stu-id="cc830-120">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="cc830-121">dışı `ppValue`karakter cinsinden boyut veya `ppValue` bir dize yoksa sıfır.</span><span class="sxs-lookup"><span data-stu-id="cc830-121">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc830-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cc830-122">Requirements</span></span>  
 <span data-ttu-id="cc830-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc830-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc830-124">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cc830-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cc830-125">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="cc830-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cc830-126">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc830-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc830-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc830-127">See also</span></span>

- [<span data-ttu-id="cc830-128">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cc830-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="cc830-129">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cc830-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
