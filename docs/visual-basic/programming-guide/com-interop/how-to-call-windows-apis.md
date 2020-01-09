---
title: "Nasıl yapılır: Windows API'larını Çağırma"
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: 9de9f0fbcca291af0b6aadfd8e3fe7033708fbc6
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347541"
---
# <a name="how-to-call-windows-apis-visual-basic"></a><span data-ttu-id="2b230-102">Nasıl yapılır: Windows API'larını Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b230-102">How to: Call Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="2b230-103">Bu örnek, User32. dll ' de `MessageBox` işlevini tanımlar ve çağırır ve sonra buna bir dize geçirir.</span><span class="sxs-lookup"><span data-stu-id="2b230-103">This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b230-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="2b230-104">Example</span></span>  
 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="2b230-105">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="2b230-105">Compile the code</span></span>  
 <span data-ttu-id="2b230-106">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="2b230-106">This example requires:</span></span>  
  
- <span data-ttu-id="2b230-107"><xref:System> ad alanına bir başvuru.</span><span class="sxs-lookup"><span data-stu-id="2b230-107">A reference to the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="2b230-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="2b230-108">Robust Programming</span></span>  
 <span data-ttu-id="2b230-109">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="2b230-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="2b230-110">Yöntem statik değil, soyut veya daha önce tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="2b230-110">The method is not static, is abstract, or has been previously defined.</span></span> <span data-ttu-id="2b230-111">Üst tür bir arabirimdir, ya da *ad* veya *DLL* uzunluğu sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="2b230-111">The parent type is an interface, or the length of *name* or *dllName* is zero.</span></span> <span data-ttu-id="2b230-112">(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="2b230-112">(<xref:System.ArgumentException>)</span></span>  
  
- <span data-ttu-id="2b230-113">Ad veya *DLL* *adı* `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="2b230-113">The *name* or *dllName* is `Nothing`.</span></span> <span data-ttu-id="2b230-114">(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="2b230-114">(<xref:System.ArgumentNullException>)</span></span>  
  
- <span data-ttu-id="2b230-115">Kapsayan tür daha önce `CreateType`kullanılarak oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="2b230-115">The containing type has been previously created using `CreateType`.</span></span> <span data-ttu-id="2b230-116">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="2b230-116">(<xref:System.InvalidOperationException>)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b230-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b230-117">See also</span></span>

- [<span data-ttu-id="2b230-118">Platform çağırma ' ye daha yakından bakış</span><span class="sxs-lookup"><span data-stu-id="2b230-118">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="2b230-119">Platform Çağırma Örnekleri</span><span class="sxs-lookup"><span data-stu-id="2b230-119">Platform Invoke Examples</span></span>](../../../framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="2b230-120">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="2b230-120">Consuming Unmanaged DLL Functions</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- <span data-ttu-id="2b230-121">[Yansıma Yayma ile bir yöntem tanımlama](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2b230-121">[Defining a Method with Reflection Emit](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span></span>
- [<span data-ttu-id="2b230-122">İzlenecek yol: Windows API'lerini Çağırma</span><span class="sxs-lookup"><span data-stu-id="2b230-122">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [<span data-ttu-id="2b230-123">COM Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="2b230-123">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)
