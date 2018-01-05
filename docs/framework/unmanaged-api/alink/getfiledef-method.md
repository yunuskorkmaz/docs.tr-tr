---
title: GetFileDef Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.GetFileDef
api_location: alink.dll
api_type: COM
f1_keywords: GetFileDef
helpviewer_keywords: GetFileDef method
ms.assetid: 4e3fbe6c-b82a-4181-ab17-7faa1263f5b3
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 473cbaba8712ee247733ba3075c0163e259cf4dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="getfiledef-method"></a><span data-ttu-id="e85bc-102">GetFileDef Metodu</span><span class="sxs-lookup"><span data-stu-id="e85bc-102">GetFileDef Method</span></span>
<span data-ttu-id="e85bc-103">(Aksine, belirtecin ALink tarafından atanan) meta verilerinde kullanılan gerçek FileDef belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="e85bc-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e85bc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e85bc-104">Syntax</span></span>  
  
```  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e85bc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e85bc-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e85bc-106">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="e85bc-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="e85bc-107">Belirteç eklenen dosyasının AddFile yöntemi veya Addımport yöntemi alınan gibi.</span><span class="sxs-lookup"><span data-stu-id="e85bc-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="e85bc-108">FileDef belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="e85bc-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e85bc-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e85bc-109">Return Value</span></span>  
 <span data-ttu-id="e85bc-110">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="e85bc-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e85bc-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e85bc-111">Requirements</span></span>  
 <span data-ttu-id="e85bc-112">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="e85bc-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e85bc-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e85bc-113">See Also</span></span>  
 [<span data-ttu-id="e85bc-114">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e85bc-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="e85bc-115">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e85bc-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="e85bc-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="e85bc-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
