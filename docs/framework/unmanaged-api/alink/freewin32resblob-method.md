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
ms.openlocfilehash: 196a57b3e919ea4ccbc0b91e5b6f281ad3c30b62
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789889"
---
# <a name="freewin32resblob-method"></a><span data-ttu-id="0c4df-102">FreeWin32ResBlob Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0c4df-102">FreeWin32ResBlob Method</span></span>
<span data-ttu-id="0c4df-103">Win32 kaynak blob ve ilişkili kaynakları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="0c4df-103">Releases the Win32 resource blob and associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c4df-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0c4df-104">Syntax</span></span>  
  
```  
HRESULT FreeWin32ResBlob(  
    const void** ppResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c4df-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0c4df-105">Parameters</span></span>  
 `ppResBlob`  
 <span data-ttu-id="0c4df-106">Kaynak blob'yayımlanacak.</span><span class="sxs-lookup"><span data-stu-id="0c4df-106">The resource blob to be released.</span></span> <span data-ttu-id="0c4df-107">Bu yöntem, blob işaretçiyi NULL olarak atar.</span><span class="sxs-lookup"><span data-stu-id="0c4df-107">This method assigns the blob pointer to NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0c4df-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0c4df-108">Return Value</span></span>  
 <span data-ttu-id="0c4df-109">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="0c4df-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c4df-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0c4df-110">Requirements</span></span>  
 <span data-ttu-id="0c4df-111">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="0c4df-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c4df-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c4df-112">See also</span></span>

- [<span data-ttu-id="0c4df-113">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c4df-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="0c4df-114">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0c4df-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="0c4df-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="0c4df-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
