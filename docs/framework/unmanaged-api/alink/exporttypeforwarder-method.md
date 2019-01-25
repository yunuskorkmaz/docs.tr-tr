---
title: ExportTypeForwarder Metodu
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
ms.openlocfilehash: 03949fb52d23e3b0f107f9f1d5208208369c3960
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574621"
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="f4cc5-102">ExportTypeForwarder Metodu</span><span class="sxs-lookup"><span data-stu-id="f4cc5-102">ExportTypeForwarder Method</span></span>
<span data-ttu-id="f4cc5-103">Bir tür ileticisi verilen derleme türü tabloya ekler.</span><span class="sxs-lookup"><span data-stu-id="f4cc5-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4cc5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f4cc5-104">Syntax</span></span>  
  
```  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f4cc5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f4cc5-105">Parameters</span></span>  
 `tkAssemblyRef`  
 <span data-ttu-id="f4cc5-106">Tür ileticisi başvurduğu derlemesine başvuru.</span><span class="sxs-lookup"><span data-stu-id="f4cc5-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="f4cc5-107">Dışarı aktarmak için tam nitelikli tür adı.</span><span class="sxs-lookup"><span data-stu-id="f4cc5-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f4cc5-108">`ComType` gibi bayrakları `tdPublic` veya `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="f4cc5-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="f4cc5-109">Bu değer için geçirilebilir [DefineExportedType yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="f4cc5-109">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="f4cc5-110">Verilen türde bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="f4cc5-110">Receives the token of the exported type.</span></span> <span data-ttu-id="f4cc5-111">Bu, iç içe geçmiş türler yalnızca yayma için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f4cc5-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4cc5-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f4cc5-112">Return Value</span></span>  
 <span data-ttu-id="f4cc5-113">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4cc5-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4cc5-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f4cc5-114">Requirements</span></span>  
 <span data-ttu-id="f4cc5-115">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="f4cc5-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4cc5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4cc5-116">See also</span></span>
- [<span data-ttu-id="f4cc5-117">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f4cc5-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="f4cc5-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f4cc5-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="f4cc5-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="f4cc5-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
