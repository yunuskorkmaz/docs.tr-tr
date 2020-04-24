---
title: Son değişiklikler-.NET Core 'a .NET Framework
titleSuffix: ''
description: .NET Framework 'den .NET Core 'a yapılan son değişiklikleri listeler.
ms.date: 12/18/2019
ms.openlocfilehash: 6a6cbffed5a54e3683832da54d408d77bb553cf1
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135639"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a><span data-ttu-id="44f39-103">.NET Framework 'den .NET Core 'a geçiş için son değişiklikler</span><span class="sxs-lookup"><span data-stu-id="44f39-103">Breaking changes for migration from .NET Framework to .NET Core</span></span>

<span data-ttu-id="44f39-104">.NET Framework bir uygulamayı .NET Core 'a geçiriyorsanız, bu makalede listelenen son değişiklikler sizi etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="44f39-104">If you're migrating an app from .NET Framework to .NET Core, the breaking changes listed in this article may affect you.</span></span> <span data-ttu-id="44f39-105">Son değişiklikler, eklenen .NET Core sürümüne göre kategoriye ve bu kategorilerin içine göre gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="44f39-105">Breaking changes are grouped by category, and within those categories, by the version of .NET Core in which they were introduced.</span></span>

> [!NOTE]
> <span data-ttu-id="44f39-106">Bu makale, .NET Framework ve .NET Core arasındaki önemli değişikliklerden oluşan bir liste değildir.</span><span class="sxs-lookup"><span data-stu-id="44f39-106">This article is not a complete list of breaking changes between .NET Framework and .NET Core.</span></span> <span data-ttu-id="44f39-107">Bunlara göz önünde bulundurulduğumuz için en önemli son değişiklikler buraya eklenir.</span><span class="sxs-lookup"><span data-stu-id="44f39-107">The most important breaking changes are added here as we become aware of them.</span></span>

## <a name="core-net-libraries"></a><span data-ttu-id="44f39-108">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="44f39-108">Core .NET libraries</span></span>

- [<span data-ttu-id="44f39-109">UseShellExecute varsayılan değerindeki değişiklik</span><span class="sxs-lookup"><span data-stu-id="44f39-109">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute)
- [<span data-ttu-id="44f39-110">Fılesystemınfo. Attributes tarafından oluşturulan UnauthorizedAccessException</span><span class="sxs-lookup"><span data-stu-id="44f39-110">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes)
- [<span data-ttu-id="44f39-111">Bozuk işlem durumu özel durumlarını işleme desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="44f39-111">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported)

### <a name="net-core-21"></a><span data-ttu-id="44f39-112">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="44f39-112">.NET Core 2.1</span></span>

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

### <a name="net-core-10"></a><span data-ttu-id="44f39-113">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="44f39-113">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

## <a name="cryptography"></a><span data-ttu-id="44f39-114">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="44f39-114">Cryptography</span></span>

- [<span data-ttu-id="44f39-115">SignedCms. ComputeSignature Boolean parametresi dikkate alındı</span><span class="sxs-lookup"><span data-stu-id="44f39-115">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected)

### <a name="net-core-21"></a><span data-ttu-id="44f39-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="44f39-116">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***

## <a name="windows-forms"></a><span data-ttu-id="44f39-117">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="44f39-117">Windows Forms</span></span>

<span data-ttu-id="44f39-118">Sürüm 3,0 ' de .NET Core 'a Windows Forms desteği eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="44f39-118">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="44f39-119">.NET Framework bir Windows Forms uygulamasını .NET Core 'a geçiriyorsanız, burada listelenen son değişiklikler uygulamanızı etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="44f39-119">If you're migrating a Windows Forms app from .NET Framework to .NET Core, the breaking changes listed here may affect your app.</span></span>

- [<span data-ttu-id="44f39-120">Kaldırılan denetimler</span><span class="sxs-lookup"><span data-stu-id="44f39-120">Removed controls</span></span>](#removed-controls)
- [<span data-ttu-id="44f39-121">Araç ipucu gösterildiğinde CellFormatting olayı oluşturulmaz</span><span class="sxs-lookup"><span data-stu-id="44f39-121">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [<span data-ttu-id="44f39-122">Control. DefaultFont Segoe UI 9 nk olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="44f39-122">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt)
- [<span data-ttu-id="44f39-123">FolderBrowserDialog 'u modernleştirme</span><span class="sxs-lookup"><span data-stu-id="44f39-123">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog)
- [<span data-ttu-id="44f39-124">SerializableAttribute bazı Windows Forms türlerinden kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="44f39-124">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types)
- [<span data-ttu-id="44f39-125">AllowUpdateChildControlIndexForTabControls uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="44f39-125">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [<span data-ttu-id="44f39-126">DomainUpDown. UseLegacyScrolling uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="44f39-126">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [<span data-ttu-id="44f39-127">DoNotLoadLatestRichEditControl uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="44f39-127">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [<span data-ttu-id="44f39-128">Donotsupportselectallshortcutınmultilinetextbox uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="44f39-128">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [<span data-ttu-id="44f39-129">DontSupportReentrantFilterMessage uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="44f39-129">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [<span data-ttu-id="44f39-130">EnableVisualStyleValidation uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="44f39-130">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [<span data-ttu-id="44f39-131">UseLegacyContextMenuStripSourceControlValue uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="44f39-131">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [<span data-ttu-id="44f39-132">UseLegacyImages uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="44f39-132">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported)
- [<span data-ttu-id="44f39-133">Erişilebilir nesne. Runtimeıdfirtıtem için erişim değişikliği</span><span class="sxs-lookup"><span data-stu-id="44f39-133">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [<span data-ttu-id="44f39-134">Yinelenen API 'Ler Windows Forms kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="44f39-134">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms)

### <a name="net-core-31"></a><span data-ttu-id="44f39-135">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="44f39-135">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

### <a name="net-core-30"></a><span data-ttu-id="44f39-136">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="44f39-136">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="44f39-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44f39-137">See also</span></span>

- [<span data-ttu-id="44f39-138">.NET Core üzerinde her zaman özel durum oluşturan API 'Ler</span><span class="sxs-lookup"><span data-stu-id="44f39-138">APIs that always throw exceptions on .NET Core</span></span>](unsupported-apis.md)
- [<span data-ttu-id="44f39-139">.NET Core 'da .NET Framework teknolojileri kullanılamıyor</span><span class="sxs-lookup"><span data-stu-id="44f39-139">.NET Framework technologies unavailable on .NET Core</span></span>](../porting/net-framework-tech-unavailable.md)
