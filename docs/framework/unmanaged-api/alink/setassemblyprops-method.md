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
ms.openlocfilehash: dc9ca5d9533a6c4a297155a47ac0061f1232d242
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481120"
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="093fd-102">SetAssemblyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="093fd-102">SetAssemblyProps Method</span></span>
<span data-ttu-id="093fd-103">Derleme düzeyi özellikleri atar.</span><span class="sxs-lookup"><span data-stu-id="093fd-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="093fd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="093fd-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="093fd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="093fd-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="093fd-106">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="093fd-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="093fd-107">Bu dosya özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="093fd-107">File that defines the property.</span></span> <span data-ttu-id="093fd-108">NULL olabilir `AssemblyID` ilişkisiz bir netmodule göstermez.</span><span class="sxs-lookup"><span data-stu-id="093fd-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="093fd-109">Değiştirme seçeneğine gösterir.</span><span class="sxs-lookup"><span data-stu-id="093fd-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="093fd-110">Seçenek yeni değeri.</span><span class="sxs-lookup"><span data-stu-id="093fd-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="093fd-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="093fd-111">Return Value</span></span>  
 <span data-ttu-id="093fd-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="093fd-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="093fd-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="093fd-113">Requirements</span></span>  
 <span data-ttu-id="093fd-114">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="093fd-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="093fd-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="093fd-115">See also</span></span>
- [<span data-ttu-id="093fd-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="093fd-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="093fd-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="093fd-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="093fd-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="093fd-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
