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
ms.openlocfilehash: 180eb1a3129cfcd96668ecfee11947c15c5e0915
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776907"
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="69265-102">SetAssemblyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="69265-102">SetAssemblyProps Method</span></span>
<span data-ttu-id="69265-103">Derleme düzeyi özellikleri atar.</span><span class="sxs-lookup"><span data-stu-id="69265-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69265-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="69265-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="69265-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="69265-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="69265-106">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="69265-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="69265-107">Özelliği tanımlayan dosya.</span><span class="sxs-lookup"><span data-stu-id="69265-107">File that defines the property.</span></span> <span data-ttu-id="69265-108">İlişkisiz bir netmodule belirtmezse `AssemblyID` null olabilir.</span><span class="sxs-lookup"><span data-stu-id="69265-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="69265-109">Değiştirme seçeneğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="69265-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="69265-110">Seçeneğin yeni değeri.</span><span class="sxs-lookup"><span data-stu-id="69265-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69265-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="69265-111">Return Value</span></span>  
 <span data-ttu-id="69265-112">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="69265-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69265-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="69265-113">Requirements</span></span>  
 <span data-ttu-id="69265-114">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="69265-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69265-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69265-115">See also</span></span>

- [<span data-ttu-id="69265-116">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="69265-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="69265-117">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="69265-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="69265-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="69265-118">ALink API</span></span>](index.md)
