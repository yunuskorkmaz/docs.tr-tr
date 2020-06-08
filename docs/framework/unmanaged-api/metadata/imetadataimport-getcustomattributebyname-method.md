---
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
ms.openlocfilehash: e6921a0f6420546ba1e866e37a7a7cb129a77c67
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491465"
---
# <a name="imetadataimportgetcustomattributebyname-method"></a><span data-ttu-id="31a0c-102">IMetaDataImport::GetCustomAttributeByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="31a0c-102">IMetaDataImport::GetCustomAttributeByName Method</span></span>
<span data-ttu-id="31a0c-103">Adı ve sahibi verilen özel özniteliği alır.</span><span class="sxs-lookup"><span data-stu-id="31a0c-103">Gets the custom attribute, given its name and owner.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31a0c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="31a0c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCustomAttributeByName (  
   [in]  mdToken          tkObj,  
   [in]  LPCWSTR          szName,  
   [out] const void       **ppData,  
   [out] ULONG            *pcbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31a0c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="31a0c-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="31a0c-106">'ndaki Özel özniteliğin sahibi olan nesneyi temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="31a0c-106">[in] A metadata token representing the object that owns the custom attribute.</span></span>  
  
 `szName`  
 <span data-ttu-id="31a0c-107">'ndaki Özel özniteliğin adı.</span><span class="sxs-lookup"><span data-stu-id="31a0c-107">[in] The name of the custom attribute.</span></span>  
  
 `ppData`  
 <span data-ttu-id="31a0c-108">dışı Özel özniteliğin değeri olan bir veri dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="31a0c-108">[out] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="31a0c-109">dışı \* ' De döndürülen verilerin bayt cinsinden boyutu `ppData` .</span><span class="sxs-lookup"><span data-stu-id="31a0c-109">[out] The size in bytes of the data returned in \*`ppData`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31a0c-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="31a0c-110">Remarks</span></span>  
 <span data-ttu-id="31a0c-111">Aynı sahip için birden çok özel öznitelik tanımlamak geçerlidir; aynı ada bile sahip olabilirler.</span><span class="sxs-lookup"><span data-stu-id="31a0c-111">It is legal to define multiple custom attributes for the same owner; they may even have the same name.</span></span> <span data-ttu-id="31a0c-112">Ancak `GetCustomAttributeByName` yalnızca bir örnek döndürür.</span><span class="sxs-lookup"><span data-stu-id="31a0c-112">However, `GetCustomAttributeByName` returns only one instance.</span></span> <span data-ttu-id="31a0c-113">( `GetCustomAttributeByName` karşılaştığı ilk örneği döndürür.) Özel bir özniteliğin tüm örneklerini bulmak için, [IMetaDataImport:: EnumCustomAttributes](imetadataimport-enumcustomattributes-method.md) yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="31a0c-113">(`GetCustomAttributeByName` returns the first instance that it encounters.) To find all instances of a custom attribute, call the [IMetaDataImport::EnumCustomAttributes](imetadataimport-enumcustomattributes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31a0c-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="31a0c-114">Requirements</span></span>  
 <span data-ttu-id="31a0c-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31a0c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31a0c-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="31a0c-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="31a0c-117">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="31a0c-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="31a0c-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31a0c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31a0c-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31a0c-119">See also</span></span>

- [<span data-ttu-id="31a0c-120">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31a0c-120">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="31a0c-121">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31a0c-121">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
