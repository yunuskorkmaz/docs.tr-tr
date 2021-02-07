---
description: 'Daha fazla bilgi edinin: SetAssemblyProps Yöntemi'
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
ms.openlocfilehash: 212d8aad22ac1cb231db46f20ff65de2339a21aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662357"
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="562b7-103">SetAssemblyProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="562b7-103">SetAssemblyProps Method</span></span>

<span data-ttu-id="562b7-104">Derleme düzeyi özellikleri atar.</span><span class="sxs-lookup"><span data-stu-id="562b7-104">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="562b7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="562b7-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="562b7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="562b7-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="562b7-107">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="562b7-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="562b7-108">Özelliği tanımlayan dosya.</span><span class="sxs-lookup"><span data-stu-id="562b7-108">File that defines the property.</span></span> <span data-ttu-id="562b7-109">`AssemblyID`İlişkisiz bir netmodule BELIRTMEZSE null olabilir.</span><span class="sxs-lookup"><span data-stu-id="562b7-109">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="562b7-110">Değiştirme seçeneğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="562b7-110">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="562b7-111">Seçeneğin yeni değeri.</span><span class="sxs-lookup"><span data-stu-id="562b7-111">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="562b7-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="562b7-112">Return Value</span></span>  

 <span data-ttu-id="562b7-113">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="562b7-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="562b7-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="562b7-114">Requirements</span></span>  

 <span data-ttu-id="562b7-115">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="562b7-115">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="562b7-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="562b7-116">See also</span></span>

- [<span data-ttu-id="562b7-117">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="562b7-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="562b7-118">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="562b7-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="562b7-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="562b7-119">ALink API</span></span>](index.md)
