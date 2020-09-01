---
description: C# Derleyici Seçenekleri
title: C# Derleyici Seçenekleri
ms.date: 08/28/2020
f1_keywords:
- cs.build.options
helpviewer_keywords:
- compiler options [C#]
- csc.exe
- cl.exe compiler, C# options
- Visual C# compiler
- Visual C#, compiler options
ms.assetid: d3403556-1816-4546-a782-e8223a772e44
ms.openlocfilehash: 502bd83ae52be9ae2f914847bb6bf7c7f2a0c411
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271821"
---
# <a name="c-compiler-options"></a><span data-ttu-id="a0d78-103">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="a0d78-103">C# Compiler Options</span></span>

<span data-ttu-id="a0d78-104">Derleyici yürütülebilir (. exe) dosyalar, dinamik bağlantı kitaplıkları (. dll) veya kod modülleri (. netmodule) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a0d78-104">The compiler produces executable (.exe) files, dynamic-link libraries (.dll), or code modules (.netmodule).</span></span>

<span data-ttu-id="a0d78-105">Her derleyici seçeneği iki biçimde mevcuttur: **-Option** ve **/Option**.</span><span class="sxs-lookup"><span data-stu-id="a0d78-105">Every compiler option is available in two forms: **-option** and **/option**.</span></span> <span data-ttu-id="a0d78-106">Belgeler yalnızca **-seçenek** formunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a0d78-106">The documentation only shows the **-option** form.</span></span>

<span data-ttu-id="a0d78-107">Visual Studio 'da *web.config* dosyasında derleyici seçeneklerini ayarlarsınız.</span><span class="sxs-lookup"><span data-stu-id="a0d78-107">In Visual Studio, you set compiler options in the *web.config* file.</span></span> <span data-ttu-id="a0d78-108">Daha fazla bilgi için bkz. [ \<compiler> öğesi](../../../framework/configure-apps/file-schema/compiler/compiler-element.md).</span><span class="sxs-lookup"><span data-stu-id="a0d78-108">For more information, see [\<compiler> Element](../../../framework/configure-apps/file-schema/compiler/compiler-element.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a0d78-109">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="a0d78-109">In this section</span></span>

- <span data-ttu-id="a0d78-110">[csc.exeIle komut satırı oluşturma ](command-line-building-with-csc-exe.md) Komut satırından bir Visual C# uygulaması oluşturma hakkında bilgi.</span><span class="sxs-lookup"><span data-stu-id="a0d78-110">[Command-line Building With csc.exe](command-line-building-with-csc-exe.md) Information about building a Visual C# application from the command line.</span></span>

- <span data-ttu-id="a0d78-111">[Visual Studio komut satırı için ortam değişkenlerini ayarlama](how-to-set-environment-variables-for-the-visual-studio-command-line.md) Komut satırı yapılarını etkinleştirmek üzere *VsDevCmd.bat* çalıştırmak için adımlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0d78-111">[How to set environment variables for the Visual Studio Command Line](how-to-set-environment-variables-for-the-visual-studio-command-line.md) Provides steps for running *VsDevCmd.bat* to enable command-line builds.</span></span>

- <span data-ttu-id="a0d78-112">[Kategoriye göre listelenen C# derleyici seçenekleri](listed-by-category.md) Derleyici seçeneklerinin kategorik bir listesi.</span><span class="sxs-lookup"><span data-stu-id="a0d78-112">[C# Compiler Options Listed by Category](listed-by-category.md) A categorical listing of the compiler options.</span></span>

- <span data-ttu-id="a0d78-113">[Alfabetik olarak listelenen C# derleyici seçenekleri](listed-alphabetically.md) Derleyici seçeneklerinin alfabetik bir listesi.</span><span class="sxs-lookup"><span data-stu-id="a0d78-113">[C# Compiler Options Listed Alphabetically](listed-alphabetically.md) An alphabetical listing of the compiler options.</span></span>

## <a name="related-sections"></a><span data-ttu-id="a0d78-114">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="a0d78-114">Related sections</span></span>

- <span data-ttu-id="a0d78-115">[Derleme sayfası, proje Tasarımcısı](/visualstudio/ide/reference/build-page-project-designer-csharp) Projenizin nasıl derlendiğini, oluşturulduğunu ve hata ayıklandığını yöneten özellikleri ayarlama.</span><span class="sxs-lookup"><span data-stu-id="a0d78-115">[Build Page, Project Designer](/visualstudio/ide/reference/build-page-project-designer-csharp) Setting properties that govern how your project is compiled, built, and debugged.</span></span> <span data-ttu-id="a0d78-116">Visual C# projelerindeki özel derleme adımları hakkındaki bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="a0d78-116">Includes information about custom build steps in Visual C# projects.</span></span>

- <span data-ttu-id="a0d78-117">[Varsayılan ve özel derlemeler](/visualstudio/ide/compiling-and-building-in-visual-studio) Yapı türleri ve yapılandırmalara ilişkin bilgiler.</span><span class="sxs-lookup"><span data-stu-id="a0d78-117">[Default and Custom Builds](/visualstudio/ide/compiling-and-building-in-visual-studio) Information on build types and configurations.</span></span>

- <span data-ttu-id="a0d78-118">[Derlemeleri hazırlama ve yönetme](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) Visual Studio geliştirme ortamı içinde oluşturmaya yönelik yordamlar.</span><span class="sxs-lookup"><span data-stu-id="a0d78-118">[Preparing and Managing Builds](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) Procedures for building within the Visual Studio development environment.</span></span>
