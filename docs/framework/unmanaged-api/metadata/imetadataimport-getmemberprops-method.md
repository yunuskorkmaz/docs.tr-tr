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
ms.openlocfilehash: 98d7be5adc81cff09b121265e7d5b5f712122607
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611416"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="1dc76-102">IMetaDataImport::GetMemberProps Metodu</span><span class="sxs-lookup"><span data-stu-id="1dc76-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="1dc76-103">' In adı, ikili imzası ve göreli sanal adres dahil olmak üzere, meta veri bilgilerini alır <xref:System.Type> belirtilen metaveri belirteci tarafından başvurulan üyesi.</span><span class="sxs-lookup"><span data-stu-id="1dc76-103">Gets metadata information, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dc76-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1dc76-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="1dc76-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1dc76-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="1dc76-106">[in] Belirteç ilişkili meta verileri almak için bir üyeye başvuruda bulunuyor.</span><span class="sxs-lookup"><span data-stu-id="1dc76-106">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="1dc76-107">[out] Üye sınıfı temsil eden meta veri belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1dc76-107">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="1dc76-108">[out] Üyenin adı.</span><span class="sxs-lookup"><span data-stu-id="1dc76-108">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="1dc76-109">[in] Geniş karakter cinsinden boyutu `szMember` arabellek.</span><span class="sxs-lookup"><span data-stu-id="1dc76-109">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="1dc76-110">[out] Döndürülen adının geniş karakter cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="1dc76-110">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="1dc76-111">[out] Üyeye uygulanan tüm bayrak değerleri.</span><span class="sxs-lookup"><span data-stu-id="1dc76-111">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="1dc76-112">[out] İkili meta veri imzası üyenin bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1dc76-112">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="1dc76-113">[out] Bayt cinsinden boyutu `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="1dc76-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="1dc76-114">[out] Göreli sanal adres üyenin bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1dc76-114">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="1dc76-115">[out] Üye ile ilişkili tüm yöntemi uygulama bayrakları.</span><span class="sxs-lookup"><span data-stu-id="1dc76-115">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="1dc76-116">[out] İşaretler bayrak bir <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="1dc76-116">[out] A flag that marks a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="1dc76-117">[out] Bu üye tarafından döndürülen bir sabit dize değeri.</span><span class="sxs-lookup"><span data-stu-id="1dc76-117">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="1dc76-118">[out] Karakter cinsinden boyutu `ppValue`, ya da sıfır `ppValue` bir dize tutmaz.</span><span class="sxs-lookup"><span data-stu-id="1dc76-118">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dc76-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1dc76-119">Requirements</span></span>  
 <span data-ttu-id="1dc76-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dc76-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dc76-121">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="1dc76-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1dc76-122">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1dc76-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1dc76-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dc76-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dc76-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1dc76-124">See also</span></span>
- [<span data-ttu-id="1dc76-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1dc76-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="1dc76-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1dc76-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
