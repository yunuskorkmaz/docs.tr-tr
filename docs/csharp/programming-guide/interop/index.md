---
title: 'Birlikte çalışabilirlik - C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
  - COM interop
  - interoperability
  - 'platform invoke, accessing APIs with C#'
  - 'C# language, interoperability'
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
---
# <a name="interoperability-c-programming-guide"></a><span data-ttu-id="74eb8-102">Birlikte Çalışabilirlik (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="74eb8-102">Interoperability (C# Programming Guide)</span></span>
<span data-ttu-id="74eb8-103">Birlikte çalışabilirlik, yönetilmeyen kodda mevcut yatırımlarınızdan yararlanın ve korumak sağlar.</span><span class="sxs-lookup"><span data-stu-id="74eb8-103">Interoperability enables you to preserve and take advantage of existing investments in unmanaged code.</span></span> <span data-ttu-id="74eb8-104">Ortak dil çalışma zamanı (CLR) denetimi altında çalışan kod çağrılır *yönetilen kod*, ve CLR dışında çalışan kod çağrılır *yönetilmeyen kod*.</span><span class="sxs-lookup"><span data-stu-id="74eb8-104">Code that runs under the control of the common language runtime (CLR) is called *managed code*, and code that runs outside the CLR is called *unmanaged code*.</span></span> <span data-ttu-id="74eb8-105">COM, COM +, C++ bileşenleri, ActiveX bileşenleri ve Microsoft Windows API yönetilmeyen kod örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="74eb8-105">COM, COM+, C++ components, ActiveX components, and Microsoft Windows API are examples of unmanaged code.</span></span>  
  
 <span data-ttu-id="74eb8-106">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Etkinleştirir birlikte çalışabilirlik platformu aracılığıyla yönetilmeyen kod ile çağırma Hizmetleri <xref:System.Runtime.InteropServices> ad alanı, C++ birlikte çalışabilirlik ve COM birlikte çalışabilirlik (COM birlikte çalışma).</span><span class="sxs-lookup"><span data-stu-id="74eb8-106">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] enables interoperability with unmanaged code through platform invoke services, the <xref:System.Runtime.InteropServices> namespace, C++ interoperability, and COM interoperability (COM interop).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="74eb8-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="74eb8-107">In This Section</span></span>  
 [<span data-ttu-id="74eb8-108">Birlikte Çalışabilirliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="74eb8-108">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 <span data-ttu-id="74eb8-109">C# yönetilen kod ve yönetimsiz kod birlikte çalışmak için yöntemler açıklanır.</span><span class="sxs-lookup"><span data-stu-id="74eb8-109">Describes methods to interoperate between C# managed code and unmanaged code.</span></span>  
  
 [<span data-ttu-id="74eb8-110">Nasıl yapılır: Visual kullanarak Office birlikte çalışma nesnelerine erişim C# özellikleri</span><span class="sxs-lookup"><span data-stu-id="74eb8-110">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 <span data-ttu-id="74eb8-111">Görsel Office programlama kolaylaştırmak için C# içinde sunulan özellikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="74eb8-111">Describes features that are introduced in Visual C# to facilitate Office programming.</span></span>  
  
 [<span data-ttu-id="74eb8-112">Nasıl yapılır: COM birlikte çalışma programlamada dizin oluşturulmuş özellikleri kullanma</span><span class="sxs-lookup"><span data-stu-id="74eb8-112">How to: Use Indexed Properties in COM Interop Programming</span></span>](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 <span data-ttu-id="74eb8-113">Dizinli Özellikler parametrelere sahip COM özelliklere erişmek için kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="74eb8-113">Describes how to use indexed properties to access COM properties that have parameters.</span></span>  
  
 [<span data-ttu-id="74eb8-114">Nasıl yapılır: Wave dosyasını oynatmak için Platform çağırma kullanma</span><span class="sxs-lookup"><span data-stu-id="74eb8-114">How to: Use Platform Invoke to Play a Wave File</span></span>](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)  
 <span data-ttu-id="74eb8-115">Platform kullanmayı açıklar Windows işletim sisteminde .wav ses dosyasını oynatmak için hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="74eb8-115">Describes how to use platform invoke services to play a .wav sound file on the Windows operating system.</span></span>  
  
 [<span data-ttu-id="74eb8-116">İzlenecek yol: Office programlama</span><span class="sxs-lookup"><span data-stu-id="74eb8-116">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 <span data-ttu-id="74eb8-117">Bir Excel çalışma kitabının ve çalışma kitabının bağlantısını içeren bir Word belgesi nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="74eb8-117">Shows how to create an Excel workbook and a Word document that contains a link to the workbook.</span></span>  
  
 [<span data-ttu-id="74eb8-118">Örnek COM Sınıfı</span><span class="sxs-lookup"><span data-stu-id="74eb8-118">Example COM Class</span></span>](../../../csharp/programming-guide/interop/example-com-class.md)  
 <span data-ttu-id="74eb8-119">C# sınıfı bir COM nesnesi olarak kullanıma sunmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="74eb8-119">Demonstrates how to expose a C# class as a COM object.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="74eb8-120">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="74eb8-120">C# Language Specification</span></span>  

<span data-ttu-id="74eb8-121">Daha fazla bilgi için [temel kavramları](~/_csharplang/spec/unsafe-code.md) içinde [ C# dil belirtimi](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="74eb8-121">For more information, see [Basic concepts](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="74eb8-122">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="74eb8-122">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="74eb8-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74eb8-123">See also</span></span>

- <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>
- [<span data-ttu-id="74eb8-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="74eb8-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="74eb8-125">Yönetilmeyen Kod ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="74eb8-125">Interoperating with Unmanaged Code</span></span>](../../../../docs/framework/interop/index.md)
- [<span data-ttu-id="74eb8-126">İzlenecek yol: Office programlama</span><span class="sxs-lookup"><span data-stu-id="74eb8-126">Walkthrough: Office Programming</span></span>](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
