---
title: GetResolutionScope Metodu
ms.date: 03/30/2017
api_name:
- IALink.GetResolutionScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetResolutionScope
helpviewer_keywords:
- GetResolutionScope method
ms.assetid: 5b48ca60-dacd-44b2-9979-4a5122f00812
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6c6d298c84b801b87832c56026b05f647cb5a9dd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135187"
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="661e1-102">GetResolutionScope Metodu</span><span class="sxs-lookup"><span data-stu-id="661e1-102">GetResolutionScope Method</span></span>
<span data-ttu-id="661e1-103">Kapsamı belirli bir türden alır.</span><span class="sxs-lookup"><span data-stu-id="661e1-103">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="661e1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="661e1-104">Syntax</span></span>  
  
```  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="661e1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="661e1-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="661e1-106">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="661e1-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="661e1-107">Geçirilmesi gereken başvuru dosya.</span><span class="sxs-lookup"><span data-stu-id="661e1-107">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="661e1-108">Dosyanın belirteç türü, genellikle alınan tanımlanan [ImportFile yöntemi](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="661e1-108">Token of file that type is defined in, usually retrieved with [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="661e1-109">Derleme veya modül başvurusu alır.</span><span class="sxs-lookup"><span data-stu-id="661e1-109">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="661e1-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="661e1-110">Return Value</span></span>  
 <span data-ttu-id="661e1-111">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="661e1-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="661e1-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="661e1-112">Requirements</span></span>  
 <span data-ttu-id="661e1-113">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="661e1-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="661e1-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="661e1-114">See also</span></span>

- [<span data-ttu-id="661e1-115">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="661e1-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="661e1-116">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="661e1-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="661e1-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="661e1-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
