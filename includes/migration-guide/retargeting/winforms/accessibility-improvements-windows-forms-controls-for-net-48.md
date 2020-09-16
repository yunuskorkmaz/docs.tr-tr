---
ms.openlocfilehash: 882c4c0455b7df538079ffe1b7d1d7ca8af1904a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606629"
---
### <a name="accessibility-improvements-in-windows-forms-controls-for-net-48"></a><span data-ttu-id="d4d00-101">.NET 4,8 için Windows Forms Denetimlerinde erişilebilirlik geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="d4d00-101">Accessibility improvements in Windows Forms controls for .NET 4.8</span></span>

#### <a name="details"></a><span data-ttu-id="d4d00-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="d4d00-102">Details</span></span>

<span data-ttu-id="d4d00-103">Windows Forms Framework, Windows Forms müşterileri daha iyi destekleyecek şekilde erişilebilirlik teknolojileriyle nasıl çalıştığını iyileştirmeye devam etmektedir.</span><span class="sxs-lookup"><span data-stu-id="d4d00-103">The Windows Forms Framework is continuing to improve how it works with accessibility technologies to better support Windows Forms customers.</span></span> <span data-ttu-id="d4d00-104">Bunlar aşağıdaki değişiklikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="d4d00-104">These include the following changes:</span></span>

- <span data-ttu-id="d4d00-105">Yüksek Karşıtlık modunda görüntülemeyi artırmak için değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="d4d00-105">Changes to improve display during High Contrast mode.</span></span>
- <span data-ttu-id="d4d00-106">Ekran okuyucusu ile etkileşim olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="d4d00-106">Changes to interaction with Narrator.</span></span>
- <span data-ttu-id="d4d00-107">Erişilebilir hiyerarşideki değişiklikler (UI Otomasyon ağacı aracılığıyla gezinmeyi geliştirir).</span><span class="sxs-lookup"><span data-stu-id="d4d00-107">Changes in the Accessible hierarchy (improving navigation through the UI Automation tree).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d4d00-108">Öneri</span><span class="sxs-lookup"><span data-stu-id="d4d00-108">Suggestion</span></span>

<span data-ttu-id="d4d00-109">**Bu değişiklikleri kabul etme veya devre dışı bırakma** Uygulamanın bu değişikliklerden faydalanabilir olması için .NET Framework 4,8 üzerinde çalışması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d4d00-109">**How to opt in or out of these changes** In order for the application to benefit from these changes, it must run on the .NET Framework 4.8.</span></span> <span data-ttu-id="d4d00-110">Uygulama, aşağıdaki yollarla bu değişiklikleri kabul edebilir:</span><span class="sxs-lookup"><span data-stu-id="d4d00-110">The application can opt in into these changes in either of the following ways:</span></span>

- <span data-ttu-id="d4d00-111">.NET Framework 4,8 ' i hedeflemek için yeniden derlenir.</span><span class="sxs-lookup"><span data-stu-id="d4d00-111">It is recompiled to target the .NET Framework 4.8.</span></span> <span data-ttu-id="d4d00-112">Bu erişilebilirlik değişiklikleri, .NET Framework 4,8 ' i hedefleyen Windows Forms uygulamalarda varsayılan olarak etkinleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d4d00-112">These accessibility changes are enabled by default on Windows Forms applications that target the .NET Framework 4.8.</span></span>
- <span data-ttu-id="d4d00-113">[AppContext switch](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `<runtime>` Aşağıdaki örnekte gösterildiği gibi, uygulama yapılandırma dosyasının bölümüne aşağıdaki AppContext anahtarını ekleyerek ve ' ı ' a ayarlayarak, .NET Framework 4.7.2 veya önceki bir sürümü, eski erişilebilirlik davranışlarından daha fazla bilgi sağlar `false` .</span><span class="sxs-lookup"><span data-stu-id="d4d00-113">It targets the .NET Framework 4.7.2 or earlier version and opts out of the legacy accessibility behaviors by adding the following [AppContext switch](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the `<runtime>` section of the app config file and setting it to `false`, as the following example shows.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
  </startup>
  <runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
  </runtime>
</configuration>
```

<span data-ttu-id="d4d00-114">.NET Framework 4,8 ' de eklenen erişilebilirlik özelliklerini kabul etmek için ayrıca .NET Framework 4.7.1 ve 4.7.2 erişilebilirlik özelliklerini de kabul etmeniz gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d4d00-114">Note that to opt in to the accessibility features added in .NET Framework 4.8, you must also opt in to accessibility features of .NET Framework 4.7.1 and 4.7.2 as well.</span></span> <span data-ttu-id="d4d00-115">.NET Framework 4,8 ' i hedefleyen ve eski erişilebilirlik davranışını korumak isteyen uygulamalar, bu AppContext anahtarını açıkça ayarlayarak eski erişilebilirlik özelliklerinin kullanımını kabul edebilir `true` . Klavye araç Ipucu çağırma desteğini etkinleştirmek için `Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false` satırın AppContextSwitchOverrides değerine eklenmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="d4d00-115">Applications that target the .NET Framework 4.8 and want to preserve the legacy accessibility behavior can opt in to the use of legacy accessibility features by explicitly setting this AppContext switch to `true`.Enabling the keyboard ToolTip invocation support requires adding the `Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false` line to the AppContextSwitchOverrides value:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false" />
```

<span data-ttu-id="d4d00-116">Bu özelliğin etkinleştirilmesinde, .NET Framework 4.7.1-4,8 ' nin belirtilen erişilebilirlik özelliklerine yönelik olarak etkinleştirilmesi gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d4d00-116">Note that enabling this feature requires opting in to the aforementioned accessibility features of .NET Framework 4.7.1 - 4.8.</span></span> <span data-ttu-id="d4d00-117">Ayrıca, erişilebilirlik özelliklerinden herhangi biri kabul edilmez ancak araç ipucu görüntüleme özelliği kabul edildiğinde, <xref:System.NotSupportedException> Bu özelliklere ilk erişimde bir çalışma zamanı atılır.</span><span class="sxs-lookup"><span data-stu-id="d4d00-117">Also, if any of the accessibility features are not opted in but the tooltip display feature is opted in, a runtime <xref:System.NotSupportedException> will be thrown on the first access to these features.</span></span> <span data-ttu-id="d4d00-118">Özel durum iletisi, klavye araç Ipuçlarının etkinleştirilecek düzey 3 ' ün erişilebilirlik geliştirmeleri gerektirdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d4d00-118">The exception message indicates that keyboard ToolTips require accessibility improvements of level 3 to be enabled.</span></span>

<span data-ttu-id="d4d00-119">**Yüksek Karşıtlık Temaları 'nda işletim sistemi tanımlı renklerin kullanımı**</span><span class="sxs-lookup"><span data-stu-id="d4d00-119">**Use of OS-defined colors in High Contrast themes**</span></span>

- <span data-ttu-id="d4d00-120">Gelişmiş yüksek karşıtlıklı Temalar.</span><span class="sxs-lookup"><span data-stu-id="d4d00-120">Improved high-contrast themes.</span></span>

<span data-ttu-id="d4d00-121">**İyileştirilmiş ekran okuyucusu desteği**</span><span class="sxs-lookup"><span data-stu-id="d4d00-121">**Improved Narrator support**</span></span>

- <span data-ttu-id="d4d00-122">Ekran okuyucusu artık <xref:System.Windows.Forms.DataGridViewColumn> erişilebilir bir adı duyurusu yaparken öğesinin sıralama yönünü duyurur <xref:System.Windows.Forms.DataGridViewCell> .</span><span class="sxs-lookup"><span data-stu-id="d4d00-122">Narrator now announces the sort direction of the <xref:System.Windows.Forms.DataGridViewColumn> when announcing an accessible name of a <xref:System.Windows.Forms.DataGridViewCell>.</span></span>

<span data-ttu-id="d4d00-123">**Geliştirilmiş CheckedListBox erişilebilirlik desteği**</span><span class="sxs-lookup"><span data-stu-id="d4d00-123">**Improved CheckedListBox Accessibility support**</span></span>

- <span data-ttu-id="d4d00-124">Denetim için iyileştirilmiş ekran okuyucusu desteği <xref:System.Windows.Forms.CheckedListBox> .</span><span class="sxs-lookup"><span data-stu-id="d4d00-124">Improved Narrator support for the <xref:System.Windows.Forms.CheckedListBox> control.</span></span> <span data-ttu-id="d4d00-125"><xref:System.Windows.Forms.CheckedListBox>Klavye kullanılarak denetime gezinilirken, ekran okuyucusu öğeyi odaklar <xref:System.Windows.Forms.CheckedListBox> ve duyurur.</span><span class="sxs-lookup"><span data-stu-id="d4d00-125">When navigating to the <xref:System.Windows.Forms.CheckedListBox> control using the keyboard, Narrator focuses the <xref:System.Windows.Forms.CheckedListBox> item and announces it.</span></span>
- <span data-ttu-id="d4d00-126">Boş bir CheckedListBox denetiminin artık, denetim odaklanıldığında bir sanal ilk öğe için çizilmiş bir odak dikdörtgeni vardır.</span><span class="sxs-lookup"><span data-stu-id="d4d00-126">An empty CheckedListBox control now has a focus rectangle drawn for a virtual first item when the control becomes focused.</span></span>

<span data-ttu-id="d4d00-127">**Geliştirilmiş ComboBox erişilebilirlik desteği**</span><span class="sxs-lookup"><span data-stu-id="d4d00-127">**Improved ComboBox Accessibility support**</span></span>

- <span data-ttu-id="d4d00-128"><xref:System.Windows.Forms.ComboBox>UI Otomasyonu bildirimleri ve DIĞER UI Otomasyon özelliklerini kullanma olanağı sunan denetim IÇIN UI Otomasyonu desteği etkinleştirildi.</span><span class="sxs-lookup"><span data-stu-id="d4d00-128">Enabled UI Automation support for the <xref:System.Windows.Forms.ComboBox> control, with the ability to use UI Automation notifications and other UI Automation features.</span></span>
<span data-ttu-id="d4d00-129">**Geliştirilmiş DataGridView erişilebilirlik desteği**</span><span class="sxs-lookup"><span data-stu-id="d4d00-129">**Improved DataGridView Accessibility support**</span></span>

- <span data-ttu-id="d4d00-130"><xref:System.Windows.Forms.DataGridView>UI Otomasyonu bildirimlerini ve DIĞER UI Otomasyon özelliklerini kullanma yeteneği olan denetim IÇIN UI Otomasyonu desteği etkinleştirildi.</span><span class="sxs-lookup"><span data-stu-id="d4d00-130">Enabled UI Automation support for <xref:System.Windows.Forms.DataGridView> control with ability to use UI Automation notifications and other UI Automation features.</span></span>
- <span data-ttu-id="d4d00-131">Ya da öğesine karşılık gelen UI Otomasyon öğesi <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl> , <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl> buna karşılık gelen bir Düzenle hücresinin alt öğesidir.</span><span class="sxs-lookup"><span data-stu-id="d4d00-131">The UI Automation element which corresponds to the <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl> or <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl> is now a child of corresponding editing cell.</span></span>

<span data-ttu-id="d4d00-132">**İyileştirilmiş LinkLabel erişilebilirlik desteği**</span><span class="sxs-lookup"><span data-stu-id="d4d00-132">**Improved LinkLabel Accessibility support**</span></span>

- <span data-ttu-id="d4d00-133">Gelişmiş <xref:System.Windows.Forms.LinkLabel> Denetim erişilebilirliği: ilgili <xref:System.Windows.Forms.LinkLabel> denetim devre dışı bırakılmışsa, ekran okuyucusu bağlantının devre dışı durumunu duyurur.</span><span class="sxs-lookup"><span data-stu-id="d4d00-133">Improved <xref:System.Windows.Forms.LinkLabel> control accessibility: Narrator announces the disabled state for the link if the corresponding <xref:System.Windows.Forms.LinkLabel> control is disabled.</span></span>

<span data-ttu-id="d4d00-134">**Geliştirilmiş ProgressBar erişilebilirlik desteği**</span><span class="sxs-lookup"><span data-stu-id="d4d00-134">**Improved ProgressBar Accessibility support**</span></span>

- <span data-ttu-id="d4d00-135"><xref:System.Windows.Forms.ProgressBar>UI Otomasyonu bildirimleri ve DIĞER UI Otomasyon özelliklerini kullanma özelliği ile denetim IÇIN UI Otomasyonu desteği etkinleştirildi.</span><span class="sxs-lookup"><span data-stu-id="d4d00-135">Enabled UI Automation support for the <xref:System.Windows.Forms.ProgressBar> control with the ability to use UI Automation notifications and other UI Automation features.</span></span> <span data-ttu-id="d4d00-136">Geliştiriciler artık, ekran okuyucusu 'Nun ilerlemeyi göstermek için duyurabileceği Kullanıcı Arabirimi Otomasyonu bildirimlerini kullanabiliyor.</span><span class="sxs-lookup"><span data-stu-id="d4d00-136">Developers are now able to use UI Automation notifications which Narrator can announce to indicate progress.</span></span>
<span data-ttu-id="d4d00-137">UI Otomasyonu olaylarına genel bakış için Kullanıcı Arabirimi Otomasyonu bildirim olayları dahil bir genel bakış için bkz. [UI Otomasyonu olaylarına genel](/windows/desktop/WinAuto/uiauto-eventsoverview)bakış.</span><span class="sxs-lookup"><span data-stu-id="d4d00-137">For an overview of UI automation events overview, including UI automation notification events, see the [UI Automation Events Overview](/windows/desktop/WinAuto/uiauto-eventsoverview).</span></span>

<span data-ttu-id="d4d00-138">**Geliştirilmiş PropertyGrid erişilebilirlik desteği**</span><span class="sxs-lookup"><span data-stu-id="d4d00-138">**Improved PropertyGrid Accessibility support**</span></span>

- <span data-ttu-id="d4d00-139"><xref:System.Windows.Forms.PropertyGrid>UI Otomasyonu bildirimleri ve DIĞER UI Otomasyon özelliklerini kullanma olanağı sunan denetim IÇIN UI Otomasyonu desteği etkinleştirildi.</span><span class="sxs-lookup"><span data-stu-id="d4d00-139">Enabled UI Automation support for the <xref:System.Windows.Forms.PropertyGrid> control, with the ability to use UI Automation notifications and other UI Automation features.</span></span>
- <span data-ttu-id="d4d00-140">Şu anda düzenlenmekte olan özelliğe karşılık gelen UI Otomasyon öğesi artık ilgili özellik öğesi UI Otomasyon öğesinin bir alt öğesidir.</span><span class="sxs-lookup"><span data-stu-id="d4d00-140">The UI Automation element which corresponds to the currently edited property is now a child of the corresponding property item UI Automation element.</span></span>
- <span data-ttu-id="d4d00-141">Ana <xref:System.Windows.Forms.PropertyGrid> Denetim Kategori görünümü olarak AYARLANDıYSA UI Otomasyonu özellik öğesi öğesi artık karşılık gelen category öğesinin bir alt öğesidir.</span><span class="sxs-lookup"><span data-stu-id="d4d00-141">The UI Automation property item element is now a child of the corresponding category element if the parent <xref:System.Windows.Forms.PropertyGrid> control is set to category view.</span></span>

<span data-ttu-id="d4d00-142">**Geliştirilmiş ToolStrip desteği**</span><span class="sxs-lookup"><span data-stu-id="d4d00-142">**Improved ToolStrip support**</span></span>

- <span data-ttu-id="d4d00-143"><xref:System.Windows.Forms.ToolStrip>UI Otomasyonu bildirimleri ve DIĞER UI Otomasyon özelliklerini kullanma olanağı sunan denetim IÇIN UI Otomasyonu desteği etkinleştirildi.</span><span class="sxs-lookup"><span data-stu-id="d4d00-143">Enabled UI Automation support for the <xref:System.Windows.Forms.ToolStrip> control, with the ability to use UI Automation notifications and other UI Automation features.</span></span>
- <span data-ttu-id="d4d00-144">Öğeler aracılığıyla geliştirilmiş gezinme <xref:System.Windows.Forms.ToolStrip> .</span><span class="sxs-lookup"><span data-stu-id="d4d00-144">Improved navigation through <xref:System.Windows.Forms.ToolStrip> items.</span></span>
- <span data-ttu-id="d4d00-145">Öğe modunda, ekran okuyucusu odağı görünmez ve gizli öğelere gitmez.</span><span class="sxs-lookup"><span data-stu-id="d4d00-145">In items mode, Narrator focus does not disappear and does not go to hidden items.</span></span>

<span data-ttu-id="d4d00-146">**Geliştirilmiş görsel ipuçları**</span><span class="sxs-lookup"><span data-stu-id="d4d00-146">**Improved Visual cues**</span></span>

- <span data-ttu-id="d4d00-147">Boş bir <xref:System.Windows.Forms.CheckedListBox> Denetim artık odak aldığında odak göstergesi görüntülüyor.</span><span class="sxs-lookup"><span data-stu-id="d4d00-147">An empty <xref:System.Windows.Forms.CheckedListBox> control now displays a focus indicator when it receives focus.</span></span>
<span data-ttu-id="d4d00-148">Not: UI Otomasyon desteği çalışma zamanında denetimler için etkinleştirilmiştir ancak tasarım zamanında kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="d4d00-148">Note: UI automation support is enabled for controls in runtime but is not used in design time.</span></span> <span data-ttu-id="d4d00-149">UI Otomasyonu 'na genel bakış için bkz. [UI Otomasyonu genel bakış](../../../../docs/framework/ui-automation/ui-automation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d4d00-149">For an overview of UI automation, see the [UI Automation Overview](../../../../docs/framework/ui-automation/ui-automation-overview.md).</span></span>

<span data-ttu-id="d4d00-150">**Denetimlerin klavye ile araç Ipuçlarını çağırma**</span><span class="sxs-lookup"><span data-stu-id="d4d00-150">**Invoking controls' ToolTips with a keyboard**</span></span>

- <span data-ttu-id="d4d00-151">Denetim araç ipucu artık, klavye ile denetim altına odaklanarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="d4d00-151">Control tooltip can now be invoked by focusing the control with keyboard.</span></span> <span data-ttu-id="d4d00-152">Bu özelliğin uygulama için açıkça etkinleştirilmesi gerekir ( \*\* &quot; Bu değişikliklerin &quot; nasıl kabul edilebilir veya devre dışı\*\*kılındığı bölümüne bakın)</span><span class="sxs-lookup"><span data-stu-id="d4d00-152">This feature needs to be enabled explicitly for the application (see section **&quot;How to opt in or out of these changes&quot;**)</span></span>

| <span data-ttu-id="d4d00-153">Name</span><span class="sxs-lookup"><span data-stu-id="d4d00-153">Name</span></span>    | <span data-ttu-id="d4d00-154">Değer</span><span class="sxs-lookup"><span data-stu-id="d4d00-154">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d4d00-155">Kapsam</span><span class="sxs-lookup"><span data-stu-id="d4d00-155">Scope</span></span>   | <span data-ttu-id="d4d00-156">Ana</span><span class="sxs-lookup"><span data-stu-id="d4d00-156">Major</span></span>       |
| <span data-ttu-id="d4d00-157">Sürüm</span><span class="sxs-lookup"><span data-stu-id="d4d00-157">Version</span></span> | <span data-ttu-id="d4d00-158">4,8</span><span class="sxs-lookup"><span data-stu-id="d4d00-158">4.8</span></span>         |
| <span data-ttu-id="d4d00-159">Tür</span><span class="sxs-lookup"><span data-stu-id="d4d00-159">Type</span></span>    | <span data-ttu-id="d4d00-160">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="d4d00-160">Retargeting</span></span> |
