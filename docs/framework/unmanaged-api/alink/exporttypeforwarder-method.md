---
title: ExportTypeForwarder Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ExportTypeForwarder
api_location: alink.dll
api_type: COM
f1_keywords: ExportTypeForwarder
helpviewer_keywords: ExportTypeForwarder method
ms.assetid: 55989fa9-ab43-4f08-8eb6-2eb56fa7ca76
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0f117d64673729113d917d700e3a26f9723b5a6e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="06542-102">ExportTypeForwarder Metodu</span><span class="sxs-lookup"><span data-stu-id="06542-102">ExportTypeForwarder Method</span></span>
<span data-ttu-id="06542-103">Tür iletici verilen derleme türü tablosuna ekler.</span><span class="sxs-lookup"><span data-stu-id="06542-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06542-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06542-104">Syntax</span></span>  
  
```  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="06542-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="06542-105">Parameters</span></span>  
 `tkAssemblyRef`  
 <span data-ttu-id="06542-106">Tür iletici başvurduğu derlemesine başvuru.</span><span class="sxs-lookup"><span data-stu-id="06542-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="06542-107">Dışarı aktarmak için tam olarak nitelenmiş tür adı.</span><span class="sxs-lookup"><span data-stu-id="06542-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="06542-108">`ComType`gibi bayrakları `tdPublic` veya `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="06542-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="06542-109">Bu değer için geçirilebilir [DefineExportedType yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="06542-109">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="06542-110">Dışarı aktarılan tür belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="06542-110">Receives the token of the exported type.</span></span> <span data-ttu-id="06542-111">Bu, yalnızca iç içe geçmiş türler yayma için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="06542-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06542-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="06542-112">Return Value</span></span>  
 <span data-ttu-id="06542-113">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="06542-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06542-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="06542-114">Requirements</span></span>  
 <span data-ttu-id="06542-115">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="06542-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06542-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="06542-116">See Also</span></span>  
 [<span data-ttu-id="06542-117">Ialink arabirimi</span><span class="sxs-lookup"><span data-stu-id="06542-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="06542-118">Ialink2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="06542-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="06542-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="06542-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
