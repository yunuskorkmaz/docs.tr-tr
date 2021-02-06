---
description: 'Daha fazla bilgi edinin: ExportNestedType yöntemi'
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
ms.openlocfilehash: 66cf4c3572857a0e7e99efa966cdb0b9ae2be673
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638151"
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="84860-103">ExportNestedType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="84860-103">ExportNestedType Method</span></span>

<span data-ttu-id="84860-104">İç içe geçmiş türleri verilebilir olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="84860-104">Specifies nested types as exportable.</span></span> <span data-ttu-id="84860-105">[ExportType Yöntemi](exporttype-method.md) iç içe geçmiş türleri de dışa aktarabilir, ancak bu yöntem daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="84860-105">The [ExportType Method](exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84860-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="84860-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="84860-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="84860-107">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="84860-108">Dışarı aktarılacak derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="84860-108">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="84860-109">Dışarı aktarılabilir hale getirilme türünü tanımlayan dosya belirteci veya dosya derlemesi.</span><span class="sxs-lookup"><span data-stu-id="84860-109">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="84860-110">Dışarı aktarılabilir hale getirilme türünün tür belirteci.</span><span class="sxs-lookup"><span data-stu-id="84860-110">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="84860-111">Üst tür belirteci.</span><span class="sxs-lookup"><span data-stu-id="84860-111">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="84860-112">Dışarı aktarılacak tam tür adı.</span><span class="sxs-lookup"><span data-stu-id="84860-112">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="84860-113">`ComType` veya gibi bayraklar `tdPublic` `tdNested` .</span><span class="sxs-lookup"><span data-stu-id="84860-113">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="84860-114">Bu değer [DefineExportedType yöntemine](../metadata/imetadataassemblyemit-defineexportedtype-method.md)geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="84860-114">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="84860-115">İçe aktarılmış tür için belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="84860-115">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84860-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="84860-116">Return Value</span></span>  

 <span data-ttu-id="84860-117">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="84860-117">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84860-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="84860-118">Requirements</span></span>  

 <span data-ttu-id="84860-119">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="84860-119">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84860-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84860-120">See also</span></span>

- [<span data-ttu-id="84860-121">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="84860-121">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="84860-122">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="84860-122">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="84860-123">ALink API</span><span class="sxs-lookup"><span data-stu-id="84860-123">ALink API</span></span>](index.md)
