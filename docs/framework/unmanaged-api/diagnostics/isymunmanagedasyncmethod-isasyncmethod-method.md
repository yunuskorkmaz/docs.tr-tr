---
title: ISymUnmanagedAsyncMethod::IsAsyncMethod Yöntemi
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
ms.openlocfilehash: 0ea4c21e9e6a49d7bbbad5e1853598c440cd6410
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129207"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="fd71b-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fd71b-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="fd71b-103">Metodun zaman uyumsuz bilgilere sahip olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="fd71b-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="fd71b-104">Bu yöntem `FALSE` döndürürse, bu arabirimdeki diğer yöntemleri çağırmak geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="fd71b-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="fd71b-105">Bu durumda `E_UNEXPECTED` hepsi döndürülür.</span><span class="sxs-lookup"><span data-stu-id="fd71b-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd71b-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fd71b-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd71b-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fd71b-107">Parameters</span></span>  
  
|<span data-ttu-id="fd71b-108">Parametre</span><span class="sxs-lookup"><span data-stu-id="fd71b-108">Parameter</span></span>|<span data-ttu-id="fd71b-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd71b-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="fd71b-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fd71b-110">Return Value</span></span>  
 <span data-ttu-id="fd71b-111">`HRESULT`döndürür.</span><span class="sxs-lookup"><span data-stu-id="fd71b-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd71b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fd71b-112">Requirements</span></span>  
 <span data-ttu-id="fd71b-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="fd71b-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd71b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd71b-114">See also</span></span>

- [<span data-ttu-id="fd71b-115">ISymUnmanagedAsyncMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd71b-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
