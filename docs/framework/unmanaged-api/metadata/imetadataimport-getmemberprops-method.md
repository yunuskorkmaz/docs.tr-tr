---
description: ': IMetaDataImport:: GetMemberProps yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 073c8fae06c3df69f0b3152b109417b818637d1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783904"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="cb90f-103">IMetaDataImport::GetMemberProps Metodu</span><span class="sxs-lookup"><span data-stu-id="cb90f-103">IMetaDataImport::GetMemberProps Method</span></span>

<span data-ttu-id="cb90f-104">Belirtilen <xref:System.Type> meta veri belirtecinin başvurduğu üyenin adı, ikili imzası ve göreli sanal adresi de dahil olmak üzere, belirtilen üye tanımı için meta verilerde depolanan bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="cb90f-104">Gets information stored in the metadata for a specified member definition, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span> <span data-ttu-id="cb90f-105">Bu basit bir yardımcı yöntemdir: *MB* bir MethodDef Ise **GetMethodProps** çağrılır; *MB* bir fieldDef Ise, **GetFieldProps** çağırılır.</span><span class="sxs-lookup"><span data-stu-id="cb90f-105">This is a simple helper method: if *mb* is a MethodDef, then **GetMethodProps** is called; if *mb* is a FieldDef, then **GetFieldProps** is called.</span></span> <span data-ttu-id="cb90f-106">Ayrıntılar için diğer yöntemlere bakın.</span><span class="sxs-lookup"><span data-stu-id="cb90f-106">See these other methods for details.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="cb90f-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb90f-107">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="cb90f-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cb90f-108">Parameters</span></span>  

 `mb`  
 <span data-ttu-id="cb90f-109">'ndaki İlişkili meta verileri almak için üyeye başvuran belirteç.</span><span class="sxs-lookup"><span data-stu-id="cb90f-109">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="cb90f-110">dışı Üyenin sınıfını temsil eden meta veri belirtecinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="cb90f-110">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="cb90f-111">dışı Üyenin adı.</span><span class="sxs-lookup"><span data-stu-id="cb90f-111">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="cb90f-112">'ndaki Arabelleğin geniş karakterdeki boyutu `szMember` .</span><span class="sxs-lookup"><span data-stu-id="cb90f-112">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="cb90f-113">dışı Döndürülen adın geniş karakterdeki boyutu.</span><span class="sxs-lookup"><span data-stu-id="cb90f-113">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="cb90f-114">dışı Üyeye uygulanan bayrak değerleri.</span><span class="sxs-lookup"><span data-stu-id="cb90f-114">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="cb90f-115">dışı Üyenin ikili meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cb90f-115">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="cb90f-116">dışı Bayt cinsinden boyut `ppvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="cb90f-116">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="cb90f-117">dışı Üyenin göreli sanal adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cb90f-117">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="cb90f-118">dışı Üyeyle ilişkili herhangi bir yöntem uygulama bayrağı.</span><span class="sxs-lookup"><span data-stu-id="cb90f-118">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="cb90f-119">dışı Bir işareti olan bayrak <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="cb90f-119">[out] A flag that marks a <xref:System.ValueType>.</span></span> <span data-ttu-id="cb90f-120">Bu `ELEMENT_TYPE_*` değerlerden biridir.</span><span class="sxs-lookup"><span data-stu-id="cb90f-120">It is one of the `ELEMENT_TYPE_*` values.</span></span>
  
 `ppValue`  
 <span data-ttu-id="cb90f-121">dışı Bu üye tarafından döndürülen sabit dize değeri.</span><span class="sxs-lookup"><span data-stu-id="cb90f-121">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="cb90f-122">dışı Karakter cinsinden boyut `ppValue` veya dize yoksa sıfır `ppValue` .</span><span class="sxs-lookup"><span data-stu-id="cb90f-122">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb90f-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb90f-123">Requirements</span></span>  

 <span data-ttu-id="cb90f-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb90f-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb90f-125">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cb90f-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cb90f-126">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="cb90f-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cb90f-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb90f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb90f-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb90f-128">See also</span></span>

- [<span data-ttu-id="cb90f-129">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb90f-129">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="cb90f-130">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb90f-130">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
