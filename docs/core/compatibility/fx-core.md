---
title: Son değişiklikler-.NET Core 'a .NET Framework
titleSuffix: ''
description: .NET Framework 'den .NET Core 'a yapılan son değişiklikleri listeler.
ms.date: 12/18/2019
ms.openlocfilehash: f712be14d7debc4b3008f8459e6ee925754b25f0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449418"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a>.NET Framework 'den .NET Core 'a geçiş için son değişiklikler

.NET Framework bir uygulamayı .NET Core 'a geçiriyorsanız, bu makalede listelenen son değişiklikler sizi etkileyebilir. Son değişiklikler, eklenen .NET Core sürümüne göre kategoriye ve bu kategorilerin içine göre gruplandırılır.

> [!NOTE]
> Bu makale, .NET Framework ve .NET Core arasındaki önemli değişikliklerden oluşan bir liste değildir. Bunlara göz önünde bulundurulduğumuz için en önemli son değişiklikler buraya eklenir.

## <a name="corefx"></a>CoreFx

- [UseShellExecute varsayılan değerindeki değişiklik](#change-in-default-value-of-useshellexecute)
- [Fılesystemınfo. Attributes tarafından oluşturulan UnauthorizedAccessException](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes)

### <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

### <a name="net-core-10"></a>.NET Core 1,0

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

## <a name="cryptography"></a>Şifreleme

- [SignedCms. ComputeSignature Boolean parametresi dikkate alındı](#boolean-parameter-of-signedcmscomputesignature-is-respected)

### <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***

## <a name="windows-forms"></a>Windows Forms

Sürüm 3,0 ' de .NET Core 'a Windows Forms desteği eklenmiştir. .NET Framework bir Windows Forms uygulamasını .NET Core 'a geçiriyorsanız, burada listelenen son değişiklikler uygulamanızı etkileyebilir.

- [Kaldırılan denetimler](#removed-controls)
- [Araç ipucu gösterildiğinde CellFormatting olayı oluşturulmaz](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [Control. DefaultFont Segoe UI 9 nk olarak değiştirildi](#default-control-font-changed-to-segoe-ui-9-pt)
- [FolderBrowserDialog 'u modernleştirme](#modernization-of-the-folderbrowserdialog)
- [SerializableAttribute bazı Windows Forms türlerinden kaldırıldı](#serializableattribute-removed-from-some-windows-forms-types)
- [AllowUpdateChildControlIndexForTabControls uyumluluk anahtarı desteklenmiyor](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [DomainUpDown. UseLegacyScrolling uyumluluk anahtarı desteklenmiyor](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [DoNotLoadLatestRichEditControl uyumluluk anahtarı desteklenmiyor](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [Donotsupportselectallshortcutınmultilinetextbox uyumluluk anahtarı desteklenmiyor](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [DontSupportReentrantFilterMessage uyumluluk anahtarı desteklenmiyor](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [EnableVisualStyleValidation uyumluluk anahtarı desteklenmiyor](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [UseLegacyContextMenuStripSourceControlValue uyumluluk anahtarı desteklenmiyor](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [UseLegacyImages uyumluluk anahtarı desteklenmiyor](#uselegacyimages-compatibility-switch-not-supported)
- [Erişilebilir nesne. Runtimeıdfirtıtem için erişim değişikliği](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [Yinelenen API 'Ler Windows Forms kaldırıldı](#duplicated-apis-removed-from-windows-forms)

### <a name="net-core-31"></a>.NET Core 3,1

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

- [.NET Core üzerinde her zaman özel durum oluşturan API 'Ler](unsupported-apis.md)
- [.NET Core 'da .NET Framework teknolojileri kullanılamıyor](../porting/net-framework-tech-unavailable.md)
