---
title: ExportTypeForwarder Metodu
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3fe418b1f8a5d5a6d3c2d36184ca76d5ef9989bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="85366-102">ExportTypeForwarder Metodu</span><span class="sxs-lookup"><span data-stu-id="85366-102">ExportTypeForwarder Method</span></span>
<span data-ttu-id="85366-103">Tür iletici verilen derleme türü tablosuna ekler.</span><span class="sxs-lookup"><span data-stu-id="85366-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85366-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="85366-104">Syntax</span></span>  
  
```  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="85366-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="85366-105">Parameters</span></span>  
 `tkAssemblyRef`  
 <span data-ttu-id="85366-106">Tür iletici başvurduğu derlemesine başvuru.</span><span class="sxs-lookup"><span data-stu-id="85366-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="85366-107">Dışarı aktarmak için tam olarak nitelenmiş tür adı.</span><span class="sxs-lookup"><span data-stu-id="85366-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="85366-108">`ComType`gibi bayrakları `tdPublic` veya `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="85366-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="85366-109">Bu değer için geçirilebilir [DefineExportedType yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="85366-109">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="85366-110">Dışarı aktarılan tür belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="85366-110">Receives the token of the exported type.</span></span> <span data-ttu-id="85366-111">Bu, yalnızca iç içe geçmiş türler yayma için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="85366-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85366-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="85366-112">Return Value</span></span>  
 <span data-ttu-id="85366-113">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="85366-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85366-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="85366-114">Requirements</span></span>  
 <span data-ttu-id="85366-115">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="85366-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85366-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="85366-116">See Also</span></span>  
 [<span data-ttu-id="85366-117">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85366-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="85366-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85366-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="85366-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="85366-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
