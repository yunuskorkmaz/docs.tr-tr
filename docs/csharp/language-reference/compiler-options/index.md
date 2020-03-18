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
ms.openlocfilehash: 787f9c5fff79eb67e2d74043782532c1fc4034b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73972758"
---
# <a name="c-compiler-options"></a><span data-ttu-id="43601-102">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="43601-102">C# Compiler Options</span></span>

<span data-ttu-id="43601-103">Derleyici çalıştırılabilir (.exe) dosyaları, dinamik bağlantı kitaplıkları (.dll) veya kod modülleri (.netmodule) üretir.</span><span class="sxs-lookup"><span data-stu-id="43601-103">The compiler produces executable (.exe) files, dynamic-link libraries (.dll), or code modules (.netmodule).</span></span>

<span data-ttu-id="43601-104">Her derleyici seçeneği iki şekilde kullanılabilir: **-option** ve **/option**.</span><span class="sxs-lookup"><span data-stu-id="43601-104">Every compiler option is available in two forms: **-option** and **/option**.</span></span> <span data-ttu-id="43601-105">Belgeler yalnızca **seçenek** formunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="43601-105">The documentation only shows the **-option** form.</span></span>

<span data-ttu-id="43601-106">Visual Studio'da, *web.config* dosyasında derleyici seçeneklerini ayarlarsınız.</span><span class="sxs-lookup"><span data-stu-id="43601-106">In Visual Studio, you set compiler options in the *web.config* file.</span></span> <span data-ttu-id="43601-107">Daha fazla bilgi için [ \<derleyici> Öğesi'ne](../../../framework/configure-apps/file-schema/compiler/compiler-element.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="43601-107">For more information, see [\<compiler> Element](../../../framework/configure-apps/file-schema/compiler/compiler-element.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="43601-108">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="43601-108">In this section</span></span>

- <span data-ttu-id="43601-109">[komut satırı Bina csc.exe ile](command-line-building-with-csc-exe.md) Komut satırından Visual C# uygulaması oluşturma hakkında bilgi.</span><span class="sxs-lookup"><span data-stu-id="43601-109">[Command-line Building With csc.exe](command-line-building-with-csc-exe.md) Information about building a Visual C# application from the command line.</span></span>

- <span data-ttu-id="43601-110">[Visual Studio Komut Satırı için ortam değişkenleri nasıl ayarlanır?](how-to-set-environment-variables-for-the-visual-studio-command-line.md) Komut satırı yapılarını etkinleştirmek için *vsvars32.bat'ı* çalıştırmak için adımlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="43601-110">[How to set environment variables for the Visual Studio Command Line](how-to-set-environment-variables-for-the-visual-studio-command-line.md) Provides steps for running *vsvars32.bat* to enable command-line builds.</span></span>

- <span data-ttu-id="43601-111">[C# Derleyici Seçenekleri Kategoriye Göre Listelendi](listed-by-category.md) Derleyici seçeneklerinin kategorik bir listesi.</span><span class="sxs-lookup"><span data-stu-id="43601-111">[C# Compiler Options Listed by Category](listed-by-category.md) A categorical listing of the compiler options.</span></span>

- <span data-ttu-id="43601-112">[C# Derleyici Seçenekleri Alfabetik Olarak Listelenmiştir](listed-alphabetically.md) Derleyici seçeneklerinin alfabetik listesi.</span><span class="sxs-lookup"><span data-stu-id="43601-112">[C# Compiler Options Listed Alphabetically](listed-alphabetically.md) An alphabetical listing of the compiler options.</span></span>

## <a name="related-sections"></a><span data-ttu-id="43601-113">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="43601-113">Related sections</span></span>

- <span data-ttu-id="43601-114">[Yapı Sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/build-page-project-designer-csharp) Projenizin nasıl derlendiğini, oluşturulup debutedildiğini yöneten özellikleri ayarlama.</span><span class="sxs-lookup"><span data-stu-id="43601-114">[Build Page, Project Designer](/visualstudio/ide/reference/build-page-project-designer-csharp) Setting properties that govern how your project is compiled, built, and debugged.</span></span> <span data-ttu-id="43601-115">Visual C# projelerinde özel yapı adımları hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="43601-115">Includes information about custom build steps in Visual C# projects.</span></span>

- <span data-ttu-id="43601-116">[Varsayılan ve Özel Yapılar](/visualstudio/ide/compiling-and-building-in-visual-studio) Yapı türleri ve yapılandırmaları hakkında bilgi.</span><span class="sxs-lookup"><span data-stu-id="43601-116">[Default and Custom Builds](/visualstudio/ide/compiling-and-building-in-visual-studio) Information on build types and configurations.</span></span>

- <span data-ttu-id="43601-117">[Yapı Ların Hazırlanması ve Yönetilmesi](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) Visual Studio geliştirme ortamı içinde bina için prosedürler.</span><span class="sxs-lookup"><span data-stu-id="43601-117">[Preparing and Managing Builds](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) Procedures for building within the Visual Studio development environment.</span></span>
