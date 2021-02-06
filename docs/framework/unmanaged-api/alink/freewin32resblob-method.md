---
description: 'Daha fazla bilgi edinin: FreeWin32ResBlob Yöntemi'
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
ms.openlocfilehash: 56c83632b623eec76e8e2d24030c79a8262f506f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637951"
---
# <a name="freewin32resblob-method"></a><span data-ttu-id="61086-103">FreeWin32ResBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="61086-103">FreeWin32ResBlob Method</span></span>

<span data-ttu-id="61086-104">Win32 kaynak blobu ve ilişkili kaynakları yayınlar.</span><span class="sxs-lookup"><span data-stu-id="61086-104">Releases the Win32 resource blob and associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61086-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="61086-105">Syntax</span></span>  
  
```cpp  
HRESULT FreeWin32ResBlob(  
    const void** ppResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="61086-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="61086-106">Parameters</span></span>  

 `ppResBlob`  
 <span data-ttu-id="61086-107">Yayımlanacak kaynak blobu.</span><span class="sxs-lookup"><span data-stu-id="61086-107">The resource blob to be released.</span></span> <span data-ttu-id="61086-108">Bu yöntem, blob işaretçisini NULL 'a atar.</span><span class="sxs-lookup"><span data-stu-id="61086-108">This method assigns the blob pointer to NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61086-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="61086-109">Return Value</span></span>  

 <span data-ttu-id="61086-110">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="61086-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61086-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="61086-111">Requirements</span></span>  

 <span data-ttu-id="61086-112">ALink. h gerektirir</span><span class="sxs-lookup"><span data-stu-id="61086-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61086-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61086-113">See also</span></span>

- [<span data-ttu-id="61086-114">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="61086-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="61086-115">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="61086-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="61086-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="61086-116">ALink API</span></span>](index.md)
