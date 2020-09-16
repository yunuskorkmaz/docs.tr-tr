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
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="87d4f-103">Windows Forms 'deki değişiklikler kesiliyor</span><span class="sxs-lookup"><span data-stu-id="87d4f-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="87d4f-104">Sürüm 3,0 ' de .NET Core 'a Windows Forms desteği eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="87d4f-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="87d4f-105">Bu makalede, sunulan .NET sürümüne göre Windows Forms yönelik son değişiklikler listelenir.</span><span class="sxs-lookup"><span data-stu-id="87d4f-105">This article lists breaking changes for Windows Forms by the .NET version in which they were introduced.</span></span> <span data-ttu-id="87d4f-106">Bir Windows Forms uygulamasını .NET Framework veya .NET Core 'un önceki bir sürümünden (3,0 veya üzeri) yükseltiyorsanız, bu makale sizin için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="87d4f-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article applies to you.</span></span>

<span data-ttu-id="87d4f-107">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="87d4f-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="87d4f-108">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="87d4f-108">Breaking change</span></span> | <span data-ttu-id="87d4f-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="87d4f-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="87d4f-110">OutputType WPF ve WinForms uygulamaları için WinExe olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="87d4f-110">OutputType set to WinExe for WPF and WinForms apps</span></span>](#outputtype-set-to-winexe-for-wpf-and-winforms-apps) | <span data-ttu-id="87d4f-111">5.0</span><span class="sxs-lookup"><span data-stu-id="87d4f-111">5.0</span></span> |
| [<span data-ttu-id="87d4f-112">DataGridView ile ilgili API 'Ler artık InvalidOperationException 'yi oluşturur</span><span class="sxs-lookup"><span data-stu-id="87d4f-112">DataGridView-related APIs now throw InvalidOperationException</span></span>](#datagridview-related-apis-now-throw-invalidoperationexception) | <span data-ttu-id="87d4f-113">5.0</span><span class="sxs-lookup"><span data-stu-id="87d4f-113">5.0</span></span> |
| [<span data-ttu-id="87d4f-114">WinForms ve WPF uygulamaları Microsoft. NET. SDK kullanır</span><span class="sxs-lookup"><span data-stu-id="87d4f-114">WinForms and WPF apps use Microsoft.NET.Sdk</span></span>](#winforms-and-wpf-apps-use-microsoftnetsdk) | <span data-ttu-id="87d4f-115">5.0</span><span class="sxs-lookup"><span data-stu-id="87d4f-115">5.0</span></span> |
| [<span data-ttu-id="87d4f-116">Durum çubuğu denetimleri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="87d4f-116">Removed status bar controls</span></span>](#removed-status-bar-controls) | <span data-ttu-id="87d4f-117">5.0</span><span class="sxs-lookup"><span data-stu-id="87d4f-117">5.0</span></span> |
| [<span data-ttu-id="87d4f-118">WinForms yöntemleri artık ArgumentException oluşturur</span><span class="sxs-lookup"><span data-stu-id="87d4f-118">WinForms methods now throw ArgumentException</span></span>](#winforms-methods-now-throw-argumentexception) | <span data-ttu-id="87d4f-119">5.0</span><span class="sxs-lookup"><span data-stu-id="87d4f-119">5.0</span></span> |
| [<span data-ttu-id="87d4f-120">WinForms yöntemleri şimdi ArgumentNullException oluşturur</span><span class="sxs-lookup"><span data-stu-id="87d4f-120">WinForms methods now throw ArgumentNullException</span></span>](#winforms-methods-now-throw-argumentnullexception) | <span data-ttu-id="87d4f-121">5.0</span><span class="sxs-lookup"><span data-stu-id="87d4f-121">5.0</span></span> |
| [<span data-ttu-id="87d4f-122">WinForms özellikleri artık ArgumentOutOfRangeException oluşturur</span><span class="sxs-lookup"><span data-stu-id="87d4f-122">WinForms properties now throw ArgumentOutOfRangeException</span></span>](#winforms-properties-now-throw-argumentoutofrangeexception) | <span data-ttu-id="87d4f-123">5.0</span><span class="sxs-lookup"><span data-stu-id="87d4f-123">5.0</span></span> |
| [<span data-ttu-id="87d4f-124">Kaldırılan denetimler</span><span class="sxs-lookup"><span data-stu-id="87d4f-124">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="87d4f-125">3,1</span><span class="sxs-lookup"><span data-stu-id="87d4f-125">3.1</span></span> |
| [<span data-ttu-id="87d4f-126">Araç ipucu gösterildiğinde CellFormatting olayı oluşturulmaz</span><span class="sxs-lookup"><span data-stu-id="87d4f-126">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="87d4f-127">3,1</span><span class="sxs-lookup"><span data-stu-id="87d4f-127">3.1</span></span> |
| [<span data-ttu-id="87d4f-128">Control. DefaultFont Segoe UI 9 nk olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="87d4f-128">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="87d4f-129">3.0</span><span class="sxs-lookup"><span data-stu-id="87d4f-129">3.0</span></span> |
| [<span data-ttu-id="87d4f-130">FolderBrowserDialog 'u modernleştirme</span><span class="sxs-lookup"><span data-stu-id="87d4f-130">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="87d4f-131">3.0</span><span class="sxs-lookup"><span data-stu-id="87d4f-131">3.0</span></span> |
| [<span data-ttu-id="87d4f-132">SerializableAttribute bazı Windows Forms türlerinden kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="87d4f-132">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="87d4f-133">3.0</span><span class="sxs-lookup"><span data-stu-id="87d4f-133">3.0</span></span> |
| [<span data-ttu-id="87d4f-134">AllowUpdateChildControlIndexForTabControls uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="87d4f-134">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="87d4f-135">3.0</span><span class="sxs-lookup"><span data-stu-id="87d4f-135">3.0</span></span> |
| [<span data-ttu-id="87d4f-136">DomainUpDown. UseLegacyScrolling uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="87d4f-136">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="87d4f-137">3.0</span><span class="sxs-lookup"><span data-stu-id="87d4f-137">3.0</span></span> |
| [<span data-ttu-id="87d4f-138">DoNotLoadLatestRichEditControl uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="87d4f-138">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="87d4f-139">3.0</span><span class="sxs-lookup"><span data-stu-id="87d4f-139">3.0</span></span> |
| [<span data-ttu-id="87d4f-140">Donotsupportselectallshortcutınmultilinetextbox uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="87d4f-140">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="87d4f-141">3.0</span><span class="sxs-lookup"><span data-stu-id="87d4f-141">3.0</span></span> |
| [<span data-ttu-id="87d4f-142">DontSupportReentrantFilterMessage uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="87d4f-142">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="87d4f-143">3.0</span><span class="sxs-lookup"><span data-stu-id="87d4f-143">3.0</span></span> |
| [<span data-ttu-id="87d4f-144">EnableVisualStyleValidation uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="87d4f-144">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="87d4f-145">3.0</span><span class="sxs-lookup"><span data-stu-id="87d4f-145">3.0</span></span> |
| [<span data-ttu-id="87d4f-146">UseLegacyContextMenuStripSourceControlValue uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="87d4f-146">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="87d4f-147">3.0</span><span class="sxs-lookup"><span data-stu-id="87d4f-147">3.0</span></span> |
| [<span data-ttu-id="87d4f-148">UseLegacyImages uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="87d4f-148">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="87d4f-149">3.0</span><span class="sxs-lookup"><span data-stu-id="87d4f-149">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="87d4f-150">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="87d4f-150">.NET 5.0</span></span>

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

## <a name="net-core-31"></a><span data-ttu-id="87d4f-151">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="87d4f-151">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="87d4f-152">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="87d4f-152">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="87d4f-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87d4f-153">See also</span></span>

- [<span data-ttu-id="87d4f-154">.NET Core 'a Windows Forms uygulaması bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="87d4f-154">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)
