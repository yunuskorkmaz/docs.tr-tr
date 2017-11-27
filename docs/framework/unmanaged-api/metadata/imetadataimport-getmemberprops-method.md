---
title: IMetaDataImport::GetMemberProps Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetMemberProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetMemberProps
helpviewer_keywords:
- IMetaDataImport::GetMemberProps method [.NET Framework metadata]
- GetMemberProps method [.NET Framework metadata]
ms.assetid: 42790918-4142-4938-b8f4-a56979a55846
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b52d3130400310379c69eb0202217d1cd37ff18d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="b133e-102">IMetaDataImport::GetMemberProps Metodu</span><span class="sxs-lookup"><span data-stu-id="b133e-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="b133e-103">Adını, ikili imza ve göreli sanal adres, meta veri bilgilerini alır <xref:System.Type> belirtilen meta veri simgesi tarafından başvurulan üye.</span><span class="sxs-lookup"><span data-stu-id="b133e-103">Gets metadata information, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b133e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b133e-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="b133e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b133e-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="b133e-106">[in] İlişkili meta verileri almak için üye başvuran belirteci.</span><span class="sxs-lookup"><span data-stu-id="b133e-106">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="b133e-107">[out] Üye sınıfı temsil eder meta veri simgesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b133e-107">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="b133e-108">[out] Üyenin adı.</span><span class="sxs-lookup"><span data-stu-id="b133e-108">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="b133e-109">[in] Geniş karakter cinsinden boyutu `szMember` arabellek.</span><span class="sxs-lookup"><span data-stu-id="b133e-109">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="b133e-110">[out] Döndürülen adını geniş karakter cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="b133e-110">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="b133e-111">[out] Üyeye uygulanan tüm bayrak değeri.</span><span class="sxs-lookup"><span data-stu-id="b133e-111">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="b133e-112">[out] Üyenin ikili meta verileri imza için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b133e-112">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="b133e-113">[out] Bayt cinsinden boyutu `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="b133e-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="b133e-114">[out] Göreli sanal adres üyesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b133e-114">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="b133e-115">[out] Üye ile ilişkili tüm yöntemi uygulama bayrakları.</span><span class="sxs-lookup"><span data-stu-id="b133e-115">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="b133e-116">[out] İşaretler bir bayrak bir <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="b133e-116">[out] A flag that marks a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="b133e-117">[out] Bu üye tarafından döndürülen bir sabit dize değeri.</span><span class="sxs-lookup"><span data-stu-id="b133e-117">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="b133e-118">[out] Karakter cinsinden boyutu `ppValue`, ya da sıfır `ppValue` bir dize tutmaz.</span><span class="sxs-lookup"><span data-stu-id="b133e-118">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b133e-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b133e-119">Requirements</span></span>  
 <span data-ttu-id="b133e-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b133e-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b133e-121">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b133e-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b133e-122">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b133e-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b133e-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b133e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b133e-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b133e-124">See Also</span></span>  
 [<span data-ttu-id="b133e-125">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="b133e-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="b133e-126">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="b133e-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
