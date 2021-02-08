---
description: 'Şu konuda daha fazla bilgi edinin: ırivmanagedasyncmethodpropertieswriter arabirimi'
title: ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi
ms.date: 03/30/2017
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
ms.openlocfilehash: 4c8b1bc037485e22160af28b59d751859a157499
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790197"
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a><span data-ttu-id="95a34-103">ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="95a34-103">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>

<span data-ttu-id="95a34-104">Her yöntem sembolü için isteğe bağlı zaman uyumsuz yöntem bilgilerini tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="95a34-104">Allows you to define optional async method information for each method symbol.</span></span> <span data-ttu-id="95a34-105">Her zaman açık bir yöntemle kullanın; diğer bir deyişle, [OpenMethod yöntemi](isymunmanagedwriter-openmethod-method.md) ve [CloseMethod yöntemi](isymunmanagedwriter-closemethod-method.md)çağrıları arasında.</span><span class="sxs-lookup"><span data-stu-id="95a34-105">Always use with an opened method; that is, between calls to the [OpenMethod Method](isymunmanagedwriter-openmethod-method.md) and the [CloseMethod Method](isymunmanagedwriter-closemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95a34-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="95a34-106">Syntax</span></span>  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="95a34-107">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="95a34-107">Methods</span></span>  

 <span data-ttu-id="95a34-108">Bu arabirim aşağıdaki yöntemleri içerir:</span><span class="sxs-lookup"><span data-stu-id="95a34-108">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="95a34-109">Yöntem</span><span class="sxs-lookup"><span data-stu-id="95a34-109">Method</span></span>|<span data-ttu-id="95a34-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="95a34-110">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="95a34-111">DefineAsyncStepInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="95a34-111">DefineAsyncStepInfo Method</span></span>](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|<span data-ttu-id="95a34-112">Geçerli yöntemde zaman uyumsuz await işlemleri grubunu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="95a34-112">Define a group of async await operations in the current method.</span></span><br /><br /> <span data-ttu-id="95a34-113">Her bir yield boşluğu bir await 'ın dönüş yönergesiyle eşleşir ve potansiyel bir verimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="95a34-113">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="95a34-114">Her bir `breakpointMethod` / `breakpointOffset` çift zaman uyumsuz işlemin hangi noktada sürdürüleceği tanımlar; farklı bir yöntemde olabilir.</span><span class="sxs-lookup"><span data-stu-id="95a34-114">Each `breakpointMethod`/`breakpointOffset` pair identifies where the asynchronous operation will resume; it may be in a different method.</span></span>|  
|[<span data-ttu-id="95a34-115">DefineCatchHandlerILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="95a34-115">DefineCatchHandlerILOffset Method</span></span>](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|<span data-ttu-id="95a34-116">Bir zaman uyumsuz yöntemi sarmalayan derleyicinin ürettiği catch işleyicisinin Il sapmasını belirler.</span><span class="sxs-lookup"><span data-stu-id="95a34-116">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span><br /><br /> <span data-ttu-id="95a34-117">Oluşturulan catch 'in Il kayması, hata ayıklayıcı tarafından, Kullanıcı kodu yönteminde meydana gelse bile, Kullanıcı olmayan kod gibi catch 'i işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="95a34-117">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code, even though it may occur in a user code method.</span></span> <span data-ttu-id="95a34-118">Özellikle, bir **catch Handlerfound** özel durum olayına yanıt olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="95a34-118">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>|  
|[<span data-ttu-id="95a34-119">DefineKickoffMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="95a34-119">DefineKickoffMethod Method</span></span>](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|<span data-ttu-id="95a34-120">Zaman uyumsuz işlemi başlatan başlangıç yöntemini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="95a34-120">Sets the starting method that initiates the async operation.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="95a34-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="95a34-121">Requirements</span></span>  

 <span data-ttu-id="95a34-122">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="95a34-122">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95a34-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95a34-123">See also</span></span>

- [<span data-ttu-id="95a34-124">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="95a34-124">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
