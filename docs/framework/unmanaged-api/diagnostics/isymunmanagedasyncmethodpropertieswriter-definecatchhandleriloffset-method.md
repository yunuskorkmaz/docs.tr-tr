---
description: 'Şu konuda daha fazla bilgi edinin: ıvmunmanagedasyncmethodpropertieswriter::D efinecatch handlerılıngıgı'
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Yöntemi
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
ms.openlocfilehash: fcb2c6efa7ea83252a46a9b08cdfa7b2c14f09d1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737798"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="72520-103">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="72520-103">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>

<span data-ttu-id="72520-104">Bir zaman uyumsuz yöntemi sarmalayan derleyicinin ürettiği catch işleyicisinin Il sapmasını belirler.</span><span class="sxs-lookup"><span data-stu-id="72520-104">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="72520-105">Oluşturulan catch 'in Il kayması, Kullanıcı kodu yönteminde meydana gelse bile, Kullanıcı olmayan kod gibi catch 'i işlemek için hata ayıklayıcı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="72520-105">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="72520-106">Özellikle, bir **catch Handlerfound** özel durum olayına yanıt olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="72520-106">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72520-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72520-107">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72520-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="72520-108">Parameters</span></span>  
  
|<span data-ttu-id="72520-109">Parametre</span><span class="sxs-lookup"><span data-stu-id="72520-109">Parameter</span></span>|<span data-ttu-id="72520-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="72520-110">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="72520-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="72520-111">Return Value</span></span>  

 <span data-ttu-id="72520-112">`HRESULT` döndürür.</span><span class="sxs-lookup"><span data-stu-id="72520-112">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72520-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="72520-113">Requirements</span></span>  

 <span data-ttu-id="72520-114">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="72520-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72520-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72520-115">See also</span></span>

- [<span data-ttu-id="72520-116">ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72520-116">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)
