---
description: ': IMetaDataImport:: GetFieldMarshal yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataImport::GetFieldMarshal Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldMarshal
helpviewer_keywords:
- GetFieldMarshal method [.NET Framework metadata]
- IMetaDataImport::GetFieldMarshal method [.NET Framework metadata]
ms.assetid: 4e2d88c6-8a3a-4fbe-900b-b4f4c06bf6bf
topic_type:
- apiref
ms.openlocfilehash: d6ca1f80a8b9bae4d9c02466042300bc3662f7c3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803535"
---
# <a name="imetadataimportgetfieldmarshal-method"></a><span data-ttu-id="1215d-103">IMetaDataImport::GetFieldMarshal Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1215d-103">IMetaDataImport::GetFieldMarshal Method</span></span>

<span data-ttu-id="1215d-104">Belirtilen alan meta veri belirteciyle temsil edilen alanın yerel, yönetilmeyen türüne yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="1215d-104">Gets a pointer to the native, unmanaged type of the field represented by the specified field metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1215d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1215d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldMarshal (  
   [in]  mdToken             tk,
   [out] PCCOR_SIGNATURE     *ppvNativeType,  
   [out] ULONG               *pcbNativeType
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1215d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1215d-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="1215d-107">'ndaki İçin birlikte çalışma sıralama bilgilerini almak için alanı temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="1215d-107">[in] The metadata token that represents the field to get interop marshaling information for.</span></span>  
  
 `ppvNativeType`  
 <span data-ttu-id="1215d-108">dışı Alanın yerel türünün meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1215d-108">[out] A pointer to the metadata signature of the field's native type.</span></span>  
  
 `pcbNativeType`  
 <span data-ttu-id="1215d-109">dışı Bayt cinsinden boyut `ppvNativeType` .</span><span class="sxs-lookup"><span data-stu-id="1215d-109">[out] The size in bytes of `ppvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1215d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1215d-110">Requirements</span></span>  

 <span data-ttu-id="1215d-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1215d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1215d-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1215d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1215d-113">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="1215d-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1215d-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1215d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1215d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1215d-115">See also</span></span>

- [<span data-ttu-id="1215d-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1215d-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="1215d-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1215d-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
