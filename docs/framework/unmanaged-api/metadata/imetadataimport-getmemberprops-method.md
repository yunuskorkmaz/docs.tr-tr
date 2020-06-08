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
ms.openlocfilehash: 0357444aa8fa38bce5a7175cf6aacfe1a2b2b16e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503646"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="065a8-102">IMetaDataImport::GetMemberProps Metodu</span><span class="sxs-lookup"><span data-stu-id="065a8-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="065a8-103">Belirtilen <xref:System.Type> meta veri belirtecinin başvurduğu üyenin adı, ikili imzası ve göreli sanal adresi de dahil olmak üzere, belirtilen üye tanımı için meta verilerde depolanan bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="065a8-103">Gets information stored in the metadata for a specified member definition, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span> <span data-ttu-id="065a8-104">Bu basit bir yardımcı yöntemdir: *MB* bir MethodDef Ise **GetMethodProps** çağrılır; *MB* bir fieldDef Ise, **GetFieldProps** çağırılır.</span><span class="sxs-lookup"><span data-stu-id="065a8-104">This is a simple helper method: if *mb* is a MethodDef, then **GetMethodProps** is called; if *mb* is a FieldDef, then **GetFieldProps** is called.</span></span> <span data-ttu-id="065a8-105">Ayrıntılar için diğer yöntemlere bakın.</span><span class="sxs-lookup"><span data-stu-id="065a8-105">See these other methods for details.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="065a8-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="065a8-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="065a8-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="065a8-107">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="065a8-108">'ndaki İlişkili meta verileri almak için üyeye başvuran belirteç.</span><span class="sxs-lookup"><span data-stu-id="065a8-108">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="065a8-109">dışı Üyenin sınıfını temsil eden meta veri belirtecinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="065a8-109">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="065a8-110">dışı Üyenin adı.</span><span class="sxs-lookup"><span data-stu-id="065a8-110">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="065a8-111">'ndaki Arabelleğin geniş karakterdeki boyutu `szMember` .</span><span class="sxs-lookup"><span data-stu-id="065a8-111">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="065a8-112">dışı Döndürülen adın geniş karakterdeki boyutu.</span><span class="sxs-lookup"><span data-stu-id="065a8-112">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="065a8-113">dışı Üyeye uygulanan bayrak değerleri.</span><span class="sxs-lookup"><span data-stu-id="065a8-113">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="065a8-114">dışı Üyenin ikili meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="065a8-114">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="065a8-115">dışı Bayt cinsinden boyut `ppvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="065a8-115">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="065a8-116">dışı Üyenin göreli sanal adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="065a8-116">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="065a8-117">dışı Üyeyle ilişkili herhangi bir yöntem uygulama bayrağı.</span><span class="sxs-lookup"><span data-stu-id="065a8-117">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="065a8-118">dışı Bir işareti olan bayrak <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="065a8-118">[out] A flag that marks a <xref:System.ValueType>.</span></span> <span data-ttu-id="065a8-119">Bu `ELEMENT_TYPE_*` değerlerden biridir.</span><span class="sxs-lookup"><span data-stu-id="065a8-119">It is one of the `ELEMENT_TYPE_*` values.</span></span>
  
 `ppValue`  
 <span data-ttu-id="065a8-120">dışı Bu üye tarafından döndürülen sabit dize değeri.</span><span class="sxs-lookup"><span data-stu-id="065a8-120">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="065a8-121">dışı Karakter cinsinden boyut `ppValue` veya dize yoksa sıfır `ppValue` .</span><span class="sxs-lookup"><span data-stu-id="065a8-121">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="065a8-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="065a8-122">Requirements</span></span>  
 <span data-ttu-id="065a8-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="065a8-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="065a8-124">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="065a8-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="065a8-125">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="065a8-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="065a8-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="065a8-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="065a8-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="065a8-127">See also</span></span>

- [<span data-ttu-id="065a8-128">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="065a8-128">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="065a8-129">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="065a8-129">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
