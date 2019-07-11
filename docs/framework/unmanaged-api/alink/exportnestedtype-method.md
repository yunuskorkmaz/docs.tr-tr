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
ms.openlocfilehash: 7dfaedad48291ac09f6959bc7b314ae0d9da76e5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742048"
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="80140-102">ExportNestedType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="80140-102">ExportNestedType Method</span></span>
<span data-ttu-id="80140-103">İç içe geçmiş türler dışarı aktarılabilir olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="80140-103">Specifies nested types as exportable.</span></span> <span data-ttu-id="80140-104">[ExportType yöntemi](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md) dışarı aktarma iç içe geçmiş türleri de kullanabilirsiniz, ancak bu daha hızlı bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="80140-104">The [ExportType Method](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80140-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80140-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="80140-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="80140-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="80140-107">Dışarı aktarmak için derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="80140-107">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="80140-108">Dosya belirteci veya derleme dosyasının dışarı aktarılabilir hale türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="80140-108">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="80140-109">Dışarı aktarılabilir hale türünde belirteç türü.</span><span class="sxs-lookup"><span data-stu-id="80140-109">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="80140-110">Üst tür belirteci.</span><span class="sxs-lookup"><span data-stu-id="80140-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="80140-111">Dışarı aktarmak için tam nitelikli tür adı.</span><span class="sxs-lookup"><span data-stu-id="80140-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="80140-112">`ComType` gibi bayrakları `tdPublic` veya `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="80140-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="80140-113">Bu değer için geçirilebilir [DefineExportedType yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="80140-113">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="80140-114">Dışarı aktarılan tür için belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="80140-114">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80140-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="80140-115">Return Value</span></span>  
 <span data-ttu-id="80140-116">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="80140-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80140-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80140-117">Requirements</span></span>  
 <span data-ttu-id="80140-118">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="80140-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80140-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80140-119">See also</span></span>

- [<span data-ttu-id="80140-120">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="80140-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="80140-121">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="80140-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="80140-122">ALink API</span><span class="sxs-lookup"><span data-stu-id="80140-122">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
