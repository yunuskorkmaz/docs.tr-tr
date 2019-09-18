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
ms.openlocfilehash: 5fb95ab7ff4fcac7169238d90637d7b83078d6dd
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046113"
---
# <a name="dynamic-source-code-generation-and-compilation"></a><span data-ttu-id="61d81-102">Dinamik Kaynak Kodu Oluşturma ve Derleme</span><span class="sxs-lookup"><span data-stu-id="61d81-102">Dynamic Source Code Generation and Compilation</span></span>
<span data-ttu-id="61d81-103">.NET Framework, kaynak kodu oluşturan program geliştiricilerinin, kodu temsil eden tek bir modele göre, çalışma zamanında birden çok programlama dilinde kaynak kodu oluşturmasını sağlayan Kod Belge Nesne Modeli (CodeDOM) adlı bir mekanizma içerir işlemek için.</span><span class="sxs-lookup"><span data-stu-id="61d81-103">The .NET Framework includes a mechanism called the Code Document Object Model (CodeDOM) that enables developers of programs that emit source code to generate source code in multiple programming languages at run time, based on a single model that represents the code to render.</span></span>  
  
 <span data-ttu-id="61d81-104">Kaynak kodunu temsil etmek için CodeDOM öğeleri birbirlerine bağlanır ve bu, bazı kaynak kodların yapısını modelleyen, CodeDOM grafiği olarak bilinen bir veri yapısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="61d81-104">To represent source code, CodeDOM elements are linked to each other to form a data structure known as a CodeDOM graph, which models the structure of some source code.</span></span>  
  
 <span data-ttu-id="61d81-105">Ad `System.CodeDom` alanı, belirli bir programlama dilinden bağımsız olarak kaynak kodun mantıksal yapısını temsil eden türleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="61d81-105">The `System.CodeDom` namespace defines types that can represent the logical structure of source code, independent of a specific programming language.</span></span> <span data-ttu-id="61d81-106">Ad `System.CodeDom.Compiler` alanı, CodeDOM grafiklerinden kaynak kodu oluşturmak ve desteklenen dillerde kaynak kodu derlemesini yönetmek için türleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="61d81-106">The `System.CodeDom.Compiler` namespace defines types for generating source code from CodeDOM graphs and managing the compilation of source code in supported languages.</span></span> <span data-ttu-id="61d81-107">Derleyici satıcıları veya geliştiriciler desteklenen dillerin kümesini genişletebilir.</span><span class="sxs-lookup"><span data-stu-id="61d81-107">Compiler vendors or developers can extend the set of supported languages.</span></span>  
  
 <span data-ttu-id="61d81-108">Dilden bağımsız kaynak kodu modelleme, bir programın birden çok dilde veya belirsiz bir hedef dil için bir program modeli için kaynak kodu oluşturması gerektiğinde değerli olabilir.</span><span class="sxs-lookup"><span data-stu-id="61d81-108">Language-independent source code modeling can be valuable when a program needs to generate source code for a program model in multiple languages or for an uncertain target language.</span></span> <span data-ttu-id="61d81-109">Örneğin, bazı tasarımcılar, kaynak kodu doğru programlama dilinde oluşturmak için CodeDOM 'yi bir dil soyutlama arabirimi olarak kullanır, bu dil için CodeDOM desteği kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="61d81-109">For example, some designers use the CodeDOM as a language abstraction interface to produce source code in the correct programming language, if CodeDOM support for the language is available.</span></span>  
  
 <span data-ttu-id="61d81-110">.NET Framework,, ve <xref:Microsoft.CSharp.CSharpCodeProvider> <xref:Microsoft.JScript.JScriptCodeProvider> <xref:Microsoft.VisualBasic.VBCodeProvider>için kod oluşturucuları ve kod derleyicileri içerir.</span><span class="sxs-lookup"><span data-stu-id="61d81-110">The .NET Framework includes code generators and code compilers for <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>, and <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="61d81-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="61d81-111">In This Section</span></span>  
 [<span data-ttu-id="61d81-112">CodeDOM'yi Kullanma</span><span class="sxs-lookup"><span data-stu-id="61d81-112">Using the CodeDOM</span></span>](using-the-codedom.md)  
 <span data-ttu-id="61d81-113">Ortak kullanımları açıklar ve CodeDOM kullanılarak basit nesne grafı oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="61d81-113">Describes common uses, and demonstrates building a simple object graph using the CodeDOM.</span></span>  
  
 [<span data-ttu-id="61d81-114">Kaynak kodu oluşturma ve bir CodeDOM grafiğinden program derleme</span><span class="sxs-lookup"><span data-stu-id="61d81-114">Generating Source Code and Compiling a Program from a CodeDOM Graph</span></span>](generating-and-compiling-source-code-from-a-codedom-graph.md)  
 <span data-ttu-id="61d81-115">Kaynak kodu oluşturmayı ve `System.CodeDom.Compiler` ad alanında tanımlanan sınıfları kullanarak oluşturulan kodu bir dış derleyici ile derlemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="61d81-115">Describes how to generate source code and compile the generated code with an external compiler using classes defined in the `System.CodeDom.Compiler` namespace.</span></span>  
  
 [<span data-ttu-id="61d81-116">Nasıl yapılır: CodeDOM kullanarak XML belge dosyası oluşturma</span><span class="sxs-lookup"><span data-stu-id="61d81-116">How to: Create an XML Documentation File Using CodeDOM</span></span>](how-to-create-an-xml-documentation-file-using-codedom.md)  
 <span data-ttu-id="61d81-117">XML belge açıklamalarıyla kod oluşturmak için CodeDOM kullanmayı ve XML belge çıkışını oluşturacak şekilde oluşturulan kodu derlemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="61d81-117">Describes how to use CodeDOM to generate code with XML documentation comments, and compile the generated code so that it creates the XML documentation output.</span></span>  
  
 [<span data-ttu-id="61d81-118">Nasıl yapılır: CodeDOM kullanarak sınıf oluşturma</span><span class="sxs-lookup"><span data-stu-id="61d81-118">How to: Create a Class Using CodeDOM</span></span>](how-to-create-a-class-using-codedom.md)  
 <span data-ttu-id="61d81-119">Alanları, özellikleri, bir yöntemi, oluşturucuyu ve bir giriş noktasını içeren bir sınıf oluşturmak için CodeDOM nasıl kullanacağınızı açıklar.</span><span class="sxs-lookup"><span data-stu-id="61d81-119">Describes how to use CodeDOM to generate a class containing fields, properties, a method, a constructor, and an entry point.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="61d81-120">Başvuru</span><span class="sxs-lookup"><span data-stu-id="61d81-120">Reference</span></span>  
 <xref:System.CodeDom>  
 <span data-ttu-id="61d81-121">Ortak dil çalışma zamanını hedefleyen programlama dillerinde kod öğelerini temsil eden öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="61d81-121">Defines elements that represent code elements in programming languages that target the common language runtime.</span></span>  
  
 <xref:System.CodeDom.Compiler>  
 <span data-ttu-id="61d81-122">Çalışma zamanında kod oluşturma ve derleme için arabirimler tanımlar.</span><span class="sxs-lookup"><span data-stu-id="61d81-122">Defines interfaces for generating and compiling code at run time.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="61d81-123">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="61d81-123">Related Sections</span></span>  
 <span data-ttu-id="61d81-124">[CodeDOM hızlı başvurusu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="61d81-124">[CodeDOM Quick Reference](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100))</span></span>  
 <span data-ttu-id="61d81-125">Geliştiricilerin kaynak kodu öğelerini temsil eden CodeDOM öğelerini bulması için hızlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="61d81-125">Provides a quick way for developers to find the CodeDOM elements that represent source code elements.</span></span>
