---
title: Birlikte çalışabilirlik C# -Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: 3a70d2ae077552bab536e96367cab0fda1661310
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712058"
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="3d8e7-102">Birlikte Çalışabilirlik (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="3d8e7-102">Interoperability (C# Programming Guide)</span></span>
<span data-ttu-id="3d8e7-103">Birlikte çalışabilirlik, yönetilmeyen koddaki mevcut yatırımlardan korunmanızı ve avantajlarını yapmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="3d8e7-103">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="3d8e7-104">Ortak dil çalışma zamanının (CLR) denetimi altında çalışan koda *yönetilen kod*adı verılır ve CLR dışında çalışan koda *yönetilmeyen kod*denir.</span><span class="sxs-lookup"><span data-stu-id="3d8e7-104">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="3d8e7-105">COM, COM+, C++ bileşenler, ActiveX bileşenleri ve MICROSOFT Windows API, yönetilmeyen kod örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="3d8e7-105">COM, COM+, C++ components, ActiveX components, and Microsoft Windows API are examples of unmanaged code.</span></span>  
  
 <span data-ttu-id="3d8e7-106">.NET Framework platform çağırma Hizmetleri, <xref:System.Runtime.InteropServices> ad alanı, C++ birlikte ÇALıŞABILIRLIK ve com birlikte ÇALıŞABILIRLIĞI (com birlikte çalışma) aracılığıyla yönetilmeyen kodla birlikte çalışabilirliğe izin verebilir.</span><span class="sxs-lookup"><span data-stu-id="3d8e7-106">The .NET Framework enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3d8e7-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="3d8e7-107">In This Section</span></span>  
 [<span data-ttu-id="3d8e7-108">Birlikte Çalışabilirliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3d8e7-108">Interoperability Overview</span></span>](./interoperability-overview.md)  
 <span data-ttu-id="3d8e7-109">Yönetilen kod ve yönetilmeyen kod C# arasında birlikte çalışma yöntemlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="3d8e7-109">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="3d8e7-110">Özellikleri kullanarak C# Office birlikte çalışma nesnelerine erişme</span><span class="sxs-lookup"><span data-stu-id="3d8e7-110">How to access Office interop objects by using C# features</span></span>](./how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="3d8e7-111">Office programlama işlemini kolaylaştırmak için görselde C# tanıtılan özellikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="3d8e7-111">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="3d8e7-112">COM birlikte çalışma programlamada dizinli özellikleri kullanma</span><span class="sxs-lookup"><span data-stu-id="3d8e7-112">How to use indexed properties in COM interop programming</span></span>](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="3d8e7-113">Parametreleri olan COM özelliklerine erişmek için dizinlenmiş özelliklerin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="3d8e7-113">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="3d8e7-114">Bir WAV dosyasını oynatmak için platform çağırma kullanma</span><span class="sxs-lookup"><span data-stu-id="3d8e7-114">How to use platform invoke to play a WAV file</span></span>](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="3d8e7-115">Windows işletim sisteminde bir. wav ses dosyası oynatmak için platform çağırma Hizmetleri ' nin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="3d8e7-115">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="3d8e7-116">İzlenecek yol: Office programlama</span><span class="sxs-lookup"><span data-stu-id="3d8e7-116">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)  
 <span data-ttu-id="3d8e7-117">Çalışma kitabının bir bağlantısını içeren bir Excel çalışma kitabı ve Word belgesi oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="3d8e7-117">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="3d8e7-118">Örnek COM Sınıfı</span><span class="sxs-lookup"><span data-stu-id="3d8e7-118">Example COM Class</span></span>](./example-com-class.md)  
 <span data-ttu-id="3d8e7-119">Bir C# SıNıFıN bir com nesnesi olarak nasıl kullanıma sunuleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3d8e7-119">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="3d8e7-120">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="3d8e7-120">C# Language Specification</span></span>  

<span data-ttu-id="3d8e7-121">Daha fazla bilgi için bkz. [ C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [temel kavramlar](~/_csharplang/spec/unsafe-code.md) .</span><span class="sxs-lookup"><span data-stu-id="3d8e7-121">For more information, see [Basic concepts](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="3d8e7-122">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="3d8e7-122">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3d8e7-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d8e7-123">See also</span></span>

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [<span data-ttu-id="3d8e7-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3d8e7-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3d8e7-125">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="3d8e7-125">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)
- [<span data-ttu-id="3d8e7-126">İzlenecek yol: Office programlama</span><span class="sxs-lookup"><span data-stu-id="3d8e7-126">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
