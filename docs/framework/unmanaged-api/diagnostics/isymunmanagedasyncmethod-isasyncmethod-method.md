---
title: ISymUnmanagedAsyncMethod::IsAsyncMethod Yöntemi
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
ms.openlocfilehash: af02aba1a0d390c103e8c6108f90b93fe2a98ff3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707158"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="b1747-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1747-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>

<span data-ttu-id="b1747-103">Metodun zaman uyumsuz bilgilere sahip olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="b1747-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="b1747-104">Bu yöntem döndürürse `FALSE` , bu arabirimdeki diğer yöntemleri çağırmak geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="b1747-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="b1747-105">Hepsi `E_UNEXPECTED` Bu durumda döndürülür.</span><span class="sxs-lookup"><span data-stu-id="b1747-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1747-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b1747-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1747-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b1747-107">Parameters</span></span>  
  
|<span data-ttu-id="b1747-108">Parametre</span><span class="sxs-lookup"><span data-stu-id="b1747-108">Parameter</span></span>|<span data-ttu-id="b1747-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1747-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="b1747-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b1747-110">Return Value</span></span>  

 <span data-ttu-id="b1747-111">`HRESULT` döndürür.</span><span class="sxs-lookup"><span data-stu-id="b1747-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1747-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b1747-112">Requirements</span></span>  

 <span data-ttu-id="b1747-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b1747-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1747-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1747-114">See also</span></span>

- [<span data-ttu-id="b1747-115">ISymUnmanagedAsyncMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1747-115">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)
