---
title: ExportTypeForwarder Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.ExportTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportTypeForwarder
helpviewer_keywords:
- ExportTypeForwarder method
ms.assetid: 55989fa9-ab43-4f08-8eb6-2eb56fa7ca76
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f97f46595f43c7576c499c6b9944f7e3509662fb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742010"
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="8b36f-102">ExportTypeForwarder Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b36f-102">ExportTypeForwarder Method</span></span>
<span data-ttu-id="8b36f-103">Bir tür ileticisi verilen derleme türü tabloya ekler.</span><span class="sxs-lookup"><span data-stu-id="8b36f-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b36f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8b36f-104">Syntax</span></span>  
  
```cpp  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b36f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8b36f-105">Parameters</span></span>  
 `tkAssemblyRef`  
 <span data-ttu-id="8b36f-106">Tür ileticisi başvurduğu derlemesine başvuru.</span><span class="sxs-lookup"><span data-stu-id="8b36f-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="8b36f-107">Dışarı aktarmak için tam nitelikli tür adı.</span><span class="sxs-lookup"><span data-stu-id="8b36f-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8b36f-108">`ComType` gibi bayrakları `tdPublic` veya `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="8b36f-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="8b36f-109">Bu değer için geçirilebilir [DefineExportedType yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="8b36f-109">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="8b36f-110">Verilen türde bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="8b36f-110">Receives the token of the exported type.</span></span> <span data-ttu-id="8b36f-111">Bu, iç içe geçmiş türler yalnızca yayma için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8b36f-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b36f-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8b36f-112">Return Value</span></span>  
 <span data-ttu-id="8b36f-113">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="8b36f-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b36f-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8b36f-114">Requirements</span></span>  
 <span data-ttu-id="8b36f-115">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="8b36f-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b36f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b36f-116">See also</span></span>

- [<span data-ttu-id="8b36f-117">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b36f-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="8b36f-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b36f-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="8b36f-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="8b36f-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
