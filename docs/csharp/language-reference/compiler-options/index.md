---
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
ms.openlocfilehash: dab91ddd1f2b9c91560329eeb1c51ca7f6f175bd
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73455254"
---
# <a name="c-compiler-options"></a><span data-ttu-id="eaca3-102">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="eaca3-102">C# Compiler Options</span></span>

<span data-ttu-id="eaca3-103">Derleyici yürütülebilir (. exe) dosyalar, dinamik bağlantı kitaplıkları (. dll) veya kod modülleri (. netmodule) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="eaca3-103">The compiler produces executable (.exe) files, dynamic-link libraries (.dll), or code modules (.netmodule).</span></span>

<span data-ttu-id="eaca3-104">Her derleyici seçeneği iki biçimde mevcuttur: **-Option** ve **/Option**.</span><span class="sxs-lookup"><span data-stu-id="eaca3-104">Every compiler option is available in two forms: **-option** and **/option**.</span></span> <span data-ttu-id="eaca3-105">Belgeler yalnızca **-seçenek** formunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="eaca3-105">The documentation only shows the **-option** form.</span></span>

<span data-ttu-id="eaca3-106">Visual Studio 'da, *Web. config* dosyasında derleyici seçeneklerini ayarlarsınız.</span><span class="sxs-lookup"><span data-stu-id="eaca3-106">In Visual Studio, you set compiler options in the *web.config* file.</span></span> <span data-ttu-id="eaca3-107">Daha fazla bilgi için bkz. [\<derleyici > öğesi](../../../framework/configure-apps/file-schema/compiler/compiler-element.md).</span><span class="sxs-lookup"><span data-stu-id="eaca3-107">For more information, see [\<compiler> Element](../../../framework/configure-apps/file-schema/compiler/compiler-element.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="eaca3-108">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="eaca3-108">In this section</span></span>

- <span data-ttu-id="eaca3-109">[CSC. exe Ile komut satırı oluşturma](command-line-building-with-csc-exe.md) Komut satırından görsel C# uygulama oluşturma hakkında bilgi.</span><span class="sxs-lookup"><span data-stu-id="eaca3-109">[Command-line Building With csc.exe](command-line-building-with-csc-exe.md) Information about building a Visual C# application from the command line.</span></span>

- <span data-ttu-id="eaca3-110">[Nasıl yapılır: Visual Studio komut satırı Için ortam değişkenlerini ayarlama](how-to-set-environment-variables-for-the-visual-studio-command-line.md) Komut satırı yapılarını etkinleştirmek için *vsvars32. bat* dosyasını çalıştırmaya yönelik adımları sağlar.</span><span class="sxs-lookup"><span data-stu-id="eaca3-110">[How to: Set Environment Variables for the Visual Studio Command Line](how-to-set-environment-variables-for-the-visual-studio-command-line.md) Provides steps for running *vsvars32.bat* to enable command-line builds.</span></span>

- <span data-ttu-id="eaca3-111">[Kategoriye göre listelenen derleyici seçenekleri C# ](listed-by-category.md) Derleyici seçeneklerinin kategorik bir listesi.</span><span class="sxs-lookup"><span data-stu-id="eaca3-111">[C# Compiler Options Listed by Category](listed-by-category.md) A categorical listing of the compiler options.</span></span>

- <span data-ttu-id="eaca3-112">[Alfabetik olarak listelenen derleyici seçenekleri C# ](listed-alphabetically.md) Derleyici seçeneklerinin alfabetik bir listesi.</span><span class="sxs-lookup"><span data-stu-id="eaca3-112">[C# Compiler Options Listed Alphabetically](listed-alphabetically.md) An alphabetical listing of the compiler options.</span></span>

## <a name="related-sections"></a><span data-ttu-id="eaca3-113">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="eaca3-113">Related sections</span></span>

- <span data-ttu-id="eaca3-114">[Derleme sayfası, proje Tasarımcısı](/visualstudio/ide/reference/build-page-project-designer-csharp) Projenizin nasıl derlendiğini, oluşturulduğunu ve hata ayıklandığını yöneten özellikleri ayarlama.</span><span class="sxs-lookup"><span data-stu-id="eaca3-114">[Build Page, Project Designer](/visualstudio/ide/reference/build-page-project-designer-csharp) Setting properties that govern how your project is compiled, built, and debugged.</span></span> <span data-ttu-id="eaca3-115">Görsel C# projelerdeki özel derleme adımları hakkındaki bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="eaca3-115">Includes information about custom build steps in Visual C# projects.</span></span>

- <span data-ttu-id="eaca3-116">[Varsayılan ve özel derlemeler](/visualstudio/ide/compiling-and-building-in-visual-studio) Yapı türleri ve yapılandırmalara ilişkin bilgiler.</span><span class="sxs-lookup"><span data-stu-id="eaca3-116">[Default and Custom Builds](/visualstudio/ide/compiling-and-building-in-visual-studio) Information on build types and configurations.</span></span>

- <span data-ttu-id="eaca3-117">[Derlemeleri hazırlama ve yönetme](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) Visual Studio geliştirme ortamı içinde oluşturmaya yönelik yordamlar.</span><span class="sxs-lookup"><span data-stu-id="eaca3-117">[Preparing and Managing Builds](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) Procedures for building within the Visual Studio development environment.</span></span>
