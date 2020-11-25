---
title: Windows Forms son değişiklikler
description: .NET Core 3,0 ve 3,1 için Windows Forms 'deki son değişiklikleri listeler.
ms.date: 09/08/2020
ms.openlocfilehash: b944f7eea89b61f41feb8eef99e949c2d6017960
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726437"
---
# <a name="breaking-changes-in-windows-forms-for-net-core-30-and-31"></a><span data-ttu-id="fea45-103">.NET Core 3,0 ve 3,1 için Windows Forms 'deki değişiklikler kesiliyor</span><span class="sxs-lookup"><span data-stu-id="fea45-103">Breaking changes in Windows Forms for .NET Core 3.0 and 3.1</span></span>

<span data-ttu-id="fea45-104">Sürüm 3,0 ' de .NET Core 'a Windows Forms desteği eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="fea45-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="fea45-105">Bu makalede, sunulan .NET sürümüne göre Windows Forms yönelik son değişiklikler listelenir.</span><span class="sxs-lookup"><span data-stu-id="fea45-105">This article lists breaking changes for Windows Forms by the .NET version in which they were introduced.</span></span> <span data-ttu-id="fea45-106">Bir Windows Forms uygulamasını .NET Framework veya .NET Core 'un önceki bir sürümünden (3,0 veya üzeri) yükseltiyorsanız, bu makale sizin için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="fea45-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article applies to you.</span></span>

<span data-ttu-id="fea45-107">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="fea45-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="fea45-108">Son değişiklik</span><span class="sxs-lookup"><span data-stu-id="fea45-108">Breaking change</span></span> | <span data-ttu-id="fea45-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="fea45-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="fea45-110">Kaldırılan denetimler</span><span class="sxs-lookup"><span data-stu-id="fea45-110">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="fea45-111">3,1</span><span class="sxs-lookup"><span data-stu-id="fea45-111">3.1</span></span> |
| [<span data-ttu-id="fea45-112">Araç ipucu gösterildiğinde CellFormatting olayı oluşturulmaz</span><span class="sxs-lookup"><span data-stu-id="fea45-112">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="fea45-113">3,1</span><span class="sxs-lookup"><span data-stu-id="fea45-113">3.1</span></span> |
| [<span data-ttu-id="fea45-114">Control. DefaultFont Segoe UI 9 nk olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="fea45-114">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="fea45-115">3,0</span><span class="sxs-lookup"><span data-stu-id="fea45-115">3.0</span></span> |
| [<span data-ttu-id="fea45-116">FolderBrowserDialog 'u modernleştirme</span><span class="sxs-lookup"><span data-stu-id="fea45-116">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="fea45-117">3,0</span><span class="sxs-lookup"><span data-stu-id="fea45-117">3.0</span></span> |
| [<span data-ttu-id="fea45-118">SerializableAttribute bazı Windows Forms türlerinden kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="fea45-118">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="fea45-119">3,0</span><span class="sxs-lookup"><span data-stu-id="fea45-119">3.0</span></span> |
| [<span data-ttu-id="fea45-120">AllowUpdateChildControlIndexForTabControls uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="fea45-120">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="fea45-121">3,0</span><span class="sxs-lookup"><span data-stu-id="fea45-121">3.0</span></span> |
| [<span data-ttu-id="fea45-122">DomainUpDown. UseLegacyScrolling uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="fea45-122">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="fea45-123">3,0</span><span class="sxs-lookup"><span data-stu-id="fea45-123">3.0</span></span> |
| [<span data-ttu-id="fea45-124">DoNotLoadLatestRichEditControl uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="fea45-124">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="fea45-125">3,0</span><span class="sxs-lookup"><span data-stu-id="fea45-125">3.0</span></span> |
| [<span data-ttu-id="fea45-126">Donotsupportselectallshortcutınmultilinetextbox uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="fea45-126">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="fea45-127">3,0</span><span class="sxs-lookup"><span data-stu-id="fea45-127">3.0</span></span> |
| [<span data-ttu-id="fea45-128">DontSupportReentrantFilterMessage uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="fea45-128">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="fea45-129">3,0</span><span class="sxs-lookup"><span data-stu-id="fea45-129">3.0</span></span> |
| [<span data-ttu-id="fea45-130">EnableVisualStyleValidation uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="fea45-130">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="fea45-131">3,0</span><span class="sxs-lookup"><span data-stu-id="fea45-131">3.0</span></span> |
| [<span data-ttu-id="fea45-132">UseLegacyContextMenuStripSourceControlValue uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="fea45-132">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="fea45-133">3,0</span><span class="sxs-lookup"><span data-stu-id="fea45-133">3.0</span></span> |
| [<span data-ttu-id="fea45-134">UseLegacyImages uyumluluk anahtarı desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="fea45-134">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="fea45-135">3,0</span><span class="sxs-lookup"><span data-stu-id="fea45-135">3.0</span></span> |

## <a name="net-core-31"></a><span data-ttu-id="fea45-136">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="fea45-136">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

<span data-ttu-id="fea45-137">\*\*_</span><span class="sxs-lookup"><span data-stu-id="fea45-137">\*\*_</span></span>

## <a name="net-core-30"></a><span data-ttu-id="fea45-138">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="fea45-138">.NET Core 3.0</span></span>

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

<span data-ttu-id="fea45-139">_\*\*</span><span class="sxs-lookup"><span data-stu-id="fea45-139">_\*\*</span></span>

## <a name="see-also"></a><span data-ttu-id="fea45-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fea45-140">See also</span></span>

- [<span data-ttu-id="fea45-141">.NET Core 'a Windows Forms uygulaması bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="fea45-141">Port a Windows Forms app to .NET Core</span></span>](/dotnet/desktop/winforms/migration/?view=netdesktop-5.0&preserve-view=true)
