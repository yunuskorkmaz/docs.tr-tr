---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Yöntemi
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
ms.openlocfilehash: 58dde2fcce3f4bf578907171e5b575c30c678cfc
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441779"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="f4ed1-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4ed1-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="f4ed1-103">Bir zaman uyumsuz yöntemi sarmalayan derleyicinin ürettiği catch işleyicisinin Il sapmasını belirler.</span><span class="sxs-lookup"><span data-stu-id="f4ed1-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="f4ed1-104">Oluşturulan catch 'in Il kayması, Kullanıcı kodu yönteminde meydana gelse bile, Kullanıcı olmayan kod gibi catch 'i işlemek için hata ayıklayıcı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f4ed1-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="f4ed1-105">Özellikle, bir **catch Handlerfound** özel durum olayına yanıt olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f4ed1-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4ed1-106">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f4ed1-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4ed1-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f4ed1-107">Parameters</span></span>  
  
|<span data-ttu-id="f4ed1-108">Parametre</span><span class="sxs-lookup"><span data-stu-id="f4ed1-108">Parameter</span></span>|<span data-ttu-id="f4ed1-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4ed1-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="f4ed1-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f4ed1-110">Return Value</span></span>  
 <span data-ttu-id="f4ed1-111">`HRESULT` döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4ed1-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4ed1-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f4ed1-112">Requirements</span></span>  
 <span data-ttu-id="f4ed1-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f4ed1-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4ed1-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4ed1-114">See also</span></span>

- [<span data-ttu-id="f4ed1-115">ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f4ed1-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)
