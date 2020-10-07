---
title: Windows Forms son değişiklikler
description: .NET Core ve .NET 5 için Windows Forms 'deki son değişiklikleri listeler.
ms.date: 09/08/2020
ms.openlocfilehash: 2311faab026bf1dfde348e231937eff73ec46172
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91804873"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="2f621-103">Windows Forms 'deki değişiklikler kesiliyor</span><span class="sxs-lookup"><span data-stu-id="2f621-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="2f621-104">Sürüm 3,0 ' de .NET Core 'a Windows Forms desteği eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="2f621-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="2f621-105">Bu makalede, sunulan .NET sürümüne göre Windows Forms yönelik son değişiklikler listelenir.</span><span class="sxs-lookup"><span data-stu-id="2f621-105">This article lists breaking changes for Windows Forms by the .NET version in which they were introduced.</span></span> <span data-ttu-id="2f621-106">Bir Windows Forms uygulamasını .NET Framework veya .NET Core 'un önceki bir sürümünden (3,0 veya üzeri) yükseltiyorsanız, bu makale sizin için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2f621-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article applies to you.</span></span>

<span data-ttu-id="2f621-107">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="2f621-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="2f621-108">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="2f621-108">Breaking change</span></span> | <span data-ttu-id="2f621-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="2f621-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="2f621-110">DataGridView artık özelleştirilmiş hücre stilleri için yazı tiplerini sıfırlıyor</span><span class="sxs-lookup"><span data-stu-id="2f621-110">DataGridView no longer resets fonts for customized cell styles</span></span>](#datagridview-no-longer-resets-fonts-for-customized-cell-styles) | <span data-ttu-id="2f621-111">5.0</span><span class="sxs-lookup"><span data-stu-id="2f621-111">5.0</span></span> |
| [<span data-ttu-id="2f621-112">OutputType WPF ve WinForms uygulamaları için WinExe olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="2f621-112">OutputType set to WinExe for WPF and WinForms apps</span></span>](#outputtype-set-to-winexe-for-wpf-and-winforms-apps) | <span data-ttu-id="2f621-113">5.0</span><span class="sxs-lookup"><span data-stu-id="2f621-113">5.0</span></span> |
| [<span data-ttu-id="2f621-114">DataGridView ile ilgili API 'Ler artık InvalidOperationException 'yi oluşturur</span><span class="sxs-lookup"><span data-stu-id="2f621-114">DataGridView-related APIs now throw InvalidOperationException</span></span>](#datagridview-related-apis-now-throw-invalidoperationexception) | <span data-ttu-id="2f621-115">5.0</span><span class="sxs-lookup"><span data-stu-id="2f621-115">5.0</span></span> |
| [<span data-ttu-id="2f621-116">WinForms ve WPF uygulamaları Microsoft. NET. SDK kullanır</span><span class="sxs-lookup"><span data-stu-id="2f621-116">WinForms and WPF apps use Microsoft.NET.Sdk</span></span>](#winforms-and-wpf-apps-use-microsoftnetsdk) | <span data-ttu-id="2f621-117">5.0</span><span class="sxs-lookup"><span data-stu-id="2f621-117">5.0</span></span> |
| [<span data-ttu-id="2f621-118">Durum çubuğu denetimleri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="2f621-118">Removed status bar controls</span></span>](#removed-status-bar-controls) | <span data-ttu-id="2f621-119">5.0</span><span class="sxs-lookup"><span data-stu-id="2f621-119">5.0</span></span> |
| [<span data-ttu-id="2f621-120">WinForms yöntemleri artık ArgumentException oluşturur</span><span class="sxs-lookup"><span data-stu-id="2f621-120">WinForms methods now throw ArgumentException</span></span>](#winforms-methods-now-throw-argumentexception) | <span data-ttu-id="2f621-121">5.0</span><span class="sxs-lookup"><span data-stu-id="2f621-121">5.0</span></span> |
| [<span data-ttu-id="2f621-122">WinForms yöntemleri şimdi ArgumentNullException oluşturur</span><span class="sxs-lookup"><span data-stu-id="2f621-122">WinForms methods now throw ArgumentNullException</span></span>](#winforms-methods-now-throw-argumentnullexception) | <span data-ttu-id="2f621-123">5.0</span><span class="sxs-lookup"><span data-stu-id="2f621-123">5.0</span></span> |
| [<span data-ttu-id="2f621-124">WinForms özellikleri artık ArgumentOutOfRangeException oluşturur</span><span class="sxs-lookup"><span data-stu-id="2f621-124">WinForms properties now throw ArgumentOutOfRangeException</span></span>](#winforms-properties-now-throw-argumentoutofrangeexception) | <span data-ttu-id="2f621-125">5.0</span><span class="sxs-lookup"><span data-stu-id="2f621-125">5.0</span></span> |
| [<span data-ttu-id="2f621-126">Kaldırılan denetimler</span><span class="sxs-lookup"><span data-stu-id="2f621-126">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="2f621-127">3,1</span><span class="sxs-lookup"><span data-stu-id="2f621-127">3.1</span></span> |
| [<span data-ttu-id="2f621-128">Araç ipucu gösterildiğinde CellFormatting olayı oluşturulmaz</span><span class="sxs-lookup"><span data-stu-id="2f621-128">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="2f621-129">3,1</span><span class="sxs-lookup"><span data-stu-id="2f621-129">3.1</span></span> |
| [<span data-ttu-id="2f621-130">Control. DefaultFont Segoe UI 9 nk olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="2f621-130">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="2f621-131">3.0</span><span class="sxs-lookup"><span data-stu-id="2f621-131">3.0</span></span> |
| [<span data-ttu-id="2f621-132">FolderBrowserDialog 'u modernleştirme</span><span class="sxs-lookup"><span data-stu-id="2f621-132">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="2f621-133">3.0</span><span class="sxs-lookup"><span data-stu-id="2f621-133">3.0</span></span> |
| [<span data-ttu-id="2f621-134">SerializableAttribute bazı Windows Forms türlerinden kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="2f621-134">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="2f621-135">3.0</span><span class="sxs-lookup"><span data-stu-id="2f621-135">3.0</span></span> |
| [<span data-ttu-id="2f621-136">AllowUpdateChildControlIndexForTabControls uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="2f621-136">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="2f621-137">3.0</span><span class="sxs-lookup"><span data-stu-id="2f621-137">3.0</span></span> |
| [<span data-ttu-id="2f621-138">DomainUpDown. UseLegacyScrolling uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="2f621-138">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="2f621-139">3.0</span><span class="sxs-lookup"><span data-stu-id="2f621-139">3.0</span></span> |
| [<span data-ttu-id="2f621-140">DoNotLoadLatestRichEditControl uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="2f621-140">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="2f621-141">3.0</span><span class="sxs-lookup"><span data-stu-id="2f621-141">3.0</span></span> |
| [<span data-ttu-id="2f621-142">Donotsupportselectallshortcutınmultilinetextbox uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="2f621-142">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="2f621-143">3.0</span><span class="sxs-lookup"><span data-stu-id="2f621-143">3.0</span></span> |
| [<span data-ttu-id="2f621-144">DontSupportReentrantFilterMessage uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="2f621-144">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="2f621-145">3.0</span><span class="sxs-lookup"><span data-stu-id="2f621-145">3.0</span></span> |
| [<span data-ttu-id="2f621-146">EnableVisualStyleValidation uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="2f621-146">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="2f621-147">3.0</span><span class="sxs-lookup"><span data-stu-id="2f621-147">3.0</span></span> |
| [<span data-ttu-id="2f621-148">UseLegacyContextMenuStripSourceControlValue uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="2f621-148">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="2f621-149">3.0</span><span class="sxs-lookup"><span data-stu-id="2f621-149">3.0</span></span> |
| [<span data-ttu-id="2f621-150">UseLegacyImages uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="2f621-150">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="2f621-151">3.0</span><span class="sxs-lookup"><span data-stu-id="2f621-151">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="2f621-152">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="2f621-152">.NET 5.0</span></span>

[!INCLUDE [datagridview-doesnt-reset-custom-font-settings](../../../includes/core-changes/windowsforms/5.0/datagridview-doesnt-reset-custom-font-settings.md)]

***

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

## <a name="net-core-31"></a><span data-ttu-id="2f621-153">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="2f621-153">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="2f621-154">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2f621-154">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2f621-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f621-155">See also</span></span>

- [<span data-ttu-id="2f621-156">.NET Core 'a Windows Forms uygulaması bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="2f621-156">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)
