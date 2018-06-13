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
ms.openlocfilehash: e67a71c25c0ae8ee7c54fae2e38d1116a5d92eff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402595"
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="0b2fc-102">GetResolutionScope Metodu</span><span class="sxs-lookup"><span data-stu-id="0b2fc-102">GetResolutionScope Method</span></span>
<span data-ttu-id="0b2fc-103">Belirli bir türde kapsamını alır.</span><span class="sxs-lookup"><span data-stu-id="0b2fc-103">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b2fc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b2fc-104">Syntax</span></span>  
  
```  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0b2fc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0b2fc-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="0b2fc-106">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="0b2fc-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="0b2fc-107">Gerekli bir başvuru dosyası.</span><span class="sxs-lookup"><span data-stu-id="0b2fc-107">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="0b2fc-108">Belirteç dosyasının bu türü ile genellikle alınan tanımlı [ImportFile yöntemi](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="0b2fc-108">Token of file that type is defined in, usually retrieved with [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="0b2fc-109">Derleme veya modül başvurusu alır.</span><span class="sxs-lookup"><span data-stu-id="0b2fc-109">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b2fc-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0b2fc-110">Return Value</span></span>  
 <span data-ttu-id="0b2fc-111">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="0b2fc-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b2fc-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b2fc-112">Requirements</span></span>  
 <span data-ttu-id="0b2fc-113">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0b2fc-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b2fc-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0b2fc-114">See Also</span></span>  
 [<span data-ttu-id="0b2fc-115">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b2fc-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="0b2fc-116">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b2fc-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="0b2fc-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="0b2fc-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
