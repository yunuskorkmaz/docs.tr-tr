---
title: "Nasıl yapılır: Windows API'larını Çağırma (Visual Basic)"
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: 081f4242ef5883a8b25b8819ba3aff835b1e6ac7
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44129701"
---
# <a name="how-to-call-windows-apis-visual-basic"></a><span data-ttu-id="af844-102">Nasıl yapılır: Windows API'larını Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af844-102">How to: Call Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="af844-103">Bu örnekte, tanımlar ve çağrı `MessageBox` user32.dll işlevi ve bir dize geçirir.</span><span class="sxs-lookup"><span data-stu-id="af844-103">This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af844-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="af844-104">Example</span></span>  
 [!code-vb[VbVbalrInterop#1](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-call-windows-apis_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="af844-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="af844-105">Compiling the Code</span></span>  
 <span data-ttu-id="af844-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="af844-106">This example requires:</span></span>  
  
-   <span data-ttu-id="af844-107">Bir başvuru <xref:System> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="af844-107">A reference to the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="af844-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="af844-108">Robust Programming</span></span>  
 <span data-ttu-id="af844-109">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="af844-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="af844-110">Yöntem statik değil, Özet veya önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="af844-110">The method is not static, is abstract, or has been previously defined.</span></span> <span data-ttu-id="af844-111">Üst türü bir arabirim veya uzunluğu olan *adı* veya *dll* sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="af844-111">The parent type is an interface, or the length of *name* or *dllName* is zero.</span></span> <span data-ttu-id="af844-112">(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="af844-112">(<xref:System.ArgumentException>)</span></span>  
  
-   <span data-ttu-id="af844-113">*Adı* veya *dll* olduğu `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="af844-113">The *name* or *dllName* is `Nothing`.</span></span> <span data-ttu-id="af844-114">(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="af844-114">(<xref:System.ArgumentNullException>)</span></span>  
  
-   <span data-ttu-id="af844-115">Kapsayan türü kullanılarak önceden oluşturuldu `CreateType`.</span><span class="sxs-lookup"><span data-stu-id="af844-115">The containing type has been previously created using `CreateType`.</span></span> <span data-ttu-id="af844-116">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="af844-116">(<xref:System.InvalidOperationException>)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af844-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af844-117">See also</span></span>

- [<span data-ttu-id="af844-118">Yakından Platform çağırma</span><span class="sxs-lookup"><span data-stu-id="af844-118">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)  
- [<span data-ttu-id="af844-119">Platform Çağırma Örnekleri</span><span class="sxs-lookup"><span data-stu-id="af844-119">Platform Invoke Examples</span></span>](../../../framework/interop/platform-invoke-examples.md)  
- [<span data-ttu-id="af844-120">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="af844-120">Consuming Unmanaged DLL Functions</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md)  
- [<span data-ttu-id="af844-121">Yayma yansıma ile bir yöntem tanımlama</span><span class="sxs-lookup"><span data-stu-id="af844-121">Defining a Method with Reflection Emit</span></span>](https://msdn.microsoft.com/library/84fd3bf6-628f-41aa-83d9-b990cf926e81)  
- [<span data-ttu-id="af844-122">İzlenecek yol: Windows API'lerini Çağırma</span><span class="sxs-lookup"><span data-stu-id="af844-122">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
- [<span data-ttu-id="af844-123">COM Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="af844-123">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)
