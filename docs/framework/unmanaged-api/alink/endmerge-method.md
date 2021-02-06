---
description: 'Daha fazla bilgi edinin: EndMerge yöntemi'
title: EndMerge Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.EndMerge
- EndMerge
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EndMerge
helpviewer_keywords:
- EndMerge method
ms.assetid: 1d03bb15-a2c8-4a04-8fc6-b126c89c3778
topic_type:
- apiref
ms.openlocfilehash: aac23d6d87f3fe74c1094bdd4a7f9c9f7f3fa7cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638164"
---
# <a name="endmerge-method"></a><span data-ttu-id="4304a-103">EndMerge Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4304a-103">EndMerge Method</span></span>

<span data-ttu-id="4304a-104">Tüm özel özniteliklerin yayma kapsamıyla birleştirildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4304a-104">Indicates that all custom attributes have been merged into the emit scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4304a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4304a-105">Syntax</span></span>  
  
```cpp  
HRESULT EndMerge(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="4304a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4304a-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="4304a-107">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4304a-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4304a-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4304a-108">Return Value</span></span>  

 <span data-ttu-id="4304a-109">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="4304a-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4304a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4304a-110">Requirements</span></span>  

 <span data-ttu-id="4304a-111">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="4304a-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4304a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4304a-112">See also</span></span>

- [<span data-ttu-id="4304a-113">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4304a-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="4304a-114">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4304a-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="4304a-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="4304a-115">ALink API</span></span>](index.md)
