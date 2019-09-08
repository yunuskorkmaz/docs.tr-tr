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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 570e48788a11045882ef546bf6bc22315c2a02b0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777268"
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="ee44b-102">ExportNestedType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ee44b-102">ExportNestedType Method</span></span>
<span data-ttu-id="ee44b-103">İç içe geçmiş türleri verilebilir olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="ee44b-103">Specifies nested types as exportable.</span></span> <span data-ttu-id="ee44b-104">[ExportType Yöntemi](exporttype-method.md) iç içe geçmiş türleri de dışa aktarabilir, ancak bu yöntem daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="ee44b-104">The [ExportType Method](exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee44b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ee44b-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ee44b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ee44b-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="ee44b-107">Dışarı aktarılacak derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="ee44b-107">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="ee44b-108">Dışarı aktarılabilir hale getirilme türünü tanımlayan dosya belirteci veya dosya derlemesi.</span><span class="sxs-lookup"><span data-stu-id="ee44b-108">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="ee44b-109">Dışarı aktarılabilir hale getirilme türünün tür belirteci.</span><span class="sxs-lookup"><span data-stu-id="ee44b-109">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="ee44b-110">Üst tür belirteci.</span><span class="sxs-lookup"><span data-stu-id="ee44b-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="ee44b-111">Dışarı aktarılacak tam tür adı.</span><span class="sxs-lookup"><span data-stu-id="ee44b-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ee44b-112">`ComType``tdPublic` veya`tdNested`gibi bayraklar.</span><span class="sxs-lookup"><span data-stu-id="ee44b-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="ee44b-113">Bu değer [DefineExportedType yöntemine](../metadata/imetadataassemblyemit-defineexportedtype-method.md)geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ee44b-113">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="ee44b-114">İçe aktarılmış tür için belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="ee44b-114">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ee44b-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ee44b-115">Return Value</span></span>  
 <span data-ttu-id="ee44b-116">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="ee44b-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee44b-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ee44b-117">Requirements</span></span>  
 <span data-ttu-id="ee44b-118">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="ee44b-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee44b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee44b-119">See also</span></span>

- [<span data-ttu-id="ee44b-120">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee44b-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="ee44b-121">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee44b-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="ee44b-122">ALink API</span><span class="sxs-lookup"><span data-stu-id="ee44b-122">ALink API</span></span>](index.md)
