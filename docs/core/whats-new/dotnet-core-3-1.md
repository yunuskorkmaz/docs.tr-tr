---
title: ​.NET Core 3.1’deki yenilikler
description: .NET Core 3,1 ' de bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 323a2390f079c17b81db01e4e3787916251943bf
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156562"
---
# <a name="whats-new-in-net-core-31"></a><span data-ttu-id="30e78-103">​.NET Core 3.1’deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="30e78-103">What's new in .NET Core 3.1</span></span>

<span data-ttu-id="30e78-104">Bu makalede .NET Core 3,1 ' deki yenilikler açıklanır.</span><span class="sxs-lookup"><span data-stu-id="30e78-104">This article describes what is new in .NET Core 3.1.</span></span> <span data-ttu-id="30e78-105">Bu sürüm, .NET Core 3,0 ' de küçük, küçük, ancak önemli düzeltmeleri içeren küçük iyileştirmeler içerir.</span><span class="sxs-lookup"><span data-stu-id="30e78-105">This release contains minor improvements to .NET Core 3.0, focusing on small, but important, fixes.</span></span> <span data-ttu-id="30e78-106">.NET Core 3,1 hakkındaki en önemli özellik, [uzun süreli destek (LTS)](#long-term-support) sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="30e78-106">The most important feature about .NET Core 3.1 is that it's a [long-term support (LTS)](#long-term-support) release.</span></span>

<span data-ttu-id="30e78-107">Visual Studio 2019 kullanıyorsanız, .NET Core 3,1 projeleriyle çalışmak için [Visual studio 2019 sürüm 16,4](https://visualstudio.microsoft.com/downloads/) ' e güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="30e78-107">If you're using Visual Studio 2019, you must update to [Visual Studio 2019 version 16.4](https://visualstudio.microsoft.com/downloads/) to work with .NET Core 3.1 projects.</span></span> <span data-ttu-id="30e78-108">Visual Studio 'daki yenilikler hakkında daha fazla bilgi için bkz. [Visual studio 2019 sürüm 16,4 ' deki](/visualstudio/releases/2019/release-notes#whats-new-in-visual-studio-2019-version-164)yenilikler.</span><span class="sxs-lookup"><span data-stu-id="30e78-108">For more information on what's new in Visual Studio, see [What's New in Visual Studio 2019 version 16.4](/visualstudio/releases/2019/release-notes#whats-new-in-visual-studio-2019-version-164).</span></span>

<span data-ttu-id="30e78-109">Mac için Visual Studio Ayrıca, Mac için Visual Studio 8,4 ' de .NET Core 3,1 ' u destekler ve içerir.</span><span class="sxs-lookup"><span data-stu-id="30e78-109">Visual Studio for Mac also supports and includes .NET Core 3.1 in Visual Studio for Mac 8.4.</span></span>

<span data-ttu-id="30e78-110">Yayın hakkında daha fazla bilgi için bkz. [.NET Core 3,1 duyurusu](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span><span class="sxs-lookup"><span data-stu-id="30e78-110">For more information about the release, see the [.NET Core 3.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

- <span data-ttu-id="30e78-111">Windows, macOS veya Linux 'ta [.NET Core 3,1 'Yi indirip kullanmaya](https://dotnet.microsoft.com/download/dotnet-core/3.1) başlayın.</span><span class="sxs-lookup"><span data-stu-id="30e78-111">[Download and get started with .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) on Windows, macOS, or Linux.</span></span>

## <a name="long-term-support"></a><span data-ttu-id="30e78-112">Uzun süreli destek</span><span class="sxs-lookup"><span data-stu-id="30e78-112">Long-term support</span></span>

<span data-ttu-id="30e78-113">.NET Core 3,1, bir sonraki üç yılda Microsoft desteğiyle desteklenen bir LTS sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="30e78-113">.NET Core 3.1 is an LTS release with support from Microsoft for the next three years.</span></span> <span data-ttu-id="30e78-114">Uygulamalarınızı .NET Core 3,1 ' e taşımanız önemle tavsiye edilir.</span><span class="sxs-lookup"><span data-stu-id="30e78-114">It's highly recommended that you move your apps to .NET Core 3.1.</span></span> <span data-ttu-id="30e78-115">Diğer ana yayınların geçerli yaşam döngüsü aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="30e78-115">The current lifecycle of other major releases is as follows:</span></span>

| <span data-ttu-id="30e78-116">Yayınla</span><span class="sxs-lookup"><span data-stu-id="30e78-116">Release</span></span> | <span data-ttu-id="30e78-117">Not</span><span class="sxs-lookup"><span data-stu-id="30e78-117">Note</span></span> |
| ------- | ---- |
| <span data-ttu-id="30e78-118">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="30e78-118">.NET Core 3.0</span></span> | <span data-ttu-id="30e78-119">3 Mart 2020 ' de yaşam sonu.</span><span class="sxs-lookup"><span data-stu-id="30e78-119">End of life on March 3, 2020.</span></span>     |
| <span data-ttu-id="30e78-120">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="30e78-120">.NET Core 2.2</span></span> | <span data-ttu-id="30e78-121">23 Aralık 2019 ' de yaşam sonu.</span><span class="sxs-lookup"><span data-stu-id="30e78-121">End of life on December 23, 2019.</span></span> |
| <span data-ttu-id="30e78-122">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="30e78-122">.NET Core 2.1</span></span> | <span data-ttu-id="30e78-123">21 Ağustos 2021 ' de yaşam sonu.</span><span class="sxs-lookup"><span data-stu-id="30e78-123">End of life on August 21, 2021.</span></span>    |

<span data-ttu-id="30e78-124">Daha fazla bilgi için bkz. [.NET Core destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="30e78-124">For more information, see the [.NET Core support policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

## <a name="macos-apphost-and-notarization"></a><span data-ttu-id="30e78-125">macOS appHost ve notarlama</span><span class="sxs-lookup"><span data-stu-id="30e78-125">macOS appHost and notarization</span></span>

<span data-ttu-id="30e78-126">*yalnızca macOS*</span><span class="sxs-lookup"><span data-stu-id="30e78-126">*macOS only*</span></span>

<span data-ttu-id="30e78-127">MacOS için .NET Core SDK 3,1 ' den başlayarak, appHost ayarı varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="30e78-127">Starting with the notarized .NET Core SDK 3.1 for macOS, the appHost setting is disabled by default.</span></span> <span data-ttu-id="30e78-128">Daha fazla bilgi için bkz. [MacOS Catalina Notarleştirme ve .NET Core indirmeleri ve projeleri üzerindeki etki](../install/macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="30e78-128">For more information, see [macOS Catalina Notarization and the impact on .NET Core downloads and projects](../install/macos-notarization-issues.md).</span></span>

<span data-ttu-id="30e78-129">AppHost ayarı etkinleştirildiğinde, .NET Core, oluşturduğunuzda veya yayımladığınızda yerel bir MAK-O çalıştırılabilir dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="30e78-129">When the appHost setting is enabled, .NET Core generates a native Mach-O executable when you build or publish.</span></span> <span data-ttu-id="30e78-130">Uygulamanız, `dotnet run` komutuyla kaynak koddan çalıştırıldığında veya mak-O yürütülebilir dosyasını doğrudan başlatarak appHost bağlamında çalışır.</span><span class="sxs-lookup"><span data-stu-id="30e78-130">Your app runs in the context of the appHost when it is run from source code with the `dotnet run` command, or by starting the Mach-O executable directly.</span></span>

<span data-ttu-id="30e78-131">AppHost olmadan, bir kullanıcıya [çalışma zamanına bağımlı](../deploying/index.md#publish-runtime-dependent) bir uygulama başlatabilir tek yol `dotnet <filename.dll>` komuttur.</span><span class="sxs-lookup"><span data-stu-id="30e78-131">Without the appHost, the only way a user can start a [runtime-dependent](../deploying/index.md#publish-runtime-dependent) app is with the `dotnet <filename.dll>` command.</span></span> <span data-ttu-id="30e78-132">Uygulamanızı [kendi içinde](../deploying/index.md#publish-self-contained)yayımladığınızda her zaman bir appHost oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="30e78-132">An appHost is always created when you publish your app [self-contained](../deploying/index.md#publish-self-contained).</span></span>

<span data-ttu-id="30e78-133">AppHost 'yi proje düzeyinde yapılandırabilir ya da `-p:UseAppHost` parametresiyle belirli bir `dotnet` komutu için appHost ' yi değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="30e78-133">You can either configure the appHost at the project level, or toggle the appHost for a specific `dotnet` command with the `-p:UseAppHost` parameter:</span></span>

- <span data-ttu-id="30e78-134">Proje dosyası</span><span class="sxs-lookup"><span data-stu-id="30e78-134">Project file</span></span>

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- <span data-ttu-id="30e78-135">Komut satırı parametresi</span><span class="sxs-lookup"><span data-stu-id="30e78-135">Command-line parameter</span></span>

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

<span data-ttu-id="30e78-136">`UseAppHost` ayarı hakkında daha fazla bilgi için bkz. [Microsoft. net. SDK Için MSBuild özellikleri](../project-sdk/msbuild-props.md#useapphost).</span><span class="sxs-lookup"><span data-stu-id="30e78-136">For more information about the `UseAppHost` setting, see [MSBuild properties for Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span></span>

## <a name="windows-forms"></a><span data-ttu-id="30e78-137">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="30e78-137">Windows Forms</span></span>

<span data-ttu-id="30e78-138">*Yalnızca Windows*</span><span class="sxs-lookup"><span data-stu-id="30e78-138">*Windows only*</span></span>

> [!WARNING]
> <span data-ttu-id="30e78-139">Windows Forms üzerinde önemli değişiklikler var.</span><span class="sxs-lookup"><span data-stu-id="30e78-139">There are breaking changes in Windows Forms.</span></span>

<span data-ttu-id="30e78-140">Eski denetimler, Visual Studio Tasarımcı araç kutusunda bir süredir kullanılamayan Windows Forms eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="30e78-140">Legacy controls were included in Windows Forms that have been unavailable in the Visual Studio Designer Toolbox for some time.</span></span> <span data-ttu-id="30e78-141">Bunlar .NET Framework 2,0 ' deki yeni denetimlerle değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="30e78-141">These were replaced with new controls back in .NET Framework 2.0.</span></span> <span data-ttu-id="30e78-142">Bunlar .NET Core 3,1 için masaüstü SDK 'dan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="30e78-142">These have been removed from the Desktop SDK for .NET Core 3.1.</span></span>

| <span data-ttu-id="30e78-143">Denetim kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="30e78-143">Removed control</span></span> | <span data-ttu-id="30e78-144">Önerilen değiştirme</span><span class="sxs-lookup"><span data-stu-id="30e78-144">Recommended replacement</span></span> | <span data-ttu-id="30e78-145">İlişkili API 'Ler kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="30e78-145">Associated APIs removed</span></span> |
| --------------- | ----------------------- | ----------------------- |
| <span data-ttu-id="30e78-146">DataGrid</span><span class="sxs-lookup"><span data-stu-id="30e78-146">DataGrid</span></span>        | <xref:System.Windows.Forms.DataGridView>      | <span data-ttu-id="30e78-147">DataGridCell</span><span class="sxs-lookup"><span data-stu-id="30e78-147">DataGridCell</span></span><br/><span data-ttu-id="30e78-148">DataGridRow</span><span class="sxs-lookup"><span data-stu-id="30e78-148">DataGridRow</span></span><br/><span data-ttu-id="30e78-149">DataGridTableCollection</span><span class="sxs-lookup"><span data-stu-id="30e78-149">DataGridTableCollection</span></span><br/><span data-ttu-id="30e78-150">DataGridColumnCollection</span><span class="sxs-lookup"><span data-stu-id="30e78-150">DataGridColumnCollection</span></span><br/><span data-ttu-id="30e78-151">'Da</span><span class="sxs-lookup"><span data-stu-id="30e78-151">DataGridTableStyle</span></span><br/><span data-ttu-id="30e78-152">DataGridColumnStyle</span><span class="sxs-lookup"><span data-stu-id="30e78-152">DataGridColumnStyle</span></span><br/><span data-ttu-id="30e78-153">DataGridLineStyle</span><span class="sxs-lookup"><span data-stu-id="30e78-153">DataGridLineStyle</span></span><br/><span data-ttu-id="30e78-154">DataGridParentRowsLabel</span><span class="sxs-lookup"><span data-stu-id="30e78-154">DataGridParentRowsLabel</span></span><br/><span data-ttu-id="30e78-155">DataGridParentRowsLabelStyle</span><span class="sxs-lookup"><span data-stu-id="30e78-155">DataGridParentRowsLabelStyle</span></span><br/><span data-ttu-id="30e78-156">DataGridBoolColumn</span><span class="sxs-lookup"><span data-stu-id="30e78-156">DataGridBoolColumn</span></span><br/><span data-ttu-id="30e78-157">DataGridTextBox</span><span class="sxs-lookup"><span data-stu-id="30e78-157">DataGridTextBox</span></span><br/><span data-ttu-id="30e78-158">GridColumnStylesCollection</span><span class="sxs-lookup"><span data-stu-id="30e78-158">GridColumnStylesCollection</span></span><br/><span data-ttu-id="30e78-159">GridTableStylesCollection</span><span class="sxs-lookup"><span data-stu-id="30e78-159">GridTableStylesCollection</span></span><br/><span data-ttu-id="30e78-160">HitTestType</span><span class="sxs-lookup"><span data-stu-id="30e78-160">HitTestType</span></span> |
| <span data-ttu-id="30e78-161">ToolBar</span><span class="sxs-lookup"><span data-stu-id="30e78-161">ToolBar</span></span>         | <xref:System.Windows.Forms.ToolStrip>         | <span data-ttu-id="30e78-162">Araç Barappearance</span><span class="sxs-lookup"><span data-stu-id="30e78-162">ToolBarAppearance</span></span> |
| <span data-ttu-id="30e78-163">ToolBarButton</span><span class="sxs-lookup"><span data-stu-id="30e78-163">ToolBarButton</span></span>   | <xref:System.Windows.Forms.ToolStripButton>   | <span data-ttu-id="30e78-164">Toolbarbuttonkerkeventargs</span><span class="sxs-lookup"><span data-stu-id="30e78-164">ToolBarButtonClickEventArgs</span></span><br/><span data-ttu-id="30e78-165">Toolbarbuttonclick Kerkeventhandler</span><span class="sxs-lookup"><span data-stu-id="30e78-165">ToolBarButtonClickEventHandler</span></span><br/><span data-ttu-id="30e78-166">ToolBarButtonStyle</span><span class="sxs-lookup"><span data-stu-id="30e78-166">ToolBarButtonStyle</span></span><br/><span data-ttu-id="30e78-167">ToolBarTextAlign</span><span class="sxs-lookup"><span data-stu-id="30e78-167">ToolBarTextAlign</span></span> |
| <span data-ttu-id="30e78-168">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="30e78-168">ContextMenu</span></span>     | <xref:System.Windows.Forms.ContextMenuStrip>  |  |
| :::no-loc text="Menu"::: | <xref:System.Windows.Forms.ToolStripDropDown><br/><xref:System.Windows.Forms.ToolStripDropDownMenu> | <span data-ttu-id="30e78-169">MenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="30e78-169">MenuItemCollection</span></span> |
| <span data-ttu-id="30e78-170">MainMenu</span><span class="sxs-lookup"><span data-stu-id="30e78-170">MainMenu</span></span>        | <xref:System.Windows.Forms.MenuStrip>         |  |
| <span data-ttu-id="30e78-171">MenuItem</span><span class="sxs-lookup"><span data-stu-id="30e78-171">MenuItem</span></span>        | <xref:System.Windows.Forms.ToolStripMenuItem> |  |

<span data-ttu-id="30e78-172">Uygulamalarınızı .NET Core 3,1 ' a güncelleştirmenizi ve değiştirme denetimlerine taşımanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="30e78-172">We recommend you update your applications to .NET Core 3.1 and move to the replacement controls.</span></span> <span data-ttu-id="30e78-173">Denetimlerin değiştirilmesi basit bir işlemdir, temelde "bul ve Değiştir" tür.</span><span class="sxs-lookup"><span data-stu-id="30e78-173">Replacing the controls is a straightforward process, essentially "find and replace" on the type.</span></span>

## <a name="ccli"></a><span data-ttu-id="30e78-174">C++/CLI</span><span class="sxs-lookup"><span data-stu-id="30e78-174">C++/CLI</span></span>

<span data-ttu-id="30e78-175">*Yalnızca Windows*</span><span class="sxs-lookup"><span data-stu-id="30e78-175">*Windows only*</span></span>

<span data-ttu-id="30e78-176">/CLI ("yönetilen C++ C++" olarak da bilinir) projeleri oluşturmak için destek eklendi.</span><span class="sxs-lookup"><span data-stu-id="30e78-176">Support has been added for creating C++/CLI (also known as "managed C++") projects.</span></span> <span data-ttu-id="30e78-177">Bu projelerden oluşturulan ikili dosyalar .NET Core 3,0 ve sonraki sürümlerle uyumludur.</span><span class="sxs-lookup"><span data-stu-id="30e78-177">Binaries produced from these projects are compatible with .NET Core 3.0 and later versions.</span></span>

<span data-ttu-id="30e78-178">Visual Studio 2019 sürüm C++16,4 ' de/CLI desteği eklemek Için, [Masaüstü geliştirmeyi iş yüküyle C++ birlikte](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads)yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="30e78-178">To add support for C++/CLI in Visual Studio 2019 version 16.4, install the [Desktop development with C++ workload](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads).</span></span> <span data-ttu-id="30e78-179">Bu iş yükü, Visual Studio 'ya iki şablon ekler:</span><span class="sxs-lookup"><span data-stu-id="30e78-179">This workload adds two templates to Visual Studio:</span></span>

- <span data-ttu-id="30e78-180">CLR sınıf kitaplığı (.NET Core)</span><span class="sxs-lookup"><span data-stu-id="30e78-180">CLR Class Library (.NET Core)</span></span>
- <span data-ttu-id="30e78-181">CLR boş proje (.NET Core)</span><span class="sxs-lookup"><span data-stu-id="30e78-181">CLR Empty Project (.NET Core)</span></span>

## <a name="next-steps"></a><span data-ttu-id="30e78-182">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="30e78-182">Next steps</span></span>

- [<span data-ttu-id="30e78-183">.NET Core 3,0 ve 3,1 arasındaki son değişiklikleri gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="30e78-183">Review the breaking changes between .NET Core 3.0 and 3.1.</span></span>](../compatibility/3.0-3.1.md)
- [<span data-ttu-id="30e78-184">Windows Forms uygulamalar için .NET Core 3,1 'deki son değişiklikleri gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="30e78-184">Review the breaking changes in .NET Core 3.1 for Windows Forms apps.</span></span>](../compatibility/winforms.md#net-core-31)
