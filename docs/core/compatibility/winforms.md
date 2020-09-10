---
title: Windows Forms son değişiklikler
description: .NET Core ve .NET 5 için Windows Forms 'deki son değişiklikleri listeler.
ms.date: 09/08/2020
ms.openlocfilehash: c3d2d23601d6a2d9d44761c4371fe34d3d5ed1f3
ms.sourcegitcommit: 1e8382d0ce8b5515864f8fbb178b9fd692a7503f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89656357"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="e9f38-103">Windows Forms 'deki değişiklikler kesiliyor</span><span class="sxs-lookup"><span data-stu-id="e9f38-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="e9f38-104">Sürüm 3,0 ' de .NET Core 'a Windows Forms desteği eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="e9f38-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="e9f38-105">Bu makalede, sunulan .NET sürümüne göre Windows Forms yönelik son değişiklikler listelenir.</span><span class="sxs-lookup"><span data-stu-id="e9f38-105">This article lists breaking changes for Windows Forms by the .NET version in which they were introduced.</span></span> <span data-ttu-id="e9f38-106">Bir Windows Forms uygulamasını .NET Framework veya .NET Core 'un önceki bir sürümünden (3,0 veya üzeri) yükseltiyorsanız, bu makale sizin için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e9f38-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article applies to you.</span></span>

<span data-ttu-id="e9f38-107">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="e9f38-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="e9f38-108">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="e9f38-108">Breaking change</span></span> | <span data-ttu-id="e9f38-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e9f38-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="e9f38-110">DataGridView ile ilgili API 'Ler artık InvalidOperationException 'yi oluşturur</span><span class="sxs-lookup"><span data-stu-id="e9f38-110">DataGridView-related APIs now throw InvalidOperationException</span></span>](#datagridview-related-apis-now-throw-invalidoperationexception) | <span data-ttu-id="e9f38-111">5.0</span><span class="sxs-lookup"><span data-stu-id="e9f38-111">5.0</span></span> |
| [<span data-ttu-id="e9f38-112">WinForms ve WPF uygulamaları Microsoft. NET. SDK kullanır</span><span class="sxs-lookup"><span data-stu-id="e9f38-112">WinForms and WPF apps use Microsoft.NET.Sdk</span></span>](#winforms-and-wpf-apps-use-microsoftnetsdk) | <span data-ttu-id="e9f38-113">5.0</span><span class="sxs-lookup"><span data-stu-id="e9f38-113">5.0</span></span> |
| [<span data-ttu-id="e9f38-114">Durum çubuğu denetimleri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="e9f38-114">Removed status bar controls</span></span>](#removed-status-bar-controls) | <span data-ttu-id="e9f38-115">5.0</span><span class="sxs-lookup"><span data-stu-id="e9f38-115">5.0</span></span> |
| [<span data-ttu-id="e9f38-116">WinForms yöntemleri artık ArgumentException oluşturur</span><span class="sxs-lookup"><span data-stu-id="e9f38-116">WinForms methods now throw ArgumentException</span></span>](#winforms-methods-now-throw-argumentexception) | <span data-ttu-id="e9f38-117">5.0</span><span class="sxs-lookup"><span data-stu-id="e9f38-117">5.0</span></span> |
| [<span data-ttu-id="e9f38-118">WinForms yöntemleri şimdi ArgumentNullException oluşturur</span><span class="sxs-lookup"><span data-stu-id="e9f38-118">WinForms methods now throw ArgumentNullException</span></span>](#winforms-methods-now-throw-argumentnullexception) | <span data-ttu-id="e9f38-119">5.0</span><span class="sxs-lookup"><span data-stu-id="e9f38-119">5.0</span></span> |
| [<span data-ttu-id="e9f38-120">WinForms özellikleri artık ArgumentOutOfRangeException oluşturur</span><span class="sxs-lookup"><span data-stu-id="e9f38-120">WinForms properties now throw ArgumentOutOfRangeException</span></span>](#winforms-properties-now-throw-argumentoutofrangeexception) | <span data-ttu-id="e9f38-121">5.0</span><span class="sxs-lookup"><span data-stu-id="e9f38-121">5.0</span></span> |
| [<span data-ttu-id="e9f38-122">Kaldırılan denetimler</span><span class="sxs-lookup"><span data-stu-id="e9f38-122">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="e9f38-123">3,1</span><span class="sxs-lookup"><span data-stu-id="e9f38-123">3.1</span></span> |
| [<span data-ttu-id="e9f38-124">Araç ipucu gösterildiğinde CellFormatting olayı oluşturulmaz</span><span class="sxs-lookup"><span data-stu-id="e9f38-124">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="e9f38-125">3,1</span><span class="sxs-lookup"><span data-stu-id="e9f38-125">3.1</span></span> |
| [<span data-ttu-id="e9f38-126">Control. DefaultFont Segoe UI 9 nk olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="e9f38-126">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="e9f38-127">3.0</span><span class="sxs-lookup"><span data-stu-id="e9f38-127">3.0</span></span> |
| [<span data-ttu-id="e9f38-128">FolderBrowserDialog 'u modernleştirme</span><span class="sxs-lookup"><span data-stu-id="e9f38-128">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="e9f38-129">3.0</span><span class="sxs-lookup"><span data-stu-id="e9f38-129">3.0</span></span> |
| [<span data-ttu-id="e9f38-130">SerializableAttribute bazı Windows Forms türlerinden kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="e9f38-130">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="e9f38-131">3.0</span><span class="sxs-lookup"><span data-stu-id="e9f38-131">3.0</span></span> |
| [<span data-ttu-id="e9f38-132">AllowUpdateChildControlIndexForTabControls uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="e9f38-132">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="e9f38-133">3.0</span><span class="sxs-lookup"><span data-stu-id="e9f38-133">3.0</span></span> |
| [<span data-ttu-id="e9f38-134">DomainUpDown. UseLegacyScrolling uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="e9f38-134">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="e9f38-135">3.0</span><span class="sxs-lookup"><span data-stu-id="e9f38-135">3.0</span></span> |
| [<span data-ttu-id="e9f38-136">DoNotLoadLatestRichEditControl uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="e9f38-136">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="e9f38-137">3.0</span><span class="sxs-lookup"><span data-stu-id="e9f38-137">3.0</span></span> |
| [<span data-ttu-id="e9f38-138">Donotsupportselectallshortcutınmultilinetextbox uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="e9f38-138">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="e9f38-139">3.0</span><span class="sxs-lookup"><span data-stu-id="e9f38-139">3.0</span></span> |
| [<span data-ttu-id="e9f38-140">DontSupportReentrantFilterMessage uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="e9f38-140">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="e9f38-141">3.0</span><span class="sxs-lookup"><span data-stu-id="e9f38-141">3.0</span></span> |
| [<span data-ttu-id="e9f38-142">EnableVisualStyleValidation uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="e9f38-142">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="e9f38-143">3.0</span><span class="sxs-lookup"><span data-stu-id="e9f38-143">3.0</span></span> |
| [<span data-ttu-id="e9f38-144">UseLegacyContextMenuStripSourceControlValue uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="e9f38-144">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="e9f38-145">3.0</span><span class="sxs-lookup"><span data-stu-id="e9f38-145">3.0</span></span> |
| [<span data-ttu-id="e9f38-146">UseLegacyImages uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="e9f38-146">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="e9f38-147">3.0</span><span class="sxs-lookup"><span data-stu-id="e9f38-147">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="e9f38-148">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="e9f38-148">.NET 5.0</span></span>

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

## <a name="net-core-31"></a><span data-ttu-id="e9f38-149">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="e9f38-149">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="e9f38-150">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e9f38-150">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e9f38-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9f38-151">See also</span></span>

- [<span data-ttu-id="e9f38-152">.NET Core 'a Windows Forms uygulaması bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="e9f38-152">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)
