---
title: ExportNestedType Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e6d40fffb2d40012d69599ad1bfcdbdaf454aa02
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="813ec-102">ExportNestedType Metodu</span><span class="sxs-lookup"><span data-stu-id="813ec-102">ExportNestedType Method</span></span>
<span data-ttu-id="813ec-103">İç içe geçmiş türler verilebilir olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="813ec-103">Specifies nested types as exportable.</span></span> <span data-ttu-id="813ec-104">[ExportType yöntemi](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md) iç içe geçmiş verme türlerini de kullanabilirsiniz, ancak bu daha hızlı bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="813ec-104">The [ExportType Method](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="813ec-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="813ec-105">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="813ec-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="813ec-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="813ec-107">Dışarı aktarmak için derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="813ec-107">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="813ec-108">Dosya belirteci veya derleme dosyasının dışa aktarılabilir duruma getirilmek üzere türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="813ec-108">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="813ec-109">Dışarı aktarılabilir yapılması türünde belirteç yazın.</span><span class="sxs-lookup"><span data-stu-id="813ec-109">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="813ec-110">Üst tür belirteci.</span><span class="sxs-lookup"><span data-stu-id="813ec-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="813ec-111">Dışarı aktarmak için tam olarak nitelenmiş tür adı.</span><span class="sxs-lookup"><span data-stu-id="813ec-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="813ec-112">`ComType`gibi bayrakları `tdPublic` veya `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="813ec-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="813ec-113">Bu değer için geçirilebilir [DefineExportedType yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="813ec-113">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="813ec-114">Dışarı aktarılan tür için belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="813ec-114">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="813ec-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="813ec-115">Return Value</span></span>  
 <span data-ttu-id="813ec-116">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="813ec-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="813ec-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="813ec-117">Requirements</span></span>  
 <span data-ttu-id="813ec-118">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="813ec-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="813ec-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="813ec-119">See Also</span></span>  
 [<span data-ttu-id="813ec-120">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="813ec-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="813ec-121">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="813ec-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="813ec-122">ALink API</span><span class="sxs-lookup"><span data-stu-id="813ec-122">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
