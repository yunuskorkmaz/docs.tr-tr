---
title: Windows Forms son değişiklikler
description: .NET Core 3,0 ve 3,1 için Windows Forms 'deki son değişiklikleri listeler.
ms.date: 09/08/2020
ms.openlocfilehash: b944f7eea89b61f41feb8eef99e949c2d6017960
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726437"
---
# <a name="breaking-changes-in-windows-forms-for-net-core-30-and-31"></a>.NET Core 3,0 ve 3,1 için Windows Forms 'deki değişiklikler kesiliyor

Sürüm 3,0 ' de .NET Core 'a Windows Forms desteği eklenmiştir. Bu makalede, sunulan .NET sürümüne göre Windows Forms yönelik son değişiklikler listelenir. Bir Windows Forms uygulamasını .NET Framework veya .NET Core 'un önceki bir sürümünden (3,0 veya üzeri) yükseltiyorsanız, bu makale sizin için geçerlidir.

Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:

| Son değişiklik | Sunulan sürüm |
| - | :-: |
| [Kaldırılan denetimler](#removed-controls) | 3,1 |
| [Araç ipucu gösterildiğinde CellFormatting olayı oluşturulmaz](#cellformatting-event-not-raised-if-tooltip-is-shown) | 3,1 |
| [Control. DefaultFont Segoe UI 9 nk olarak değiştirildi](#default-control-font-changed-to-segoe-ui-9-pt) | 3,0 |
| [FolderBrowserDialog 'u modernleştirme](#modernization-of-the-folderbrowserdialog) | 3,0 |
| [SerializableAttribute bazı Windows Forms türlerinden kaldırıldı](#serializableattribute-removed-from-some-windows-forms-types) | 3,0 |
| [AllowUpdateChildControlIndexForTabControls uyumluluk anahtarı desteklenmiyor](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | 3,0 |
| [DomainUpDown. UseLegacyScrolling uyumluluk anahtarı desteklenmiyor](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | 3,0 |
| [DoNotLoadLatestRichEditControl uyumluluk anahtarı desteklenmiyor](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | 3,0 |
| [Donotsupportselectallshortcutınmultilinetextbox uyumluluk anahtarı desteklenmiyor](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | 3,0 |
| [DontSupportReentrantFilterMessage uyumluluk anahtarı desteklenmiyor](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | 3,0 |
| [EnableVisualStyleValidation uyumluluk anahtarı desteklenmiyor](#enablevisualstylevalidation-compatibility-switch-not-supported) | 3,0 |
| [UseLegacyContextMenuStripSourceControlValue uyumluluk anahtarı desteklenmiyor](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | 3,0 |
| [UseLegacyImages uyumluluk anahtarı desteklenmiyor](#uselegacyimages-compatibility-switch-not-supported) | 3,0 |

## <a name="net-core-31"></a>.NET Core 3,1

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

**_

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9pt](~/includes/core-changes/windowsforms/3.0/control-defaultfont-changed.md)]

_*_

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/3.0/modernized-folderbrowserdialog.md)]

_*_

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/3.0/remove-serializationattribute.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyscrolling.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotloadlatestricheditcontrol.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-dontsupportreentrantfiltermessage.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-enablevisualstylevalidation.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyimages.md)]

_**

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core 'a Windows Forms uygulaması bağlantı noktası](/dotnet/desktop/winforms/migration/?view=netdesktop-5.0&preserve-view=true)
