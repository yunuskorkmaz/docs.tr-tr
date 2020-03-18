---
title: ​.NET Core 3.1’deki yenilikler
description: .NET Core 3.1'de bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 323a2390f079c17b81db01e4e3787916251943bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156562"
---
# <a name="whats-new-in-net-core-31"></a>​.NET Core 3.1’deki yenilikler

Bu makalede, .NET Core 3.1'deki yenilikler açıklanmaktadır. Bu sürüm, küçük ama önemli düzeltmelere odaklanan .NET Core 3.0'da küçük iyileştirmeler içerir. .NET Core 3.1 ile ilgili en önemli [özellik, uzun vadeli bir destek (LTS)](#long-term-support) sürümü olmasıdır.

Visual Studio 2019 kullanıyorsanız, .NET Core 3.1 projeleri ile çalışmak için [Visual Studio 2019 sürüm 16.4'e](https://visualstudio.microsoft.com/downloads/) güncellemeniz gerekir. Visual Studio'daki yenilikler hakkında daha fazla bilgi için [Visual Studio 2019 sürüm 16.4'te Neler Yeni](/visualstudio/releases/2019/release-notes#whats-new-in-visual-studio-2019-version-164)olduğunu görün.

Mac için Visual Studio da destekler ve Mac 8.4 için Visual Studio .NET Core 3.1 içerir.

Sürüm hakkında daha fazla bilgi için [.NET Core 3.1 duyurusuna](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/)bakın.

- Windows, macOS veya Linux'ta [.NET Core 3.1'i indirin](https://dotnet.microsoft.com/download/dotnet-core/3.1) ve başlayın.

## <a name="long-term-support"></a>Uzun vadeli destek

.NET Core 3.1, önümüzdeki üç yıl boyunca Microsoft'un desteğiyle bir LTS sürümüdür. Uygulamalarınızı .NET Core 3.1'e taşımanız önerilir. Diğer önemli sürümlerin geçerli yaşam döngüsü aşağıdaki gibidir:

| Yayınla | Not |
| ------- | ---- |
| .NET Core 3.0 | 3 Mart 2020'de yaşamın sonu.     |
| .NET Core 2.2 | 23 Aralık 2019 tarihinde sona erecek. |
| .NET Core 2.1 | 21 Ağustos 2021'de yaşamın sonu.    |

Daha fazla bilgi için [.NET Core destek ilkesine](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)bakın.

## <a name="macos-apphost-and-notarization"></a>macOS appHost ve noterizasyon

*yalnızca macOS*

macOS için noterize .NET Core SDK 3.1 ile başlayarak, appHost ayarı varsayılan olarak devre dışı bırakılır. Daha fazla bilgi için [macOS Catalina Notarization ve .NET Core indirme ve projeleri üzerindeki etkisine](../install/macos-notarization-issues.md)bakın.

appHost ayarı etkinleştirildiğinde, .NET Core, oluşturduğunuzda veya yayımladığınızda yerel bir Mach-O çalıştırılabilir oluşturur. `dotnet run` Uygulamanız, komutla kaynak kodundan çalıştırıldığında veya doğrudan Yürütülebilir Mach-O'yu başlatarak appHost bağlamında çalışır.

appHost olmadan, bir kullanıcının çalışma [süresine bağlı](../deploying/index.md#publish-runtime-dependent) bir uygulamayı `dotnet <filename.dll>` başlatmasının tek yolu komuttur. Uygulamanızı [bağımsız](../deploying/index.md#publish-self-contained)olarak yayımladığınızda her zaman bir appHost oluşturulur.

Ya proje düzeyinde appHost yapılandırabilirsiniz, ya da `dotnet` `-p:UseAppHost` parametre ile belirli bir komut için appHost geçiş:

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

`UseAppHost` Ayar hakkında daha fazla bilgi için [Microsoft.NET.Sdk için MSBuild özelliklerine](../project-sdk/msbuild-props.md#useapphost)bakın.

## <a name="windows-forms"></a>Windows Forms

*Yalnızca Windows*

> [!WARNING]
> Windows Formlar'da kırılma lar vardır.

Eski denetimler, bir süredir Visual Studio Designer Toolbox'ta kullanılamayan Windows Formları'na dahil edildi. Bunlar .NET Framework 2.0'da yeni denetimlerle değiştirildi. Bunlar .NET Core 3.1 için Masaüstü SDK'dan kaldırıldı.

| Kaldırıldı denetimi | Önerilen değiştirme | İlişkili API'ler kaldırıldı |
| --------------- | ----------------------- | ----------------------- |
| DataGrid        | <xref:System.Windows.Forms.DataGridView>      | Datagridcell<br/>DataGridRow<br/>DataGridTableCollection<br/>Datagridcolumncollection<br/>Datagridtablestyle<br/>DataGridColumnStyle<br/>DataGridLineStyle<br/>DataGridParentRowsLabel<br/>DataGridParentRowsLabelStyle<br/>Datagridboolcolumn<br/>Datagridtextbox<br/>Gridcolumnstylescollection<br/>Gridtablestylescollection<br/>HitTestType |
| ToolBar         | <xref:System.Windows.Forms.ToolStrip>         | Araç Çubuğu Görünümü |
| Toolbarbutton   | <xref:System.Windows.Forms.ToolStripButton>   | AraçÇubuğuDüğmeClickEventArgs<br/>AraçÇubuğuDüğmeClickEventHandler<br/>ToolBarButtonStyle<br/>Araç ÇubuğuTextAlign |
| ContextMenu     | <xref:System.Windows.Forms.ContextMenuStrip>  |  |
| :::no-loc text="Menu"::: | <xref:System.Windows.Forms.ToolStripDropDown><br/><xref:System.Windows.Forms.ToolStripDropDownMenu> | Menuıtemcollection |
| Mainmenu        | <xref:System.Windows.Forms.MenuStrip>         |  |
| MenuItem        | <xref:System.Windows.Forms.ToolStripMenuItem> |  |

Uygulamalarınızı .NET Core 3.1'e güncellemenizi ve değiştirme denetimlerine geçmenizi öneririz. Denetimleri değiştirmek basit bir işlemdir, esasen türünde "bul ve değiştir".

## <a name="ccli"></a>C++/CLI

*Yalnızca Windows*

C++/CLI ("yönetilen C++" olarak da bilinir) projeleri oluşturmak için destek eklendi. Bu projelerden üretilen ikili ler .NET Core 3.0 ve sonraki sürümlerle uyumludur.

Visual Studio 2019 sürüm 16.4'te C++/CLI desteği eklemek için, [C++ iş yüküyle Masaüstü geliştirmeyi](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads)yükleyin. Bu iş yükü Visual Studio'ya iki şablon ekler:

- CLR Sınıf Kütüphanesi (.NET Çekirdek)
- CLR Boş Proje (.NET Çekirdek)

## <a name="next-steps"></a>Sonraki adımlar

- [.NET Core 3.0 ve 3.1 arasındaki kesme değişikliklerini gözden geçirin.](../compatibility/3.0-3.1.md)
- [Windows Forms uygulamaları için .NET Core 3.1'deki son dakika değişikliklerini gözden geçirin.](../compatibility/winforms.md#net-core-31)
