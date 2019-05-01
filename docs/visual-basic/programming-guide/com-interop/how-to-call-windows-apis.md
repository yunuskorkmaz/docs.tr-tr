---
title: "Nasıl yapılır: (Visual Basic) Windows API'lerini çağırma"
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: e7b76495b83cb9a1dfe7629a1d82695d2046eac2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61818722"
---
# <a name="how-to-call-windows-apis-visual-basic"></a><span data-ttu-id="28050-102">Nasıl yapılır: (Visual Basic) Windows API'lerini çağırma</span><span class="sxs-lookup"><span data-stu-id="28050-102">How to: Call Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="28050-103">Bu örnekte, tanımlar ve çağrı `MessageBox` user32.dll işlevi ve bir dize geçirir.</span><span class="sxs-lookup"><span data-stu-id="28050-103">This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28050-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="28050-104">Example</span></span>  
 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="28050-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="28050-105">Compiling the Code</span></span>  
 <span data-ttu-id="28050-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="28050-106">This example requires:</span></span>  
  
- <span data-ttu-id="28050-107">Bir başvuru <xref:System> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="28050-107">A reference to the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="28050-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="28050-108">Robust Programming</span></span>  
 <span data-ttu-id="28050-109">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="28050-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="28050-110">Yöntem statik değil, Özet veya önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="28050-110">The method is not static, is abstract, or has been previously defined.</span></span> <span data-ttu-id="28050-111">Üst türü bir arabirim veya uzunluğu olan *adı* veya *dll* sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="28050-111">The parent type is an interface, or the length of *name* or *dllName* is zero.</span></span> <span data-ttu-id="28050-112">(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="28050-112">(<xref:System.ArgumentException>)</span></span>  
  
- <span data-ttu-id="28050-113">*Adı* veya *dll* olduğu `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="28050-113">The *name* or *dllName* is `Nothing`.</span></span> <span data-ttu-id="28050-114">(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="28050-114">(<xref:System.ArgumentNullException>)</span></span>  
  
- <span data-ttu-id="28050-115">Kapsayan türü kullanılarak önceden oluşturuldu `CreateType`.</span><span class="sxs-lookup"><span data-stu-id="28050-115">The containing type has been previously created using `CreateType`.</span></span> <span data-ttu-id="28050-116">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="28050-116">(<xref:System.InvalidOperationException>)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28050-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28050-117">See also</span></span>

- [<span data-ttu-id="28050-118">Yakından Platform çağırma</span><span class="sxs-lookup"><span data-stu-id="28050-118">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="28050-119">Platform Çağırma Örnekleri</span><span class="sxs-lookup"><span data-stu-id="28050-119">Platform Invoke Examples</span></span>](../../../framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="28050-120">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="28050-120">Consuming Unmanaged DLL Functions</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- <span data-ttu-id="28050-121">[Yayma yansıma ile bir yöntem tanımlama](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="28050-121">[Defining a Method with Reflection Emit](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span></span>
- [<span data-ttu-id="28050-122">İzlenecek yol: Windows API'lerini Çağırma</span><span class="sxs-lookup"><span data-stu-id="28050-122">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [<span data-ttu-id="28050-123">COM Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="28050-123">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)
