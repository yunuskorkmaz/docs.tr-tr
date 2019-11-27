---
title: IMetaDataImport::GetNameFromToken Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNameFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNameFromToken
helpviewer_keywords:
- GetNameFromToken method [.NET Framework metadata]
- IMetaDataImport::GetNameFromToken method [.NET Framework metadata]
ms.assetid: 32114ecf-8916-4ab2-a201-179c017344f1
topic_type:
- apiref
ms.openlocfilehash: 6ed30f07fcec9c730e1514350c594399f0aa16e5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437269"
---
# <a name="imetadataimportgetnamefromtoken-method"></a><span data-ttu-id="8bf49-102">IMetaDataImport::GetNameFromToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8bf49-102">IMetaDataImport::GetNameFromToken Method</span></span>
<span data-ttu-id="8bf49-103">Belirtilen meta veri belirtecinin başvurduğu nesnenin UTF-8 adını alır.</span><span class="sxs-lookup"><span data-stu-id="8bf49-103">Gets the UTF-8 name of the object referenced by the specified metadata token.</span></span> <span data-ttu-id="8bf49-104">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="8bf49-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bf49-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8bf49-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8bf49-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8bf49-106">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="8bf49-107">'ndaki Adını döndürmek için nesneyi temsil eden belirteç.</span><span class="sxs-lookup"><span data-stu-id="8bf49-107">[in] The token representing the object to return the name for.</span></span>  
  
 `pszUtf8NamePtr`  
 <span data-ttu-id="8bf49-108">dışı Yığında UTF-8 nesne adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8bf49-108">[out] A pointer to the UTF-8 object name in the heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8bf49-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8bf49-109">Remarks</span></span>  
 <span data-ttu-id="8bf49-110">`GetNameFromToken` artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="8bf49-110">`GetNameFromToken` is obsolete.</span></span> <span data-ttu-id="8bf49-111">Alternatif olarak, bir alan için `GetFieldProps` veya bir yöntem için `GetMethodProps` gibi belirli bir belirteç türünün özelliklerini almak için bir yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="8bf49-111">As an alternative, call a method to get the properties of the particular type of token required, such as `GetFieldProps` for a field or `GetMethodProps` for a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bf49-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8bf49-112">Requirements</span></span>  
 <span data-ttu-id="8bf49-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bf49-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bf49-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8bf49-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8bf49-115">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="8bf49-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8bf49-116">**.NET Framework sürümleri:** 1,0</span><span class="sxs-lookup"><span data-stu-id="8bf49-116">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bf49-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8bf49-117">See also</span></span>

- [<span data-ttu-id="8bf49-118">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8bf49-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="8bf49-119">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8bf49-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
