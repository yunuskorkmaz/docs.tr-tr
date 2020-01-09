---
title: ​.NET Core 3.1’deki yenilikler
description: .NET Core 3,1 ' de bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: a9f47c2909375251460b45792822e491d56fb242
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75342857"
---
# <a name="whats-new-in-net-core-31"></a>​.NET Core 3.1’deki yenilikler

Bu makalede .NET Core 3,1 ' deki yenilikler açıklanır. Bu sürüm, .NET Core 3,0 ' de küçük, küçük, ancak önemli düzeltmeleri içeren küçük iyileştirmeler içerir. .NET Core 3,1 hakkındaki en önemli özellik, [uzun süreli destek (LTS)](#long-term-support) sürümüdür.

Visual Studio 2019 kullanıyorsanız, .NET Core 3,1 projeleriyle çalışmak için [Visual studio 2019 sürüm 16,4](https://visualstudio.microsoft.com/downloads/) ' e güncelleştirmeniz gerekir. Visual Studio 'daki yenilikler hakkında daha fazla bilgi için [Visual Studio bloguna](https://devblogs.microsoft.com/visualstudio/tis-the-season-visual-studio-2019/)bakın.

Mac için Visual Studio Ayrıca, Mac için Visual Studio 8,4 Önizleme kanalında .NET Core 3,1 'i de destekler. .NET Core 3,1 ' i kullanmak için Önizleme kanalını kabul etmeniz gerekir.

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

/CLI ("yönetilen C++ C++" olarak da bilinir) projeleri oluşturmak için destek eklendi. Bu projelerden oluşturulan ikili dosyalar .NET Core 3,0 ve sonraki sürümlerle uyumludur.

Visual Studio 2019 16,4 C++' de/CLI desteği eklemek için, [ C++ iş yüküyle masaüstü geliştirmeyi](https://docs.microsoft.com/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads)yükler. Bu iş yükü, Visual Studio 'ya iki şablon ekler:

- CLR sınıf kitaplığı (.NET Core)
- CLR boş proje (.NET Core)

## <a name="next-steps"></a>Sonraki adımlar

- [.NET Core 3,0 ve 3,1 arasındaki son değişiklikleri gözden geçirin.](../compatibility/3.0-3.1.md)
- [Windows Forms uygulamalar için .NET Framework ve .NET Core 3,0 arasındaki son değişiklikleri gözden geçirin.](../porting/winforms-breaking-changes.md)
