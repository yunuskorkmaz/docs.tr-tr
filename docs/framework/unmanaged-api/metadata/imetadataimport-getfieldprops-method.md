---
title: IMetaDataImport::GetFieldProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldProps
helpviewer_keywords:
- IMetaDataImport::GetFieldProps method [.NET Framework metadata]
- GetFieldProps method [.NET Framework metadata]
ms.assetid: 7b0e9b10-8cef-4ba6-8432-40bf63e65ab1
topic_type:
- apiref
ms.openlocfilehash: 462512fd2c2b33905b45bb67599b23b301fc71f7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438000"
---
# <a name="imetadataimportgetfieldprops-method"></a><span data-ttu-id="791a8-102">IMetaDataImport::GetFieldProps Metodu</span><span class="sxs-lookup"><span data-stu-id="791a8-102">IMetaDataImport::GetFieldProps Method</span></span>
<span data-ttu-id="791a8-103">Belirtilen FieldDef belirtecinin başvurduğu alanla ilişkili meta verileri alır.</span><span class="sxs-lookup"><span data-stu-id="791a8-103">Gets metadata associated with the field referenced by the specified FieldDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="791a8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="791a8-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="791a8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="791a8-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="791a8-106">'ndaki İlişkili meta verileri almak için alanı temsil eden bir FieldDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="791a8-106">[in] A FieldDef token that represents the field to get associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="791a8-107">dışı Bir TypeDef belirtecinin, alanın ait olduğu sınıfın türünü temsil eden bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="791a8-107">[out] A pointer to a TypeDef token that represents the type of the class that the field belongs to.</span></span>  
  
 `szField`  
 <span data-ttu-id="791a8-108">dışı Alanın adı.</span><span class="sxs-lookup"><span data-stu-id="791a8-108">[out] The name of the field.</span></span>  
  
 `cchField`  
 <span data-ttu-id="791a8-109">'ndaki *SzField*arabelleğinin geniş karakterdeki boyutu.</span><span class="sxs-lookup"><span data-stu-id="791a8-109">[in] The size in wide characters of the buffer for *szField*.</span></span>  
  
 `pchField`  
 <span data-ttu-id="791a8-110">dışı Döndürülen arabelleğin gerçek boyutu.</span><span class="sxs-lookup"><span data-stu-id="791a8-110">[out] The actual size of the returned buffer.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="791a8-111">dışı Alanın meta verileriyle ilişkili bayraklar.</span><span class="sxs-lookup"><span data-stu-id="791a8-111">[out] Flags associated with the field's metadata.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="791a8-112">'ndaki Alanı açıklayan ikili meta veri değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="791a8-112">[in] A pointer to the binary metadata value that describes the field.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="791a8-113">dışı `ppvSigBlob`bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="791a8-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="791a8-114">dışı Alanın değer türünü belirten bayrak.</span><span class="sxs-lookup"><span data-stu-id="791a8-114">[out] A flag that specifies the value type of the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="791a8-115">dışı Alan için sabit bir değer.</span><span class="sxs-lookup"><span data-stu-id="791a8-115">[out] A constant value for the field.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="791a8-116">dışı `ppValue`karakter cinsinden boyut veya hiçbir dize yoksa sıfır.</span><span class="sxs-lookup"><span data-stu-id="791a8-116">[out] The size in chars of `ppValue`, or zero if no string exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="791a8-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="791a8-117">Requirements</span></span>  
 <span data-ttu-id="791a8-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="791a8-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="791a8-119">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="791a8-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="791a8-120">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="791a8-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="791a8-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="791a8-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="791a8-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="791a8-122">See also</span></span>

- [<span data-ttu-id="791a8-123">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="791a8-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="791a8-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="791a8-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
