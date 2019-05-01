---
title: Dinamik Kaynak Kodu Oluşturma ve Derleme
ms.date: 03/30/2017
helpviewer_keywords:
- Code Document Object Model
- System.CodeDom namespace
- language-independent source code modeling
- CodeDOM
- multiple languages supported by CodeDOM
- source code in multiple languages
- languages, multiple language support by CodeDOM
ms.assetid: d077a3e8-bd81-4bdf-b6a3-323857ea30fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8feb94f3d57c25d634bd51b8f41eca42d5e5757a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793334"
---
# <a name="dynamic-source-code-generation-and-compilation"></a><span data-ttu-id="d4e17-102">Dinamik Kaynak Kodu Oluşturma ve Derleme</span><span class="sxs-lookup"><span data-stu-id="d4e17-102">Dynamic Source Code Generation and Compilation</span></span>
<span data-ttu-id="d4e17-103">.NET Framework kod belge nesne geliştiricilerin kodunu temsil eden tek bir modelini temel alan kaynak kodu, çalışma zamanında birden fazla programlama dilinde oluşturmak için kaynak kodu yayma programlar sağlayan modeli (CodeDOM) adlı bir mekanizma içerir İşlenecek.</span><span class="sxs-lookup"><span data-stu-id="d4e17-103">The .NET Framework includes a mechanism called the Code Document Object Model (CodeDOM) that enables developers of programs that emit source code to generate source code in multiple programming languages at run time, based on a single model that represents the code to render.</span></span>  
  
 <span data-ttu-id="d4e17-104">Kaynak kodu temsil etmek için diğer bazı kaynak kodunun yapısını modeller CodeDOM grafiği bilinen bir veri yapısı oluşturmak için CodeDOM öğelerini bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d4e17-104">To represent source code, CodeDOM elements are linked to each other to form a data structure known as a CodeDOM graph, which models the structure of some source code.</span></span>  
  
 <span data-ttu-id="d4e17-105">`System.CodeDom` Ad alanı, kaynak kodu, belirli bir programlama dilini bağımsız mantıksal yapısını temsil edebilen türleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d4e17-105">The `System.CodeDom` namespace defines types that can represent the logical structure of source code, independent of a specific programming language.</span></span> <span data-ttu-id="d4e17-106">`System.CodeDom.Compiler` CodeDOM grafiklerinden kaynak kodu oluşturma ve derleme desteklenen dilde kaynak kodu yönetmek için ad alanını tanımlayan tür.</span><span class="sxs-lookup"><span data-stu-id="d4e17-106">The `System.CodeDom.Compiler` namespace defines types for generating source code from CodeDOM graphs and managing the compilation of source code in supported languages.</span></span> <span data-ttu-id="d4e17-107">Derleyici satıcılar veya geliştiricilerin desteklenen dil kümesini genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4e17-107">Compiler vendors or developers can extend the set of supported languages.</span></span>  
  
 <span data-ttu-id="d4e17-108">Birden çok dilde bir program modeli için veya belirsiz bir hedef dil için kaynak kodu oluşturmak bir program gerektiğinde dilden bağımsız kaynak kodu modelleme yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="d4e17-108">Language-independent source code modeling can be valuable when a program needs to generate source code for a program model in multiple languages or for an uncertain target language.</span></span> <span data-ttu-id="d4e17-109">Örneğin, dil desteğini CodeDOM varsa bazı tasarımcıları doğru programlama dilinde, kaynak kodunu üretmek için bir dil soyutlama arabirimi CodeDOM kullanın.</span><span class="sxs-lookup"><span data-stu-id="d4e17-109">For example, some designers use the CodeDOM as a language abstraction interface to produce source code in the correct programming language, if CodeDOM support for the language is available.</span></span>  
  
 <span data-ttu-id="d4e17-110">.NET Framework kod oluşturucuları ve için kod derleyicileri içerir <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>, ve <xref:Microsoft.VisualBasic.VBCodeProvider>.</span><span class="sxs-lookup"><span data-stu-id="d4e17-110">The .NET Framework includes code generators and code compilers for <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>, and <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d4e17-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d4e17-111">In This Section</span></span>  
 [<span data-ttu-id="d4e17-112">CodeDOM'yi Kullanma</span><span class="sxs-lookup"><span data-stu-id="d4e17-112">Using the CodeDOM</span></span>](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)  
 <span data-ttu-id="d4e17-113">Yaygın kullanımları açıklar ve CodeDOM kullanarak bir Basit Nesne grafiği oluşturmayı göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="d4e17-113">Describes common uses, and demonstrates building a simple object graph using the CodeDOM.</span></span>  
  
 [<span data-ttu-id="d4e17-114">Kaynak kodu üretme ve CodeDOM grafiğinden bir programı derleme</span><span class="sxs-lookup"><span data-stu-id="d4e17-114">Generating Source Code and Compiling a Program from a CodeDOM Graph</span></span>](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)  
 <span data-ttu-id="d4e17-115">Kaynak kodu oluşturun ve oluşturulan kod içinde tanımlanan sınıflar kullanarak dış bir derleyici ile derleme açıklar `System.CodeDom.Compiler` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="d4e17-115">Describes how to generate source code and compile the generated code with an external compiler using classes defined in the `System.CodeDom.Compiler` namespace.</span></span>  
  
 [<span data-ttu-id="d4e17-116">Nasıl yapılır: CodeDOM kullanarak XML belge dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="d4e17-116">How to: Create an XML Documentation File Using CodeDOM</span></span>](../../../docs/framework/reflection-and-codedom/how-to-create-an-xml-documentation-file-using-codedom.md)  
 <span data-ttu-id="d4e17-117">XML belgeleri açıklamaları olan kod oluşturma ve XML belgeleri çıktısı oluşturması oluşturulan kodu derlemek için CodeDOM kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="d4e17-117">Describes how to use CodeDOM to generate code with XML documentation comments, and compile the generated code so that it creates the XML documentation output.</span></span>  
  
 [<span data-ttu-id="d4e17-118">Nasıl yapılır: CodeDOM kullanarak sınıf oluşturma</span><span class="sxs-lookup"><span data-stu-id="d4e17-118">How to: Create a Class Using CodeDOM</span></span>](../../../docs/framework/reflection-and-codedom/how-to-create-a-class-using-codedom.md)  
 <span data-ttu-id="d4e17-119">CodeDOM alanlar, özellikler, bir yöntem, bir oluşturucu ve bir giriş noktası içeren bir sınıf oluşturmak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d4e17-119">Describes how to use CodeDOM to generate a class containing fields, properties, a method, a constructor, and an entry point.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d4e17-120">Başvuru</span><span class="sxs-lookup"><span data-stu-id="d4e17-120">Reference</span></span>  
 <xref:System.CodeDom>  
 <span data-ttu-id="d4e17-121">Ortak dil çalışma zamanını hedefleyen programlama dillerinde kod öğelerini temsil eden öğelerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d4e17-121">Defines elements that represent code elements in programming languages that target the common language runtime.</span></span>  
  
 <xref:System.CodeDom.Compiler>  
 <span data-ttu-id="d4e17-122">Arabirimleri oluşturma ve çalışma zamanında kod derlemek için tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d4e17-122">Defines interfaces for generating and compiling code at run time.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d4e17-123">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="d4e17-123">Related Sections</span></span>  
 <span data-ttu-id="d4e17-124">[CodeDOM hızlı başvuru](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d4e17-124">[CodeDOM Quick Reference](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))</span></span>  
 <span data-ttu-id="d4e17-125">Kaynak kod öğelerini temsil eden CodeDOM öğeleri bulmak, geliştiriciler için hızlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4e17-125">Provides a quick way for developers to find the CodeDOM elements that represent source code elements.</span></span>
