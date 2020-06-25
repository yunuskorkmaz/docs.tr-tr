---
title: ​.NET Core 3.1’deki yenilikler
description: .NET Core 3,1 ' de bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
author: adegeo
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 2373b21e92c6ca68aac33684a9bd0912a2e642b3
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324266"
---
# <a name="whats-new-in-net-core-31"></a>​.NET Core 3.1’deki yenilikler

Bu makalede .NET Core 3,1 ' deki yenilikler açıklanır. Bu sürüm, .NET Core 3,0 ' de küçük, küçük, ancak önemli düzeltmeleri içeren küçük iyileştirmeler içerir. .NET Core 3,1 hakkındaki en önemli özellik, [uzun süreli destek (LTS)](#long-term-support) sürümüdür.

Visual Studio 2019 kullanıyorsanız, .NET Core 3,1 projeleriyle çalışmak için [Visual studio 2019 sürüm 16,4 veya sonraki bir sürüme](https://visualstudio.microsoft.com/downloads/) güncelleştirmeniz gerekir. Visual Studio sürüm 16,4 ' deki yenilikler hakkında daha fazla bilgi için bkz. [Visual studio 2019 sürüm 16,4 yenilikleri](/visualstudio/releases/2019/release-notes-v16.4#whats-new-in-visual-studio-2019-version-164).

Mac için Visual Studio Ayrıca, Mac için Visual Studio 8,4 ' de .NET Core 3,1 ' u destekler ve içerir.

Yayın hakkında daha fazla bilgi için bkz. [.NET Core 3,1 duyurusu](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).

- Windows, macOS veya Linux 'ta [.NET Core 3,1 'Yi indirip kullanmaya](https://dotnet.microsoft.com/download/dotnet-core/3.1) başlayın.

## <a name="long-term-support"></a>Uzun süreli destek

.NET Core 3,1, bir sonraki üç yılda Microsoft desteğiyle desteklenen bir LTS sürümüdür. Uygulamalarınızı .NET Core 3,1 ' e taşımanız önemle tavsiye edilir. Diğer ana yayınların geçerli yaşam döngüsü aşağıdaki gibidir:

| Sürüm | Not |
| ------- | ---- |
| .NET Core 3.0 | 3 Mart 2020 ' de yaşam sonu.     |
| .NET Core 2.2 | 23 Aralık 2019 ' de yaşam sonu. |
| .NET Core 2.1 | 21 Ağustos 2021 ' de yaşam sonu.    |

Daha fazla bilgi için bkz. [.NET Core destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).

## <a name="macos-apphost-and-notarization"></a>macOS appHost ve notarlama

*yalnızca macOS*

MacOS için .NET Core SDK 3,1 ' den başlayarak, appHost ayarı varsayılan olarak devre dışıdır. Daha fazla bilgi için bkz. [MacOS Catalina Notarleştirme ve .NET Core indirmeleri ve projeleri üzerindeki etki](../install/macos-notarization-issues.md).

AppHost ayarı etkinleştirildiğinde, .NET Core, oluşturduğunuzda veya yayımladığınızda yerel bir MAK-O çalıştırılabilir dosyası oluşturur. Uygulamanız, komutuyla kaynak koddan çalıştırıldığında `dotnet run` veya mak-O yürütülebilir dosyasını doğrudan başlatarak appHost bağlamında çalışır.

AppHost olmadan, bir kullanıcıya [çalışma zamanına bağımlı](../deploying/index.md#publish-runtime-dependent) bir uygulama başlatabilir `dotnet <filename.dll>` . Uygulamanızı [kendi içinde](../deploying/index.md#publish-self-contained)yayımladığınızda her zaman bir appHost oluşturulur.

AppHost 'yi proje düzeyinde yapılandırabilir veya parametresi ile belirli bir komut için appHost ' ı kapatabilirsiniz `dotnet` `-p:UseAppHost` :

- Proje dosyası

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- Komut satırı parametresi

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

Ayarı hakkında daha fazla bilgi için `UseAppHost` bkz. [MICROSOFT. net. SDK için MSBuild özellikleri](../project-sdk/msbuild-props.md#useapphost).

## <a name="windows-forms"></a>Windows Forms

*Yalnızca Windows*

> [!WARNING]
> Windows Forms üzerinde önemli değişiklikler var.

Eski denetimler, Visual Studio Tasarımcı araç kutusunda bir süredir kullanılamayan Windows Forms eklenmiştir. Bunlar .NET Framework 2,0 ' deki yeni denetimlerle değiştirilmiştir. Bunlar .NET Core 3,1 için masaüstü SDK 'dan kaldırılmıştır.

| Denetim kaldırıldı | Önerilen değiştirme | İlişkili API 'Ler kaldırıldı |
| --------------- | ----------------------- | ----------------------- |
| DataGrid        | <xref:System.Windows.Forms.DataGridView>      | DataGridCell<br/>DataGridRow<br/>DataGridTableCollection<br/>DataGridColumnCollection<br/>'Da<br/>DataGridColumnStyle<br/>DataGridLineStyle<br/>DataGridParentRowsLabel<br/>DataGridParentRowsLabelStyle<br/>DataGridBoolColumn<br/>DataGridTextBox<br/>GridColumnStylesCollection<br/>GridTableStylesCollection<br/>HitTestType |
| ToolBar         | <xref:System.Windows.Forms.ToolStrip>         | Araç Barappearance |
| ToolBarButton   | <xref:System.Windows.Forms.ToolStripButton>   | Toolbarbuttonkerkeventargs<br/>Toolbarbuttonclick Kerkeventhandler<br/>ToolBarButtonStyle<br/>ToolBarTextAlign |
| ContextMenu     | <xref:System.Windows.Forms.ContextMenuStrip>  |  |
| :::no-loc text="Menu"::: | <xref:System.Windows.Forms.ToolStripDropDown><br/><xref:System.Windows.Forms.ToolStripDropDownMenu> | MenuItemCollection |
| MainMenu        | <xref:System.Windows.Forms.MenuStrip>         |  |
| MenuItem        | <xref:System.Windows.Forms.ToolStripMenuItem> |  |

Uygulamalarınızı .NET Core 3,1 ' a güncelleştirmenizi ve değiştirme denetimlerine taşımanızı öneririz. Denetimlerin değiştirilmesi basit bir işlemdir, temelde "bul ve Değiştir" tür.

## <a name="ccli"></a>C++/CLI

*Yalnızca Windows*

C++/CLı ("yönetilen C++" olarak da bilinir) projeleri oluşturmak için destek eklenmiştir. Bu projelerden oluşturulan ikili dosyalar .NET Core 3,0 ve sonraki sürümlerle uyumludur.

Visual Studio 2019 sürüm 16,4 ' de C++/CLı desteği eklemek için, [c++ iş yüküne sahip masaüstü geliştirme](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads)'yı yükler. Bu iş yükü, Visual Studio 'ya iki şablon ekler:

- CLR sınıf kitaplığı (.NET Core)
- CLR boş proje (.NET Core)

## <a name="next-steps"></a>Sonraki adımlar

- [.NET Core 3,0 ve 3,1 arasındaki son değişiklikleri gözden geçirin.](../compatibility/3.0-3.1.md)
- [Windows Forms uygulamalar için .NET Core 3,1 'deki son değişiklikleri gözden geçirin.](../compatibility/winforms.md#net-core-31)
