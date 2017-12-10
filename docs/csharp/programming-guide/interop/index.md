---
title: "Birlikte Çalışabilirlik (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2965543066b0846a6a4f8a3199590049947122f2
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="fc6c3-102">Birlikte Çalışabilirlik (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="fc6c3-102">Interoperability (C# Programming Guide)</span></span>
<span data-ttu-id="fc6c3-103">Birlikte çalışabilirlik korumak ve yönetilmeyen kodunda Yatırımlar yararlanmak sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc6c3-103">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="fc6c3-104">Ortak dil çalışma zamanı (CLR) denetimi altında çalışan bir kod çağrılır *yönetilen kod*, ve CLR dışında çalışan kod çağrılır *yönetilmeyen kod*.</span><span class="sxs-lookup"><span data-stu-id="fc6c3-104">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="fc6c3-105">COM, COM +, C++ bileşenleri, ActiveX bileşenlerini ve Microsoft Win32 API yönetilmeyen kod gösterilebilir.</span><span class="sxs-lookup"><span data-stu-id="fc6c3-105">COM, COM+, C++ components, ActiveX components, and Microsoft Win32 API are examples of unmanaged code.</span></span>  
  
 <span data-ttu-id="fc6c3-106">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Platform yoluyla yönetilmeyen kod ile birlikte çalışabilirlik sağlar çağırma Hizmetleri <xref:System.Runtime.InteropServices> ad alanı, C++ birlikte çalışabilirlik ve COM birlikte çalışabilirliği (COM birlikte çalışma).</span><span class="sxs-lookup"><span data-stu-id="fc6c3-106">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fc6c3-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="fc6c3-107">In This Section</span></span>  
 [<span data-ttu-id="fc6c3-108">Birlikte çalışabilirliğe genel bakış</span><span class="sxs-lookup"><span data-stu-id="fc6c3-108">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 <span data-ttu-id="fc6c3-109">Yönetilmeyen kod ile C# yönetilen kodu arasında birlikte çalışmak için yöntemler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fc6c3-109">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="fc6c3-110">Nasıl yapılır: Visual C# özelliklerini kullanarak Office birlikte çalışma nesnelerine erişim</span><span class="sxs-lookup"><span data-stu-id="fc6c3-110">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="fc6c3-111">Visual C Office programlama kolaylaştırmak için #'de kullanılmaya başlanmıştır özellikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="fc6c3-111">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="fc6c3-112">Nasıl yapılır: Dizin oluşturulmuş özellikleri COM birlikte çalışma programlamada kullanma</span><span class="sxs-lookup"><span data-stu-id="fc6c3-112">How to: Use Indexed Properties in COM Interop Programming</span></span>](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="fc6c3-113">Dizinli Özellikler parametrelere sahip erişim COM özellikleri için kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="fc6c3-113">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="fc6c3-114">Nasıl yapılır: Wave dosyasını oynatmak için Platform çağırma kullanma</span><span class="sxs-lookup"><span data-stu-id="fc6c3-114">How to: Use Platform Invoke to Play a Wave File</span></span>](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="fc6c3-115">Platform kullanmayı açıklar Windows işletim sisteminde .wav ses dosyasını oynatmak için Hizmetleri çağırma.</span><span class="sxs-lookup"><span data-stu-id="fc6c3-115">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="fc6c3-116">İzlenecek yol: Office programlama</span><span class="sxs-lookup"><span data-stu-id="fc6c3-116">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 <span data-ttu-id="fc6c3-117">Bir Excel çalışma kitabı ve çalışma kitabı bağlantısını içeren bir Word belgesi nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc6c3-117">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="fc6c3-118">Örnek COM sınıfı</span><span class="sxs-lookup"><span data-stu-id="fc6c3-118">Example COM Class</span></span>](../../../csharp/programming-guide/interop/example-com-class.md)  
 <span data-ttu-id="fc6c3-119">Bir C# sınıf bir COM nesnesi olarak kullanıma sunmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fc6c3-119">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="fc6c3-120">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="fc6c3-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fc6c3-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fc6c3-121">See Also</span></span>  
 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="fc6c3-122">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fc6c3-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="fc6c3-123">Yönetilmeyen kod ile birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="fc6c3-123">Interoperating with Unmanaged Code</span></span>](../../../../docs/framework/interop/index.md)  
 [<span data-ttu-id="fc6c3-124">İzlenecek yol: Office programlama</span><span class="sxs-lookup"><span data-stu-id="fc6c3-124">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
