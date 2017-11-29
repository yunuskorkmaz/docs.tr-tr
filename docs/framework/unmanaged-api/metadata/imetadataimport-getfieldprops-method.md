---
title: IMetaDataImport::GetFieldProps Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetFieldProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetFieldProps
helpviewer_keywords:
- IMetaDataImport::GetFieldProps method [.NET Framework metadata]
- GetFieldProps method [.NET Framework metadata]
ms.assetid: 7b0e9b10-8cef-4ba6-8432-40bf63e65ab1
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d5874169e0f8c452b177309702444ea84858557e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetfieldprops-method"></a><span data-ttu-id="62df6-102">IMetaDataImport::GetFieldProps Metodu</span><span class="sxs-lookup"><span data-stu-id="62df6-102">IMetaDataImport::GetFieldProps Method</span></span>
<span data-ttu-id="62df6-103">Belirtilen fieldDef simgesi tarafından başvurulan alanıyla ilişkili meta verileri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="62df6-103">Gets metadata associated with the field referenced by the specified FieldDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62df6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62df6-104">Syntax</span></span>  
  
```  
HRESULT GetFieldProps (  
   [in]  mdFieldDef        mb,   
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szField,  
   [in]  ULONG             cchField,   
   [out] ULONG             *pchField,  
   [out] DWORD             *pdwAttr,  
   [in]  PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pcbSigBlob,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62df6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="62df6-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="62df6-106">[in] İlişkili meta verileri almak için alanını temsil eden bir fieldDef simgesi belirteci.</span><span class="sxs-lookup"><span data-stu-id="62df6-106">[in] A FieldDef token that represents the field to get associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="62df6-107">[out] Alanın ait sınıf türünü temsil eden bir TypeDef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="62df6-107">[out] A pointer to a TypeDef token that represents the type of the class that the field belongs to.</span></span>  
  
 `szField`  
 <span data-ttu-id="62df6-108">[out] Alanın adı.</span><span class="sxs-lookup"><span data-stu-id="62df6-108">[out] The name of the field.</span></span>  
  
 `cchField`  
 <span data-ttu-id="62df6-109">[in] Geniş karakterler için arabellek boyutu *szField*.</span><span class="sxs-lookup"><span data-stu-id="62df6-109">[in] The size in wide characters of the buffer for *szField*.</span></span>  
  
 `pchField`  
 <span data-ttu-id="62df6-110">[out] Döndürülen arabellek gerçek boyutu.</span><span class="sxs-lookup"><span data-stu-id="62df6-110">[out] The actual size of the returned buffer.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="62df6-111">[out] Alanın meta verileriyle ilişkili bayraklar.</span><span class="sxs-lookup"><span data-stu-id="62df6-111">[out] Flags associated with the field's metadata.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="62df6-112">[in] Alan açıklar ikili meta veri değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="62df6-112">[in] A pointer to the binary metadata value that describes the field.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="62df6-113">[out] Bayt cinsinden boyutu `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="62df6-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="62df6-114">[out] Alan değeri türünü belirten bir bayrak.</span><span class="sxs-lookup"><span data-stu-id="62df6-114">[out] A flag that specifies the value type of the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="62df6-115">[out] Alan için sabit bir değer.</span><span class="sxs-lookup"><span data-stu-id="62df6-115">[out] A constant value for the field.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="62df6-116">[out] Karakter boyutu `ppValue`, veya dize varsa sıfır.</span><span class="sxs-lookup"><span data-stu-id="62df6-116">[out] The size in chars of `ppValue`, or zero if no string exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62df6-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="62df6-117">Requirements</span></span>  
 <span data-ttu-id="62df6-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62df6-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62df6-119">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="62df6-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="62df6-120">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="62df6-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="62df6-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62df6-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62df6-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="62df6-122">See Also</span></span>  
 [<span data-ttu-id="62df6-123">Imetadataımport arabirimi</span><span class="sxs-lookup"><span data-stu-id="62df6-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="62df6-124">Imetadataımport2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="62df6-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
