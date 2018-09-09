---
title: COM Birlikte Çalışması Özel Durumlarını İşleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- HRESULTs
- exceptions, COM interop
- COM interop, exceptions
ms.assetid: e6104aa8-8e5f-4069-b864-def85579c96c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a17752257589ea4ee4d9e58182d4448f02f6460
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44225207"
---
# <a name="handling-com-interop-exceptions"></a><span data-ttu-id="cfaf9-102">COM Birlikte Çalışması Özel Durumlarını İşleme</span><span class="sxs-lookup"><span data-stu-id="cfaf9-102">Handling COM Interop Exceptions</span></span>
<span data-ttu-id="cfaf9-103">Yönetilen ve yönetilmeyen kod özel durumları işlemek için birlikte çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="cfaf9-103">Managed and unmanaged code can work together to handle exceptions.</span></span> <span data-ttu-id="cfaf9-104">Bir yöntem, yönetilen kodda bir özel durum oluşturursa, ortak dil çalışma zamanı için bir COM nesnesi HRESULT geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cfaf9-104">If a method throws an exception in managed code, the common language runtime can pass an HRESULT to a COM object.</span></span> <span data-ttu-id="cfaf9-105">Bir hata HRESULT döndüren bir yöntemi yönetilmeyen kodda başarısız olursa, çalışma zamanı, yönetilen kod tarafından yakalanan özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cfaf9-105">If a method fails in unmanaged code by returning a failure HRESULT, the runtime throws an exception that can be caught by managed code.</span></span>  
  
 <span data-ttu-id="cfaf9-106">Çalışma zamanı, COM birlikte çalışma HRESULT daha ayrıntılı özel durumlar için otomatik olarak eşler.</span><span class="sxs-lookup"><span data-stu-id="cfaf9-106">The runtime automatically maps the HRESULT from COM interop to more specific exceptions.</span></span> <span data-ttu-id="cfaf9-107">Örneğin, E_ACCESSDENIED olur <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY olur <xref:System.OutOfMemoryException>ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="cfaf9-107">For example, E_ACCESSDENIED becomes <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY becomes <xref:System.OutOfMemoryException>, and so on.</span></span>  
  
 <span data-ttu-id="cfaf9-108">HRESULT özel bir sonuç ise veya çalışma zamanı bilinmiyorsa, genel çalışma geçirir <xref:System.Runtime.InteropServices.COMException> istemciye.</span><span class="sxs-lookup"><span data-stu-id="cfaf9-108">If the HRESULT is a custom result or if it is unknown to the runtime, the runtime passes a generic <xref:System.Runtime.InteropServices.COMException> to the client.</span></span> <span data-ttu-id="cfaf9-109">**ErrorCode** özelliği **COMException** HRESULT değerini içerir.</span><span class="sxs-lookup"><span data-stu-id="cfaf9-109">The **ErrorCode** property of the **COMException** contains the HRESULT value.</span></span>  
  
## <a name="working-with-ierrorinfo"></a><span data-ttu-id="cfaf9-110">IErrorInfo ile çalışma</span><span class="sxs-lookup"><span data-stu-id="cfaf9-110">Working with IErrorInfo</span></span>  
 <span data-ttu-id="cfaf9-111">Yönetilen kod için hata COM'dan geçirildiğinde, çalışma zamanı hata bilgilerini özel durum nesnesiyle doldurur.</span><span class="sxs-lookup"><span data-stu-id="cfaf9-111">When an error is passed from COM to managed code, the runtime populates the exception object with error information.</span></span> <span data-ttu-id="cfaf9-112">IErrorInfo destekleyen ve HRESULTS dönüş COM nesneleri, yönetilen kod özel durumlar için bu bilgileri sağlayın.</span><span class="sxs-lookup"><span data-stu-id="cfaf9-112">COM objects that support IErrorInfo and return HRESULTS provide this information to managed code exceptions.</span></span> <span data-ttu-id="cfaf9-113">Örneğin, çalışma zamanı özel durumun COM hata açıklamasını eşler <xref:System.Exception.Message%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="cfaf9-113">For example, the runtime maps the Description from the COM error to the exception's <xref:System.Exception.Message%2A> property.</span></span> <span data-ttu-id="cfaf9-114">HRESULT ek hata bilgisi sağlıyorsa, çalışma zamanının birçok özel durumun özellikleri varsayılan değerlerle doldurur.</span><span class="sxs-lookup"><span data-stu-id="cfaf9-114">If the HRESULT provides no additional error information, the runtime fills many of the exception's properties with default values.</span></span>  
  
 <span data-ttu-id="cfaf9-115">Yönetilmeyen kodda bir yöntem başarısız olursa, bir özel durum için bir yönetilen kod kesimi geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="cfaf9-115">If a method fails in unmanaged code, an exception can be passed to a managed code segment.</span></span> <span data-ttu-id="cfaf9-116">Konu [HRESULTS ve özel durumları](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) HRESULTS çalışma zamanı özel durum nesnelere nasıl eşleştiğini gösteren bir tablo içeriyor.</span><span class="sxs-lookup"><span data-stu-id="cfaf9-116">The topic [HRESULTS and Exceptions](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) contains a table showing how HRESULTS map to runtime exception objects.</span></span>  

## <a name="see-also"></a><span data-ttu-id="cfaf9-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfaf9-117">See also</span></span>

- [<span data-ttu-id="cfaf9-118">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="cfaf9-118">Exceptions</span></span>](index.md)
