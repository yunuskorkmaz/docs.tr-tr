---
title: Windows Forms son değişiklikler
description: .NET Core için Windows Forms 'deki son değişiklikleri listeler.
ms.date: 01/08/2020
ms.openlocfilehash: beb9a42e4b5007f03480cd74f57bbfbbfc3f48b1
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556252"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="5f133-103">Windows Forms 'deki değişiklikler kesiliyor</span><span class="sxs-lookup"><span data-stu-id="5f133-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="5f133-104">Sürüm 3,0 ' de .NET Core 'a Windows Forms desteği eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="5f133-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="5f133-105">Bu makalede, sunulan .NET Core sürümü tarafından Windows Forms yönelik son değişiklikler listelenir.</span><span class="sxs-lookup"><span data-stu-id="5f133-105">This article lists breaking changes for Windows Forms by the .NET Core version in which they were introduced.</span></span> <span data-ttu-id="5f133-106">Bir Windows Forms uygulamasını .NET Framework veya .NET Core 'un önceki bir sürümünden (3,0 veya üzeri) yükseltiyorsanız, bu makale sizin için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5f133-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article is applicable to you.</span></span>

<span data-ttu-id="5f133-107">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="5f133-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="5f133-108">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="5f133-108">Breaking change</span></span> | <span data-ttu-id="5f133-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="5f133-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="5f133-110">Durum çubuğu denetimleri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="5f133-110">Removed status bar controls</span></span>](#removed-status-bar-controls) | <span data-ttu-id="5f133-111">5.0</span><span class="sxs-lookup"><span data-stu-id="5f133-111">5.0</span></span> |
| [<span data-ttu-id="5f133-112">WinForms yöntemleri artık ArgumentException oluşturur</span><span class="sxs-lookup"><span data-stu-id="5f133-112">WinForms methods now throw ArgumentException</span></span>](#winforms-methods-now-throw-argumentexception) | <span data-ttu-id="5f133-113">5.0</span><span class="sxs-lookup"><span data-stu-id="5f133-113">5.0</span></span> |
| [<span data-ttu-id="5f133-114">WinForms yöntemleri şimdi ArgumentNullException oluşturur</span><span class="sxs-lookup"><span data-stu-id="5f133-114">WinForms methods now throw ArgumentNullException</span></span>](#winforms-methods-now-throw-argumentnullexception) | <span data-ttu-id="5f133-115">5.0</span><span class="sxs-lookup"><span data-stu-id="5f133-115">5.0</span></span> |
| [<span data-ttu-id="5f133-116">WinForms özellikleri artık ArgumentOutOfRangeException oluşturur</span><span class="sxs-lookup"><span data-stu-id="5f133-116">WinForms properties now throw ArgumentOutOfRangeException</span></span>](#winforms-properties-now-throw-argumentoutofrangeexception) | <span data-ttu-id="5f133-117">5.0</span><span class="sxs-lookup"><span data-stu-id="5f133-117">5.0</span></span> |
| [<span data-ttu-id="5f133-118">Kaldırılan denetimler</span><span class="sxs-lookup"><span data-stu-id="5f133-118">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="5f133-119">3,1</span><span class="sxs-lookup"><span data-stu-id="5f133-119">3.1</span></span> |
| [<span data-ttu-id="5f133-120">Araç ipucu gösterildiğinde CellFormatting olayı oluşturulmaz</span><span class="sxs-lookup"><span data-stu-id="5f133-120">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="5f133-121">3,1</span><span class="sxs-lookup"><span data-stu-id="5f133-121">3.1</span></span> |
| [<span data-ttu-id="5f133-122">Control. DefaultFont Segoe UI 9 nk olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="5f133-122">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="5f133-123">3,0</span><span class="sxs-lookup"><span data-stu-id="5f133-123">3.0</span></span> |
| [<span data-ttu-id="5f133-124">FolderBrowserDialog 'u modernleştirme</span><span class="sxs-lookup"><span data-stu-id="5f133-124">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="5f133-125">3,0</span><span class="sxs-lookup"><span data-stu-id="5f133-125">3.0</span></span> |
| [<span data-ttu-id="5f133-126">SerializableAttribute bazı Windows Forms türlerinden kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="5f133-126">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="5f133-127">3,0</span><span class="sxs-lookup"><span data-stu-id="5f133-127">3.0</span></span> |
| [<span data-ttu-id="5f133-128">AllowUpdateChildControlIndexForTabControls uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="5f133-128">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="5f133-129">3,0</span><span class="sxs-lookup"><span data-stu-id="5f133-129">3.0</span></span> |
| [<span data-ttu-id="5f133-130">DomainUpDown. UseLegacyScrolling uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="5f133-130">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="5f133-131">3,0</span><span class="sxs-lookup"><span data-stu-id="5f133-131">3.0</span></span> |
| [<span data-ttu-id="5f133-132">DoNotLoadLatestRichEditControl uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="5f133-132">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="5f133-133">3,0</span><span class="sxs-lookup"><span data-stu-id="5f133-133">3.0</span></span> |
| [<span data-ttu-id="5f133-134">Donotsupportselectallshortcutınmultilinetextbox uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="5f133-134">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="5f133-135">3,0</span><span class="sxs-lookup"><span data-stu-id="5f133-135">3.0</span></span> |
| [<span data-ttu-id="5f133-136">DontSupportReentrantFilterMessage uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="5f133-136">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="5f133-137">3,0</span><span class="sxs-lookup"><span data-stu-id="5f133-137">3.0</span></span> |
| [<span data-ttu-id="5f133-138">EnableVisualStyleValidation uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="5f133-138">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="5f133-139">3,0</span><span class="sxs-lookup"><span data-stu-id="5f133-139">3.0</span></span> |
| [<span data-ttu-id="5f133-140">UseLegacyContextMenuStripSourceControlValue uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="5f133-140">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="5f133-141">3,0</span><span class="sxs-lookup"><span data-stu-id="5f133-141">3.0</span></span> |
| [<span data-ttu-id="5f133-142">UseLegacyImages uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="5f133-142">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="5f133-143">3,0</span><span class="sxs-lookup"><span data-stu-id="5f133-143">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="5f133-144">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="5f133-144">.NET 5.0</span></span>

[!INCLUDE [winforms-deprecated-controls](../../../includes/core-changes/windowsforms/5.0/winforms-deprecated-controls.md)]

***

[!INCLUDE [invalid-args-cause-argumentexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentexception.md)]

***

[!INCLUDE [null-args-cause-argumentnullexception](../../../includes/core-changes/windowsforms/5.0/null-args-cause-argumentnullexception.md)]

***

[!INCLUDE [invalid-args-cause-argumentoutofrangeexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentoutofrangeexception.md)]

***

## <a name="net-core-31"></a><span data-ttu-id="5f133-145">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="5f133-145">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="5f133-146">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="5f133-146">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5f133-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f133-147">See also</span></span>

- [<span data-ttu-id="5f133-148">.NET Core 'a Windows Forms uygulaması bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="5f133-148">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)
