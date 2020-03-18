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
ms.openlocfilehash: 17cd739ac40b43bdd4a93b83a4ab9d0d92400e2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708938"
---
# <a name="handling-com-interop-exceptions"></a><span data-ttu-id="79619-102">COM Birlikte Çalışması Özel Durumlarını İşleme</span><span class="sxs-lookup"><span data-stu-id="79619-102">Handling COM Interop Exceptions</span></span>
<span data-ttu-id="79619-103">Yönetilen ve yönetilmeyen kod, özel durumları işlemek için birlikte çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="79619-103">Managed and unmanaged code can work together to handle exceptions.</span></span> <span data-ttu-id="79619-104">Yönetilen kodda bir yöntem özel durum atarsa, ortak dil çalışma süresi bir Com nesnesine Bir HRESULT geçirebilir.</span><span class="sxs-lookup"><span data-stu-id="79619-104">If a method throws an exception in managed code, the common language runtime can pass an HRESULT to a COM object.</span></span> <span data-ttu-id="79619-105">Bir yöntem bir hata HRESULT döndürerek yönetilmeyen kod başarısız olursa, çalışma zamanı yönetilen kod tarafından yakalanmış olabilir bir özel durum atar.</span><span class="sxs-lookup"><span data-stu-id="79619-105">If a method fails in unmanaged code by returning a failure HRESULT, the runtime throws an exception that can be caught by managed code.</span></span>  
  
 <span data-ttu-id="79619-106">Çalışma süresi otomatik olarak COM interop gelen HRESULT daha özel özel durumlar alakadar eşler.</span><span class="sxs-lookup"><span data-stu-id="79619-106">The runtime automatically maps the HRESULT from COM interop to more specific exceptions.</span></span> <span data-ttu-id="79619-107">Örneğin, E_ACCESSDENIED <xref:System.UnauthorizedAccessException>olur , <xref:System.OutOfMemoryException>E_OUTOFMEMORY olur , ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="79619-107">For example, E_ACCESSDENIED becomes <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY becomes <xref:System.OutOfMemoryException>, and so on.</span></span>  
  
 <span data-ttu-id="79619-108">HRESULT özel bir sonuçsa veya çalışma zamanı bilinmiyorsa, çalışma <xref:System.Runtime.InteropServices.COMException> süresi genel bir istemciye geçer.</span><span class="sxs-lookup"><span data-stu-id="79619-108">If the HRESULT is a custom result or if it is unknown to the runtime, the runtime passes a generic <xref:System.Runtime.InteropServices.COMException> to the client.</span></span> <span data-ttu-id="79619-109">**COMException'ın** **ErrorCode** özelliği HRESULT değerini içerir.</span><span class="sxs-lookup"><span data-stu-id="79619-109">The **ErrorCode** property of the **COMException** contains the HRESULT value.</span></span>  
  
## <a name="working-with-ierrorinfo"></a><span data-ttu-id="79619-110">iErrorInfo ile çalışma</span><span class="sxs-lookup"><span data-stu-id="79619-110">Working with IErrorInfo</span></span>  
 <span data-ttu-id="79619-111">Com'dan yönetilen koda bir hata aktarıldığında, çalışma zamanı hata bilgileriyle özel durum nesnesini doldurur.</span><span class="sxs-lookup"><span data-stu-id="79619-111">When an error is passed from COM to managed code, the runtime populates the exception object with error information.</span></span> <span data-ttu-id="79619-112">IErrorInfo'u destekleyen ve HRESULTS'i döndüren COM nesneleri bu bilgileri yönetilen kod özel durumlarına sağlar.</span><span class="sxs-lookup"><span data-stu-id="79619-112">COM objects that support IErrorInfo and return HRESULTS provide this information to managed code exceptions.</span></span> <span data-ttu-id="79619-113">Örneğin, çalışma zamanı, Com hatasından özel <xref:System.Exception.Message%2A> durum özelliğine Açıklama eşler.</span><span class="sxs-lookup"><span data-stu-id="79619-113">For example, the runtime maps the Description from the COM error to the exception's <xref:System.Exception.Message%2A> property.</span></span> <span data-ttu-id="79619-114">HRESULT ek hata bilgisi sağlamazsa, çalışma süresi özel durum özelliklerinin çoğunu varsayılan değerlerle doldurur.</span><span class="sxs-lookup"><span data-stu-id="79619-114">If the HRESULT provides no additional error information, the runtime fills many of the exception's properties with default values.</span></span>  
  
 <span data-ttu-id="79619-115">Bir yöntem yönetilmeyen kodda başarısız olursa, yönetilen kod kesimine bir özel durum geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="79619-115">If a method fails in unmanaged code, an exception can be passed to a managed code segment.</span></span> <span data-ttu-id="79619-116">Konu [HRESULTS ve Özel Durumlar](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) çalışma zamanı özel durum nesneleri için HRESULTS eşler nasıl gösteren bir tablo içerir.</span><span class="sxs-lookup"><span data-stu-id="79619-116">The topic [HRESULTS and Exceptions](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) contains a table showing how HRESULTS map to runtime exception objects.</span></span>  

## <a name="see-also"></a><span data-ttu-id="79619-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79619-117">See also</span></span>

- [<span data-ttu-id="79619-118">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="79619-118">Exceptions</span></span>](index.md)
