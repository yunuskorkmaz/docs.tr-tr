---
title: ExportType Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ExportType
api_location: alink.dll
api_type: COM
f1_keywords: ExportType
helpviewer_keywords: ExportType method
ms.assetid: 91a7ce63-f5b8-4f16-b2c4-e1d0baa88944
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3f7bd3991fa57f11674b7ef0b9b62d12376fa765
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="exporttype-method"></a><span data-ttu-id="355f9-102">ExportType Metodu</span><span class="sxs-lookup"><span data-stu-id="355f9-102">ExportType Method</span></span>
<span data-ttu-id="355f9-103">Bir tür verilebilir olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="355f9-103">Specifies that a type is exportable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="355f9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="355f9-104">Syntax</span></span>  
  
```  
HRESULT ExportType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="355f9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="355f9-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="355f9-106">Dışarı aktarmak için derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="355f9-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="355f9-107">Dosya belirteç veya derleme kimliği dosyasının dışarı aktarılabilir türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="355f9-107">File token or assembly ID of file that defines the exportable type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="355f9-108">Dışarı aktarılabilir yapılması türünde belirteç.</span><span class="sxs-lookup"><span data-stu-id="355f9-108">Token of type to be made exportable.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="355f9-109">Dışarı aktarılabilir duruma getirilmek üzere tam olarak nitelenmiş tür adı.</span><span class="sxs-lookup"><span data-stu-id="355f9-109">Fully qualified type name to be made exportable.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="355f9-110">`ComType`gibi bayrakları `tdPublic` veya `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="355f9-110">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="355f9-111">Bu parametre için geçirilebilir [DefineExportedType yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="355f9-111">This parameter may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="355f9-112">Dışarı aktarılan tür için belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="355f9-112">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="355f9-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="355f9-113">Return Value</span></span>  
 <span data-ttu-id="355f9-114">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="355f9-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="355f9-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="355f9-115">Requirements</span></span>  
 <span data-ttu-id="355f9-116">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="355f9-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="355f9-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="355f9-117">See Also</span></span>  
 [<span data-ttu-id="355f9-118">Ialink arabirimi</span><span class="sxs-lookup"><span data-stu-id="355f9-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="355f9-119">Ialink2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="355f9-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="355f9-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="355f9-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
