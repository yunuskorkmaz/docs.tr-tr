---
title: Windows Formlar değişiklikleri kırma
description: .NET Core için Windows Formlarında çığır açan değişiklikleri listeler.
ms.date: 01/08/2020
ms.openlocfilehash: 7fba78382d011bc9d489924fa185a44e598c5a76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399100"
---
# <a name="breaking-changes-in-windows-forms"></a>Windows Formlarında değişiklik kırma

Windows Forms desteği 3.0 sürümünde .NET Core'a eklendi. Bu makalede, windows formları için son dakika değişiklikleri tanıtıldıkları .NET Core sürümüne göre listelenir. Bir Windows Forms uygulamasını .NET Framework'den veya .NET Core'un önceki sürümünden (3.0 veya sonraki) yükseltiyorsanız, bu makale sizin için geçerlidir.

Aşağıdaki kesme değişiklikleri bu sayfada belgelenmiştir:

- [Kaldırılan denetimler](#removed-controls)
- [Araç ipucu gösterilirse CellFormatting olayı yükseltilmez](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [Control.DefaultFont Segoe UI 9 pt olarak değiştirildi](#default-control-font-changed-to-segoe-ui-9-pt)
- [FolderBrowserDialog modernizasyonu](#modernization-of-the-folderbrowserdialog)
- [SerializableAttribute bazı Windows Forms türlerinden kaldırıldı](#serializableattribute-removed-from-some-windows-forms-types)
- [AllowUpdateChildControlIndexForTabControls uyumluluk anahtarı desteklenmiyor](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [DomainUpDown.UseLegacyScrolling uyumluluk anahtarı desteklenmiyor](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [DoNotLoadLatestRichEditControl uyumluluk anahtarı desteklenmiyor](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [DoNotSupportSelectAllShortcutInMultilineTextBox uyumluluk anahtarı desteklenmiyor](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [DontSupportReentrantFilterMessage uyumluluk anahtarı desteklenmiyor](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [EtkinleştirVisualStyleValidation uyumluluk anahtarı desteklenmiyor](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [UseLegacyContextMenuStripSourceControlValue uyumluluk anahtarı desteklenmiyor](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [UseLegacyImages uyumluluk anahtarı desteklenmiyor](#uselegacyimages-compatibility-switch-not-supported)
- [ErişilebilirObject.RuntimeIDFirstItem için erişim değişikliği](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [Windows Formlarından Kaldırılan Yinelenen API'ler](#duplicated-apis-removed-from-windows-forms)

## <a name="net-core-31"></a>.NET Çekirdek 3.1

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

[!INCLUDE[Change of access for AccessibleObject.RuntimeIDFirstItem](~/includes/core-changes/windowsforms/3.0/changed-access-for-runtimeidfirstitem.md)]

***

[!INCLUDE[Duplicated APIs removed from Windows Forms](~/includes/core-changes/windowsforms/3.0/remove-duplicated-apis.md)]

***

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms uygulamasını .NET Core'a taşıma](../porting/winforms.md)
