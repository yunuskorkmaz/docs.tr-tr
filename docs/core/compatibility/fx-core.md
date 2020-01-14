---
title: Son değişiklikler-.NET Core 'a .NET Framework
description: .NET Framework 'den .NET Core 'a yapılan son değişiklikleri listeler.
ms.date: 12/18/2019
ms.openlocfilehash: 9f4ecc8a9de7279bb4b222b3df77e1eb17b33f0a
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937388"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a><span data-ttu-id="1c8f3-103">.NET Framework 'den .NET Core 'a geçiş için son değişiklikler</span><span class="sxs-lookup"><span data-stu-id="1c8f3-103">Breaking changes for migration from .NET Framework to .NET Core</span></span>

<span data-ttu-id="1c8f3-104">.NET Framework bir uygulamayı .NET Core 'a geçiriyorsanız, bu makalede listelenen son değişiklikler sizi etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="1c8f3-104">If you're migrating an app from .NET Framework to .NET Core, the breaking changes listed in this article may affect you.</span></span> <span data-ttu-id="1c8f3-105">Son değişiklikler kategoriye göre ve bu kategoriler içinde tanıtılan .NET Core sürümüne göre gruplandırılır.</span><span class="sxs-lookup"><span data-stu-id="1c8f3-105">Breaking changes are grouped by category, and within those categories, by the version of .NET Core they were introduced in.</span></span>

> [!NOTE]
> <span data-ttu-id="1c8f3-106">Bu makale, .NET Framework ve .NET Core arasındaki önemli değişikliklerden oluşan bir liste değildir.</span><span class="sxs-lookup"><span data-stu-id="1c8f3-106">This article is not a complete list of breaking changes between .NET Framework and .NET Core.</span></span> <span data-ttu-id="1c8f3-107">Bunlara göz önünde bulundurulduğumuz için en önemli son değişiklikler buraya eklenir.</span><span class="sxs-lookup"><span data-stu-id="1c8f3-107">The most important breaking changes are added here as we become aware of them.</span></span>

## <a name="corefx"></a><span data-ttu-id="1c8f3-108">CoreFx</span><span class="sxs-lookup"><span data-stu-id="1c8f3-108">CoreFx</span></span>

<span data-ttu-id="1c8f3-109">Hataya neden olan değişiklikler:</span><span class="sxs-lookup"><span data-stu-id="1c8f3-109">Breaking changes:</span></span>

- [<span data-ttu-id="1c8f3-110">UseShellExecute varsayılan değerindeki değişiklik</span><span class="sxs-lookup"><span data-stu-id="1c8f3-110">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute)

***

### <a name="net-core-21"></a><span data-ttu-id="1c8f3-111">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="1c8f3-111">.NET Core 2.1</span></span>

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

## <a name="windows-forms"></a><span data-ttu-id="1c8f3-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1c8f3-112">Windows Forms</span></span>

<span data-ttu-id="1c8f3-113">Sürüm 3,0 ' de .NET Core 'a Windows Forms desteği eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="1c8f3-113">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="1c8f3-114">.NET Framework bir Windows Forms uygulamasını .NET Core 'a geçiriyorsanız, burada listelenen son değişiklikler uygulamanızı etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="1c8f3-114">If you're migrating a Windows Forms app from .NET Framework to .NET Core, the breaking changes listed here may affect your app.</span></span>

<span data-ttu-id="1c8f3-115">Hataya neden olan değişiklikler:</span><span class="sxs-lookup"><span data-stu-id="1c8f3-115">Breaking changes:</span></span>

- [<span data-ttu-id="1c8f3-116">Kaldırılan denetimler</span><span class="sxs-lookup"><span data-stu-id="1c8f3-116">Removed controls</span></span>](#removed-controls)
- [<span data-ttu-id="1c8f3-117">Araç ipucu gösterildiğinde CellFormatting olayı oluşturulmaz</span><span class="sxs-lookup"><span data-stu-id="1c8f3-117">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [<span data-ttu-id="1c8f3-118">Control. DefaultFont Segoe UI 9 nk olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="1c8f3-118">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt)
- [<span data-ttu-id="1c8f3-119">FolderBrowserDialog 'u modernleştirme</span><span class="sxs-lookup"><span data-stu-id="1c8f3-119">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog)
- [<span data-ttu-id="1c8f3-120">SerializableAttribute bazı Windows Forms türlerinden kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="1c8f3-120">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types)
- [<span data-ttu-id="1c8f3-121">AllowUpdateChildControlIndexForTabControls uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="1c8f3-121">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [<span data-ttu-id="1c8f3-122">DomainUpDown. UseLegacyScrolling uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="1c8f3-122">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [<span data-ttu-id="1c8f3-123">DoNotLoadLatestRichEditControl uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="1c8f3-123">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [<span data-ttu-id="1c8f3-124">Donotsupportselectallshortcutınmultilinetextbox uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="1c8f3-124">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [<span data-ttu-id="1c8f3-125">DontSupportReentrantFilterMessage uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="1c8f3-125">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [<span data-ttu-id="1c8f3-126">EnableVisualStyleValidation uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="1c8f3-126">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [<span data-ttu-id="1c8f3-127">UseLegacyContextMenuStripSourceControlValue uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="1c8f3-127">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [<span data-ttu-id="1c8f3-128">UseLegacyImages uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="1c8f3-128">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported)
- [<span data-ttu-id="1c8f3-129">Erişilebilir nesne. Runtimeıdfirtıtem için erişim değişikliği</span><span class="sxs-lookup"><span data-stu-id="1c8f3-129">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [<span data-ttu-id="1c8f3-130">Yinelenen API 'Ler Windows Forms kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="1c8f3-130">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms)

### <a name="net-core-31"></a><span data-ttu-id="1c8f3-131">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="1c8f3-131">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

### <a name="net-core-30"></a><span data-ttu-id="1c8f3-132">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="1c8f3-132">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="1c8f3-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c8f3-133">See also</span></span>

- [<span data-ttu-id="1c8f3-134">.NET Core üzerinde her zaman özel durum oluşturan API 'Ler</span><span class="sxs-lookup"><span data-stu-id="1c8f3-134">APIs that always throw exceptions on .NET Core</span></span>](unsupported-apis.md)
- [<span data-ttu-id="1c8f3-135">.NET Core 'da .NET Framework teknolojileri kullanılamıyor</span><span class="sxs-lookup"><span data-stu-id="1c8f3-135">.NET Framework technologies unavailable on .NET Core</span></span>](../porting/net-framework-tech-unavailable.md)
