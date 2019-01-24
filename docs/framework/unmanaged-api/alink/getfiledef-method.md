---
title: GetFileDef Metodu
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
ms.openlocfilehash: c6a8a9aedc5c2b09c6e6f6014142bce44f3a8297
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668606"
---
# <a name="getfiledef-method"></a><span data-ttu-id="06a2a-102">GetFileDef Metodu</span><span class="sxs-lookup"><span data-stu-id="06a2a-102">GetFileDef Method</span></span>
<span data-ttu-id="06a2a-103">(Aksine ALink tarafından atanan simgesi) meta verilerinde kullanılan gerçek FileDef belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="06a2a-103">Retrieves the actual FileDef token used in metadata (as opposed to the token assigned by ALink).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06a2a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06a2a-104">Syntax</span></span>  
  
```  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="06a2a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="06a2a-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="06a2a-106">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="06a2a-106">ID of the assembly.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="06a2a-107">Belirteç eklenen dosyanın AddFile yöntemi veya Addımport yöntemi alınan gibi.</span><span class="sxs-lookup"><span data-stu-id="06a2a-107">Token of the added file as retrieved from AddFile Method or AddImport Method.</span></span>  
  
 `pScope`  
 <span data-ttu-id="06a2a-108">FileDef belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="06a2a-108">Receives the FileDef token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06a2a-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="06a2a-109">Return Value</span></span>  
 <span data-ttu-id="06a2a-110">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="06a2a-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06a2a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="06a2a-111">Requirements</span></span>  
 <span data-ttu-id="06a2a-112">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="06a2a-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06a2a-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06a2a-113">See also</span></span>
- [<span data-ttu-id="06a2a-114">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="06a2a-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="06a2a-115">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="06a2a-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="06a2a-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="06a2a-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
