---
title: GetFileDef Yöntemi
ms.date: 03/30/2017
api_name:
- IALink2.GetFileDef
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetFileDef
helpviewer_keywords:
- GetFileDef method
ms.assetid: 4e3fbe6c-b82a-4181-ab17-7faa1263f5b3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9153c9b3735e265d59ba072f747c92434c95d9ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789876"
---
# <a name="getfiledef-method"></a><span data-ttu-id="db63b-102">GetFileDef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="db63b-102">GetFileDef Method</span></span>
<span data-ttu-id="db63b-103">(Aksine ALink tarafından atanan simgesi) meta verilerinde kullanılan gerçek FileDef belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="db63b-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db63b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="db63b-104">Syntax</span></span>  
  
```  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="db63b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="db63b-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="db63b-106">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="db63b-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="db63b-107">Belirteç eklenen dosyanın AddFile yöntemi veya Addımport yöntemi alınan gibi.</span><span class="sxs-lookup"><span data-stu-id="db63b-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="db63b-108">FileDef belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="db63b-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db63b-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="db63b-109">Return Value</span></span>  
 <span data-ttu-id="db63b-110">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="db63b-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db63b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="db63b-111">Requirements</span></span>  
 <span data-ttu-id="db63b-112">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="db63b-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db63b-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db63b-113">See also</span></span>

- [<span data-ttu-id="db63b-114">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="db63b-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="db63b-115">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="db63b-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="db63b-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="db63b-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
