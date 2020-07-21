---
title: Dinamik Kaynak Kodu Oluşturma ve Derleme
description: Kod Belge Nesne Modeli (CodeDOM) ile .NET 'te dinamik kaynak kodu derleyin ve oluşturun. CodeDOM öğeleri, CodeDOM grafiği oluşturacak şekilde bağlantılıdır.
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
ms.openlocfilehash: 3cdd89ac9745f6af133ca683afff64283f2727d1
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475105"
---
# <a name="compile-and-generate-dynamic-source-code"></a><span data-ttu-id="c0851-104">Derleme ve dinamik kaynak kodu oluşturma</span><span class="sxs-lookup"><span data-stu-id="c0851-104">Compile and generate dynamic source code</span></span>

<span data-ttu-id="c0851-105">.NET Framework, kaynak kodu oluşturan program geliştiricilerinin, işlenecek kodu temsil eden tek bir modele göre çalışma zamanında birden fazla programlama dilinde kaynak kodu oluşturmasını sağlayan Kod Belge Nesne Modeli (CodeDOM) adlı bir mekanizma içerir.</span><span class="sxs-lookup"><span data-stu-id="c0851-105">The .NET Framework includes a mechanism called the Code Document Object Model (CodeDOM) that enables developers of programs that emit source code to generate source code in multiple programming languages at run time, based on a single model that represents the code to render.</span></span>  
  
<span data-ttu-id="c0851-106">Kaynak kodunu temsil etmek için CodeDOM öğeleri birbirlerine bağlanır ve bu, bazı kaynak kodların yapısını modelleyen, CodeDOM grafiği olarak bilinen bir veri yapısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c0851-106">To represent source code, CodeDOM elements are linked to each other to form a data structure known as a CodeDOM graph, which models the structure of some source code.</span></span>  
  
<span data-ttu-id="c0851-107"><xref:System.CodeDom?displayProperty=fullName>Ad alanı, belirli bir programlama dilinden bağımsız olarak kaynak kodun mantıksal yapısını temsil eden türleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c0851-107">The <xref:System.CodeDom?displayProperty=fullName> namespace defines types that can represent the logical structure of source code, independent of a specific programming language.</span></span> <span data-ttu-id="c0851-108"><xref:System.CodeDom.Compiler?displayProperty=fullName>Ad alanı, CodeDOM grafiklerinden kaynak kodu oluşturmak ve desteklenen dillerde kaynak kodu derlemesini yönetmek için türleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c0851-108">The <xref:System.CodeDom.Compiler?displayProperty=fullName> namespace defines types for generating source code from CodeDOM graphs and managing the compilation of source code in supported languages.</span></span> <span data-ttu-id="c0851-109">Derleyici satıcıları veya geliştiriciler desteklenen dillerin kümesini genişletebilir.</span><span class="sxs-lookup"><span data-stu-id="c0851-109">Compiler vendors or developers can extend the set of supported languages.</span></span>  
  
<span data-ttu-id="c0851-110">Dilden bağımsız kaynak kodu modelleme, bir programın birden çok dilde veya belirsiz bir hedef dil için bir program modeli için kaynak kodu oluşturması gerektiğinde değerli olabilir.</span><span class="sxs-lookup"><span data-stu-id="c0851-110">Language-independent source code modeling can be valuable when a program needs to generate source code for a program model in multiple languages or for an uncertain target language.</span></span> <span data-ttu-id="c0851-111">Örneğin, bazı tasarımcılar, kaynak kodu doğru programlama dilinde oluşturmak için CodeDOM 'yi bir dil soyutlama arabirimi olarak kullanır, bu dil için CodeDOM desteği kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c0851-111">For example, some designers use the CodeDOM as a language abstraction interface to produce source code in the correct programming language, if CodeDOM support for the language is available.</span></span>  
  
<span data-ttu-id="c0851-112">.NET Framework,, ve için kod oluşturucuları ve kod derleyicileri içerir <xref:Microsoft.CSharp.CSharpCodeProvider> <xref:Microsoft.JScript.JScriptCodeProvider> <xref:Microsoft.VisualBasic.VBCodeProvider> .</span><span class="sxs-lookup"><span data-stu-id="c0851-112">The .NET Framework includes code generators and code compilers for <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>, and <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c0851-113">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="c0851-113">In this section</span></span>

- [<span data-ttu-id="c0851-114">CodeDOM'yi Kullanma</span><span class="sxs-lookup"><span data-stu-id="c0851-114">Using the CodeDOM</span></span>](using-the-codedom.md)

  <span data-ttu-id="c0851-115">Ortak kullanımları açıklar ve CodeDOM kullanılarak basit nesne grafı oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0851-115">Describes common uses, and demonstrates building a simple object graph using the CodeDOM.</span></span>  
  
- [<span data-ttu-id="c0851-116">Bir CodeDOM grafiğinden kaynak kodu oluşturma ve bir programı derleme</span><span class="sxs-lookup"><span data-stu-id="c0851-116">Generate Source Code and Compile a Program from a CodeDOM Graph</span></span>](generating-and-compiling-source-code-from-a-codedom-graph.md)  

  <span data-ttu-id="c0851-117">Kaynak kodu oluşturmayı ve ad alanında tanımlanan sınıfları kullanarak oluşturulan kodu bir dış derleyici ile derlemeyi açıklar `System.CodeDom.Compiler` .</span><span class="sxs-lookup"><span data-stu-id="c0851-117">Describes how to generate source code and compile the generated code with an external compiler using classes defined in the `System.CodeDom.Compiler` namespace.</span></span>  
  
- [<span data-ttu-id="c0851-118">Nasıl yapılır: CodeDOM Kullanarak XML Belge Dosyası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c0851-118">How to: Create an XML Documentation File Using CodeDOM</span></span>](how-to-create-an-xml-documentation-file-using-codedom.md)  

  <span data-ttu-id="c0851-119">XML belge açıklamalarıyla kod oluşturmak için CodeDOM kullanmayı ve XML belge çıkışını oluşturacak şekilde oluşturulan kodu derlemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="c0851-119">Describes how to use CodeDOM to generate code with XML documentation comments, and compile the generated code so that it creates the XML documentation output.</span></span>  
  
- [<span data-ttu-id="c0851-120">Nasıl yapılır: CodeDOM Kullanarak Sınıf Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c0851-120">How to: Create a Class Using CodeDOM</span></span>](how-to-create-a-class-using-codedom.md)  

  <span data-ttu-id="c0851-121">Alanları, özellikleri, bir yöntemi, oluşturucuyu ve bir giriş noktasını içeren bir sınıf oluşturmak için CodeDOM nasıl kullanacağınızı açıklar.</span><span class="sxs-lookup"><span data-stu-id="c0851-121">Describes how to use CodeDOM to generate a class containing fields, properties, a method, a constructor, and an entry point.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c0851-122">Başvuru</span><span class="sxs-lookup"><span data-stu-id="c0851-122">Reference</span></span>  

- <xref:System.CodeDom>  

  <span data-ttu-id="c0851-123">Ortak dil çalışma zamanını hedefleyen programlama dillerinde kod öğelerini temsil eden öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c0851-123">Defines elements that represent code elements in programming languages that target the common language runtime.</span></span>  
  
- <xref:System.CodeDom.Compiler>  

  <span data-ttu-id="c0851-124">Çalışma zamanında kod oluşturma ve derleme için arabirimler tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c0851-124">Defines interfaces for generating and compiling code at run time.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c0851-125">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="c0851-125">Related sections</span></span>  

- <span data-ttu-id="c0851-126">[CodeDOM hızlı başvurusu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100)) , geliştiricilerin kaynak kodu öğelerini temsil eden CodeDOM öğelerini bulmasını sağlayan hızlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="c0851-126">[CodeDOM Quick Reference](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f1dfsbhc(v=vs.100)) provides a quick way for developers to find the CodeDOM elements that represent source code elements.</span></span>
