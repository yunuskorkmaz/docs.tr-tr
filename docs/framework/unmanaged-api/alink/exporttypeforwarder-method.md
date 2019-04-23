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
ms.openlocfilehash: 5bdf9fb50fe06141df6f3818c784588b9e2138af
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212030"
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="e40bb-102">ExportTypeForwarder Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e40bb-102">ExportTypeForwarder Method</span></span>
<span data-ttu-id="e40bb-103">Bir tür ileticisi verilen derleme türü tabloya ekler.</span><span class="sxs-lookup"><span data-stu-id="e40bb-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e40bb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e40bb-104">Syntax</span></span>  
  
```  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="e40bb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e40bb-105">Parameters</span></span>  
 `tkAssemblyRef`  
 <span data-ttu-id="e40bb-106">Tür ileticisi başvurduğu derlemesine başvuru.</span><span class="sxs-lookup"><span data-stu-id="e40bb-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="e40bb-107">Dışarı aktarmak için tam nitelikli tür adı.</span><span class="sxs-lookup"><span data-stu-id="e40bb-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="e40bb-108">`ComType` gibi bayrakları `tdPublic` veya `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="e40bb-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="e40bb-109">Bu değer için geçirilebilir [DefineExportedType yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="e40bb-109">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="e40bb-110">Verilen türde bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="e40bb-110">Receives the token of the exported type.</span></span> <span data-ttu-id="e40bb-111">Bu, iç içe geçmiş türler yalnızca yayma için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e40bb-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e40bb-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e40bb-112">Return Value</span></span>  
 <span data-ttu-id="e40bb-113">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="e40bb-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e40bb-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e40bb-114">Requirements</span></span>  
 <span data-ttu-id="e40bb-115">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="e40bb-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e40bb-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e40bb-116">See also</span></span>

- [<span data-ttu-id="e40bb-117">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e40bb-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="e40bb-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e40bb-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="e40bb-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="e40bb-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
