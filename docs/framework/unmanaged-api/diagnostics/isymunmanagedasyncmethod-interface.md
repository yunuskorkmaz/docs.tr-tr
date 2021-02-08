---
description: 'Şu konuda daha fazla bilgi edinin: ırivmanagedasyncmethod arabirimi'
title: ISymUnmanagedAsyncMethod Arabirimi
ms.date: 03/30/2017
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
ms.openlocfilehash: cb3120464224137dfdcff4f13ca4aee82ef4d89e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790275"
---
# <a name="isymunmanagedasyncmethod-interface"></a><span data-ttu-id="5d1c0-103">ISymUnmanagedAsyncMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d1c0-103">ISymUnmanagedAsyncMethod Interface</span></span>

<span data-ttu-id="5d1c0-104">Bu arabirim, [ıvmunmanagedasyncmethodpropertieswriter arabirimini](isymunmanagedasyncmethodpropertieswriter-interface.md)tamamlayan okuma işlemi.</span><span class="sxs-lookup"><span data-stu-id="5d1c0-104">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d1c0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5d1c0-105">Syntax</span></span>  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="5d1c0-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5d1c0-106">Methods</span></span>  

 <span data-ttu-id="5d1c0-107">Bu arabirim aşağıdaki yöntemleri içerir:</span><span class="sxs-lookup"><span data-stu-id="5d1c0-107">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="5d1c0-108">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5d1c0-108">Method</span></span>|<span data-ttu-id="5d1c0-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d1c0-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5d1c0-110">GetAsyncStepInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d1c0-110">GetAsyncStepInfo Method</span></span>](isymunmanagedasyncmethod-getasyncstepinfo-method.md)|<span data-ttu-id="5d1c0-111">Bkz. [DefineAsyncStepInfo Yöntemi](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="5d1c0-111">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="5d1c0-112">GetAsyncStepInfoCount Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d1c0-112">GetAsyncStepInfoCount Method</span></span>](isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|<span data-ttu-id="5d1c0-113">Bkz. [DefineAsyncStepInfo Yöntemi](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="5d1c0-113">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="5d1c0-114">GetCatchHandlerILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d1c0-114">GetCatchHandlerILOffset Method</span></span>](isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|<span data-ttu-id="5d1c0-115">Bkz. [Definecatch Handlerılsapmasını metodu](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="5d1c0-115">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="5d1c0-116">GetKickoffMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d1c0-116">GetKickoffMethod Method</span></span>](isymunmanagedasyncmethod-getkickoffmethod-method.md)|<span data-ttu-id="5d1c0-117">Bkz. [DefineKickoffMethod Yöntemi](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="5d1c0-117">See [DefineKickoffMethod Method](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>|  
|[<span data-ttu-id="5d1c0-118">HasCatchHandlerILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d1c0-118">HasCatchHandlerILOffset Method</span></span>](isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|<span data-ttu-id="5d1c0-119">Bkz. [Definecatch Handlerılsapmasını metodu](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="5d1c0-119">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="5d1c0-120">IsAsyncMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d1c0-120">IsAsyncMethod Method</span></span>](isymunmanagedasyncmethod-isasyncmethod-method.md)|<span data-ttu-id="5d1c0-121">Metodun zaman uyumsuz bilgilere sahip olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="5d1c0-121">Checks if the method has async information or not.</span></span><br /><br /> <span data-ttu-id="5d1c0-122">Bu yöntem döndürürse `FALSE` , bu arabirimdeki diğer yöntemleri çağırmak geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="5d1c0-122">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="5d1c0-123">Hepsi `E_UNEXPECTED` Bu durumda döndürülür.</span><span class="sxs-lookup"><span data-stu-id="5d1c0-123">They will all return `E_UNEXPECTED` in this case.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5d1c0-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d1c0-124">Requirements</span></span>  

 <span data-ttu-id="5d1c0-125">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="5d1c0-125">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d1c0-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d1c0-126">See also</span></span>

- [<span data-ttu-id="5d1c0-127">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5d1c0-127">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
