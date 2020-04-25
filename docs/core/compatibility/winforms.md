---
title: Windows Forms son değişiklikler
description: .NET Core için Windows Forms 'deki son değişiklikleri listeler.
ms.date: 01/08/2020
ms.openlocfilehash: 75d369c7fb999da81a50fe46716e125c3840eb7a
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158443"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="6d4f0-103">Windows Forms 'deki değişiklikler kesiliyor</span><span class="sxs-lookup"><span data-stu-id="6d4f0-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="6d4f0-104">Sürüm 3,0 ' de .NET Core 'a Windows Forms desteği eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="6d4f0-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="6d4f0-105">Bu makalede, sunulan .NET Core sürümü tarafından Windows Forms yönelik son değişiklikler listelenir.</span><span class="sxs-lookup"><span data-stu-id="6d4f0-105">This article lists breaking changes for Windows Forms by the .NET Core version in which they were introduced.</span></span> <span data-ttu-id="6d4f0-106">Bir Windows Forms uygulamasını .NET Framework veya .NET Core 'un önceki bir sürümünden (3,0 veya üzeri) yükseltiyorsanız, bu makale sizin için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6d4f0-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article is applicable to you.</span></span>

<span data-ttu-id="6d4f0-107">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="6d4f0-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="6d4f0-108">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="6d4f0-108">Breaking change</span></span> | <span data-ttu-id="6d4f0-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="6d4f0-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="6d4f0-110">Durum çubuğu denetimleri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="6d4f0-110">Removed status bar controls</span></span>](#removed-status-bar-controls) | <span data-ttu-id="6d4f0-111">5.0</span><span class="sxs-lookup"><span data-stu-id="6d4f0-111">5.0</span></span> |
| [<span data-ttu-id="6d4f0-112">WinForms yöntemleri artık ArgumentException oluşturur</span><span class="sxs-lookup"><span data-stu-id="6d4f0-112">WinForms methods now throw ArgumentException</span></span>](#winforms-methods-now-throw-argumentexception) | <span data-ttu-id="6d4f0-113">5.0</span><span class="sxs-lookup"><span data-stu-id="6d4f0-113">5.0</span></span> |
| [<span data-ttu-id="6d4f0-114">WinForms yöntemleri şimdi ArgumentNullException oluşturur</span><span class="sxs-lookup"><span data-stu-id="6d4f0-114">WinForms methods now throw ArgumentNullException</span></span>](#winforms-methods-now-throw-argumentnullexception) | <span data-ttu-id="6d4f0-115">5.0</span><span class="sxs-lookup"><span data-stu-id="6d4f0-115">5.0</span></span> |
| [<span data-ttu-id="6d4f0-116">Kaldırılan denetimler</span><span class="sxs-lookup"><span data-stu-id="6d4f0-116">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="6d4f0-117">3.1</span><span class="sxs-lookup"><span data-stu-id="6d4f0-117">3.1</span></span> |
| [<span data-ttu-id="6d4f0-118">Araç ipucu gösterildiğinde CellFormatting olayı oluşturulmaz</span><span class="sxs-lookup"><span data-stu-id="6d4f0-118">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="6d4f0-119">3.1</span><span class="sxs-lookup"><span data-stu-id="6d4f0-119">3.1</span></span> |
| [<span data-ttu-id="6d4f0-120">Control. DefaultFont Segoe UI 9 nk olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="6d4f0-120">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="6d4f0-121">3,0</span><span class="sxs-lookup"><span data-stu-id="6d4f0-121">3.0</span></span> |
| [<span data-ttu-id="6d4f0-122">FolderBrowserDialog 'u modernleştirme</span><span class="sxs-lookup"><span data-stu-id="6d4f0-122">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="6d4f0-123">3,0</span><span class="sxs-lookup"><span data-stu-id="6d4f0-123">3.0</span></span> |
| [<span data-ttu-id="6d4f0-124">SerializableAttribute bazı Windows Forms türlerinden kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="6d4f0-124">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="6d4f0-125">3,0</span><span class="sxs-lookup"><span data-stu-id="6d4f0-125">3.0</span></span> |
| [<span data-ttu-id="6d4f0-126">AllowUpdateChildControlIndexForTabControls uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="6d4f0-126">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="6d4f0-127">3,0</span><span class="sxs-lookup"><span data-stu-id="6d4f0-127">3.0</span></span> |
| [<span data-ttu-id="6d4f0-128">DomainUpDown. UseLegacyScrolling uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="6d4f0-128">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="6d4f0-129">3,0</span><span class="sxs-lookup"><span data-stu-id="6d4f0-129">3.0</span></span> |
| [<span data-ttu-id="6d4f0-130">DoNotLoadLatestRichEditControl uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="6d4f0-130">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="6d4f0-131">3,0</span><span class="sxs-lookup"><span data-stu-id="6d4f0-131">3.0</span></span> |
| [<span data-ttu-id="6d4f0-132">Donotsupportselectallshortcutınmultilinetextbox uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="6d4f0-132">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="6d4f0-133">3,0</span><span class="sxs-lookup"><span data-stu-id="6d4f0-133">3.0</span></span> |
| [<span data-ttu-id="6d4f0-134">DontSupportReentrantFilterMessage uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="6d4f0-134">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="6d4f0-135">3,0</span><span class="sxs-lookup"><span data-stu-id="6d4f0-135">3.0</span></span> |
| [<span data-ttu-id="6d4f0-136">EnableVisualStyleValidation uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="6d4f0-136">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="6d4f0-137">3,0</span><span class="sxs-lookup"><span data-stu-id="6d4f0-137">3.0</span></span> |
| [<span data-ttu-id="6d4f0-138">UseLegacyContextMenuStripSourceControlValue uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="6d4f0-138">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="6d4f0-139">3,0</span><span class="sxs-lookup"><span data-stu-id="6d4f0-139">3.0</span></span> |
| [<span data-ttu-id="6d4f0-140">UseLegacyImages uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="6d4f0-140">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="6d4f0-141">3,0</span><span class="sxs-lookup"><span data-stu-id="6d4f0-141">3.0</span></span> |
| [<span data-ttu-id="6d4f0-142">Erişilebilir nesne. Runtimeıdfirtıtem için erişim değişikliği</span><span class="sxs-lookup"><span data-stu-id="6d4f0-142">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem) | <span data-ttu-id="6d4f0-143">3,0</span><span class="sxs-lookup"><span data-stu-id="6d4f0-143">3.0</span></span> |
| [<span data-ttu-id="6d4f0-144">Yinelenen API 'Ler Windows Forms kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="6d4f0-144">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms) | <span data-ttu-id="6d4f0-145">3,0</span><span class="sxs-lookup"><span data-stu-id="6d4f0-145">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="6d4f0-146">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="6d4f0-146">.NET 5.0</span></span>

[!INCLUDE [winforms-deprecated-controls](../../../includes/core-changes/windowsforms/5.0/winforms-deprecated-controls.md)]

***

[!INCLUDE [invalid-args-cause-argumentexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentexception.md)]

***

[!INCLUDE [null-args-cause-argumentnullexception](../../../includes/core-changes/windowsforms/5.0/null-args-cause-argumentnullexception.md)]

***

## <a name="net-core-31"></a><span data-ttu-id="6d4f0-147">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="6d4f0-147">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="6d4f0-148">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6d4f0-148">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6d4f0-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d4f0-149">See also</span></span>

- [<span data-ttu-id="6d4f0-150">.NET Core 'a Windows Forms uygulaması bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="6d4f0-150">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)
