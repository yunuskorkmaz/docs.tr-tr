---
title: Windows Forms son değişiklikler
description: .NET Core ve .NET 5 için Windows Forms 'deki son değişiklikleri listeler.
ms.date: 09/08/2020
ms.openlocfilehash: 3e7d077d07203d9c231ae4a7805e593c5432c135
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679012"
---
# <a name="breaking-changes-in-windows-forms"></a>Windows Forms 'deki değişiklikler kesiliyor

Sürüm 3,0 ' de .NET Core 'a Windows Forms desteği eklenmiştir. Bu makalede, sunulan .NET sürümüne göre Windows Forms yönelik son değişiklikler listelenir. Bir Windows Forms uygulamasını .NET Framework veya .NET Core 'un önceki bir sürümünden (3,0 veya üzeri) yükseltiyorsanız, bu makale sizin için geçerlidir.

Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:

| Son değişiklik | Sunulan sürüm |
| - | :-: |
| [OutputType WPF ve WinForms uygulamaları için WinExe olarak ayarlandı](#outputtype-set-to-winexe-for-wpf-and-winforms-apps) | 5.0 |
| [DataGridView ile ilgili API 'Ler artık InvalidOperationException 'yi oluşturur](#datagridview-related-apis-now-throw-invalidoperationexception) | 5.0 |
| [WinForms ve WPF uygulamaları Microsoft. NET. SDK kullanır](#winforms-and-wpf-apps-use-microsoftnetsdk) | 5.0 |
| [Durum çubuğu denetimleri kaldırıldı](#removed-status-bar-controls) | 5.0 |
| [WinForms yöntemleri artık ArgumentException oluşturur](#winforms-methods-now-throw-argumentexception) | 5.0 |
| [WinForms yöntemleri şimdi ArgumentNullException oluşturur](#winforms-methods-now-throw-argumentnullexception) | 5.0 |
| [WinForms özellikleri artık ArgumentOutOfRangeException oluşturur](#winforms-properties-now-throw-argumentoutofrangeexception) | 5.0 |
| [Kaldırılan denetimler](#removed-controls) | 3,1 |
| [Araç ipucu gösterildiğinde CellFormatting olayı oluşturulmaz](#cellformatting-event-not-raised-if-tooltip-is-shown) | 3,1 |
| [Control. DefaultFont Segoe UI 9 nk olarak değiştirildi](#default-control-font-changed-to-segoe-ui-9-pt) | 3.0 |
| [FolderBrowserDialog 'u modernleştirme](#modernization-of-the-folderbrowserdialog) | 3.0 |
| [SerializableAttribute bazı Windows Forms türlerinden kaldırıldı](#serializableattribute-removed-from-some-windows-forms-types) | 3.0 |
| [AllowUpdateChildControlIndexForTabControls uyumluluk anahtarı desteklenmiyor](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | 3.0 |
| [DomainUpDown. UseLegacyScrolling uyumluluk anahtarı desteklenmiyor](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | 3.0 |
| [DoNotLoadLatestRichEditControl uyumluluk anahtarı desteklenmiyor](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | 3.0 |
| [Donotsupportselectallshortcutınmultilinetextbox uyumluluk anahtarı desteklenmiyor](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | 3.0 |
| [DontSupportReentrantFilterMessage uyumluluk anahtarı desteklenmiyor](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | 3.0 |
| [EnableVisualStyleValidation uyumluluk anahtarı desteklenmiyor](#enablevisualstylevalidation-compatibility-switch-not-supported) | 3.0 |
| [UseLegacyContextMenuStripSourceControlValue uyumluluk anahtarı desteklenmiyor](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | 3.0 |
| [UseLegacyImages uyumluluk anahtarı desteklenmiyor](#uselegacyimages-compatibility-switch-not-supported) | 3.0 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [automatically-infer-winexe-output-type](../../../includes/core-changes/windowsforms/5.0/automatically-infer-winexe-output-type.md)]

***

[!INCLUDE [null-owner-causes-invalidoperationexception](../../../includes/core-changes/windowsforms/5.0/null-owner-causes-invalidoperationexception.md)]

***

[!INCLUDE [sdk-and-target-framework-change](../../../includes/core-changes/windowsforms/5.0/sdk-and-target-framework-change.md)]

***

[!INCLUDE [winforms-deprecated-controls](../../../includes/core-changes/windowsforms/5.0/winforms-deprecated-controls.md)]

***

[!INCLUDE [invalid-args-cause-argumentexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentexception.md)]

***

[!INCLUDE [null-args-cause-argumentnullexception](../../../includes/core-changes/windowsforms/5.0/null-args-cause-argumentnullexception.md)]

***

[!INCLUDE [invalid-args-cause-argumentoutofrangeexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentoutofrangeexception.md)]

***

## <a name="net-core-31"></a>.NET Core 3,1

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9pt](~/includes/core-changes/windowsforms/3.0/control-defaultfont-changed.md)]

***

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/3.0/modernized-folderbrowserdialog.md)]

***

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/3.0/remove-serializationattribute.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyscrolling.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotloadlatestricheditcontrol.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-dontsupportreentrantfiltermessage.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-enablevisualstylevalidation.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyimages.md)]

***

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core 'a Windows Forms uygulaması bağlantı noktası](../porting/winforms.md)
