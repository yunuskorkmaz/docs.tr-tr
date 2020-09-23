---
title: "Nasıl yapılır: Windows API'lerini Çağırma"
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: 40b40c1a489d514c82cbccdeacda27900d9ec87d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91083364"
---
# <a name="how-to-call-windows-apis-visual-basic"></a><span data-ttu-id="3f921-102">Nasıl yapılır: Windows API'larını Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f921-102">How to: Call Windows APIs (Visual Basic)</span></span>

<span data-ttu-id="3f921-103">Bu örnek, user32.dll işlevi tanımlar ve çağırır `MessageBox` ve sonra bir String öğesine geçirir.</span><span class="sxs-lookup"><span data-stu-id="3f921-103">This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f921-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="3f921-104">Example</span></span>  

 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="3f921-105">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="3f921-105">Compile the code</span></span>  

 <span data-ttu-id="3f921-106">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="3f921-106">This example requires:</span></span>  
  
- <span data-ttu-id="3f921-107"><xref:System>Ad alanına başvuru.</span><span class="sxs-lookup"><span data-stu-id="3f921-107">A reference to the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="3f921-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="3f921-108">Robust Programming</span></span>  

 <span data-ttu-id="3f921-109">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="3f921-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="3f921-110">Yöntem statik değil, soyut veya daha önce tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="3f921-110">The method is not static, is abstract, or has been previously defined.</span></span> <span data-ttu-id="3f921-111">Üst tür bir arabirimdir, ya da *ad* veya *DLL* uzunluğu sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="3f921-111">The parent type is an interface, or the length of *name* or *dllName* is zero.</span></span> <span data-ttu-id="3f921-112">(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="3f921-112">(<xref:System.ArgumentException>)</span></span>  
  
- <span data-ttu-id="3f921-113">Ad veya *DLL* *adı* `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="3f921-113">The *name* or *dllName* is `Nothing`.</span></span> <span data-ttu-id="3f921-114">(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="3f921-114">(<xref:System.ArgumentNullException>)</span></span>  
  
- <span data-ttu-id="3f921-115">İçeren tür önceden kullanılarak oluşturulmuştur `CreateType` .</span><span class="sxs-lookup"><span data-stu-id="3f921-115">The containing type has been previously created using `CreateType`.</span></span> <span data-ttu-id="3f921-116">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="3f921-116">(<xref:System.InvalidOperationException>)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f921-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f921-117">See also</span></span>

- [<span data-ttu-id="3f921-118">Platform çağırma ' ye daha yakından bakış</span><span class="sxs-lookup"><span data-stu-id="3f921-118">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="3f921-119">Platform Çağırma Örnekleri</span><span class="sxs-lookup"><span data-stu-id="3f921-119">Platform Invoke Examples</span></span>](../../../framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="3f921-120">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="3f921-120">Consuming Unmanaged DLL Functions</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- <span data-ttu-id="3f921-121">[Yansıma Yayma ile bir yöntem tanımlama](/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3f921-121">[Defining a Method with Reflection Emit](/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span></span>
- [<span data-ttu-id="3f921-122">İzlenecek yol: Windows API'lerini Çağırma</span><span class="sxs-lookup"><span data-stu-id="3f921-122">Walkthrough: Calling Windows APIs</span></span>](walkthrough-calling-windows-apis.md)
- [<span data-ttu-id="3f921-123">COM birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="3f921-123">COM Interop</span></span>](index.md)
