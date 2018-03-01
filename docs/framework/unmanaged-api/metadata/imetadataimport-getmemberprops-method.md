---
title: IMetaDataImport::GetMemberProps Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 543929390977fc593e86947feece06f43bc0cad6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="1cfc9-102">IMetaDataImport::GetMemberProps Metodu</span><span class="sxs-lookup"><span data-stu-id="1cfc9-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="1cfc9-103">Adını, ikili imza ve göreli sanal adres, meta veri bilgilerini alır <xref:System.Type> belirtilen meta veri simgesi tarafından başvurulan üye.</span><span class="sxs-lookup"><span data-stu-id="1cfc9-103">Gets metadata information, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cfc9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1cfc9-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="1cfc9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1cfc9-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="1cfc9-106">[in] İlişkili meta verileri almak için üye başvuran belirteci.</span><span class="sxs-lookup"><span data-stu-id="1cfc9-106">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="1cfc9-107">[out] Üye sınıfı temsil eder meta veri simgesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1cfc9-107">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="1cfc9-108">[out] Üyenin adı.</span><span class="sxs-lookup"><span data-stu-id="1cfc9-108">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="1cfc9-109">[in] Geniş karakter cinsinden boyutu `szMember` arabellek.</span><span class="sxs-lookup"><span data-stu-id="1cfc9-109">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="1cfc9-110">[out] Döndürülen adını geniş karakter cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="1cfc9-110">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="1cfc9-111">[out] Üyeye uygulanan tüm bayrak değeri.</span><span class="sxs-lookup"><span data-stu-id="1cfc9-111">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="1cfc9-112">[out] Üyenin ikili meta verileri imza için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1cfc9-112">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="1cfc9-113">[out] Bayt cinsinden boyutu `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="1cfc9-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="1cfc9-114">[out] Göreli sanal adres üyesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1cfc9-114">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="1cfc9-115">[out] Üye ile ilişkili tüm yöntemi uygulama bayrakları.</span><span class="sxs-lookup"><span data-stu-id="1cfc9-115">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="1cfc9-116">[out] İşaretler bir bayrak bir <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="1cfc9-116">[out] A flag that marks a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="1cfc9-117">[out] Bu üye tarafından döndürülen bir sabit dize değeri.</span><span class="sxs-lookup"><span data-stu-id="1cfc9-117">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="1cfc9-118">[out] Karakter cinsinden boyutu `ppValue`, ya da sıfır `ppValue` bir dize tutmaz.</span><span class="sxs-lookup"><span data-stu-id="1cfc9-118">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cfc9-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1cfc9-119">Requirements</span></span>  
 <span data-ttu-id="1cfc9-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cfc9-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cfc9-121">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1cfc9-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1cfc9-122">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1cfc9-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1cfc9-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cfc9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cfc9-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1cfc9-124">See Also</span></span>  
 [<span data-ttu-id="1cfc9-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1cfc9-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="1cfc9-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1cfc9-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
