---
title: Birlikte çalışabilirlik-C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: e53465066cf27a5f46c66ac73ee242370be23395
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84242013"
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="14fe8-102">Birlikte Çalışabilirlik (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="14fe8-102">Interoperability (C# Programming Guide)</span></span>

<span data-ttu-id="14fe8-103">Birlikte çalışabilirlik, yönetilmeyen koddaki mevcut yatırımlardan korunmanızı ve avantajlarını yapmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="14fe8-103">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="14fe8-104">Ortak dil çalışma zamanının (CLR) denetimi altında çalışan koda *yönetilen kod*adı verılır ve CLR dışında çalışan koda *yönetilmeyen kod*denir.</span><span class="sxs-lookup"><span data-stu-id="14fe8-104">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="14fe8-105">COM, COM+, C++ bileşenleri, ActiveX bileşenleri ve Microsoft Windows API, yönetilmeyen kod örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="14fe8-105">COM, COM+, C++ components, ActiveX components, and Microsoft Windows API are examples of unmanaged code.</span></span>  
  
<span data-ttu-id="14fe8-106">.NET, platform çağırma Hizmetleri, <xref:System.Runtime.InteropServices> ad alanı, C++ birlikte çalışabilirliği ve com birlikte çalışabilirliği (com birlikte çalışma) aracılığıyla yönetilmeyen kod ile birlikte çalışabilirliği etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="14fe8-106">.NET enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="14fe8-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="14fe8-107">In This Section</span></span>  
 [<span data-ttu-id="14fe8-108">Birlikte Çalışabilirliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="14fe8-108">Interoperability Overview</span></span>](./interoperability-overview.md)  
 <span data-ttu-id="14fe8-109">C# yönetilen kodu ve yönetilmeyen kod arasında birlikte çalışma yöntemlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="14fe8-109">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="14fe8-110">Visual C# özelliklerini kullanarak Office birlikte çalışma nesnelerine erişim</span><span class="sxs-lookup"><span data-stu-id="14fe8-110">How to access Office interop objects by using C# features</span></span>](./how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="14fe8-111">Visual C# ' de Office programlamayı kolaylaştırmak Için sunulan özellikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="14fe8-111">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="14fe8-112">COM birlikte çalışma programlamada dizin oluşturulmuş özellikleri kullanma</span><span class="sxs-lookup"><span data-stu-id="14fe8-112">How to use indexed properties in COM interop programming</span></span>](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="14fe8-113">Parametreleri olan COM özelliklerine erişmek için dizinlenmiş özelliklerin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="14fe8-113">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="14fe8-114">WAV dosyasını oynatmak için platform çağırma kullanma</span><span class="sxs-lookup"><span data-stu-id="14fe8-114">How to use platform invoke to play a WAV file</span></span>](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="14fe8-115">Windows işletim sisteminde bir. wav ses dosyası oynatmak için platform çağırma Hizmetleri ' nin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="14fe8-115">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="14fe8-116">İzlenecek yol: Office programlama</span><span class="sxs-lookup"><span data-stu-id="14fe8-116">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)  
 <span data-ttu-id="14fe8-117">Çalışma kitabının bir bağlantısını içeren bir Excel çalışma kitabı ve Word belgesi oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="14fe8-117">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="14fe8-118">Örnek COM Sınıfı</span><span class="sxs-lookup"><span data-stu-id="14fe8-118">Example COM Class</span></span>](./example-com-class.md)  
 <span data-ttu-id="14fe8-119">C# sınıfının bir COM nesnesi olarak nasıl kullanıma sunuleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="14fe8-119">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="14fe8-120">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="14fe8-120">C# Language Specification</span></span>  

<span data-ttu-id="14fe8-121">Daha fazla bilgi için bkz. [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [temel kavramlar](~/_csharplang/spec/unsafe-code.md) .</span><span class="sxs-lookup"><span data-stu-id="14fe8-121">For more information, see [Basic concepts](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="14fe8-122">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="14fe8-122">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="14fe8-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14fe8-123">See also</span></span>

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [<span data-ttu-id="14fe8-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="14fe8-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="14fe8-125">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="14fe8-125">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)
- [<span data-ttu-id="14fe8-126">İzlenecek yol: Office programlama</span><span class="sxs-lookup"><span data-stu-id="14fe8-126">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
