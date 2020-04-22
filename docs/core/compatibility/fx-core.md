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
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a><span data-ttu-id="9cf36-103">.NET Framework'den .NET Core'a geçiş için son dakika değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="9cf36-103">Breaking changes for migration from .NET Framework to .NET Core</span></span>

<span data-ttu-id="9cf36-104">Bir uygulamayı .NET Framework'den .NET Core'a geçiriyorsanız, bu makalede listelenen son dakika değişiklikleri sizi etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="9cf36-104">If you're migrating an app from .NET Framework to .NET Core, the breaking changes listed in this article may affect you.</span></span> <span data-ttu-id="9cf36-105">Son kesme değişiklikleri kategoriye ve bu kategoriler içinde ,.NET Core sürümüne göre gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="9cf36-105">Breaking changes are grouped by category, and within those categories, by the version of .NET Core in which they were introduced.</span></span>

> [!NOTE]
> <span data-ttu-id="9cf36-106">Bu makale, .NET Framework ve .NET Core arasındaki son dakika değişikliklerinin tam bir listesi değildir.</span><span class="sxs-lookup"><span data-stu-id="9cf36-106">This article is not a complete list of breaking changes between .NET Framework and .NET Core.</span></span> <span data-ttu-id="9cf36-107">En önemli kırılma değişiklikleri biz bunların farkında olmak gibi burada eklenir.</span><span class="sxs-lookup"><span data-stu-id="9cf36-107">The most important breaking changes are added here as we become aware of them.</span></span>

## <a name="core-net-libraries"></a><span data-ttu-id="9cf36-108">Çekirdek .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="9cf36-108">Core .NET libraries</span></span>

- [<span data-ttu-id="9cf36-109">UseShellExecute'ın varsayılan değerindeki değişiklik</span><span class="sxs-lookup"><span data-stu-id="9cf36-109">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute)
- [<span data-ttu-id="9cf36-110">FileSystemInfo.Attributes tarafından atılan Yetkisiz ErişimÖzel Durum</span><span class="sxs-lookup"><span data-stu-id="9cf36-110">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes)

### <a name="net-core-21"></a><span data-ttu-id="9cf36-111">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="9cf36-111">.NET Core 2.1</span></span>

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

### <a name="net-core-10"></a><span data-ttu-id="9cf36-112">.NET Çekirdek 1.0</span><span class="sxs-lookup"><span data-stu-id="9cf36-112">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

## <a name="cryptography"></a><span data-ttu-id="9cf36-113">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="9cf36-113">Cryptography</span></span>

- [<span data-ttu-id="9cf36-114">İmzaCms.ComputeSignature boolean parametre saygı duyulur</span><span class="sxs-lookup"><span data-stu-id="9cf36-114">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected)

### <a name="net-core-21"></a><span data-ttu-id="9cf36-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="9cf36-115">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***

## <a name="windows-forms"></a><span data-ttu-id="9cf36-116">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9cf36-116">Windows Forms</span></span>

<span data-ttu-id="9cf36-117">Windows Forms desteği 3.0 sürümünde .NET Core'a eklendi.</span><span class="sxs-lookup"><span data-stu-id="9cf36-117">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="9cf36-118">Bir Windows Forms uygulamasını .NET Framework'den .NET Core'a geçirmiyorsanız, burada listelenen son dakika değişiklikleri uygulamanızı etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="9cf36-118">If you're migrating a Windows Forms app from .NET Framework to .NET Core, the breaking changes listed here may affect your app.</span></span>

- [<span data-ttu-id="9cf36-119">Kaldırılan denetimler</span><span class="sxs-lookup"><span data-stu-id="9cf36-119">Removed controls</span></span>](#removed-controls)
- [<span data-ttu-id="9cf36-120">Araç ipucu gösterilirse CellFormatting olayı yükseltilmez</span><span class="sxs-lookup"><span data-stu-id="9cf36-120">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [<span data-ttu-id="9cf36-121">Control.DefaultFont Segoe UI 9 pt olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="9cf36-121">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt)
- [<span data-ttu-id="9cf36-122">FolderBrowserDialog modernizasyonu</span><span class="sxs-lookup"><span data-stu-id="9cf36-122">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog)
- [<span data-ttu-id="9cf36-123">SerializableAttribute bazı Windows Forms türlerinden kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="9cf36-123">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types)
- [<span data-ttu-id="9cf36-124">AllowUpdateChildControlIndexForTabControls uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="9cf36-124">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [<span data-ttu-id="9cf36-125">DomainUpDown.UseLegacyScrolling uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="9cf36-125">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [<span data-ttu-id="9cf36-126">DoNotLoadLatestRichEditControl uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="9cf36-126">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [<span data-ttu-id="9cf36-127">DoNotSupportSelectAllShortcutInMultilineTextBox uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="9cf36-127">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [<span data-ttu-id="9cf36-128">DontSupportReentrantFilterMessage uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="9cf36-128">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [<span data-ttu-id="9cf36-129">EtkinleştirVisualStyleValidation uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="9cf36-129">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [<span data-ttu-id="9cf36-130">UseLegacyContextMenuStripSourceControlValue uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="9cf36-130">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [<span data-ttu-id="9cf36-131">UseLegacyImages uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="9cf36-131">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported)
- [<span data-ttu-id="9cf36-132">ErişilebilirObject.RuntimeIDFirstItem için erişim değişikliği</span><span class="sxs-lookup"><span data-stu-id="9cf36-132">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [<span data-ttu-id="9cf36-133">Windows Formlarından Kaldırılan Yinelenen API'ler</span><span class="sxs-lookup"><span data-stu-id="9cf36-133">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms)

### <a name="net-core-31"></a><span data-ttu-id="9cf36-134">.NET Çekirdek 3.1</span><span class="sxs-lookup"><span data-stu-id="9cf36-134">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

### <a name="net-core-30"></a><span data-ttu-id="9cf36-135">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9cf36-135">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9cf36-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9cf36-136">See also</span></span>

- [<span data-ttu-id="9cf36-137">.NET Core'da her zaman özel durumlar oluşturan API'ler</span><span class="sxs-lookup"><span data-stu-id="9cf36-137">APIs that always throw exceptions on .NET Core</span></span>](unsupported-apis.md)
- [<span data-ttu-id="9cf36-138">.NET Framework teknolojileri .NET Core'da kullanılamıyor</span><span class="sxs-lookup"><span data-stu-id="9cf36-138">.NET Framework technologies unavailable on .NET Core</span></span>](../porting/net-framework-tech-unavailable.md)
