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
ms.openlocfilehash: 1e9f51799ea56cb1e5819d708a0e4a8136a94f3d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741485"
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="0c8a2-102">SetAssemblyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c8a2-102">SetAssemblyProps Method</span></span>
<span data-ttu-id="0c8a2-103">Derleme düzeyi özellikleri atar.</span><span class="sxs-lookup"><span data-stu-id="0c8a2-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c8a2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0c8a2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c8a2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0c8a2-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="0c8a2-106">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="0c8a2-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="0c8a2-107">Bu dosya özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0c8a2-107">File that defines the property.</span></span> <span data-ttu-id="0c8a2-108">NULL olabilir `AssemblyID` ilişkisiz bir netmodule göstermez.</span><span class="sxs-lookup"><span data-stu-id="0c8a2-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="0c8a2-109">Değiştirme seçeneğine gösterir.</span><span class="sxs-lookup"><span data-stu-id="0c8a2-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="0c8a2-110">Seçenek yeni değeri.</span><span class="sxs-lookup"><span data-stu-id="0c8a2-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0c8a2-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0c8a2-111">Return Value</span></span>  
 <span data-ttu-id="0c8a2-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="0c8a2-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c8a2-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0c8a2-113">Requirements</span></span>  
 <span data-ttu-id="0c8a2-114">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0c8a2-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c8a2-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c8a2-115">See also</span></span>

- [<span data-ttu-id="0c8a2-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c8a2-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="0c8a2-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c8a2-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="0c8a2-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="0c8a2-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
