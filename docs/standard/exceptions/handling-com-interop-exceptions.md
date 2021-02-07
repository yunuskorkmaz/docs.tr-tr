---
description: 'Daha fazla bilgi edinin: COM birlikte çalışma özel durumlarını Işleme'
title: COM Birlikte Çalışması Özel Durumlarını İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- HRESULTs
- exceptions, COM interop
- COM interop, exceptions
ms.assetid: e6104aa8-8e5f-4069-b864-def85579c96c
ms.openlocfilehash: c7746f84d30dafcaf30c3d89d4319ca3fb2107d7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713292"
---
# <a name="handling-com-interop-exceptions"></a><span data-ttu-id="5cfa8-103">COM Birlikte Çalışması Özel Durumlarını İşleme</span><span class="sxs-lookup"><span data-stu-id="5cfa8-103">Handling COM Interop Exceptions</span></span>

<span data-ttu-id="5cfa8-104">Yönetilen ve yönetilmeyen kod, özel durumları işlemek için birlikte çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="5cfa8-104">Managed and unmanaged code can work together to handle exceptions.</span></span> <span data-ttu-id="5cfa8-105">Bir yöntem yönetilen kodda bir özel durum oluşturursa, ortak dil çalışma zamanı bir HRESULT 'yi bir COM nesnesine geçirebilir.</span><span class="sxs-lookup"><span data-stu-id="5cfa8-105">If a method throws an exception in managed code, the common language runtime can pass an HRESULT to a COM object.</span></span> <span data-ttu-id="5cfa8-106">Bir yöntem HRESULT hatası döndürerek yönetilmeyen kodda başarısız olursa, çalışma zamanı yönetilen kod tarafından yakalanamayan bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5cfa8-106">If a method fails in unmanaged code by returning a failure HRESULT, the runtime throws an exception that can be caught by managed code.</span></span>  
  
 <span data-ttu-id="5cfa8-107">Çalışma zamanı, HRESULT 'yi COM birlikte çalışabilirliğine özel özel durumlarla otomatik olarak eşleştirir.</span><span class="sxs-lookup"><span data-stu-id="5cfa8-107">The runtime automatically maps the HRESULT from COM interop to more specific exceptions.</span></span> <span data-ttu-id="5cfa8-108">Örneğin, E_ACCESSDENIED olur, <xref:System.UnauthorizedAccessException> e_outofmemory olur <xref:System.OutOfMemoryException> ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="5cfa8-108">For example, E_ACCESSDENIED becomes <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY becomes <xref:System.OutOfMemoryException>, and so on.</span></span>  
  
 <span data-ttu-id="5cfa8-109">HRESULT özel bir sonuçse veya çalışma zamanı için bilinmiyorsa, çalışma zamanı istemciye genel geçirir <xref:System.Runtime.InteropServices.COMException> .</span><span class="sxs-lookup"><span data-stu-id="5cfa8-109">If the HRESULT is a custom result or if it is unknown to the runtime, the runtime passes a generic <xref:System.Runtime.InteropServices.COMException> to the client.</span></span> <span data-ttu-id="5cfa8-110">**COMException** öğesinin **ErrorCode** özelliği HRESULT değerini içerir.</span><span class="sxs-lookup"><span data-stu-id="5cfa8-110">The **ErrorCode** property of the **COMException** contains the HRESULT value.</span></span>  
  
## <a name="working-with-ierrorinfo"></a><span data-ttu-id="5cfa8-111">IErrorInfo ile çalışma</span><span class="sxs-lookup"><span data-stu-id="5cfa8-111">Working with IErrorInfo</span></span>  

 <span data-ttu-id="5cfa8-112">COM 'dan yönetilen koda bir hata geçirildiğinde, çalışma zamanı özel durum nesnesini hata bilgileriyle doldurur.</span><span class="sxs-lookup"><span data-stu-id="5cfa8-112">When an error is passed from COM to managed code, the runtime populates the exception object with error information.</span></span> <span data-ttu-id="5cfa8-113">IErrorInfo ve döndürülen HRESULTS 'leri destekleyen COM nesneleri, bu bilgileri yönetilen kod özel durumlarına sağlar.</span><span class="sxs-lookup"><span data-stu-id="5cfa8-113">COM objects that support IErrorInfo and return HRESULTS provide this information to managed code exceptions.</span></span> <span data-ttu-id="5cfa8-114">Örneğin, çalışma zamanı, açıklamayı COM hatasından özel durumun <xref:System.Exception.Message%2A> özelliğine eşler.</span><span class="sxs-lookup"><span data-stu-id="5cfa8-114">For example, the runtime maps the Description from the COM error to the exception's <xref:System.Exception.Message%2A> property.</span></span> <span data-ttu-id="5cfa8-115">HRESULT ek bir hata bilgisi sunduğunda, çalışma zamanı özel durum özelliklerinin çoğunu varsayılan değerlerle doldurur.</span><span class="sxs-lookup"><span data-stu-id="5cfa8-115">If the HRESULT provides no additional error information, the runtime fills many of the exception's properties with default values.</span></span>  
  
 <span data-ttu-id="5cfa8-116">Yönetilmeyen kodda bir yöntem başarısız olursa, yönetilen bir kod kesimine özel durum geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5cfa8-116">If a method fails in unmanaged code, an exception can be passed to a managed code segment.</span></span> <span data-ttu-id="5cfa8-117">[HResults ve Exceptions](../../framework/interop/how-to-map-hresults-and-exceptions.md) konuları, HResults 'ın çalışma zamanı özel durum nesneleriyle nasıl eşlendiğini gösteren bir tablo içerir.</span><span class="sxs-lookup"><span data-stu-id="5cfa8-117">The topic [HRESULTS and Exceptions](../../framework/interop/how-to-map-hresults-and-exceptions.md) contains a table showing how HRESULTS map to runtime exception objects.</span></span>  

## <a name="see-also"></a><span data-ttu-id="5cfa8-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5cfa8-118">See also</span></span>

- [<span data-ttu-id="5cfa8-119">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="5cfa8-119">Exceptions</span></span>](index.md)
