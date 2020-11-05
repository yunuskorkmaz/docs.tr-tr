---
title: Windows Forms son değişiklikler
description: .NET Core ve .NET 5 için Windows Forms 'deki son değişiklikleri listeler.
ms.date: 09/08/2020
ms.openlocfilehash: 01810a690227bbcab2103f00767315dbc5d5fae3
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400642"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="1cd77-103">Windows Forms 'deki değişiklikler kesiliyor</span><span class="sxs-lookup"><span data-stu-id="1cd77-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="1cd77-104">Sürüm 3,0 ' de .NET Core 'a Windows Forms desteği eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="1cd77-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="1cd77-105">Bu makalede, sunulan .NET sürümüne göre Windows Forms yönelik son değişiklikler listelenir.</span><span class="sxs-lookup"><span data-stu-id="1cd77-105">This article lists breaking changes for Windows Forms by the .NET version in which they were introduced.</span></span> <span data-ttu-id="1cd77-106">Bir Windows Forms uygulamasını .NET Framework veya .NET Core 'un önceki bir sürümünden (3,0 veya üzeri) yükseltiyorsanız, bu makale sizin için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="1cd77-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article applies to you.</span></span>

<span data-ttu-id="1cd77-107">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="1cd77-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="1cd77-108">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="1cd77-108">Breaking change</span></span> | <span data-ttu-id="1cd77-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="1cd77-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="1cd77-110">TextFormatFlags. ModifyString artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="1cd77-110">TextFormatFlags.ModifyString is obsolete</span></span>](#textformatflagsmodifystring-is-obsolete) | <span data-ttu-id="1cd77-111">5.0</span><span class="sxs-lookup"><span data-stu-id="1cd77-111">5.0</span></span> |
| [<span data-ttu-id="1cd77-112">DataGridView artık özelleştirilmiş hücre stilleri için yazı tiplerini sıfırlıyor</span><span class="sxs-lookup"><span data-stu-id="1cd77-112">DataGridView no longer resets fonts for customized cell styles</span></span>](#datagridview-no-longer-resets-fonts-for-customized-cell-styles) | <span data-ttu-id="1cd77-113">5.0</span><span class="sxs-lookup"><span data-stu-id="1cd77-113">5.0</span></span> |
| [<span data-ttu-id="1cd77-114">OutputType WPF ve WinForms uygulamaları için WinExe olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="1cd77-114">OutputType set to WinExe for WPF and WinForms apps</span></span>](#outputtype-set-to-winexe-for-wpf-and-winforms-apps) | <span data-ttu-id="1cd77-115">5.0</span><span class="sxs-lookup"><span data-stu-id="1cd77-115">5.0</span></span> |
| [<span data-ttu-id="1cd77-116">DataGridView ile ilgili API 'Ler artık InvalidOperationException 'yi oluşturur</span><span class="sxs-lookup"><span data-stu-id="1cd77-116">DataGridView-related APIs now throw InvalidOperationException</span></span>](#datagridview-related-apis-now-throw-invalidoperationexception) | <span data-ttu-id="1cd77-117">5.0</span><span class="sxs-lookup"><span data-stu-id="1cd77-117">5.0</span></span> |
| [<span data-ttu-id="1cd77-118">WinForms ve WPF uygulamaları Microsoft. NET. SDK kullanır</span><span class="sxs-lookup"><span data-stu-id="1cd77-118">WinForms and WPF apps use Microsoft.NET.Sdk</span></span>](#winforms-and-wpf-apps-use-microsoftnetsdk) | <span data-ttu-id="1cd77-119">5.0</span><span class="sxs-lookup"><span data-stu-id="1cd77-119">5.0</span></span> |
| [<span data-ttu-id="1cd77-120">Durum çubuğu denetimleri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="1cd77-120">Removed status bar controls</span></span>](#removed-status-bar-controls) | <span data-ttu-id="1cd77-121">5.0</span><span class="sxs-lookup"><span data-stu-id="1cd77-121">5.0</span></span> |
| [<span data-ttu-id="1cd77-122">WinForms yöntemleri artık ArgumentException oluşturur</span><span class="sxs-lookup"><span data-stu-id="1cd77-122">WinForms methods now throw ArgumentException</span></span>](#winforms-methods-now-throw-argumentexception) | <span data-ttu-id="1cd77-123">5.0</span><span class="sxs-lookup"><span data-stu-id="1cd77-123">5.0</span></span> |
| [<span data-ttu-id="1cd77-124">WinForms yöntemleri şimdi ArgumentNullException oluşturur</span><span class="sxs-lookup"><span data-stu-id="1cd77-124">WinForms methods now throw ArgumentNullException</span></span>](#winforms-methods-now-throw-argumentnullexception) | <span data-ttu-id="1cd77-125">5.0</span><span class="sxs-lookup"><span data-stu-id="1cd77-125">5.0</span></span> |
| [<span data-ttu-id="1cd77-126">WinForms özellikleri artık ArgumentOutOfRangeException oluşturur</span><span class="sxs-lookup"><span data-stu-id="1cd77-126">WinForms properties now throw ArgumentOutOfRangeException</span></span>](#winforms-properties-now-throw-argumentoutofrangeexception) | <span data-ttu-id="1cd77-127">5.0</span><span class="sxs-lookup"><span data-stu-id="1cd77-127">5.0</span></span> |
| [<span data-ttu-id="1cd77-128">Kaldırılan denetimler</span><span class="sxs-lookup"><span data-stu-id="1cd77-128">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="1cd77-129">3,1</span><span class="sxs-lookup"><span data-stu-id="1cd77-129">3.1</span></span> |
| [<span data-ttu-id="1cd77-130">Araç ipucu gösterildiğinde CellFormatting olayı oluşturulmaz</span><span class="sxs-lookup"><span data-stu-id="1cd77-130">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="1cd77-131">3,1</span><span class="sxs-lookup"><span data-stu-id="1cd77-131">3.1</span></span> |
| [<span data-ttu-id="1cd77-132">Control. DefaultFont Segoe UI 9 nk olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="1cd77-132">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="1cd77-133">3,0</span><span class="sxs-lookup"><span data-stu-id="1cd77-133">3.0</span></span> |
| [<span data-ttu-id="1cd77-134">FolderBrowserDialog 'u modernleştirme</span><span class="sxs-lookup"><span data-stu-id="1cd77-134">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="1cd77-135">3,0</span><span class="sxs-lookup"><span data-stu-id="1cd77-135">3.0</span></span> |
| [<span data-ttu-id="1cd77-136">SerializableAttribute bazı Windows Forms türlerinden kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="1cd77-136">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="1cd77-137">3,0</span><span class="sxs-lookup"><span data-stu-id="1cd77-137">3.0</span></span> |
| [<span data-ttu-id="1cd77-138">AllowUpdateChildControlIndexForTabControls uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="1cd77-138">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="1cd77-139">3,0</span><span class="sxs-lookup"><span data-stu-id="1cd77-139">3.0</span></span> |
| [<span data-ttu-id="1cd77-140">DomainUpDown. UseLegacyScrolling uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="1cd77-140">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="1cd77-141">3,0</span><span class="sxs-lookup"><span data-stu-id="1cd77-141">3.0</span></span> |
| [<span data-ttu-id="1cd77-142">DoNotLoadLatestRichEditControl uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="1cd77-142">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="1cd77-143">3,0</span><span class="sxs-lookup"><span data-stu-id="1cd77-143">3.0</span></span> |
| [<span data-ttu-id="1cd77-144">Donotsupportselectallshortcutınmultilinetextbox uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="1cd77-144">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="1cd77-145">3,0</span><span class="sxs-lookup"><span data-stu-id="1cd77-145">3.0</span></span> |
| [<span data-ttu-id="1cd77-146">DontSupportReentrantFilterMessage uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="1cd77-146">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="1cd77-147">3,0</span><span class="sxs-lookup"><span data-stu-id="1cd77-147">3.0</span></span> |
| [<span data-ttu-id="1cd77-148">EnableVisualStyleValidation uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="1cd77-148">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="1cd77-149">3,0</span><span class="sxs-lookup"><span data-stu-id="1cd77-149">3.0</span></span> |
| [<span data-ttu-id="1cd77-150">UseLegacyContextMenuStripSourceControlValue uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="1cd77-150">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="1cd77-151">3,0</span><span class="sxs-lookup"><span data-stu-id="1cd77-151">3.0</span></span> |
| [<span data-ttu-id="1cd77-152">UseLegacyImages uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="1cd77-152">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="1cd77-153">3,0</span><span class="sxs-lookup"><span data-stu-id="1cd77-153">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="1cd77-154">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="1cd77-154">.NET 5.0</span></span>

[!INCLUDE [modifystring-field-of-textformatflags-obsolete](../../../includes/core-changes/windowsforms/5.0/modifystring-field-of-textformatflags-obsolete.md)]

***

[!INCLUDE [datagridview-doesnt-reset-custom-font-settings](../../../includes/core-changes/windowsforms/5.0/datagridview-doesnt-reset-custom-font-settings.md)]

<span data-ttu-id="1cd77-155">\*\*_</span><span class="sxs-lookup"><span data-stu-id="1cd77-155">\*\*_</span></span>

[!INCLUDE [automatically-infer-winexe-output-type](../../../includes/core-changes/windowsforms/5.0/automatically-infer-winexe-output-type.md)]

_*_

[!INCLUDE [null-owner-causes-invalidoperationexception](../../../includes/core-changes/windowsforms/5.0/null-owner-causes-invalidoperationexception.md)]

_*_

[!INCLUDE [sdk-and-target-framework-change](../../../includes/core-changes/windowsforms/5.0/sdk-and-target-framework-change.md)]

_*_

[!INCLUDE [winforms-deprecated-controls](../../../includes/core-changes/windowsforms/5.0/winforms-deprecated-controls.md)]

_*_

[!INCLUDE [invalid-args-cause-argumentexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentexception.md)]

_*_

[!INCLUDE [null-args-cause-argumentnullexception](../../../includes/core-changes/windowsforms/5.0/null-args-cause-argumentnullexception.md)]

_*_

[!INCLUDE [invalid-args-cause-argumentoutofrangeexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentoutofrangeexception.md)]

_*_

## <a name="net-core-31"></a><span data-ttu-id="1cd77-156">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="1cd77-156">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

_*_

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

_*_

## <a name="net-core-30"></a><span data-ttu-id="1cd77-157">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="1cd77-157">.NET Core 3.0</span></span>

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

<span data-ttu-id="1cd77-158">_\*\*</span><span class="sxs-lookup"><span data-stu-id="1cd77-158">_\*\*</span></span>

## <a name="see-also"></a><span data-ttu-id="1cd77-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1cd77-159">See also</span></span>

- [<span data-ttu-id="1cd77-160">.NET Core 'a Windows Forms uygulaması bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="1cd77-160">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)
