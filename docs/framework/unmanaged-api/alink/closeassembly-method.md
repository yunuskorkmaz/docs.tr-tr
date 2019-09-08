---
title: CloseAssembly Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.CloseAssembly
- CloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseAssembly
helpviewer_keywords:
- CloseAssembly method
ms.assetid: f66a43bc-a5c5-4190-acbe-63fd27640634
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b7828c86018724bb934de99cab4617f9885fdca6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787612"
---
# <a name="closeassembly-method"></a><span data-ttu-id="23f76-102">CloseAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="23f76-102">CloseAssembly Method</span></span>
<span data-ttu-id="23f76-103">Derleme işlemlerini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="23f76-103">Finalizes assembly operations.</span></span> <span data-ttu-id="23f76-104">Yeni bir derlemeye veya ilişkisiz modüle başlamadan önce bu yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="23f76-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23f76-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="23f76-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="23f76-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="23f76-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="23f76-107">Derlemenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="23f76-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23f76-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="23f76-108">Return Value</span></span>  
 <span data-ttu-id="23f76-109">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="23f76-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23f76-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="23f76-110">Requirements</span></span>  
 <span data-ttu-id="23f76-111">ALink. h gerektirir.</span><span class="sxs-lookup"><span data-stu-id="23f76-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23f76-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23f76-112">See also</span></span>

- [<span data-ttu-id="23f76-113">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="23f76-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="23f76-114">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="23f76-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="23f76-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="23f76-115">ALink API</span></span>](index.md)
