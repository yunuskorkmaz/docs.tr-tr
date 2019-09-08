---
title: FreeWin32ResBlob Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.FreeWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- FreeWin32ResBlob
helpviewer_keywords:
- FreeWin32ResBlob method
ms.assetid: d941102b-2679-4c49-b15e-c0fc9c53e11f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ea0fbceb1e778a2f26e0625a337b803f417b59eb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777253"
---
# <a name="freewin32resblob-method"></a><span data-ttu-id="e942b-102">FreeWin32ResBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e942b-102">FreeWin32ResBlob Method</span></span>
<span data-ttu-id="e942b-103">Win32 kaynak blobu ve ilişkili kaynakları yayınlar.</span><span class="sxs-lookup"><span data-stu-id="e942b-103">Releases the Win32 resource blob and associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e942b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e942b-104">Syntax</span></span>  
  
```cpp  
HRESULT FreeWin32ResBlob(  
    const void** ppResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="e942b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e942b-105">Parameters</span></span>  
 `ppResBlob`  
 <span data-ttu-id="e942b-106">Yayımlanacak kaynak blobu.</span><span class="sxs-lookup"><span data-stu-id="e942b-106">The resource blob to be released.</span></span> <span data-ttu-id="e942b-107">Bu yöntem, blob işaretçisini NULL 'a atar.</span><span class="sxs-lookup"><span data-stu-id="e942b-107">This method assigns the blob pointer to NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e942b-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e942b-108">Return Value</span></span>  
 <span data-ttu-id="e942b-109">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="e942b-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e942b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e942b-110">Requirements</span></span>  
 <span data-ttu-id="e942b-111">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="e942b-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e942b-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e942b-112">See also</span></span>

- [<span data-ttu-id="e942b-113">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e942b-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="e942b-114">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e942b-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="e942b-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="e942b-115">ALink API</span></span>](index.md)
