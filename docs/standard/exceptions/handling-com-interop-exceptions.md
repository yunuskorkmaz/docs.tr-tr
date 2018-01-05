---
title: "COM Birlikte Çalışması Özel Durumlarını İşleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: error-reference
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- HRESULTs
- exceptions, COM interop
- COM interop, exceptions
ms.assetid: e6104aa8-8e5f-4069-b864-def85579c96c
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e894d07e77b929b1ea22df2d34e542544ec3b1f3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="handling-com-interop-exceptions"></a><span data-ttu-id="cf268-102">COM Birlikte Çalışması Özel Durumlarını İşleme</span><span class="sxs-lookup"><span data-stu-id="cf268-102">Handling COM Interop Exceptions</span></span>
<span data-ttu-id="cf268-103">Yönetilen ve yönetilmeyen kod birlikte özel durumları işleme çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf268-103">Managed and unmanaged code can work together to handle exceptions.</span></span> <span data-ttu-id="cf268-104">Bir yöntem yönetilen kodda bir özel durum oluşturursa, ortak dil çalışma zamanı için bir COM nesnesi HRESULT geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf268-104">If a method throws an exception in managed code, the common language runtime can pass an HRESULT to a COM object.</span></span> <span data-ttu-id="cf268-105">HRESULT hata döndürerek yönetilmeyen kodunda bir yöntem başarısız olursa, çalışma zamanı tarafından yönetilen kod görevinde bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cf268-105">If a method fails in unmanaged code by returning a failure HRESULT, the runtime throws an exception that can be caught by managed code.</span></span>  
  
 <span data-ttu-id="cf268-106">Çalışma zamanı COM birlikte çalışma HRESULT ayrıntılı özel durumlar otomatik olarak eşlenir.</span><span class="sxs-lookup"><span data-stu-id="cf268-106">The runtime automatically maps the HRESULT from COM interop to more specific exceptions.</span></span> <span data-ttu-id="cf268-107">Örneğin, E_ACCESSDENIED hale <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY hale <xref:System.OutOfMemoryException>ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="cf268-107">For example, E_ACCESSDENIED becomes <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY becomes <xref:System.OutOfMemoryException>, and so on.</span></span>  
  
 <span data-ttu-id="cf268-108">Özel bir sonuç HRESULT ise veya çalışma zamanına bilinmiyorsa, çalışma zamanı genel geçirir <xref:System.Runtime.InteropServices.COMException> istemciye.</span><span class="sxs-lookup"><span data-stu-id="cf268-108">If the HRESULT is a custom result or if it is unknown to the runtime, the runtime passes a generic <xref:System.Runtime.InteropServices.COMException> to the client.</span></span> <span data-ttu-id="cf268-109">**ErrorCode** özelliği **COMException** HRESULT değeri içerir.</span><span class="sxs-lookup"><span data-stu-id="cf268-109">The **ErrorCode** property of the **COMException** contains the HRESULT value.</span></span>  
  
## <a name="working-with-ierrorinfo"></a><span data-ttu-id="cf268-110">IErrorInfo ile çalışma</span><span class="sxs-lookup"><span data-stu-id="cf268-110">Working with IErrorInfo</span></span>  
 <span data-ttu-id="cf268-111">Bir hata, yönetilen kod için COM geçirildiğinde, çalışma zamanı özel durum nesnesi hata bilgilerle doldurur.</span><span class="sxs-lookup"><span data-stu-id="cf268-111">When an error is passed from COM to managed code, the runtime populates the exception object with error information.</span></span> <span data-ttu-id="cf268-112">IErrorInfo destekleyen ve HRESULTS dönüş COM nesneleri yönetilen kod özel durumlar için bu bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf268-112">COM objects that support IErrorInfo and return HRESULTS provide this information to managed code exceptions.</span></span> <span data-ttu-id="cf268-113">Örneğin, çalışma zamanı özel durumun COM hatadan açıklamayı eşlemeleri <xref:System.Exception.Message%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="cf268-113">For example, the runtime maps the Description from the COM error to the exception's <xref:System.Exception.Message%2A> property.</span></span> <span data-ttu-id="cf268-114">HRESULT ek hata bilgisi sağlarsa, çalışma zamanı birçok özel durumun özellikleri varsayılan değerlerle doldurur.</span><span class="sxs-lookup"><span data-stu-id="cf268-114">If the HRESULT provides no additional error information, the runtime fills many of the exception's properties with default values.</span></span>  
  
 <span data-ttu-id="cf268-115">Yönetilmeyen kod içinde bir yöntem başarısız olursa, bir özel durum bir yönetilen kod kesimi geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="cf268-115">If a method fails in unmanaged code, an exception can be passed to a managed code segment.</span></span> <span data-ttu-id="cf268-116">Konu [HRESULTS ve özel durumları](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) nasıl HRESULTS çalışma zamanı özel durum nesnelere eşleme gösteren bir tablo içeriyor.</span><span class="sxs-lookup"><span data-stu-id="cf268-116">The topic [HRESULTS and Exceptions](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) contains a table showing how HRESULTS map to runtime exception objects.</span></span>  

## <a name="see-also"></a><span data-ttu-id="cf268-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cf268-117">See Also</span></span>
[<span data-ttu-id="cf268-118">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="cf268-118">Exceptions</span></span>](index.md) 
