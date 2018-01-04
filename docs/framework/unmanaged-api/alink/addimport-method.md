---
title: "Addımport Method1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- AddImport
- IALink.AddImport
api_location: alink.dll
api_type: COM
f1_keywords: AddImport
helpviewer_keywords: AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d8827821deaeda311a42855737ecf53ab635a02
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="addimport-method1"></a><span data-ttu-id="995ae-102">Addımport Method1</span><span class="sxs-lookup"><span data-stu-id="995ae-102">AddImport Method1</span></span>
<span data-ttu-id="995ae-103">İçeri aktarmalar derlemeye ekler.</span><span class="sxs-lookup"><span data-stu-id="995ae-103">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="995ae-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="995ae-104">Syntax</span></span>  
  
```  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="995ae-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="995ae-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="995ae-106">Derleme engagement'ta benzersiz kimliği.</span><span class="sxs-lookup"><span data-stu-id="995ae-106">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="995ae-107">Benzersiz kimliği alınan [ImportFile yöntemi](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), içeri aktarılacak dosya.</span><span class="sxs-lookup"><span data-stu-id="995ae-107">Unique ID, retrieved from [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="995ae-108">COM + FileDef bayrakları gibi `ffContainsNoMetaData` ve `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="995ae-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="995ae-109">`dwFlags`geçirilir [DefineFile yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="995ae-109">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="995ae-110">Sonuç dosyası kimliği aldığı belirteci işaretçi.</span><span class="sxs-lookup"><span data-stu-id="995ae-110">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="995ae-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="995ae-111">Return Value</span></span>  
 <span data-ttu-id="995ae-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="995ae-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="995ae-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="995ae-113">Requirements</span></span>  
 <span data-ttu-id="995ae-114">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="995ae-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="995ae-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="995ae-115">See Also</span></span>  
 [<span data-ttu-id="995ae-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="995ae-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="995ae-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="995ae-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="995ae-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="995ae-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
