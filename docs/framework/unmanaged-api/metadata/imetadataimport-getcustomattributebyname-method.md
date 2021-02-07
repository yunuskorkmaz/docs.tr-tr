---
description: ': IMetaDataImport:: GetCustomAttributeByName metodu hakkında daha fazla bilgi edinin'
title: IMetaDataImport::GetCustomAttributeByName Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeByName
helpviewer_keywords:
- IMetaDataImport::GetCustomAttributeByName method [.NET Framework metadata]
- GetCustomAttributeByName method [.NET Framework metadata]
ms.assetid: 909aa530-2e3b-4d0a-a38a-a2750e535d7d
topic_type:
- apiref
ms.openlocfilehash: 1a9ca5f7fe13243c01c5dbcb9f49955e9ce05c26
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745495"
---
# <a name="imetadataimportgetcustomattributebyname-method"></a><span data-ttu-id="a6f59-103">IMetaDataImport::GetCustomAttributeByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a6f59-103">IMetaDataImport::GetCustomAttributeByName Method</span></span>

<span data-ttu-id="a6f59-104">Adı ve sahibi verilen özel özniteliği alır.</span><span class="sxs-lookup"><span data-stu-id="a6f59-104">Gets the custom attribute, given its name and owner.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6f59-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a6f59-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCustomAttributeByName (  
   [in]  mdToken          tkObj,  
   [in]  LPCWSTR          szName,  
   [out] const void       **ppData,  
   [out] ULONG            *pcbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6f59-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a6f59-106">Parameters</span></span>  

 `tkObj`  
 <span data-ttu-id="a6f59-107">'ndaki Özel özniteliğin sahibi olan nesneyi temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="a6f59-107">[in] A metadata token representing the object that owns the custom attribute.</span></span>  
  
 `szName`  
 <span data-ttu-id="a6f59-108">'ndaki Özel özniteliğin adı.</span><span class="sxs-lookup"><span data-stu-id="a6f59-108">[in] The name of the custom attribute.</span></span>  
  
 `ppData`  
 <span data-ttu-id="a6f59-109">dışı Özel özniteliğin değeri olan bir veri dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a6f59-109">[out] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="a6f59-110">dışı \* ' De döndürülen verilerin bayt cinsinden boyutu `ppData` .</span><span class="sxs-lookup"><span data-stu-id="a6f59-110">[out] The size in bytes of the data returned in \*`ppData`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6f59-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a6f59-111">Remarks</span></span>  

 <span data-ttu-id="a6f59-112">Aynı sahip için birden çok özel öznitelik tanımlamak geçerlidir; aynı ada bile sahip olabilirler.</span><span class="sxs-lookup"><span data-stu-id="a6f59-112">It is legal to define multiple custom attributes for the same owner; they may even have the same name.</span></span> <span data-ttu-id="a6f59-113">Ancak `GetCustomAttributeByName` yalnızca bir örnek döndürür.</span><span class="sxs-lookup"><span data-stu-id="a6f59-113">However, `GetCustomAttributeByName` returns only one instance.</span></span> <span data-ttu-id="a6f59-114">( `GetCustomAttributeByName` karşılaştığı ilk örneği döndürür.) Özel bir özniteliğin tüm örneklerini bulmak için, [IMetaDataImport:: EnumCustomAttributes](imetadataimport-enumcustomattributes-method.md) yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="a6f59-114">(`GetCustomAttributeByName` returns the first instance that it encounters.) To find all instances of a custom attribute, call the [IMetaDataImport::EnumCustomAttributes](imetadataimport-enumcustomattributes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6f59-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a6f59-115">Requirements</span></span>  

 <span data-ttu-id="a6f59-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6f59-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6f59-117">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a6f59-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a6f59-118">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="a6f59-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a6f59-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6f59-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6f59-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6f59-120">See also</span></span>

- [<span data-ttu-id="a6f59-121">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6f59-121">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="a6f59-122">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6f59-122">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
