---
title: Son dakika değişiklikleri - .NET Framework to .NET Core
titleSuffix: ''
description: .NET Framework'den .NET Core'a son dakika değişikliklerini listeler.
ms.date: 12/18/2019
ms.openlocfilehash: ef16132c8dcffbe9bcfbe02834c9a78d6d0c33e4
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021798"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a>.NET Framework'den .NET Core'a geçiş için son dakika değişiklikleri

Bir uygulamayı .NET Framework'den .NET Core'a geçiriyorsanız, bu makalede listelenen son dakika değişiklikleri sizi etkileyebilir. Son kesme değişiklikleri kategoriye ve bu kategoriler içinde ,.NET Core sürümüne göre gruplandırılır.

> [!NOTE]
> Bu makale, .NET Framework ve .NET Core arasındaki son dakika değişikliklerinin tam bir listesi değildir. En önemli kırılma değişiklikleri biz bunların farkında olmak gibi burada eklenir.

## <a name="core-net-libraries"></a>Çekirdek .NET kitaplıkları

- [UseShellExecute'ın varsayılan değerindeki değişiklik](#change-in-default-value-of-useshellexecute)
- [FileSystemInfo.Attributes tarafından atılan Yetkisiz ErişimÖzel Durum](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes)

### <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

### <a name="net-core-10"></a>.NET Çekirdek 1.0

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

## <a name="cryptography"></a>Şifreleme

- [İmzaCms.ComputeSignature boolean parametre saygı duyulur](#boolean-parameter-of-signedcmscomputesignature-is-respected)

### <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***

## <a name="windows-forms"></a>Windows Forms

Windows Forms desteği 3.0 sürümünde .NET Core'a eklendi. Bir Windows Forms uygulamasını .NET Framework'den .NET Core'a geçirmiyorsanız, burada listelenen son dakika değişiklikleri uygulamanızı etkileyebilir.

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

### <a name="net-core-31"></a>.NET Çekirdek 3.1

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

### <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9 pt](~/includes/core-changes/windowsforms/3.0/control-defaultfont-changed.md)]

***

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/3.0/modernized-folderbrowserdialog.md)]

***

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/3.0/remove-serializationattribute.md)]

***

[!INCLUDE[AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

***

[!INCLUDE[DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyscrolling.md)]

***

[!INCLUDE[DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotloadlatestricheditcontrol.md)]

***

[!INCLUDE[DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

***

[!INCLUDE[DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-dontsupportreentrantfiltermessage.md)]

***

[!INCLUDE[EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-enablevisualstylevalidation.md)]

***

[!INCLUDE[UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

***

[!INCLUDE[UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyimages.md)]

***

[!INCLUDE[Change of access for AccessibleObject.RuntimeIDFirstItem](~/includes/core-changes/windowsforms/3.0/changed-access-for-runtimeidfirstitem.md)]

***

[!INCLUDE[Duplicated APIs removed from Windows Forms](~/includes/core-changes/windowsforms/3.0/remove-duplicated-apis.md)]

***

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core'da her zaman özel durumlar oluşturan API'ler](unsupported-apis.md)
- [.NET Framework teknolojileri .NET Core'da kullanılamıyor](../porting/net-framework-tech-unavailable.md)
