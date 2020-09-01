---
description: C# Derleyici Seçenekleri
title: C# Derleyici Seçenekleri
ms.date: 07/20/2015
f1_keywords:
- cs.build.options
helpviewer_keywords:
- compiler options [C#]
- csc.exe
- cl.exe compiler, C# options
- Visual C# compiler
- Visual C#, compiler options
ms.assetid: d3403556-1816-4546-a782-e8223a772e44
ms.openlocfilehash: bcb246055ecb553bbefad2a0d5c95bf6a083ee6f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125533"
---
# <a name="c-compiler-options"></a><span data-ttu-id="b78e2-103">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="b78e2-103">C# Compiler Options</span></span>

<span data-ttu-id="b78e2-104">Derleyici yürütülebilir (. exe) dosyalar, dinamik bağlantı kitaplıkları (. dll) veya kod modülleri (. netmodule) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b78e2-104">The compiler produces executable (.exe) files, dynamic-link libraries (.dll), or code modules (.netmodule).</span></span>

<span data-ttu-id="b78e2-105">Her derleyici seçeneği iki biçimde mevcuttur: **-Option** ve **/Option**.</span><span class="sxs-lookup"><span data-stu-id="b78e2-105">Every compiler option is available in two forms: **-option** and **/option**.</span></span> <span data-ttu-id="b78e2-106">Belgeler yalnızca **-seçenek** formunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b78e2-106">The documentation only shows the **-option** form.</span></span>

<span data-ttu-id="b78e2-107">Visual Studio 'da *web.config* dosyasında derleyici seçeneklerini ayarlarsınız.</span><span class="sxs-lookup"><span data-stu-id="b78e2-107">In Visual Studio, you set compiler options in the *web.config* file.</span></span> <span data-ttu-id="b78e2-108">Daha fazla bilgi için bkz. [ \<compiler> öğesi](../../../framework/configure-apps/file-schema/compiler/compiler-element.md).</span><span class="sxs-lookup"><span data-stu-id="b78e2-108">For more information, see [\<compiler> Element](../../../framework/configure-apps/file-schema/compiler/compiler-element.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="b78e2-109">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="b78e2-109">In this section</span></span>

- <span data-ttu-id="b78e2-110">[csc.exeIle komut satırı oluşturma ](command-line-building-with-csc-exe.md) Komut satırından bir Visual C# uygulaması oluşturma hakkında bilgi.</span><span class="sxs-lookup"><span data-stu-id="b78e2-110">[Command-line Building With csc.exe](command-line-building-with-csc-exe.md) Information about building a Visual C# application from the command line.</span></span>

- <span data-ttu-id="b78e2-111">[Visual Studio komut satırı için ortam değişkenlerini ayarlama](how-to-set-environment-variables-for-the-visual-studio-command-line.md) Komut satırı yapılarını etkinleştirmek üzere *vsvars32.bat* çalıştırmak için adımlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="b78e2-111">[How to set environment variables for the Visual Studio Command Line](how-to-set-environment-variables-for-the-visual-studio-command-line.md) Provides steps for running *vsvars32.bat* to enable command-line builds.</span></span>

- <span data-ttu-id="b78e2-112">[Kategoriye göre listelenen C# derleyici seçenekleri](listed-by-category.md) Derleyici seçeneklerinin kategorik bir listesi.</span><span class="sxs-lookup"><span data-stu-id="b78e2-112">[C# Compiler Options Listed by Category](listed-by-category.md) A categorical listing of the compiler options.</span></span>

- <span data-ttu-id="b78e2-113">[Alfabetik olarak listelenen C# derleyici seçenekleri](listed-alphabetically.md) Derleyici seçeneklerinin alfabetik bir listesi.</span><span class="sxs-lookup"><span data-stu-id="b78e2-113">[C# Compiler Options Listed Alphabetically](listed-alphabetically.md) An alphabetical listing of the compiler options.</span></span>

## <a name="related-sections"></a><span data-ttu-id="b78e2-114">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="b78e2-114">Related sections</span></span>

- <span data-ttu-id="b78e2-115">[Derleme sayfası, proje Tasarımcısı](/visualstudio/ide/reference/build-page-project-designer-csharp) Projenizin nasıl derlendiğini, oluşturulduğunu ve hata ayıklandığını yöneten özellikleri ayarlama.</span><span class="sxs-lookup"><span data-stu-id="b78e2-115">[Build Page, Project Designer](/visualstudio/ide/reference/build-page-project-designer-csharp) Setting properties that govern how your project is compiled, built, and debugged.</span></span> <span data-ttu-id="b78e2-116">Visual C# projelerindeki özel derleme adımları hakkındaki bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="b78e2-116">Includes information about custom build steps in Visual C# projects.</span></span>

- <span data-ttu-id="b78e2-117">[Varsayılan ve özel derlemeler](/visualstudio/ide/compiling-and-building-in-visual-studio) Yapı türleri ve yapılandırmalara ilişkin bilgiler.</span><span class="sxs-lookup"><span data-stu-id="b78e2-117">[Default and Custom Builds](/visualstudio/ide/compiling-and-building-in-visual-studio) Information on build types and configurations.</span></span>

- <span data-ttu-id="b78e2-118">[Derlemeleri hazırlama ve yönetme](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) Visual Studio geliştirme ortamı içinde oluşturmaya yönelik yordamlar.</span><span class="sxs-lookup"><span data-stu-id="b78e2-118">[Preparing and Managing Builds](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) Procedures for building within the Visual Studio development environment.</span></span>
