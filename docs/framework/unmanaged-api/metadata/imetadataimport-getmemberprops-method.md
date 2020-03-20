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
ms.openlocfilehash: 72e14ea0414ebdeb8f54a4bdef8ce5208fc8ef72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177224"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="f41ec-102">IMetaDataImport::GetMemberProps Metodu</span><span class="sxs-lookup"><span data-stu-id="f41ec-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="f41ec-103">Belirtilen meta veri belirteci tarafından başvurulan üyenin <xref:System.Type> adı, ikili imza ve göreli sanal adresi de dahil olmak üzere, belirli bir üye tanımı için meta verilerde depolanan bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="f41ec-103">Gets information stored in the metadata for a specified member definition, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span> <span data-ttu-id="f41ec-104">Bu basit bir yardımcı yöntemdir: *mb* bir MethodDef ise, **getMethodProps** denir; *mb* bir FieldDef ise, o zaman **GetFieldProps** denir.</span><span class="sxs-lookup"><span data-stu-id="f41ec-104">This is a simple helper method: if *mb* is a MethodDef, then **GetMethodProps** is called; if *mb* is a FieldDef, then **GetFieldProps** is called.</span></span> <span data-ttu-id="f41ec-105">Ayrıntılar için diğer yöntemlere bakın.</span><span class="sxs-lookup"><span data-stu-id="f41ec-105">See these other methods for details.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="f41ec-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f41ec-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f41ec-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f41ec-107">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="f41ec-108">[içinde] İlişkili meta verileri almak için üyeye başvurur belirteç.</span><span class="sxs-lookup"><span data-stu-id="f41ec-108">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="f41ec-109">[çıkış] Üyenin sınıfını temsil eden meta veri belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f41ec-109">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="f41ec-110">[çıkış] Üyenin adı.</span><span class="sxs-lookup"><span data-stu-id="f41ec-110">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="f41ec-111">[içinde] `szMember` Arabellek geniş karakterlerboyutu.</span><span class="sxs-lookup"><span data-stu-id="f41ec-111">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="f41ec-112">[çıkış] Döndürülen adın geniş karakterlerindeki boyutu.</span><span class="sxs-lookup"><span data-stu-id="f41ec-112">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="f41ec-113">[çıkış] Üyeye uygulanan tüm bayrak değerleri.</span><span class="sxs-lookup"><span data-stu-id="f41ec-113">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="f41ec-114">[çıkış] Üyenin ikili meta veri imzasına işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f41ec-114">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="f41ec-115">[çıkış] `ppvSigBlob`Baytboyutu.</span><span class="sxs-lookup"><span data-stu-id="f41ec-115">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="f41ec-116">[çıkış] Üyenin göreli sanal adresine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f41ec-116">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="f41ec-117">[çıkış] Üyeyle ilişkili herhangi bir yöntem uygulama bayrakları.</span><span class="sxs-lookup"><span data-stu-id="f41ec-117">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="f41ec-118">[çıkış] Bir bayrak. <xref:System.ValueType></span><span class="sxs-lookup"><span data-stu-id="f41ec-118">[out] A flag that marks a <xref:System.ValueType>.</span></span> <span data-ttu-id="f41ec-119">Bu `ELEMENT_TYPE_*` değerlerden biridir.</span><span class="sxs-lookup"><span data-stu-id="f41ec-119">It is one of the `ELEMENT_TYPE_*` values.</span></span>
  
 `ppValue`  
 <span data-ttu-id="f41ec-120">[çıkış] Bu üye tarafından döndürülen sabit bir dize değeri.</span><span class="sxs-lookup"><span data-stu-id="f41ec-120">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="f41ec-121">[çıkış] Bir dize tutmuyorsa `ppValue` `ppValue` , veya sıfır karakter boyutu.</span><span class="sxs-lookup"><span data-stu-id="f41ec-121">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f41ec-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f41ec-122">Requirements</span></span>  
 <span data-ttu-id="f41ec-123">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f41ec-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f41ec-124">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f41ec-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f41ec-125">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="f41ec-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f41ec-126">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f41ec-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f41ec-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f41ec-127">See also</span></span>

- [<span data-ttu-id="f41ec-128">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f41ec-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="f41ec-129">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f41ec-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
