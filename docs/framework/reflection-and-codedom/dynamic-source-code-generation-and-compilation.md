---
title: "Dinamik Kaynak Kodu Oluşturma ve Derleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Code Document Object Model
- System.CodeDom namespace
- language-independent source code modeling
- CodeDOM
- multiple languages supported by CodeDOM
- source code in multiple languages
- languages, multiple language support by CodeDOM
ms.assetid: d077a3e8-bd81-4bdf-b6a3-323857ea30fb
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 535a60aa1a174319a4db3403a64c3998784bbb58
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="dynamic-source-code-generation-and-compilation"></a><span data-ttu-id="0fdfe-102">Dinamik Kaynak Kodu Oluşturma ve Derleme</span><span class="sxs-lookup"><span data-stu-id="0fdfe-102">Dynamic Source Code Generation and Compilation</span></span>
<span data-ttu-id="0fdfe-103">Kod belge nesnesi kodun temsil ettiği tek bir modelini temel alan kaynak kodu çalışma zamanında birden çok programlama dillerinde oluşturmak için kaynak kodu yayma programların geliştiriciler sağlayan modeli (CodeDOM) adlı bir mekanizma .NET Framework içerir İşlenecek.</span><span class="sxs-lookup"><span data-stu-id="0fdfe-103">The .NET Framework includes a mechanism called the Code Document Object Model (CodeDOM) that enables developers of programs that emit source code to generate source code in multiple programming languages at run time, based on a single model that represents the code to render.</span></span>  
  
 <span data-ttu-id="0fdfe-104">Kaynak kodu temsil etmek için diğer bazı kaynak kod yapısını modeller CodeDOM grafik bilinen bir veri yapısı oluşturacak şekilde CodeDOM öğeleri bağlanır.</span><span class="sxs-lookup"><span data-stu-id="0fdfe-104">To represent source code, CodeDOM elements are linked to each other to form a data structure known as a CodeDOM graph, which models the structure of some source code.</span></span>  
  
 <span data-ttu-id="0fdfe-105">`System.CodeDom` Ad alanı, belirli bir programlama dilden bağımsız kaynak kodu mantıksal yapısını temsil edebilir türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0fdfe-105">The `System.CodeDom` namespace defines types that can represent the logical structure of source code, independent of a specific programming language.</span></span> <span data-ttu-id="0fdfe-106">`System.CodeDom.Compiler` Ad alanını kaynak kodu CodeDOM grafikleri oluşturma ve desteklenen dilde kaynak kodu derleme yönetmek için türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0fdfe-106">The `System.CodeDom.Compiler` namespace defines types for generating source code from CodeDOM graphs and managing the compilation of source code in supported languages.</span></span> <span data-ttu-id="0fdfe-107">Desteklenen diller kümesi derleyici satıcılar veya geliştiricilerin genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fdfe-107">Compiler vendors or developers can extend the set of supported languages.</span></span>  
  
 <span data-ttu-id="0fdfe-108">Bir program belirsiz bir hedef dil veya birden çok dilde program modeli için kaynak kodu oluşturmak gerektiğinde dilden bağımsız kaynak kodu modelleme yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="0fdfe-108">Language-independent source code modeling can be valuable when a program needs to generate source code for a program model in multiple languages or for an uncertain target language.</span></span> <span data-ttu-id="0fdfe-109">Örneğin, dil desteğini CodeDOM kullanılabilir durumdaysa bazı tasarımcıları doğru programlama dilinde kaynak kodu oluşturmak için bir dil soyutlama arabirimi CodeDOM kullanın.</span><span class="sxs-lookup"><span data-stu-id="0fdfe-109">For example, some designers use the CodeDOM as a language abstraction interface to produce source code in the correct programming language, if CodeDOM support for the language is available.</span></span>  
  
 <span data-ttu-id="0fdfe-110">.NET Framework kod oluşturucuları ve kod derleyicileri içerir <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>, ve <xref:Microsoft.VisualBasic.VBCodeProvider>.</span><span class="sxs-lookup"><span data-stu-id="0fdfe-110">The .NET Framework includes code generators and code compilers for <xref:Microsoft.CSharp.CSharpCodeProvider>, <xref:Microsoft.JScript.JScriptCodeProvider>, and <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0fdfe-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="0fdfe-111">In This Section</span></span>  
 [<span data-ttu-id="0fdfe-112">CodeDOM'yi Kullanma</span><span class="sxs-lookup"><span data-stu-id="0fdfe-112">Using the CodeDOM</span></span>](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)  
 <span data-ttu-id="0fdfe-113">Ortak kullanımlar açıklar ve CodeDOM kullanarak basit bir nesne grafik oluşturma gösterir.</span><span class="sxs-lookup"><span data-stu-id="0fdfe-113">Describes common uses, and demonstrates building a simple object graph using the CodeDOM.</span></span>  
  
 [<span data-ttu-id="0fdfe-114">Kaynak kodu oluşturma ve CodeDOM grafiğinden bir programı derleme</span><span class="sxs-lookup"><span data-stu-id="0fdfe-114">Generating Source Code and Compiling a Program from a CodeDOM Graph</span></span>](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)  
 <span data-ttu-id="0fdfe-115">Kaynak kodu oluşturma ve içinde tanımlanan sınıflar kullanarak bir dış derleyici ile oluşturulan kod derleme açıklar `System.CodeDom.Compiler` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="0fdfe-115">Describes how to generate source code and compile the generated code with an external compiler using classes defined in the `System.CodeDom.Compiler` namespace.</span></span>  
  
 [<span data-ttu-id="0fdfe-116">Nasıl yapılır: CodeDOM Kullanarak XML Belge Dosyası Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0fdfe-116">How to: Create an XML Documentation File Using CodeDOM</span></span>](../../../docs/framework/reflection-and-codedom/how-to-create-an-xml-documentation-file-using-codedom.md)  
 <span data-ttu-id="0fdfe-117">XML belgeleri yorumları koduyla oluşturup XML belgeleri çıktısı oluşturur, böylece oluşturulan kod derleme CodeDOM kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="0fdfe-117">Describes how to use CodeDOM to generate code with XML documentation comments, and compile the generated code so that it creates the XML documentation output.</span></span>  
  
 [<span data-ttu-id="0fdfe-118">Nasıl yapılır: CodeDOM Kullanarak Sınıf Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0fdfe-118">How to: Create a Class Using CodeDOM</span></span>](../../../docs/framework/reflection-and-codedom/how-to-create-a-class-using-codedom.md)  
 <span data-ttu-id="0fdfe-119">CodeDOM alanları, özellikleri, bir yöntemi, bir oluşturucu ve bir giriş noktası içeren bir sınıf oluşturmak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="0fdfe-119">Describes how to use CodeDOM to generate a class containing fields, properties, a method, a constructor, and an entry point.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0fdfe-120">Başvuru</span><span class="sxs-lookup"><span data-stu-id="0fdfe-120">Reference</span></span>  
 <xref:System.CodeDom>  
 <span data-ttu-id="0fdfe-121">Kod öğeleri programlama dillerinde hedefleyen ortak dil çalışma zamanı temsil eden öğeleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0fdfe-121">Defines elements that represent code elements in programming languages that target the common language runtime.</span></span>  
  
 <xref:System.CodeDom.Compiler>  
 <span data-ttu-id="0fdfe-122">Kodu oluşturma ve çalışma zamanında derleme için arabirimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0fdfe-122">Defines interfaces for generating and compiling code at run time.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0fdfe-123">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="0fdfe-123">Related Sections</span></span>  
 [<span data-ttu-id="0fdfe-124">CodeDOM hızlı başvuru</span><span class="sxs-lookup"><span data-stu-id="0fdfe-124">CodeDOM Quick Reference</span></span>](http://msdn.microsoft.com/library/c77b8bfd-0a32-4e36-b59a-4f687f32c524)  
 <span data-ttu-id="0fdfe-125">Geliştiricilerin kaynak kod öğeleri temsil eden CodeDOM öğeleri bulmak hızlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="0fdfe-125">Provides a quick way for developers to find the CodeDOM elements that represent source code elements.</span></span>
