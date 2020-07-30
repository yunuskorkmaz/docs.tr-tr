---
title: Birlikte çalışabilirlik-C# Programlama Kılavuzu
description: Birlikte çalışabilirlik, ortak dil çalışma zamanı altında çalışan kodun yanına yönetilmeyen kodu destekler. Birlikte çalışabilirlik seçeneklerini anlamak için bu kaynakları kullanın.
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: d85eb51107d50e023270fcbe1ef6e08a7788ae78
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302977"
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="2ce10-104">Birlikte Çalışabilirlik (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="2ce10-104">Interoperability (C# Programming Guide)</span></span>

<span data-ttu-id="2ce10-105">Birlikte çalışabilirlik, yönetilmeyen koddaki mevcut yatırımlardan korunmanızı ve avantajlarını yapmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="2ce10-105">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="2ce10-106">Ortak dil çalışma zamanının (CLR) denetimi altında çalışan koda *yönetilen kod*adı verılır ve CLR dışında çalışan koda *yönetilmeyen kod*denir.</span><span class="sxs-lookup"><span data-stu-id="2ce10-106">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="2ce10-107">COM, COM+, C++ bileşenleri, ActiveX bileşenleri ve Microsoft Windows API, yönetilmeyen kod örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="2ce10-107">COM, COM+, C++ components, ActiveX components, and Microsoft Windows API are examples of unmanaged code.</span></span>  
  
<span data-ttu-id="2ce10-108">.NET, platform çağırma Hizmetleri, <xref:System.Runtime.InteropServices> ad alanı, C++ birlikte çalışabilirliği ve com birlikte çalışabilirliği (com birlikte çalışma) aracılığıyla yönetilmeyen kod ile birlikte çalışabilirliği etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="2ce10-108">.NET enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2ce10-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2ce10-109">In This Section</span></span>  
 [<span data-ttu-id="2ce10-110">Birlikte Çalışabilirliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2ce10-110">Interoperability Overview</span></span>](./interoperability-overview.md)  
 <span data-ttu-id="2ce10-111">C# yönetilen kodu ve yönetilmeyen kod arasında birlikte çalışma yöntemlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="2ce10-111">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="2ce10-112">Visual C# özelliklerini kullanarak Office birlikte çalışma nesnelerine erişim</span><span class="sxs-lookup"><span data-stu-id="2ce10-112">How to access Office interop objects by using C# features</span></span>](./how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="2ce10-113">Visual C# ' de Office programlamayı kolaylaştırmak Için sunulan özellikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="2ce10-113">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="2ce10-114">COM birlikte çalışma programlamada dizin oluşturulmuş özellikleri kullanma</span><span class="sxs-lookup"><span data-stu-id="2ce10-114">How to use indexed properties in COM interop programming</span></span>](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="2ce10-115">Parametreleri olan COM özelliklerine erişmek için dizinlenmiş özelliklerin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="2ce10-115">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="2ce10-116">WAV dosyasını oynatmak için platform çağırma kullanma</span><span class="sxs-lookup"><span data-stu-id="2ce10-116">How to use platform invoke to play a WAV file</span></span>](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="2ce10-117">Windows işletim sisteminde bir. wav ses dosyası oynatmak için platform çağırma Hizmetleri ' nin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="2ce10-117">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="2ce10-118">İzlenecek yol: Office programlama</span><span class="sxs-lookup"><span data-stu-id="2ce10-118">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)  
 <span data-ttu-id="2ce10-119">Çalışma kitabının bir bağlantısını içeren bir Excel çalışma kitabı ve Word belgesi oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="2ce10-119">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="2ce10-120">Örnek COM Sınıfı</span><span class="sxs-lookup"><span data-stu-id="2ce10-120">Example COM Class</span></span>](./example-com-class.md)  
 <span data-ttu-id="2ce10-121">C# sınıfının bir COM nesnesi olarak nasıl kullanıma sunuleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2ce10-121">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="2ce10-122">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="2ce10-122">C# Language Specification</span></span>  

<span data-ttu-id="2ce10-123">Daha fazla bilgi için bkz. [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [temel kavramlar](~/_csharplang/spec/unsafe-code.md) .</span><span class="sxs-lookup"><span data-stu-id="2ce10-123">For more information, see [Basic concepts](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="2ce10-124">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="2ce10-124">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2ce10-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ce10-125">See also</span></span>

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [<span data-ttu-id="2ce10-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2ce10-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2ce10-127">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="2ce10-127">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)
- [<span data-ttu-id="2ce10-128">İzlenecek yol: Office programlama</span><span class="sxs-lookup"><span data-stu-id="2ce10-128">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
