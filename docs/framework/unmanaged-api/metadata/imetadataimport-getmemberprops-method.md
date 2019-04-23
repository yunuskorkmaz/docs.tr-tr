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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83dec9b6ed3b1e538e0f1b7d13a33b8bdbc1cf54
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59200811"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="65284-102">IMetaDataImport::GetMemberProps Metodu</span><span class="sxs-lookup"><span data-stu-id="65284-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="65284-103">Belirtilen üye tanımı, adını, ikili imzası ve göreli sanal adres dahil olmak üzere, meta verileri içinde depolanan bilgilerini alır <xref:System.Type> belirtilen metaveri belirteci tarafından başvurulan üyesi.</span><span class="sxs-lookup"><span data-stu-id="65284-103">Gets information stored in the metadata for a specified member definition, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span> <span data-ttu-id="65284-104">Basit bir yardımcı yöntem budur: varsa *mb* bir MethodDef ise **GetMethodProps** ; Aranan *mb* bir fieldDef simgesi ise **GetFieldProps** çağrılır.</span><span class="sxs-lookup"><span data-stu-id="65284-104">This is a simple helper method: if *mb* is a MethodDef, then **GetMethodProps** is called; if *mb* is a FieldDef, then **GetFieldProps** is called.</span></span> <span data-ttu-id="65284-105">Bunlar diğer ayrıntılar için bkz.</span><span class="sxs-lookup"><span data-stu-id="65284-105">See these other methods for details.</span></span> 
  
## <a name="syntax"></a><span data-ttu-id="65284-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65284-106">Syntax</span></span>  
  
```  
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
  
## <a name="parameters"></a><span data-ttu-id="65284-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="65284-107">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="65284-108">[in] Belirteç ilişkili meta verileri almak için bir üyeye başvuruda bulunuyor.</span><span class="sxs-lookup"><span data-stu-id="65284-108">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="65284-109">[out] Üye sınıfı temsil eden meta veri belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="65284-109">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="65284-110">[out] Üyenin adı.</span><span class="sxs-lookup"><span data-stu-id="65284-110">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="65284-111">[in] Geniş karakter cinsinden boyutu `szMember` arabellek.</span><span class="sxs-lookup"><span data-stu-id="65284-111">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="65284-112">[out] Döndürülen adının geniş karakter cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="65284-112">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="65284-113">[out] Üyeye uygulanan tüm bayrak değerleri.</span><span class="sxs-lookup"><span data-stu-id="65284-113">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="65284-114">[out] İkili meta veri imzası üyenin bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="65284-114">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="65284-115">[out] Bayt cinsinden boyutu `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="65284-115">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="65284-116">[out] Göreli sanal adres üyenin bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="65284-116">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="65284-117">[out] Üye ile ilişkili tüm yöntemi uygulama bayrakları.</span><span class="sxs-lookup"><span data-stu-id="65284-117">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="65284-118">[out] İşaretler bayrak bir <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="65284-118">[out] A flag that marks a <xref:System.ValueType>.</span></span> <span data-ttu-id="65284-119">Biridir `ELEMENT_TYPE_*` değerleri.</span><span class="sxs-lookup"><span data-stu-id="65284-119">It is one of the `ELEMENT_TYPE_*` values.</span></span>
  
 `ppValue`  
 <span data-ttu-id="65284-120">[out] Bu üye tarafından döndürülen bir sabit dize değeri.</span><span class="sxs-lookup"><span data-stu-id="65284-120">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="65284-121">[out] Karakter cinsinden boyutu `ppValue`, ya da sıfır `ppValue` bir dize tutmaz.</span><span class="sxs-lookup"><span data-stu-id="65284-121">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65284-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="65284-122">Requirements</span></span>  
 <span data-ttu-id="65284-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65284-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65284-124">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="65284-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="65284-125">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="65284-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="65284-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65284-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65284-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65284-127">See also</span></span>

- [<span data-ttu-id="65284-128">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65284-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="65284-129">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65284-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
