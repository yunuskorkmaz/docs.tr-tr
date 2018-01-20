---
title: "C# Derleyici Seçenekleri"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: cs.build.options
helpviewer_keywords:
- compiler options [C#]
- csc.exe
- cl.exe compiler, C# options
- Visual C# compiler
- Visual C#, compiler options
ms.assetid: d3403556-1816-4546-a782-e8223a772e44
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 59000f60acdc8ada11bc5abb9e91b5f53d42b9ae
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="c-compiler-options"></a><span data-ttu-id="6e7dd-102">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="6e7dd-102">C# Compiler Options</span></span>
<span data-ttu-id="6e7dd-103">Derleyici yürütülebilir dosyanın (.exe) dosyaları, dinamik bağlantı kitaplıkları (.dll) veya kod modülleri üretir (.netmodule).</span><span class="sxs-lookup"><span data-stu-id="6e7dd-103">The compiler produces executable (.exe) files, dynamic-link libraries (.dll), or code modules (.netmodule).</span></span>  
  
 <span data-ttu-id="6e7dd-104">Her derleyici seçeneği iki biçimde sağlanır: **-seçeneği** ve **/seçeneği**.</span><span class="sxs-lookup"><span data-stu-id="6e7dd-104">Every compiler option is available in two forms: **-option** and **/option**.</span></span> <span data-ttu-id="6e7dd-105">Belgelere yalnızca gösterir **-seçeneği** formu.</span><span class="sxs-lookup"><span data-stu-id="6e7dd-105">The documentation only shows the **-option** form.</span></span>  
  
 <span data-ttu-id="6e7dd-106">Visual Studio'da, web.config dosyasında derleyici seçeneklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6e7dd-106">In Visual Studio, you set compiler options in the web.config file.</span></span> <span data-ttu-id="6e7dd-107">Daha fazla bilgi için bkz: [ \<derleyici > öğesi](../../../framework/configure-apps/file-schema/compiler/compiler-element.md).</span><span class="sxs-lookup"><span data-stu-id="6e7dd-107">For more information, see [\<compiler> Element](../../../framework/configure-apps/file-schema/compiler/compiler-element.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6e7dd-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6e7dd-108">In This Section</span></span>  
 [<span data-ttu-id="6e7dd-109">csc.exe Kullanarak Komut Satırı Derleme</span><span class="sxs-lookup"><span data-stu-id="6e7dd-109">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 <span data-ttu-id="6e7dd-110">Visual C# uygulamasını komut satırından oluşturma hakkında bilgi.</span><span class="sxs-lookup"><span data-stu-id="6e7dd-110">Information about building a Visual C# application from the command line.</span></span>  
  
 [<span data-ttu-id="6e7dd-111">Nasıl yapılır: Visual Studio Komut Satırı için Ortam Değişkenlerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="6e7dd-111">How to: Set Environment Variables for the Visual Studio Command Line</span></span>](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)  
 <span data-ttu-id="6e7dd-112">Komut satırı derlemeleri etkinleştirmek için vsvars32.bat çalıştırmak için adımları sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e7dd-112">Provides steps for running vsvars32.bat  to enable command-line builds.</span></span>  
  
 [<span data-ttu-id="6e7dd-113">Kategorilere Göre Listelenen C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="6e7dd-113">C# Compiler Options Listed by Category</span></span>](../../../csharp/language-reference/compiler-options/listed-by-category.md)  
 <span data-ttu-id="6e7dd-114">Derleyici Seçenekleri Kategorik bir listesi.</span><span class="sxs-lookup"><span data-stu-id="6e7dd-114">A categorical listing of the compiler options.</span></span>  
  
 [<span data-ttu-id="6e7dd-115">Alfabetik Listelenmiş C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="6e7dd-115">C# Compiler Options Listed Alphabetically</span></span>](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
 <span data-ttu-id="6e7dd-116">Derleyici seçenekleri alfabetik bir listesi.</span><span class="sxs-lookup"><span data-stu-id="6e7dd-116">An alphabetical listing of the compiler options.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6e7dd-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="6e7dd-117">Related Sections</span></span>  
 [<span data-ttu-id="6e7dd-118">Derleme sayfası, Proje Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="6e7dd-118">Build Page, Project Designer</span></span>](/visualstudio/ide/reference/build-page-project-designer-csharp)  
 <span data-ttu-id="6e7dd-119">Projenizin nasıl derleneceğini, yöneten özelliklerini ayarlama oluşturulmuş ve hata ayıklaması.</span><span class="sxs-lookup"><span data-stu-id="6e7dd-119">Setting properties that govern how your project is compiled, built, and debugged.</span></span> <span data-ttu-id="6e7dd-120">Visual C# projelerine özel derleme adımları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="6e7dd-120">Includes information about custom build steps in Visual C# projects.</span></span>  
  
 [<span data-ttu-id="6e7dd-121">Varsayılan ve özel yapılar</span><span class="sxs-lookup"><span data-stu-id="6e7dd-121">Default and Custom Builds</span></span>](/visualstudio/ide/compiling-and-building-in-visual-studio)  
 <span data-ttu-id="6e7dd-122">Yapı türleri ve yapılandırmalar hakkında bilgiler.</span><span class="sxs-lookup"><span data-stu-id="6e7dd-122">Information on build types and configurations.</span></span>  
  
 [<span data-ttu-id="6e7dd-123">Yapılandırmaları hazırlama ve yönetme</span><span class="sxs-lookup"><span data-stu-id="6e7dd-123">Preparing and Managing Builds</span></span>](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 <span data-ttu-id="6e7dd-124">Visual Studio geliştirme ortamında oluşturma için yordamlar.</span><span class="sxs-lookup"><span data-stu-id="6e7dd-124">Procedures for building within the Visual Studio development environment.</span></span>
