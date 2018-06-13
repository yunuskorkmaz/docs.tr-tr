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
ms.openlocfilehash: aed553a3a8d54b5229a122e76b61e3e58d4af3c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401972"
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="18132-102">SetAssemblyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="18132-102">SetAssemblyProps Method</span></span>
<span data-ttu-id="18132-103">Derleme düzeyinde özellikler atar.</span><span class="sxs-lookup"><span data-stu-id="18132-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18132-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="18132-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="18132-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="18132-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="18132-106">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="18132-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="18132-107">Özelliği tanımlar dosyası.</span><span class="sxs-lookup"><span data-stu-id="18132-107">File that defines the property.</span></span> <span data-ttu-id="18132-108">NULL olabilir `AssemblyID` ilişkisiz netmodule göstermez.</span><span class="sxs-lookup"><span data-stu-id="18132-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="18132-109">Değiştirme seçeneğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="18132-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="18132-110">Seçeneği yeni değeri.</span><span class="sxs-lookup"><span data-stu-id="18132-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="18132-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="18132-111">Return Value</span></span>  
 <span data-ttu-id="18132-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="18132-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18132-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="18132-113">Requirements</span></span>  
 <span data-ttu-id="18132-114">ALink.h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="18132-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18132-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="18132-115">See Also</span></span>  
 [<span data-ttu-id="18132-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="18132-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="18132-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="18132-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="18132-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="18132-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
