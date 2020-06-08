---
title: ISymUnmanagedAsyncMethod Arabirimi
ms.date: 03/30/2017
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
ms.openlocfilehash: 448ed719331469dce8f15500f14d5c1b0707ecf7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504458"
---
# <a name="isymunmanagedasyncmethod-interface"></a><span data-ttu-id="10f0d-102">ISymUnmanagedAsyncMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="10f0d-102">ISymUnmanagedAsyncMethod Interface</span></span>
<span data-ttu-id="10f0d-103">Bu arabirim, [ıvmunmanagedasyncmethodpropertieswriter arabirimini](isymunmanagedasyncmethodpropertieswriter-interface.md)tamamlayan okuma işlemi.</span><span class="sxs-lookup"><span data-stu-id="10f0d-103">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10f0d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10f0d-104">Syntax</span></span>  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="10f0d-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="10f0d-105">Methods</span></span>  
 <span data-ttu-id="10f0d-106">Bu arabirim aşağıdaki yöntemleri içerir:</span><span class="sxs-lookup"><span data-stu-id="10f0d-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="10f0d-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="10f0d-107">Method</span></span>|<span data-ttu-id="10f0d-108">Description</span><span class="sxs-lookup"><span data-stu-id="10f0d-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="10f0d-109">GetAsyncStepInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10f0d-109">GetAsyncStepInfo Method</span></span>](isymunmanagedasyncmethod-getasyncstepinfo-method.md)|<span data-ttu-id="10f0d-110">Bkz. [DefineAsyncStepInfo Yöntemi](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="10f0d-110">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="10f0d-111">GetAsyncStepInfoCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10f0d-111">GetAsyncStepInfoCount Method</span></span>](isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|<span data-ttu-id="10f0d-112">Bkz. [DefineAsyncStepInfo Yöntemi](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="10f0d-112">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="10f0d-113">GetCatchHandlerILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10f0d-113">GetCatchHandlerILOffset Method</span></span>](isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|<span data-ttu-id="10f0d-114">Bkz. [Definecatch Handlerılsapmasını metodu](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="10f0d-114">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="10f0d-115">GetKickoffMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10f0d-115">GetKickoffMethod Method</span></span>](isymunmanagedasyncmethod-getkickoffmethod-method.md)|<span data-ttu-id="10f0d-116">Bkz. [DefineKickoffMethod Yöntemi](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="10f0d-116">See [DefineKickoffMethod Method](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>|  
|[<span data-ttu-id="10f0d-117">HasCatchHandlerILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10f0d-117">HasCatchHandlerILOffset Method</span></span>](isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|<span data-ttu-id="10f0d-118">Bkz. [Definecatch Handlerılsapmasını metodu](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="10f0d-118">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="10f0d-119">IsAsyncMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10f0d-119">IsAsyncMethod Method</span></span>](isymunmanagedasyncmethod-isasyncmethod-method.md)|<span data-ttu-id="10f0d-120">Metodun zaman uyumsuz bilgilere sahip olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="10f0d-120">Checks if the method has async information or not.</span></span><br /><br /> <span data-ttu-id="10f0d-121">Bu yöntem döndürürse `FALSE` , bu arabirimdeki diğer yöntemleri çağırmak geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="10f0d-121">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="10f0d-122">Hepsi `E_UNEXPECTED` Bu durumda döndürülür.</span><span class="sxs-lookup"><span data-stu-id="10f0d-122">They will all return `E_UNEXPECTED` in this case.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="10f0d-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="10f0d-123">Requirements</span></span>  
 <span data-ttu-id="10f0d-124">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="10f0d-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10f0d-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10f0d-125">See also</span></span>

- [<span data-ttu-id="10f0d-126">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="10f0d-126">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
