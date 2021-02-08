---
description: 'Şu konuda daha fazla bilgi edinin: ırivmanagedasyncmethod:: IsAsyncMethod yöntemi'
title: ISymUnmanagedAsyncMethod::IsAsyncMethod Yöntemi
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
ms.openlocfilehash: 4b151f5367bac5fd92cc8237492cad6dacfb8e88
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790262"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="4d250-103">ISymUnmanagedAsyncMethod::IsAsyncMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4d250-103">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>

<span data-ttu-id="4d250-104">Metodun zaman uyumsuz bilgilere sahip olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="4d250-104">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="4d250-105">Bu yöntem döndürürse `FALSE` , bu arabirimdeki diğer yöntemleri çağırmak geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="4d250-105">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="4d250-106">Hepsi `E_UNEXPECTED` Bu durumda döndürülür.</span><span class="sxs-lookup"><span data-stu-id="4d250-106">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d250-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4d250-107">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d250-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4d250-108">Parameters</span></span>  
  
|<span data-ttu-id="4d250-109">Parametre</span><span class="sxs-lookup"><span data-stu-id="4d250-109">Parameter</span></span>|<span data-ttu-id="4d250-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d250-110">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="4d250-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4d250-111">Return Value</span></span>  

 <span data-ttu-id="4d250-112">`HRESULT` döndürür.</span><span class="sxs-lookup"><span data-stu-id="4d250-112">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d250-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4d250-113">Requirements</span></span>  

 <span data-ttu-id="4d250-114">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4d250-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d250-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d250-115">See also</span></span>

- [<span data-ttu-id="4d250-116">ISymUnmanagedAsyncMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d250-116">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)
