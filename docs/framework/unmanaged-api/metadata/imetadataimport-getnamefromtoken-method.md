---
description: ': IMetaDataImport:: GetNameFromToken Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 6195020a2b291a47e908b257896bdba64b0a40d9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720858"
---
# <a name="imetadataimportgetnamefromtoken-method"></a><span data-ttu-id="148a6-103">IMetaDataImport::GetNameFromToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="148a6-103">IMetaDataImport::GetNameFromToken Method</span></span>

<span data-ttu-id="148a6-104">Belirtilen meta veri belirtecinin başvurduğu nesnenin UTF-8 adını alır.</span><span class="sxs-lookup"><span data-stu-id="148a6-104">Gets the UTF-8 name of the object referenced by the specified metadata token.</span></span> <span data-ttu-id="148a6-105">Bu yöntem artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="148a6-105">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="148a6-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="148a6-106">Syntax</span></span>  
  
```cpp  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="148a6-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="148a6-107">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="148a6-108">'ndaki Adını döndürmek için nesneyi temsil eden belirteç.</span><span class="sxs-lookup"><span data-stu-id="148a6-108">[in] The token representing the object to return the name for.</span></span>  
  
 `pszUtf8NamePtr`  
 <span data-ttu-id="148a6-109">dışı Yığında UTF-8 nesne adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="148a6-109">[out] A pointer to the UTF-8 object name in the heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="148a6-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="148a6-110">Remarks</span></span>  

 <span data-ttu-id="148a6-111">`GetNameFromToken` artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="148a6-111">`GetNameFromToken` is obsolete.</span></span> <span data-ttu-id="148a6-112">Alternatif olarak, `GetFieldProps` bir alan veya bir yöntem için gerekli olan belirli bir belirteç türünün özelliklerini almak için bir yöntemi çağırın `GetMethodProps` .</span><span class="sxs-lookup"><span data-stu-id="148a6-112">As an alternative, call a method to get the properties of the particular type of token required, such as `GetFieldProps` for a field or `GetMethodProps` for a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="148a6-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="148a6-113">Requirements</span></span>  

 <span data-ttu-id="148a6-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="148a6-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="148a6-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="148a6-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="148a6-116">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="148a6-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="148a6-117">**.NET Framework sürümleri:** 1,0</span><span class="sxs-lookup"><span data-stu-id="148a6-117">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="148a6-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="148a6-118">See also</span></span>

- [<span data-ttu-id="148a6-119">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="148a6-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="148a6-120">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="148a6-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
