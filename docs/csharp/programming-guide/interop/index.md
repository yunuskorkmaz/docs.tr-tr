---
title: Birlikte çalışabilirlik - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
ms.openlocfilehash: 3a70d2ae077552bab536e96367cab0fda1661310
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75712058"
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="0ff6d-102">Birlikte Çalışabilirlik (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0ff6d-102">Interoperability (C# Programming Guide)</span></span>
<span data-ttu-id="0ff6d-103">Birlikte çalışabilirlik, yönetilmeyen koddaki mevcut yatırımları korumanızı ve bunlardan yararlanmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ff6d-103">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="0ff6d-104">Ortak dil çalışma zamanı (CLR) denetimi altında çalışan kod *yönetilen kod*olarak adlandırılır ve CLR dışında çalışan kod *yönetilmeyen kod*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="0ff6d-104">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="0ff6d-105">COM, COM+, C++ bileşenleri, ActiveX bileşenleri ve Microsoft Windows API'sı yönetilmeyen kod örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="0ff6d-105">COM, COM+, C++ components, ActiveX components, and Microsoft Windows API are examples of unmanaged code.</span></span>  
  
 <span data-ttu-id="0ff6d-106">.NET Framework, platform çağırma hizmetleri, <xref:System.Runtime.InteropServices> ad alanı, C++ birlikte çalışabilirlik ve COM birlikte çalışabilirlik (COM interop) aracılığıyla yönetilmeyen kodla birlikte çalışabilirlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ff6d-106">The .NET Framework enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0ff6d-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="0ff6d-107">In This Section</span></span>  
 [<span data-ttu-id="0ff6d-108">Birlikte Çalışabilirliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0ff6d-108">Interoperability Overview</span></span>](./interoperability-overview.md)  
 <span data-ttu-id="0ff6d-109">C# yönetilen kod ve yönetilmeyen kod arasında etkileşim yöntemlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="0ff6d-109">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="0ff6d-110">Visual C# özelliklerini kullanarak Office birlikte çalışma nesnelerine erişim</span><span class="sxs-lookup"><span data-stu-id="0ff6d-110">How to access Office interop objects by using C# features</span></span>](./how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="0ff6d-111">Office programlamayı kolaylaştırmak için Visual C# 'da tanıtılan özellikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="0ff6d-111">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="0ff6d-112">COM birlikte çalışma programlamada dizin oluşturulmuş özellikleri kullanma</span><span class="sxs-lookup"><span data-stu-id="0ff6d-112">How to use indexed properties in COM interop programming</span></span>](./how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="0ff6d-113">Parametreleri olan COM özelliklerine erişmek için dizinlenmiş özelliklerin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="0ff6d-113">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="0ff6d-114">WAV dosyasını oynatmak için platform çağırma kullanma</span><span class="sxs-lookup"><span data-stu-id="0ff6d-114">How to use platform invoke to play a WAV file</span></span>](./how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="0ff6d-115">Windows işletim sisteminde bir .wav ses dosyası çalmak için platform çağırma hizmetlerinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="0ff6d-115">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="0ff6d-116">Walkthrough: Office Programlama</span><span class="sxs-lookup"><span data-stu-id="0ff6d-116">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)  
 <span data-ttu-id="0ff6d-117">Excel çalışma kitabı nın ve çalışma kitabına bağlantı içeren bir Word belgesinin nasıl oluşturulup oluşturulabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0ff6d-117">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="0ff6d-118">Örnek COM Sınıfı</span><span class="sxs-lookup"><span data-stu-id="0ff6d-118">Example COM Class</span></span>](./example-com-class.md)  
 <span data-ttu-id="0ff6d-119">Bir C# sınıfının COM nesnesi olarak nasıl ortaya çıkarılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0ff6d-119">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="0ff6d-120">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="0ff6d-120">C# Language Specification</span></span>  

<span data-ttu-id="0ff6d-121">Daha fazla bilgi için [C# Language Specification'daki](/dotnet/csharp/language-reference/language-specification/introduction) [Temel kavramlara](~/_csharplang/spec/unsafe-code.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="0ff6d-121">For more information, see [Basic concepts](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="0ff6d-122">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="0ff6d-122">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0ff6d-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ff6d-123">See also</span></span>

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [<span data-ttu-id="0ff6d-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0ff6d-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0ff6d-125">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="0ff6d-125">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)
- [<span data-ttu-id="0ff6d-126">Walkthrough: Office Programlama</span><span class="sxs-lookup"><span data-stu-id="0ff6d-126">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
