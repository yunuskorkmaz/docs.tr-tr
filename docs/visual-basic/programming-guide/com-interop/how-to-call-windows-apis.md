---
title: "Nasıl yapılır: Windows API'lerini Çağırma"
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: 2c3bb599b79575180eb2b0ec89453f01901f94c0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396849"
---
# <a name="how-to-call-windows-apis-visual-basic"></a><span data-ttu-id="e786d-102">Nasıl yapılır: Windows API'larını Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e786d-102">How to: Call Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="e786d-103">Bu örnek, `MessageBox` User32. dll ' de işlevi tanımlar ve çağırır ve sonra buna bir dize geçirir.</span><span class="sxs-lookup"><span data-stu-id="e786d-103">This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e786d-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e786d-104">Example</span></span>  
 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="e786d-105">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="e786d-105">Compile the code</span></span>  
 <span data-ttu-id="e786d-106">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="e786d-106">This example requires:</span></span>  
  
- <span data-ttu-id="e786d-107"><xref:System>Ad alanına başvuru.</span><span class="sxs-lookup"><span data-stu-id="e786d-107">A reference to the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e786d-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="e786d-108">Robust Programming</span></span>  
 <span data-ttu-id="e786d-109">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="e786d-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="e786d-110">Yöntem statik değil, soyut veya daha önce tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="e786d-110">The method is not static, is abstract, or has been previously defined.</span></span> <span data-ttu-id="e786d-111">Üst tür bir arabirimdir, ya da *ad* veya *DLL* uzunluğu sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="e786d-111">The parent type is an interface, or the length of *name* or *dllName* is zero.</span></span> <span data-ttu-id="e786d-112">(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="e786d-112">(<xref:System.ArgumentException>)</span></span>  
  
- <span data-ttu-id="e786d-113">Ad veya *DLL* *adı* `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="e786d-113">The *name* or *dllName* is `Nothing`.</span></span> <span data-ttu-id="e786d-114">(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="e786d-114">(<xref:System.ArgumentNullException>)</span></span>  
  
- <span data-ttu-id="e786d-115">İçeren tür önceden kullanılarak oluşturulmuştur `CreateType` .</span><span class="sxs-lookup"><span data-stu-id="e786d-115">The containing type has been previously created using `CreateType`.</span></span> <span data-ttu-id="e786d-116">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="e786d-116">(<xref:System.InvalidOperationException>)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e786d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e786d-117">See also</span></span>

- [<span data-ttu-id="e786d-118">Platform çağırma ' ye daha yakından bakış</span><span class="sxs-lookup"><span data-stu-id="e786d-118">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="e786d-119">Platform Çağırma Örnekleri</span><span class="sxs-lookup"><span data-stu-id="e786d-119">Platform Invoke Examples</span></span>](../../../framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="e786d-120">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="e786d-120">Consuming Unmanaged DLL Functions</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- <span data-ttu-id="e786d-121">[Yansıma Yayma ile bir yöntem tanımlama](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e786d-121">[Defining a Method with Reflection Emit](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span></span>
- [<span data-ttu-id="e786d-122">İzlenecek yol: Windows API'lerini Çağırma</span><span class="sxs-lookup"><span data-stu-id="e786d-122">Walkthrough: Calling Windows APIs</span></span>](walkthrough-calling-windows-apis.md)
- [<span data-ttu-id="e786d-123">COM birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="e786d-123">COM Interop</span></span>](index.md)
