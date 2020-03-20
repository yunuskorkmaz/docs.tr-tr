---
title: ExportNestedType Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedType
- ExportNestedType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedType
helpviewer_keywords:
- ExportNestedType method
ms.assetid: dec7df60-4d30-47c8-99db-72e0419e5f76
topic_type:
- apiref
ms.openlocfilehash: 9ca2167e66ac3aa5bcc0e92ff357eed18d366c67
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179407"
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="be1dc-102">ExportNestedType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="be1dc-102">ExportNestedType Method</span></span>
<span data-ttu-id="be1dc-103">İç içe geçme türlerini dışa aktarılabilir olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="be1dc-103">Specifies nested types as exportable.</span></span> <span data-ttu-id="be1dc-104">[Dışa Aktarma Türü Yöntemi](exporttype-method.md) iç içe geçen türleri de dışa aktarabilir, ancak bu yöntem daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="be1dc-104">The [ExportType Method](exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be1dc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be1dc-105">Syntax</span></span>  
  
```cpp  
HRESULT ExportNestedType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;
```  
  
## <a name="parameters"></a><span data-ttu-id="be1dc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="be1dc-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="be1dc-107">Dışa aktarmak için montaj kimliği.</span><span class="sxs-lookup"><span data-stu-id="be1dc-107">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="be1dc-108">Dışa aktarılacak türü tanımlayan dosya belirteci veya derlemesi.</span><span class="sxs-lookup"><span data-stu-id="be1dc-108">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="be1dc-109">Dışa aktarılabilir hale getirilecek türü belirteç.</span><span class="sxs-lookup"><span data-stu-id="be1dc-109">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="be1dc-110">Ana tip belirteç.</span><span class="sxs-lookup"><span data-stu-id="be1dc-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="be1dc-111">Dışa aktarmak için tam nitelikli tür adı.</span><span class="sxs-lookup"><span data-stu-id="be1dc-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="be1dc-112">`ComType`gibi `tdPublic` bayraklar `tdNested`veya .</span><span class="sxs-lookup"><span data-stu-id="be1dc-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="be1dc-113">Bu değer [DefineExportedType Yöntemi'ne](../metadata/imetadataassemblyemit-defineexportedtype-method.md)geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="be1dc-113">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="be1dc-114">Dışa aktarılan tür için belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="be1dc-114">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be1dc-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="be1dc-115">Return Value</span></span>  
 <span data-ttu-id="be1dc-116">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="be1dc-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be1dc-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be1dc-117">Requirements</span></span>  
 <span data-ttu-id="be1dc-118">alink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="be1dc-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be1dc-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be1dc-119">See also</span></span>

- [<span data-ttu-id="be1dc-120">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="be1dc-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="be1dc-121">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="be1dc-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="be1dc-122">ALink API</span><span class="sxs-lookup"><span data-stu-id="be1dc-122">ALink API</span></span>](index.md)
