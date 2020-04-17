---
title: ​.NET Core 3.1’deki yenilikler
description: .NET Core 3.1'de bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: b52615a3fb288a6ca0622deb83f4db3c8e3587fb
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607912"
---
# <a name="whats-new-in-net-core-31"></a><span data-ttu-id="702ed-103">​.NET Core 3.1’deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="702ed-103">What's new in .NET Core 3.1</span></span>

<span data-ttu-id="702ed-104">Bu makalede, .NET Core 3.1'deki yenilikler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="702ed-104">This article describes what is new in .NET Core 3.1.</span></span> <span data-ttu-id="702ed-105">Bu sürüm, küçük ama önemli düzeltmelere odaklanan .NET Core 3.0'da küçük iyileştirmeler içerir.</span><span class="sxs-lookup"><span data-stu-id="702ed-105">This release contains minor improvements to .NET Core 3.0, focusing on small, but important, fixes.</span></span> <span data-ttu-id="702ed-106">.NET Core 3.1 ile ilgili en önemli [özellik, uzun vadeli bir destek (LTS)](#long-term-support) sürümü olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="702ed-106">The most important feature about .NET Core 3.1 is that it's a [long-term support (LTS)](#long-term-support) release.</span></span>

<span data-ttu-id="702ed-107">Visual Studio 2019 kullanıyorsanız, .NET Core 3.1 projeleri ile çalışmak için [Visual Studio 2019 sürüm 16.4 veya sonraki](https://visualstudio.microsoft.com/downloads/) sürümlerini güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="702ed-107">If you're using Visual Studio 2019, you must update to [Visual Studio 2019 version 16.4 or later](https://visualstudio.microsoft.com/downloads/) to work with .NET Core 3.1 projects.</span></span> <span data-ttu-id="702ed-108">Visual Studio sürüm 16.4'teki yenilikler hakkında bilgi için Visual [Studio 2019 sürüm 16.4'te Neler Yeni](/visualstudio/releases/2019/release-notes-v16.4#whats-new-in-visual-studio-2019-version-164)olduğunu görün.</span><span class="sxs-lookup"><span data-stu-id="702ed-108">For information on what's new in Visual Studio version 16.4, see [What's New in Visual Studio 2019 version 16.4](/visualstudio/releases/2019/release-notes-v16.4#whats-new-in-visual-studio-2019-version-164).</span></span>

<span data-ttu-id="702ed-109">Mac için Visual Studio da destekler ve Mac 8.4 için Visual Studio .NET Core 3.1 içerir.</span><span class="sxs-lookup"><span data-stu-id="702ed-109">Visual Studio for Mac also supports and includes .NET Core 3.1 in Visual Studio for Mac 8.4.</span></span>

<span data-ttu-id="702ed-110">Sürüm hakkında daha fazla bilgi için [.NET Core 3.1 duyurusuna](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/)bakın.</span><span class="sxs-lookup"><span data-stu-id="702ed-110">For more information about the release, see the [.NET Core 3.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

- <span data-ttu-id="702ed-111">Windows, macOS veya Linux'ta [.NET Core 3.1'i indirin](https://dotnet.microsoft.com/download/dotnet-core/3.1) ve başlayın.</span><span class="sxs-lookup"><span data-stu-id="702ed-111">[Download and get started with .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) on Windows, macOS, or Linux.</span></span>

## <a name="long-term-support"></a><span data-ttu-id="702ed-112">Uzun vadeli destek</span><span class="sxs-lookup"><span data-stu-id="702ed-112">Long-term support</span></span>

<span data-ttu-id="702ed-113">.NET Core 3.1, önümüzdeki üç yıl boyunca Microsoft'un desteğiyle bir LTS sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="702ed-113">.NET Core 3.1 is an LTS release with support from Microsoft for the next three years.</span></span> <span data-ttu-id="702ed-114">Uygulamalarınızı .NET Core 3.1'e taşımanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="702ed-114">It's highly recommended that you move your apps to .NET Core 3.1.</span></span> <span data-ttu-id="702ed-115">Diğer önemli sürümlerin geçerli yaşam döngüsü aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="702ed-115">The current lifecycle of other major releases is as follows:</span></span>

| <span data-ttu-id="702ed-116">Yayınla</span><span class="sxs-lookup"><span data-stu-id="702ed-116">Release</span></span> | <span data-ttu-id="702ed-117">Not</span><span class="sxs-lookup"><span data-stu-id="702ed-117">Note</span></span> |
| ------- | ---- |
| <span data-ttu-id="702ed-118">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="702ed-118">.NET Core 3.0</span></span> | <span data-ttu-id="702ed-119">3 Mart 2020'de yaşamın sonu.</span><span class="sxs-lookup"><span data-stu-id="702ed-119">End of life on March 3, 2020.</span></span>     |
| <span data-ttu-id="702ed-120">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="702ed-120">.NET Core 2.2</span></span> | <span data-ttu-id="702ed-121">23 Aralık 2019 tarihinde sona erecek.</span><span class="sxs-lookup"><span data-stu-id="702ed-121">End of life on December 23, 2019.</span></span> |
| <span data-ttu-id="702ed-122">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="702ed-122">.NET Core 2.1</span></span> | <span data-ttu-id="702ed-123">21 Ağustos 2021'de yaşamın sonu.</span><span class="sxs-lookup"><span data-stu-id="702ed-123">End of life on August 21, 2021.</span></span>    |

<span data-ttu-id="702ed-124">Daha fazla bilgi için [.NET Core destek ilkesine](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)bakın.</span><span class="sxs-lookup"><span data-stu-id="702ed-124">For more information, see the [.NET Core support policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

## <a name="macos-apphost-and-notarization"></a><span data-ttu-id="702ed-125">macOS appHost ve noterizasyon</span><span class="sxs-lookup"><span data-stu-id="702ed-125">macOS appHost and notarization</span></span>

<span data-ttu-id="702ed-126">*yalnızca macOS*</span><span class="sxs-lookup"><span data-stu-id="702ed-126">*macOS only*</span></span>

<span data-ttu-id="702ed-127">macOS için noterize .NET Core SDK 3.1 ile başlayarak, appHost ayarı varsayılan olarak devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="702ed-127">Starting with the notarized .NET Core SDK 3.1 for macOS, the appHost setting is disabled by default.</span></span> <span data-ttu-id="702ed-128">Daha fazla bilgi için [macOS Catalina Notarization ve .NET Core indirme ve projeleri üzerindeki etkisine](../install/macos-notarization-issues.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="702ed-128">For more information, see [macOS Catalina Notarization and the impact on .NET Core downloads and projects](../install/macos-notarization-issues.md).</span></span>

<span data-ttu-id="702ed-129">appHost ayarı etkinleştirildiğinde, .NET Core, oluşturduğunuzda veya yayımladığınızda yerel bir Mach-O çalıştırılabilir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="702ed-129">When the appHost setting is enabled, .NET Core generates a native Mach-O executable when you build or publish.</span></span> <span data-ttu-id="702ed-130">`dotnet run` Uygulamanız, komutla kaynak kodundan çalıştırıldığında veya doğrudan Yürütülebilir Mach-O'yu başlatarak appHost bağlamında çalışır.</span><span class="sxs-lookup"><span data-stu-id="702ed-130">Your app runs in the context of the appHost when it is run from source code with the `dotnet run` command, or by starting the Mach-O executable directly.</span></span>

<span data-ttu-id="702ed-131">appHost olmadan, bir kullanıcının çalışma [süresine bağlı](../deploying/index.md#publish-runtime-dependent) bir uygulamayı `dotnet <filename.dll>` başlatmasının tek yolu komuttur.</span><span class="sxs-lookup"><span data-stu-id="702ed-131">Without the appHost, the only way a user can start a [runtime-dependent](../deploying/index.md#publish-runtime-dependent) app is with the `dotnet <filename.dll>` command.</span></span> <span data-ttu-id="702ed-132">Uygulamanızı [bağımsız](../deploying/index.md#publish-self-contained)olarak yayımladığınızda her zaman bir appHost oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="702ed-132">An appHost is always created when you publish your app [self-contained](../deploying/index.md#publish-self-contained).</span></span>

<span data-ttu-id="702ed-133">Ya proje düzeyinde appHost yapılandırabilirsiniz, ya da `dotnet` `-p:UseAppHost` parametre ile belirli bir komut için appHost geçiş:</span><span class="sxs-lookup"><span data-stu-id="702ed-133">You can either configure the appHost at the project level, or toggle the appHost for a specific `dotnet` command with the `-p:UseAppHost` parameter:</span></span>

- <span data-ttu-id="702ed-134">Proje dosyası</span><span class="sxs-lookup"><span data-stu-id="702ed-134">Project file</span></span>

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- <span data-ttu-id="702ed-135">Komut satırı parametresi</span><span class="sxs-lookup"><span data-stu-id="702ed-135">Command-line parameter</span></span>

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

<span data-ttu-id="702ed-136">`UseAppHost` Ayar hakkında daha fazla bilgi için [Microsoft.NET.Sdk için MSBuild özelliklerine](../project-sdk/msbuild-props.md#useapphost)bakın.</span><span class="sxs-lookup"><span data-stu-id="702ed-136">For more information about the `UseAppHost` setting, see [MSBuild properties for Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span></span>

## <a name="windows-forms"></a><span data-ttu-id="702ed-137">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="702ed-137">Windows Forms</span></span>

<span data-ttu-id="702ed-138">*Yalnızca Windows*</span><span class="sxs-lookup"><span data-stu-id="702ed-138">*Windows only*</span></span>

> [!WARNING]
> <span data-ttu-id="702ed-139">Windows Formlar'da kırılma lar vardır.</span><span class="sxs-lookup"><span data-stu-id="702ed-139">There are breaking changes in Windows Forms.</span></span>

<span data-ttu-id="702ed-140">Eski denetimler, bir süredir Visual Studio Designer Toolbox'ta kullanılamayan Windows Formları'na dahil edildi.</span><span class="sxs-lookup"><span data-stu-id="702ed-140">Legacy controls were included in Windows Forms that have been unavailable in the Visual Studio Designer Toolbox for some time.</span></span> <span data-ttu-id="702ed-141">Bunlar .NET Framework 2.0'da yeni denetimlerle değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="702ed-141">These were replaced with new controls back in .NET Framework 2.0.</span></span> <span data-ttu-id="702ed-142">Bunlar .NET Core 3.1 için Masaüstü SDK'dan kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="702ed-142">These have been removed from the Desktop SDK for .NET Core 3.1.</span></span>

| <span data-ttu-id="702ed-143">Kaldırıldı denetimi</span><span class="sxs-lookup"><span data-stu-id="702ed-143">Removed control</span></span> | <span data-ttu-id="702ed-144">Önerilen değiştirme</span><span class="sxs-lookup"><span data-stu-id="702ed-144">Recommended replacement</span></span> | <span data-ttu-id="702ed-145">İlişkili API'ler kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="702ed-145">Associated APIs removed</span></span> |
| --------------- | ----------------------- | ----------------------- |
| <span data-ttu-id="702ed-146">DataGrid</span><span class="sxs-lookup"><span data-stu-id="702ed-146">DataGrid</span></span>        | <xref:System.Windows.Forms.DataGridView>      | <span data-ttu-id="702ed-147">Datagridcell</span><span class="sxs-lookup"><span data-stu-id="702ed-147">DataGridCell</span></span><br/><span data-ttu-id="702ed-148">DataGridRow</span><span class="sxs-lookup"><span data-stu-id="702ed-148">DataGridRow</span></span><br/><span data-ttu-id="702ed-149">DataGridTableCollection</span><span class="sxs-lookup"><span data-stu-id="702ed-149">DataGridTableCollection</span></span><br/><span data-ttu-id="702ed-150">Datagridcolumncollection</span><span class="sxs-lookup"><span data-stu-id="702ed-150">DataGridColumnCollection</span></span><br/><span data-ttu-id="702ed-151">Datagridtablestyle</span><span class="sxs-lookup"><span data-stu-id="702ed-151">DataGridTableStyle</span></span><br/><span data-ttu-id="702ed-152">DataGridColumnStyle</span><span class="sxs-lookup"><span data-stu-id="702ed-152">DataGridColumnStyle</span></span><br/><span data-ttu-id="702ed-153">DataGridLineStyle</span><span class="sxs-lookup"><span data-stu-id="702ed-153">DataGridLineStyle</span></span><br/><span data-ttu-id="702ed-154">DataGridParentRowsLabel</span><span class="sxs-lookup"><span data-stu-id="702ed-154">DataGridParentRowsLabel</span></span><br/><span data-ttu-id="702ed-155">DataGridParentRowsLabelStyle</span><span class="sxs-lookup"><span data-stu-id="702ed-155">DataGridParentRowsLabelStyle</span></span><br/><span data-ttu-id="702ed-156">Datagridboolcolumn</span><span class="sxs-lookup"><span data-stu-id="702ed-156">DataGridBoolColumn</span></span><br/><span data-ttu-id="702ed-157">Datagridtextbox</span><span class="sxs-lookup"><span data-stu-id="702ed-157">DataGridTextBox</span></span><br/><span data-ttu-id="702ed-158">Gridcolumnstylescollection</span><span class="sxs-lookup"><span data-stu-id="702ed-158">GridColumnStylesCollection</span></span><br/><span data-ttu-id="702ed-159">Gridtablestylescollection</span><span class="sxs-lookup"><span data-stu-id="702ed-159">GridTableStylesCollection</span></span><br/><span data-ttu-id="702ed-160">HitTestType</span><span class="sxs-lookup"><span data-stu-id="702ed-160">HitTestType</span></span> |
| <span data-ttu-id="702ed-161">ToolBar</span><span class="sxs-lookup"><span data-stu-id="702ed-161">ToolBar</span></span>         | <xref:System.Windows.Forms.ToolStrip>         | <span data-ttu-id="702ed-162">Araç Çubuğu Görünümü</span><span class="sxs-lookup"><span data-stu-id="702ed-162">ToolBarAppearance</span></span> |
| <span data-ttu-id="702ed-163">Toolbarbutton</span><span class="sxs-lookup"><span data-stu-id="702ed-163">ToolBarButton</span></span>   | <xref:System.Windows.Forms.ToolStripButton>   | <span data-ttu-id="702ed-164">AraçÇubuğuDüğmeClickEventArgs</span><span class="sxs-lookup"><span data-stu-id="702ed-164">ToolBarButtonClickEventArgs</span></span><br/><span data-ttu-id="702ed-165">AraçÇubuğuDüğmeClickEventHandler</span><span class="sxs-lookup"><span data-stu-id="702ed-165">ToolBarButtonClickEventHandler</span></span><br/><span data-ttu-id="702ed-166">ToolBarButtonStyle</span><span class="sxs-lookup"><span data-stu-id="702ed-166">ToolBarButtonStyle</span></span><br/><span data-ttu-id="702ed-167">Araç ÇubuğuTextAlign</span><span class="sxs-lookup"><span data-stu-id="702ed-167">ToolBarTextAlign</span></span> |
| <span data-ttu-id="702ed-168">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="702ed-168">ContextMenu</span></span>     | <xref:System.Windows.Forms.ContextMenuStrip>  |  |
| :::no-loc text="Menu"::: | <xref:System.Windows.Forms.ToolStripDropDown><br/><xref:System.Windows.Forms.ToolStripDropDownMenu> | <span data-ttu-id="702ed-169">Menuıtemcollection</span><span class="sxs-lookup"><span data-stu-id="702ed-169">MenuItemCollection</span></span> |
| <span data-ttu-id="702ed-170">Mainmenu</span><span class="sxs-lookup"><span data-stu-id="702ed-170">MainMenu</span></span>        | <xref:System.Windows.Forms.MenuStrip>         |  |
| <span data-ttu-id="702ed-171">MenuItem</span><span class="sxs-lookup"><span data-stu-id="702ed-171">MenuItem</span></span>        | <xref:System.Windows.Forms.ToolStripMenuItem> |  |

<span data-ttu-id="702ed-172">Uygulamalarınızı .NET Core 3.1'e güncellemenizi ve değiştirme denetimlerine geçmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="702ed-172">We recommend you update your applications to .NET Core 3.1 and move to the replacement controls.</span></span> <span data-ttu-id="702ed-173">Denetimleri değiştirmek basit bir işlemdir, esasen türünde "bul ve değiştir".</span><span class="sxs-lookup"><span data-stu-id="702ed-173">Replacing the controls is a straightforward process, essentially "find and replace" on the type.</span></span>

## <a name="ccli"></a><span data-ttu-id="702ed-174">C++/CLI</span><span class="sxs-lookup"><span data-stu-id="702ed-174">C++/CLI</span></span>

<span data-ttu-id="702ed-175">*Yalnızca Windows*</span><span class="sxs-lookup"><span data-stu-id="702ed-175">*Windows only*</span></span>

<span data-ttu-id="702ed-176">C++/CLI ("yönetilen C++" olarak da bilinir) projeleri oluşturmak için destek eklendi.</span><span class="sxs-lookup"><span data-stu-id="702ed-176">Support has been added for creating C++/CLI (also known as "managed C++") projects.</span></span> <span data-ttu-id="702ed-177">Bu projelerden üretilen ikili ler .NET Core 3.0 ve sonraki sürümlerle uyumludur.</span><span class="sxs-lookup"><span data-stu-id="702ed-177">Binaries produced from these projects are compatible with .NET Core 3.0 and later versions.</span></span>

<span data-ttu-id="702ed-178">Visual Studio 2019 sürüm 16.4'te C++/CLI desteği eklemek için, [C++ iş yüküyle Masaüstü geliştirmeyi](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads)yükleyin.</span><span class="sxs-lookup"><span data-stu-id="702ed-178">To add support for C++/CLI in Visual Studio 2019 version 16.4, install the [Desktop development with C++ workload](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads).</span></span> <span data-ttu-id="702ed-179">Bu iş yükü Visual Studio'ya iki şablon ekler:</span><span class="sxs-lookup"><span data-stu-id="702ed-179">This workload adds two templates to Visual Studio:</span></span>

- <span data-ttu-id="702ed-180">CLR Sınıf Kütüphanesi (.NET Çekirdek)</span><span class="sxs-lookup"><span data-stu-id="702ed-180">CLR Class Library (.NET Core)</span></span>
- <span data-ttu-id="702ed-181">CLR Boş Proje (.NET Çekirdek)</span><span class="sxs-lookup"><span data-stu-id="702ed-181">CLR Empty Project (.NET Core)</span></span>

## <a name="next-steps"></a><span data-ttu-id="702ed-182">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="702ed-182">Next steps</span></span>

- [<span data-ttu-id="702ed-183">.NET Core 3.0 ve 3.1 arasındaki kesme değişikliklerini gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="702ed-183">Review the breaking changes between .NET Core 3.0 and 3.1.</span></span>](../compatibility/3.0-3.1.md)
- [<span data-ttu-id="702ed-184">Windows Forms uygulamaları için .NET Core 3.1'deki son dakika değişikliklerini gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="702ed-184">Review the breaking changes in .NET Core 3.1 for Windows Forms apps.</span></span>](../compatibility/winforms.md#net-core-31)
