---
title: SetAssemblyProps Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyProps
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method
ms.assetid: a3d7cf29-1414-49e6-8aae-9b3283c4f5f0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 589bd7b2132693c89dc10ae1a5c8d0bf52ed481e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218998"
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="69382-102">SetAssemblyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="69382-102">SetAssemblyProps Method</span></span>
<span data-ttu-id="69382-103">Derleme düzeyi özellikleri atar.</span><span class="sxs-lookup"><span data-stu-id="69382-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69382-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="69382-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="69382-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="69382-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="69382-106">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="69382-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="69382-107">Bu dosya özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="69382-107">File that defines the property.</span></span> <span data-ttu-id="69382-108">NULL olabilir `AssemblyID` ilişkisiz bir netmodule göstermez.</span><span class="sxs-lookup"><span data-stu-id="69382-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="69382-109">Değiştirme seçeneğine gösterir.</span><span class="sxs-lookup"><span data-stu-id="69382-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="69382-110">Seçenek yeni değeri.</span><span class="sxs-lookup"><span data-stu-id="69382-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69382-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="69382-111">Return Value</span></span>  
 <span data-ttu-id="69382-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="69382-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69382-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="69382-113">Requirements</span></span>  
 <span data-ttu-id="69382-114">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="69382-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69382-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69382-115">See also</span></span>

- [<span data-ttu-id="69382-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="69382-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="69382-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="69382-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="69382-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="69382-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
