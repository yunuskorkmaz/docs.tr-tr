---
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
ms.openlocfilehash: a031cdb875b5eb046428d4d235d3093caddb7a6a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491296"
---
# <a name="imetadataimportgetfieldmarshal-method"></a><span data-ttu-id="5c9f6-102">IMetaDataImport::GetFieldMarshal Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c9f6-102">IMetaDataImport::GetFieldMarshal Method</span></span>
<span data-ttu-id="5c9f6-103">Belirtilen alan meta veri belirteciyle temsil edilen alanın yerel, yönetilmeyen türüne yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="5c9f6-103">Gets a pointer to the native, unmanaged type of the field represented by the specified field metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c9f6-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5c9f6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldMarshal (  
   [in]  mdToken             tk,
   [out] PCCOR_SIGNATURE     *ppvNativeType,  
   [out] ULONG               *pcbNativeType
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c9f6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5c9f6-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="5c9f6-106">'ndaki İçin birlikte çalışma sıralama bilgilerini almak için alanı temsil eden meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="5c9f6-106">[in] The metadata token that represents the field to get interop marshaling information for.</span></span>  
  
 `ppvNativeType`  
 <span data-ttu-id="5c9f6-107">dışı Alanın yerel türünün meta veri imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5c9f6-107">[out] A pointer to the metadata signature of the field's native type.</span></span>  
  
 `pcbNativeType`  
 <span data-ttu-id="5c9f6-108">dışı Bayt cinsinden boyut `ppvNativeType` .</span><span class="sxs-lookup"><span data-stu-id="5c9f6-108">[out] The size in bytes of `ppvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c9f6-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c9f6-109">Requirements</span></span>  
 <span data-ttu-id="5c9f6-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c9f6-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c9f6-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5c9f6-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5c9f6-112">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="5c9f6-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5c9f6-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c9f6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c9f6-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c9f6-114">See also</span></span>

- [<span data-ttu-id="5c9f6-115">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c9f6-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="5c9f6-116">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c9f6-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
