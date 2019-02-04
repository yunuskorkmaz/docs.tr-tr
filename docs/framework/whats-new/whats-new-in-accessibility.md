---
title: Erişilebilirlik .NET Framework'teki yenilikler
ms.custom: updateeachrelease
ms.date: 04/10/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 092b1cfc9350ea398eb18199f19a8eee7ea9f218
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675445"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="b5c26-102">Erişilebilirlik .NET Framework'teki yenilikler</span><span class="sxs-lookup"><span data-stu-id="b5c26-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="b5c26-103">.NET Framework uygulamaları daha erişilebilir, kullanıcılarınız için duruma getirmeyi amaçlar.</span><span class="sxs-lookup"><span data-stu-id="b5c26-103">The .NET Framework aims at making applications more accessible for your users.</span></span> <span data-ttu-id="b5c26-104">Yardımcı teknoloji kullanıcılar için uygun bir deneyim sağlamak için uygulamanın erişilebilirlik özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5c26-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="b5c26-105">.NET Framework, .NET Framework 4.7.1 ile başlayarak, çok sayıda erişilebilir uygulamalar oluşturmaları için geliştiricileri erişilebilirlik geliştirmeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b5c26-105">Starting with the .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span> 

## <a name="accessibility-switches"></a><span data-ttu-id="b5c26-106">Erişilebilirlik anahtarları</span><span class="sxs-lookup"><span data-stu-id="b5c26-106">Accessibility switches</span></span>

<span data-ttu-id="b5c26-107">Uygulamanızı .NET Framework 4.7 veya önceki bir sürümünü hedefler, ancak .NET Framework 4.7.1 çalıştıran erişilebilirlik özelliklerini geri çevirmek için yapılandırabilirsiniz veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="b5c26-107">You can configure your app to opt into accessibility features if it targets the .NET Framework 4.7 or an earlier version but is running on the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="b5c26-108">Uygulamanızı .NET Framework 4.7.1'i hedefleyen, eski özellikleri (ve değil yararlanın erişilebilirlik özellikleri) kullanacak şekilde de yapılandırabilirsiniz veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="b5c26-108">You can also configure your app to use legacy features (and not take advantage of accessibility features) if it targets the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="b5c26-109">Erişilebilirlik özellikleri içeren .NET Framework'ün her sürümü eklediğiniz bir sürüme özgü erişilebilirlik anahtara sahip [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğesinde [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) bölümü Uygulamanın yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="b5c26-109">Each version of the .NET Framework that includes accessibility features has a version-specific accessibility switch, which you add to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> <span data-ttu-id="b5c26-110">Desteklenen anahtarlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b5c26-110">The following are the supported switches:</span></span>

|<span data-ttu-id="b5c26-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="b5c26-111">Version</span></span>|<span data-ttu-id="b5c26-112">Anahtar</span><span class="sxs-lookup"><span data-stu-id="b5c26-112">Switch</span></span>|
|---|---|
|<span data-ttu-id="b5c26-113">.NET framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="b5c26-113">.NET Framework 4.7.1</span></span>|<span data-ttu-id="b5c26-114">"Switch.UseLegacyAccessibilityFeatures"</span><span class="sxs-lookup"><span data-stu-id="b5c26-114">"Switch.UseLegacyAccessibilityFeatures"</span></span>|
|<span data-ttu-id="b5c26-115">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="b5c26-115">.NET Framework 4.7.2</span></span>|<span data-ttu-id="b5c26-116">"Switch.UseLegacyAccessibilityFeatures.2"</span><span class="sxs-lookup"><span data-stu-id="b5c26-116">"Switch.UseLegacyAccessibilityFeatures.2"</span></span>|

### <a name="taking-advantage-of-accessibility-enhancements"></a><span data-ttu-id="b5c26-117">Erişilebilirlik geliştirmeleri yararlanma</span><span class="sxs-lookup"><span data-stu-id="b5c26-117">Taking advantage of accessibility enhancements</span></span>

<span data-ttu-id="b5c26-118">.NET Framework 4.7.1'i hedefleyen uygulamalar için varsayılan olarak etkin ya da daha yeni erişilebilirlik özellikleri.</span><span class="sxs-lookup"><span data-stu-id="b5c26-118">The new accessibility features are enabled by default for applications that target the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="b5c26-119">Ayrıca, .NET Framework'ün önceki sürümünü hedefleyecek ancak .NET Framework 4.7.1 üzerinde çalışmakta olan veya daha sonra seçebilirsiniz uygulamalar eski erişilebilirlik davranışlarını dışarı (ve böylece erişilebilirlik iyileştirmeleri yararlanmak) anahtarlara ekleyerek [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğesinde [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) uygulamanın yapılandırma dosyası ve kendi değerini bölümünü `false`.</span><span class="sxs-lookup"><span data-stu-id="b5c26-119">In addition, applications that target an earlier version of the .NET Framework but are running on the .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby take advantage of accessibility improvements) by adding switches to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `false`.</span></span> <span data-ttu-id="b5c26-120">Erişilebilirlik geliştirmeleri .NET Framework 4.7.1 sunmuştur kabul etmek nasıl aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="b5c26-120">The following shows how to opt in to accessibility enhancements introduced in the .NET Framework 4.7.1:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="b5c26-121">Erişilebilirlik özellikleri sonraki bir sürümü .NET Framework'ün kabul etmek isterseniz, aynı zamanda açıkça özellikleri için .NET Framework'ün önceki sürümlerinden kabul gerekir.</span><span class="sxs-lookup"><span data-stu-id="b5c26-121">If you choose to opt in to accessibility features in a later version of the .NET Framework, you must also explicitly opt in to the features from earlier versions of the .NET Framework.</span></span> <span data-ttu-id="b5c26-122">Hem .NET Framework 4.7.1 ve 4.7.2 erişilebilirlik geliştirmeleri avantajlarından faydalanmak için uygulamanızı yapılandırma aşağıdakileri gerektirir [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğesi:</span><span class="sxs-lookup"><span data-stu-id="b5c26-122">Configuring your app to take advantage of accessibility improvements in both the .NET Framework 4.7.1 and 4.7.2 requires the following [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a><span data-ttu-id="b5c26-123">Eski davranışı geri yükleme</span><span class="sxs-lookup"><span data-stu-id="b5c26-123">Restoring legacy behavior</span></span>

<span data-ttu-id="b5c26-124">.NET Framework 4.7.1 ile başlayan sürümlerini hedefleyen uygulamalar devre dışı bırakabilirsiniz erişilebilirlik özellikleri anahtarlara ekleyerek [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğesinde [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) bölümü Uygulamanın yapılandırma dosyası ve kendi değerini `true`.</span><span class="sxs-lookup"><span data-stu-id="b5c26-124">Applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding switches to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `true`.</span></span> <span data-ttu-id="b5c26-125">Örneğin, aşağıdaki yapılandırma, .NET Framework 4.7.2 sunulan erişilebilirlik özellikleri dışında kabul eder:</span><span class="sxs-lookup"><span data-stu-id="b5c26-125">For example, the following configuration opts out of accessibility features introduced in .NET Framework 4.7.2:</span></span>  

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-472"></a><span data-ttu-id="b5c26-126">Erişilebilirlik 4.7.2 .NET Framework'teki yenilikler</span><span class="sxs-lookup"><span data-stu-id="b5c26-126">What's new in accessibility in the .NET Framework 4.7.2</span></span>

<span data-ttu-id="b5c26-127">.NET Framework 4.7.2 aşağıdaki alanlarda yeni erişilebilirlik özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="b5c26-127">The .NET Framework 4.7.2 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="b5c26-128">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b5c26-128">Windows Forms</span></span>](#winforms472)

- [<span data-ttu-id="b5c26-129">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="b5c26-129">Windows Presentation Foundation (WPF)</span></span>](#wpf472)

<a name="winforms472"></a>
### <a name="windows-forms"></a><span data-ttu-id="b5c26-130">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b5c26-130">Windows Forms</span></span>

<span data-ttu-id="b5c26-131">**Yüksek karşıtlıklı Tema renkleri işletim sistemi tarafından tanımlanan**</span><span class="sxs-lookup"><span data-stu-id="b5c26-131">**OS-defined colors in High Contrast themes**</span></span>

<span data-ttu-id="b5c26-132">.NET Framework 4.7.2 ile başlayarak, Windows Forms yüksek karşıtlıklı tema işletim sistemi tarafından tanımlanan renk kullanır.</span><span class="sxs-lookup"><span data-stu-id="b5c26-132">Starting with .NET Framework 4.7.2, Windows Forms uses colors defined by the operating system in High Contrast themes.</span></span> <span data-ttu-id="b5c26-133">Bu, aşağıdaki denetimlerini etkiler:</span><span class="sxs-lookup"><span data-stu-id="b5c26-133">This affects the following controls:</span></span>

- <span data-ttu-id="b5c26-134">Aşağı açılan okunu <xref:System.Windows.Forms.ToolStripDropDownButton> denetimi.</span><span class="sxs-lookup"><span data-stu-id="b5c26-134">The drop-down arrow of the <xref:System.Windows.Forms.ToolStripDropDownButton> control.</span></span>

- <span data-ttu-id="b5c26-135"><xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> Ve <xref:System.Windows.Forms.CheckBox> ile denetimleri <xref:System.Windows.Forms.ButtonBase.FlatStyle> kümesine <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> veya <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b5c26-135">The <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with <xref:System.Windows.Forms.ButtonBase.FlatStyle> set to <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> or <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b5c26-136">Daha önce seçilen metin ve arkaplan renklerini değil çakışan ve okunması zor.</span><span class="sxs-lookup"><span data-stu-id="b5c26-136">Previously, selected text and background colors were not contrasting and were hard to read.</span></span>

- <span data-ttu-id="b5c26-137">Denetimleri içinde yer alan bir <xref:System.Windows.Forms.GroupBox> olan kendi <xref:System.Windows.Forms.Control.Enabled> özelliğini `false`.</span><span class="sxs-lookup"><span data-stu-id="b5c26-137">Controls contained within a <xref:System.Windows.Forms.GroupBox> that has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>
 
- <span data-ttu-id="b5c26-138"><xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, Ve <xref:System.Windows.Forms.ToolStripDropDownButton> artan parlaklık bir Karşıtlık oranı yüksek karşıtlık modunda olan denetimler.</span><span class="sxs-lookup"><span data-stu-id="b5c26-138">The <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, and <xref:System.Windows.Forms.ToolStripDropDownButton> controls, which have an increased luminosity contrast ratio in High Contrast Mode.</span></span>

- <span data-ttu-id="b5c26-139"><xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> Özelliği <xref:System.Windows.Forms.DataGridViewLinkCell>.</span><span class="sxs-lookup"><span data-stu-id="b5c26-139">The <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> property of the <xref:System.Windows.Forms.DataGridViewLinkCell>.</span></span>

<span data-ttu-id="b5c26-140">**Ekran Okuyucusu geliştirmeleri**</span><span class="sxs-lookup"><span data-stu-id="b5c26-140">**Narrator improvements**</span></span>

<span data-ttu-id="b5c26-141">.NET Framework 4.7.2 ile başlayarak, ekran okuyucusu desteği gibi geliştirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="b5c26-141">Starting with the .NET Framework 4.7.2, Narrator support is enhanced as follows:</span></span>

- <span data-ttu-id="b5c26-142">Değerini duyuruyor <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> Duyurusu metni hareketlendiremezsiniz bir <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="b5c26-142">It announces the value of the <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> property when announcing the text of a <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span> 

- <span data-ttu-id="b5c26-143">Ne zaman gösteren bir <xref:System.Windows.Forms.ToolStripMenuItem> sahip kendi <xref:System.Windows.Forms.Control.Enabled> özelliğini `false`.</span><span class="sxs-lookup"><span data-stu-id="b5c26-143">It indicates when a <xref:System.Windows.Forms.ToolStripMenuItem> has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="b5c26-144">Onay kutusunun durumunu hakkında geri bildirim sağlar, <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> özelliği `true`.</span><span class="sxs-lookup"><span data-stu-id="b5c26-144">It gives feedback on the state of a check box when the <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> property is set to `true`.</span></span>

- <span data-ttu-id="b5c26-145">Okuyucu'nın tarama modu odak sipariş ClickOnce indirme iletişim kutusu penceresine denetimleri visual sırasını tutarlıdır.</span><span class="sxs-lookup"><span data-stu-id="b5c26-145">Narrator's Scan Mode focus order is consistent with the visual order of the controls on the ClickOnce download dialog window.</span></span>

<span data-ttu-id="b5c26-146">**DataGridView geliştirmeleri**</span><span class="sxs-lookup"><span data-stu-id="b5c26-146">**DataGridView improvements**</span></span>

<span data-ttu-id="b5c26-147">4.7.2, .NET Framework ile başlayarak <xref:System.Windows.Forms.DataGridView> denetimi aşağıdaki erişilebilirlik geliştirmeleri kullanıma sunulan:</span><span class="sxs-lookup"><span data-stu-id="b5c26-147">Starting with the .NET Framework 4.7.2, the <xref:System.Windows.Forms.DataGridView> control has introduced the following accessibility improvements:</span></span>

- <span data-ttu-id="b5c26-148">Klavyeyi kullanarak satır sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="b5c26-148">Rows can be sorted using the keyboard.</span></span> <span data-ttu-id="b5c26-149">Bir kullanıcı, geçerli bir sütuna göre sıralamak için F3 tuşuna kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5c26-149">A user can use the F3 key in order to sort by the current column.</span></span>

- <span data-ttu-id="b5c26-150">Zaman <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> ayarlanır <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, sütun üst bilgisinin geçerli sütunun hücre geçerli satırda aracılığıyla kullanıcı sekmeler olarak belirtmek için rengi değişir.</span><span class="sxs-lookup"><span data-stu-id="b5c26-150">When the <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> is set to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, the column header changes color to indicate the current column as the user tabs through the cells in the current row.</span></span>

- <span data-ttu-id="b5c26-151"><xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> Özelliği bir <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> doğru üst denetimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="b5c26-151">The <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> property of a  <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> returns the correct parent control.</span></span>

<span data-ttu-id="b5c26-152">**Geliştirilmiş görsel ipuçları**</span><span class="sxs-lookup"><span data-stu-id="b5c26-152">**Improved visual cues**</span></span>

- <span data-ttu-id="b5c26-153"><xref:System.Windows.Forms.RadioButton> Ve <xref:System.Windows.Forms.CheckBox> boş denetimleriyle <xref:System.Windows.Forms.ButtonBase.Text> odağı aldıklarında bir odak göstergesi görüntü özelliği.</span><span class="sxs-lookup"><span data-stu-id="b5c26-153">The <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with an empty <xref:System.Windows.Forms.ButtonBase.Text> property  display a focus indicator when they receive the focus.</span></span>

<span data-ttu-id="b5c26-154">**Gelişmiş özellik Kılavuzu desteği**</span><span class="sxs-lookup"><span data-stu-id="b5c26-154">**Improved Property Grid Support**</span></span>

- <span data-ttu-id="b5c26-155"><xref:System.Windows.Forms.PropertyGrid> Alt öğeleri artık dönüş denetleyen bir `true` için <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> PropertyGrid öğe etkinleştirildiğinde özelliği.</span><span class="sxs-lookup"><span data-stu-id="b5c26-155">The <xref:System.Windows.Forms.PropertyGrid> control child elements now return a `true` for the  <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> property only when a PropertyGrid element is enabled.</span></span>

- <span data-ttu-id="b5c26-156"><xref:System.Windows.Forms.PropertyGrid> Alt öğeleri iade denetleyen bir `false` için <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> özelliğine yalnızca bir PropertyGrid öğesi kullanıcı tarafından değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b5c26-156">The <xref:System.Windows.Forms.PropertyGrid> control child elements return a `false` for the <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> property only when a PropertyGrid element can be changed by the user.</span></span>

<span data-ttu-id="b5c26-157">**Geliştirilmiş klavye gezintisi**</span><span class="sxs-lookup"><span data-stu-id="b5c26-157">**Improved keyboard navigation**</span></span>

- <span data-ttu-id="b5c26-158"><xref:System.Windows.Forms.ToolStripButton> Denetimi içinde bulunan zaman odağı sağlar bir <xref:System.Windows.Forms.ToolStripPanel> olan <xref:System.Windows.Forms.ToolStripPanel.TabStop> özelliği ayarlayın `true`</span><span class="sxs-lookup"><span data-stu-id="b5c26-158">The <xref:System.Windows.Forms.ToolStripButton> control allows focus when contained within a <xref:System.Windows.Forms.ToolStripPanel> that has the <xref:System.Windows.Forms.ToolStripPanel.TabStop> property set to `true`</span></span>

<a name="wpf472"></a>
### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="b5c26-159">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="b5c26-159">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="b5c26-160">**Değişiklikleri için onay kutusunu ve RadioButton denetimleri**</span><span class="sxs-lookup"><span data-stu-id="b5c26-160">**Changes to the CheckBox and RadioButton controls**</span></span>

<span data-ttu-id="b5c26-161">.NET Framework 4.7.1 ve önceki sürümlerinde, WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> ve <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> denetimleri, tutarsız ve klasik ve yüksek karşıtlık temalar, yanlış odak görsel sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b5c26-161">In the .NET Framework 4.7.1 and earlier versions, the WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> and <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> controls have inconsistent and, in Classic and High Contrast themes, incorrect focus visuals.</span></span>  <span data-ttu-id="b5c26-162">Bu sorunlar burada denetimleri herhangi bir içerik kümesi olmayan durumlarda oluşur.</span><span class="sxs-lookup"><span data-stu-id="b5c26-162">These issues occur in cases where the controls do not have any content set.</span></span>  <span data-ttu-id="b5c26-163">Bu tema kafa karıştırıcı ve odak görsel arasında geçiş görmek sabit yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5c26-163">This can make the transition between themes confusing and the focus visual hard to see.</span></span>

<span data-ttu-id="b5c26-164">.NET Framework'teki 4.7.2 Bu görsel temalar arasında daha tutarlı ve klasik ve yüksek karşıtlıklı tema daha kolay görünür.</span><span class="sxs-lookup"><span data-stu-id="b5c26-164">In the .NET Framework 4.7.2, these visuals are now more consistent across themes and more easily visible in Classic and High Contrast themes.</span></span>

<span data-ttu-id="b5c26-165">**Barındırılan bir WPF uygulamasında WinForms denetimleri**</span><span class="sxs-lookup"><span data-stu-id="b5c26-165">**WinForms controls hosted in a WPF application**</span></span>

<span data-ttu-id="b5c26-166">Bu katmandaki ilk veya son denetim WPF ise .NET Framework 4.7.1 ve önceki sürümlerinde WPF uygulamasında barındırılan WinForms denetimi için WinForms katman dışında kullanıcılar sekmesinde uygulanamadı <xref:System.Windows.Forms.Integration.ElementHost> denetimi.</span><span class="sxs-lookup"><span data-stu-id="b5c26-166">For WinForms control hosted in a WPF application in the .NET Framework 4.7.1 and earlier versions, users couldn't tab out of the WinForms layer if the first or last control in that layer is the WPF <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span> <span data-ttu-id="b5c26-167">.NET Framework'teki 4.7.2 kullanıcılar artık dışında WinForms katman sekmesinde olanağına sahip olursunuz.</span><span class="sxs-lookup"><span data-stu-id="b5c26-167">In the .NET Framework 4.7.2, users are now able to tab out of the WinForms layer.</span></span>

<span data-ttu-id="b5c26-168">Ancak, hiçbir zaman WinForms katman kaçış odaklanmak otomatik uygulamaları artık beklendiği gibi çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="b5c26-168">However, automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a><span data-ttu-id="b5c26-169">.NET Framework 4.7.1 erişilebilirlik yenilikleri</span><span class="sxs-lookup"><span data-stu-id="b5c26-169">What's new in accessibility in the .NET Framework 4.7.1</span></span>

<span data-ttu-id="b5c26-170">.NET Framework 4.7.1 aşağıdaki alanlarda yeni erişilebilirlik özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="b5c26-170">The .NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="b5c26-171">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="b5c26-171">Windows Presentation Foundation (WPF)</span></span>](#wpf471)

- [<span data-ttu-id="b5c26-172">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b5c26-172">Windows Forms</span></span>](#winforms471)

- [<span data-ttu-id="b5c26-173">ASP.NET web denetimleri</span><span class="sxs-lookup"><span data-stu-id="b5c26-173">ASP.NET web controls</span></span>](#aspnet471)

- [<span data-ttu-id="b5c26-174">.NET SDK Tools</span><span class="sxs-lookup"><span data-stu-id="b5c26-174">.NET SDK Tools</span></span>](#tools471)

- [<span data-ttu-id="b5c26-175">Windows Workflow Foundation (WF) iş akışı Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="b5c26-175">Windows Workflow Foundation (WF) Workflow Designer</span></span>](#wf471)

<a name="wpf471"></a>
### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="b5c26-176">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="b5c26-176">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="b5c26-177">**Ekran Okuyucusu geliştirmeleri**</span><span class="sxs-lookup"><span data-stu-id="b5c26-177">**Screen reader improvements**</span></span>

<span data-ttu-id="b5c26-178">Erişilebilirlik geliştirmeleri etkinleştirilirse, .NET Framework 4.7.1 ekran okuyucular etkileyen aşağıdaki geliştirmeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="b5c26-178">If accessibility improvements are enabled, the .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="b5c26-179">.NET Framework 4.7 ve önceki sürümlerinde, <xref:System.Windows.Controls.Expander> denetimleri düğme olarak ekran okuyucular tarafından Duyuruldu.</span><span class="sxs-lookup"><span data-stu-id="b5c26-179">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="b5c26-180">.NET Framework 4.7.1 ile başlayarak, bunlar Genişletilebilir/daraltılabilir gruplar olarak doğru şekilde bildirilir.</span><span class="sxs-lookup"><span data-stu-id="b5c26-180">Starting with the .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="b5c26-181">.NET Framework 4.7 ve önceki sürümlerinde, <xref:System.Windows.Controls.DataGridCell> denetimleri ekran okuyucular tarafından bildirilen "özel"</span><span class="sxs-lookup"><span data-stu-id="b5c26-181">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="b5c26-182">.NET Framework 4.7.1 ile başlayarak, yöneticiler artık doğru şekilde veri kılavuz hücresi (yerelleştirilmiş) bildirilir.</span><span class="sxs-lookup"><span data-stu-id="b5c26-182">Starting with the .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>
 
- <span data-ttu-id="b5c26-183">.NET Framework 4.7.1 ile başlayarak, adı düzenlenebilir bir ekran okuyucular duyurmaktan <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="b5c26-183">Starting with the .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="b5c26-184">.NET Framework 4.7 ve önceki sürümlerinde, <xref:System.Windows.Controls.PasswordBox> denetimleri veya "öğesi Görünümü'nde" olarak bildirilen olduğu Aksi takdirde yanlış bir davranışı.</span><span class="sxs-lookup"><span data-stu-id="b5c26-184">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="b5c26-185">.NET Framework 4.7.1 ile başlayarak Bu sorun düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b5c26-185">This issue is fixed starting with the .NET Framework 4.7.1.</span></span>

<span data-ttu-id="b5c26-186">**UIAutomation LiveRegion desteği**</span><span class="sxs-lookup"><span data-stu-id="b5c26-186">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="b5c26-187">Ekran okuyucular ekran okuyucusu Yardım kişiler gibi bir uygulama kullanıcı Arabirimi içeriği genellikle metin okuma odağa sahip kullanıcı Arabirimi içeriği çıktı tarafından okuyun.</span><span class="sxs-lookup"><span data-stu-id="b5c26-187">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="b5c26-188">Ancak, bir kullanıcı Arabirimi öğesi değiştirir ve odağı yok, Kullanıcı bildirim değil ve önemli bilgiler eksik.</span><span class="sxs-lookup"><span data-stu-id="b5c26-188">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="b5c26-189">Bu sorunu çözme sırasında Canlı bölge hedeflenir.</span><span class="sxs-lookup"><span data-stu-id="b5c26-189">Live regions aim at solving this problem.</span></span> <span data-ttu-id="b5c26-190">Bir geliştirici, ekran okuyucu veya bir kullanıcı Arabirimi öğesi için önemli bir değişiklik yapılmadığını diğer UIAutomation istemci bildirmek için bunları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5c26-190">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="b5c26-191">Ekran Okuyucu sonra nasıl ve ne zaman karar verebilirsiniz kullanıcıya bu değişikliği bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="b5c26-191">The screen reader can then decide how and when to inform the user of this change.</span></span> 

<span data-ttu-id="b5c26-192">Canlı bölge desteklemek için aşağıdaki API'leri için WPF eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="b5c26-192">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="b5c26-193"><xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> Ve <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> tanımlamak alanları **LiveSetting** özelliği ve **LiveRegionChanged** olay.</span><span class="sxs-lookup"><span data-stu-id="b5c26-193">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="b5c26-194">XAML kullanılarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="b5c26-194">They can be set by using XAML.</span></span>

- <span data-ttu-id="b5c26-195">**AutomationProperties.LiveSetting** ekran okuyucu önem UI değişikliğinin kullanıcıya bildirir özelliğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b5c26-195">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="b5c26-196"><xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> Tanımlayan özellik **AutomationProperties.LiveSetting** ekli özellik.</span><span class="sxs-lookup"><span data-stu-id="b5c26-196">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>
 
- <span data-ttu-id="b5c26-197"><xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> Sağlamak için geçersiz kılınabilir bir yöntemi, bir **LiveSetting** değeri.</span><span class="sxs-lookup"><span data-stu-id="b5c26-197">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="b5c26-198"><xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> Ve <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> almanıza ve ayarlamanıza yöntemleri bir **LiveSetting** değeri.</span><span class="sxs-lookup"><span data-stu-id="b5c26-198">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>
 
- <span data-ttu-id="b5c26-199"><xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> Aşağıdaki olası tanımlayan sabit listesi **LiveSetting** değerleri:</span><span class="sxs-lookup"><span data-stu-id="b5c26-199">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

   - <span data-ttu-id="b5c26-200"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b5c26-200"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b5c26-201">Canlı bölge içeriğini değiştiyse öğesi bildirimleri göndermez.</span><span class="sxs-lookup"><span data-stu-id="b5c26-201">The element does not send notifications if the content of the live region has changed.</span></span>   
   - <span data-ttu-id="b5c26-202"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b5c26-202"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b5c26-203">Canlı bölge içeriğini değiştiyse öğe interruptive olmayan bildirimleri gönderir.</span><span class="sxs-lookup"><span data-stu-id="b5c26-203">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>   

  - <span data-ttu-id="b5c26-204"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b5c26-204"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b5c26-205">Canlı bölge içeriğini değiştiyse öğe interruptive bildirimleri gönderir.</span><span class="sxs-lookup"><span data-stu-id="b5c26-205">The element sends interruptive notifications if the content of the live region has changed.</span></span>   

<span data-ttu-id="b5c26-206">Ayarlayarak bir LiveRegion oluşturabilirsiniz **AutomationProperties.LiveSetting** aşağıdaki örnekte gösterildiği gibi ilgi alanı, öğe özelliği:</span><span class="sxs-lookup"><span data-stu-id="b5c26-206">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>   

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="b5c26-207">Canlı bölge verileri değiştirir ve ekran okuyucu bildirmeniz gerekir, siz açıkça bir olay aşağıdaki örnekte gösterildiği gibi neden olmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b5c26-207">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="b5c26-208">**Yüksek Karşıtlık**</span><span class="sxs-lookup"><span data-stu-id="b5c26-208">**High contrast**</span></span>

<span data-ttu-id="b5c26-209">.NET Framework 4.7.1 ile başlayarak, çeşitli WPF denetimleri için yüksek karşıtlık geliştirmeleri yapıldı.</span><span class="sxs-lookup"><span data-stu-id="b5c26-209">Starting with the .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="b5c26-210">Bunlar artık ne zaman görülebilir <xref:System.Windows.SystemParameters.HighContrast%2A> tema ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="b5c26-210">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="b5c26-211">Bu güncelleştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b5c26-211">These include:</span></span>

- <span data-ttu-id="b5c26-212"><xref:System.Windows.Controls.Expander> Denetimi</span><span class="sxs-lookup"><span data-stu-id="b5c26-212"><xref:System.Windows.Controls.Expander> control</span></span>

    <span data-ttu-id="b5c26-213">Görseli odak <xref:System.Windows.Controls.Expander> denetimidir artık görünür.</span><span class="sxs-lookup"><span data-stu-id="b5c26-213">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="b5c26-214">Klavye görseller için <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, ve <xref:System.Windows.Controls.RadioButton> denetimleri görünür de.</span><span class="sxs-lookup"><span data-stu-id="b5c26-214">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="b5c26-215">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b5c26-215">For example:</span></span>

    <span data-ttu-id="b5c26-216">Sonra:</span><span class="sxs-lookup"><span data-stu-id="b5c26-216">Before:</span></span> 
    
    ![Erişilebilirlik geliştirmeleri önce odaklanılan genişletici denetimi](media/expander-before.png)

    <span data-ttu-id="b5c26-218">Sonra:</span><span class="sxs-lookup"><span data-stu-id="b5c26-218">After:</span></span> 

    ![Erişilebilirlik geliştirmeleri sonra odaklanılan genişletici denetimi](media/expander-after.png)

- <span data-ttu-id="b5c26-220"><xref:System.Windows.Controls.CheckBox> ve <xref:System.Windows.Controls.RadioButton> denetimleri</span><span class="sxs-lookup"><span data-stu-id="b5c26-220"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>
 
    <span data-ttu-id="b5c26-221">Metinde <xref:System.Windows.Controls.CheckBox> ve <xref:System.Windows.Controls.RadioButton> denetimleri, yüksek karşıtlık Temalar da seçildiğinde daha kolay sunuldu.</span><span class="sxs-lookup"><span data-stu-id="b5c26-221">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="b5c26-222">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b5c26-222">For example:</span></span>

    <span data-ttu-id="b5c26-223">Sonra:</span><span class="sxs-lookup"><span data-stu-id="b5c26-223">Before:</span></span> 

    ![Erişilebilirlik geliştirmeleri önce odaklanılan yüksek karşıtlık radyo düğmesi](media/radio-button-before.png)
    
    <span data-ttu-id="b5c26-225">Sonra:</span><span class="sxs-lookup"><span data-stu-id="b5c26-225">After:</span></span> 

    ![Erişilebilirlik geliştirmeleri sonra odaklanılan yüksek karşıtlık radyo düğmesi](media/radio-button-after.png)

- <span data-ttu-id="b5c26-227"><xref:System.Windows.Controls.ComboBox> Denetimi</span><span class="sxs-lookup"><span data-stu-id="b5c26-227"><xref:System.Windows.Controls.ComboBox> control</span></span>
 
    <span data-ttu-id="b5c26-228">.NET Framework 4.7.1, devre dışı kenarlık başlangıç <xref:System.Windows.Controls.ComboBox> devre dışı bırakılmış metinlerin aynı renge denetimidir.</span><span class="sxs-lookup"><span data-stu-id="b5c26-228">Starting with the .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="b5c26-229">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b5c26-229">For example:</span></span>
    
    <span data-ttu-id="b5c26-230">Sonra:</span><span class="sxs-lookup"><span data-stu-id="b5c26-230">Before:</span></span> 

     ![ComboBox kenarlık ve metin erişilebilirlik geliştirmeleri önce devre dışı](media/combo-disabled-before.png)

    <span data-ttu-id="b5c26-232">Sonra:</span><span class="sxs-lookup"><span data-stu-id="b5c26-232">After:</span></span>   

     ![ComboBox kenarlık ve metin sonra erişilebilirlik iyileştirmeleri devre dışı](media/combo-disabled-after.png)

    <span data-ttu-id="b5c26-234">Ayrıca, doğru bir Tema rengi devre dışı bırakılmış ve odaklanmış düğmelerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b5c26-234">In addition, disabled and focused buttons use the correct theme color.</span></span>

    <span data-ttu-id="b5c26-235">Sonra:</span><span class="sxs-lookup"><span data-stu-id="b5c26-235">Before:</span></span>

    ![Erişilebilirlik geliştirmeleri önce düğme Tema renkleri](media/button-themes-before.png) 
    
    <span data-ttu-id="b5c26-237">Sonra:</span><span class="sxs-lookup"><span data-stu-id="b5c26-237">After:</span></span> 

    ![Erişilebilirlik geliştirmeleri sonra düğme Tema renkleri](media/button-themes-after.png) 

    <span data-ttu-id="b5c26-239">Son olarak, .NET Framework 4.7 ve önceki sürümleri, ayar, bir <xref:System.Windows.Controls.ComboBox> denetimin stil `Toolbar.ComboBoxStyleKey` görünmemesini açılan liste okunu neden oldu.</span><span class="sxs-lookup"><span data-stu-id="b5c26-239">Finally, in the .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="b5c26-240">.NET Framework 4.7.1 ile başlayarak Bu sorun düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b5c26-240">This issue is fixed starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="b5c26-241">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b5c26-241">For example:</span></span>

    <span data-ttu-id="b5c26-242">Sonra:</span><span class="sxs-lookup"><span data-stu-id="b5c26-242">Before:</span></span> 

    ![Erişilebilirlik geliştirmeleri önce Toolbar.ComboBoxStyleKey](media/comboboxstylekey-before.png) 
    
    <span data-ttu-id="b5c26-244">Sonra:</span><span class="sxs-lookup"><span data-stu-id="b5c26-244">After:</span></span> 

    ![Erişilebilirlik geliştirmeleri sonra Toolbar.ComboBoxStyleKey](media/comboboxstylekey-after.png) 

- <span data-ttu-id="b5c26-246"><xref:System.Windows.Controls.DataGrid> Denetimi</span><span class="sxs-lookup"><span data-stu-id="b5c26-246"><xref:System.Windows.Controls.DataGrid> control</span></span>

    <span data-ttu-id="b5c26-247">.NET Framework 4.7.1'i, sıralama göstergesi oka başlayarak <xref:System.Windows.Controls.DataGrid> Tema renkleri kullandığı düzeltmek artık denetler.</span><span class="sxs-lookup"><span data-stu-id="b5c26-247">Starting with the .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="b5c26-248">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b5c26-248">For example:</span></span>

    <span data-ttu-id="b5c26-249">Sonra:</span><span class="sxs-lookup"><span data-stu-id="b5c26-249">Before:</span></span> 

    ![Erişilebilirlik geliştirmeleri önce sıralama göstergesi oku](media/sort-indicator-before.png) 
    
    <span data-ttu-id="b5c26-251">Sonra:</span><span class="sxs-lookup"><span data-stu-id="b5c26-251">After:</span></span>   
 
    ![Erişilebilirlik geliştirmeleri sonra sıralama göstergesi oku](media/sort-indicator-after.png) 
    
    <span data-ttu-id="b5c26-253">Ayrıca, .NET Framework 4.7 ve önceki sürümlerinde, varsayılan bağlantı stilini fare yanlış bir renk yüksek karşıtlık modlarında değiştirilecek.</span><span class="sxs-lookup"><span data-stu-id="b5c26-253">In addition, in the .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="b5c26-254">Bu, .NET Framework 4.7.1 ile başlayarak çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="b5c26-254">This is resolved starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="b5c26-255">Benzer şekilde, <xref:System.Windows.Controls.DataGrid> onay kutusu sütunları, .NET Framework 4.7.1 ile başlayarak klavye odağı geri bildirim için beklenen renkleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="b5c26-255">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with the .NET Framework 4.7.1.</span></span>

    <span data-ttu-id="b5c26-256">Sonra:</span><span class="sxs-lookup"><span data-stu-id="b5c26-256">Before:</span></span> 

    ![DataGrid varsayılan bağlantı stilini önce erişilebilirlik geliştirmeleri](media/default-link-style-before.png) 
 
    <span data-ttu-id="b5c26-258">Sonra:</span><span class="sxs-lookup"><span data-stu-id="b5c26-258">After:</span></span>    
  
    ![DataGrid varsayılan bağlantı stilini sonra erişilebilirlik geliştirmeleri](media/default-link-style-after.png)  

<span data-ttu-id="b5c26-260">.NET Framework 4.7.1 WPF erişilebilirlik geliştirmeleri hakkında daha fazla bilgi için bkz. [erişilebilirlik geliştirmeleri ' WPF'de](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span><span class="sxs-lookup"><span data-stu-id="b5c26-260">For more information on WPF accessibility improvements in the .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

<a name="winforms471"></a>
### <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="b5c26-261">Windows Forms erişilebilirlik geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="b5c26-261">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="b5c26-262">.NET Framework 4.7.1'da, Windows Forms (WinForms) aşağıdaki alanlarda erişilebilirlik değişiklikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b5c26-262">In the .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="b5c26-263">**Yüksek karşıtlık modunda geliştirilmiş görüntüleme**</span><span class="sxs-lookup"><span data-stu-id="b5c26-263">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="b5c26-264">.NET Framework 4.7.1 ile başlayarak, işletim sistemi içinde kullanılabilir olan yüksek karşıtlık modda geliştirilmiş işleme çeşitli WinForms denetimler sunar.</span><span class="sxs-lookup"><span data-stu-id="b5c26-264">Starting with the .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="b5c26-265">Windows 10 bazı yüksek karşıtlık sistem renkleri için değerleri değişti ve Windows Forms, Windows 10 Win32 altyapısını temel alır.</span><span class="sxs-lookup"><span data-stu-id="b5c26-265">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="b5c26-266">En iyi deneyim için en son Windows sürümüne çalıştırın ve en son işletim sistemi değişiklikleri için aşağıdaki görünür, böylece bir app.manifest dosyasındaki bir test uygulaması ve Çalıştır-açıklama Windows 10 işletim sistemi satırı desteklenen ekleyerek kabul et:</span><span class="sxs-lookup"><span data-stu-id="b5c26-266">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!-- Windows 10 -->
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
<span data-ttu-id="b5c26-267">Yüksek Karşıtlık değişiklikler bazı örnekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b5c26-267">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="b5c26-268">Açılır menüdeki onay <xref:System.Windows.Forms.MenuStrip> öğeleri görüntülemek daha kolay.</span><span class="sxs-lookup"><span data-stu-id="b5c26-268">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="b5c26-269">Bu onay kutusu seçildiğinde, devre dışı <xref:System.Windows.Forms.MenuStrip> öğeleri görüntülemek daha kolay.</span><span class="sxs-lookup"><span data-stu-id="b5c26-269">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="b5c26-270">Seçili metinde <xref:System.Windows.Forms.Button> Denetim seçim rengi ile karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="b5c26-270">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="b5c26-271">Devre dışı bırakılmış metinlerin okunmasını daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="b5c26-271">Disabled text is easier to read.</span></span> <span data-ttu-id="b5c26-272">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b5c26-272">For example:</span></span>

    <span data-ttu-id="b5c26-273">Sonra:</span><span class="sxs-lookup"><span data-stu-id="b5c26-273">Before:</span></span>

    ![Erişilebilirlik geliştirmeleri önce devre dışı bırakılmış metin](media/wf-disabled-before.png) 

    <span data-ttu-id="b5c26-275">Sonra:</span><span class="sxs-lookup"><span data-stu-id="b5c26-275">After:</span></span>

    ![Erişilebilirlik geliştirmeleri sonra devre dışı bırakılmış metin](media/wf-disabled-after.png) 

- <span data-ttu-id="b5c26-277">İş parçacığı özel durum iletişim kutusunda yüksek karşıtlık geliştirmeleri.</span><span class="sxs-lookup"><span data-stu-id="b5c26-277">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="b5c26-278">**Geliştirilmiş ekran okuyucu desteği**</span><span class="sxs-lookup"><span data-stu-id="b5c26-278">**Improved Narrator support**</span></span>

<span data-ttu-id="b5c26-279">Windows Forms'ta .NET Framework 4.7.1 ekran okuyucu için aşağıdaki erişilebilirlik geliştirmeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="b5c26-279">Windows Forms in the .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="b5c26-280"><xref:System.Windows.Forms.MonthCalendar> Denetim, ekran okuyucusu tarafından yanı sıra diğer UI Otomasyon araçları tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="b5c26-280">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="b5c26-281"><xref:System.Windows.Forms.CheckedListBox> Denetim, ekran okuyucusu bir liste öğesi değerini değiştirdiyseniz kullanıcıyı uyarır, böylece bir öğenin denetim durumu değiştiğinde bildirir.</span><span class="sxs-lookup"><span data-stu-id="b5c26-281">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>
 
- <span data-ttu-id="b5c26-282"><xref:System.Windows.Forms.DataGridViewCell> Denetimi için ekran okuyucusu doğru salt okunur durumunu raporlar.</span><span class="sxs-lookup"><span data-stu-id="b5c26-282">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>
 
- <span data-ttu-id="b5c26-283">Okuyucu artık devre dışı okur <xref:System.Windows.Forms.ToolStripMenuItem> metin, daha önce devre dışı bırakılmış menü öğelerinin üzerine atlarsınız ise.</span><span class="sxs-lookup"><span data-stu-id="b5c26-283">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="b5c26-284">**UIAutomation erişilebilirlik desenleri için gelişmiş destek**</span><span class="sxs-lookup"><span data-stu-id="b5c26-284">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="b5c26-285">Erişilebilirlik teknoloji Araçlar, geliştiricilerin .NET Framework 4.7.1 ile başlayarak, ortak API erişilebilirlik desenleri ve birden çok WinForms denetimi özelliklerini yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5c26-285">Starting with the .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="b5c26-286">Bu erişilebilirlik geliştirmeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="b5c26-286">These accessibility improvements include:</span></span>

- <span data-ttu-id="b5c26-287"><xref:System.Windows.Forms.ComboBox> Ve <xref:System.Windows.Forms.ToolStripSplitButton> artık destek [Genişlet/Daralt deseni](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="b5c26-287">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>
 
- <span data-ttu-id="b5c26-288"><xref:System.Windows.Forms.DataGridViewCheckBoxCell> Artık destekliyor [geçiş deseni](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="b5c26-288">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>
 
- <span data-ttu-id="b5c26-289"><xref:System.Windows.Forms.ToolStripItem> Denetim destekler <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> özelliği ve [Genişlet/Daralt deseni](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="b5c26-289">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="b5c26-290"><xref:System.Windows.Forms.NumericUpDown> Ve <xref:System.Windows.Forms.DomainUpDown> denetimleri Destek <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> özelliği.</span><span class="sxs-lookup"><span data-stu-id="b5c26-290">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span></span>

<span data-ttu-id="b5c26-291">**Geliştirilmiş özelliği tarayıcı deneyimi**</span><span class="sxs-lookup"><span data-stu-id="b5c26-291">**Improved property browser experience**</span></span>

<span data-ttu-id="b5c26-292">.NET Framework 4.7.1 ile başlayarak, Windows Forms içerir:</span><span class="sxs-lookup"><span data-stu-id="b5c26-292">Starting with the .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="b5c26-293">Daha iyi klavye gezintisi aracılığıyla çeşitli yanıdaki açılan seçimi windows.</span><span class="sxs-lookup"><span data-stu-id="b5c26-293">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="b5c26-294">Gereksiz sekme duraklarının azaltma.</span><span class="sxs-lookup"><span data-stu-id="b5c26-294">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="b5c26-295">Daha iyi denetim türlerini raporlama.</span><span class="sxs-lookup"><span data-stu-id="b5c26-295">Better reporting of control types.</span></span>
- <span data-ttu-id="b5c26-296">Geliştirilmiş ekran okuyucu davranışı.</span><span class="sxs-lookup"><span data-stu-id="b5c26-296">Improved narrator behavior.</span></span>
 
<a name="aspnet471"></a>
### <a name="aspnet-web-controls"></a><span data-ttu-id="b5c26-297">ASP.NET web denetimleri</span><span class="sxs-lookup"><span data-stu-id="b5c26-297">ASP.NET web controls</span></span>

<span data-ttu-id="b5c26-298">ASP.NET .NET Framework 4.7.1 ve Visual Studio 2017 15.3 ile başlayarak, Visual Studio'da Erişilebilirlik teknolojisi ile ASP.NET web denetimleri nasıl artırır.</span><span class="sxs-lookup"><span data-stu-id="b5c26-298">Starting with the .NET Framework 4.7.1 and Visual Studio 2017 15.3, ASP.NET improves how ASP.NET web controls work with accessibility technology in Visual Studio.</span></span> <span data-ttu-id="b5c26-299">Değişiklikler şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="b5c26-299">Changes include the following:</span></span>

- <span data-ttu-id="b5c26-300">Eksik kullanıcı Arabirimi erişilebilirliği desenleri gibi denetimleri içinde uygulamak için değişiklikleri **alan Ekle** iletişim kutusunda **Ayrıntılar görünümü** Sihirbazı'nı veya **yapılandırma ListView** iletişim **ListView** Sihirbazı.</span><span class="sxs-lookup"><span data-stu-id="b5c26-300">Changes to implement missing UI accessibility patterns in controls, like the **Add Field** dialog in the **Details View** wizard, or the **Configure ListView** dialog of the **ListView** wizard.</span></span>

- <span data-ttu-id="b5c26-301">Yüksek karşıtlık modunda görüntüleme gibi iyileştirmeye yönelik değişiklikler **veri çağrı alanları Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="b5c26-301">Changes to improve the display in High Contrast mode, like the **Data Pager Fields Editor**.</span></span>

- <span data-ttu-id="b5c26-302">Klavye ile gezintiyi iyileştirmeye yönelik değişiklikler deneyimleri denetimler için gibi **alanları** iletişim kutusunda **çağrı alanları Düzenle** DataPager denetimi Sihirbazı **ObjectContext yapılandırın**  iletişim kutusunda veya **yapılandırma veri seçimi** iletişim **veri kaynağı yapılandırma** Sihirbazı.</span><span class="sxs-lookup"><span data-stu-id="b5c26-302">Changes to improve the keyboard navigation experiences for controls, like the **Fields** dialog in the **Edit Pager Fields** wizard of the DataPager control, the **Configure ObjectContext** dialog, or the **Configure Data Selection** dialog of the **Configure Data Source** wizard.</span></span>

<a name="tools471"></a>
### <a name="net-sdk-tools"></a><span data-ttu-id="b5c26-303">.NET SDK Tools</span><span class="sxs-lookup"><span data-stu-id="b5c26-303">.NET SDK Tools</span></span>

<span data-ttu-id="b5c26-304">[Yapılandırma Aracı (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) ve [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) çeşitli erişilebilirlik sorunları çözme tarafından geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b5c26-304">The [Configuration Editor Tool (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) and [Service Trace Viewer Tool (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="b5c26-305">Bunların çoğu tanımlanmayan bir ad veya doğru uygulanmadı belirli bir UI Otomasyon düzenleri gibi küçük problemler yoktu.</span><span class="sxs-lookup"><span data-stu-id="b5c26-305">Most of these were small issues, like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="b5c26-306">Birçok kullanıcı bu yanlış değerini kullanan sunulacaktır, ancak ekran okuyucular gibi yardımcı teknolojiler kullanan müşteriler bu SDK Araçları daha erişilebilir bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5c26-306">While many users won’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span> 

<span data-ttu-id="b5c26-307">Bu geliştirmeler, klavye odağı sırası gibi önceki bazı davranışları değiştirir.</span><span class="sxs-lookup"><span data-stu-id="b5c26-307">These enhancements change some previous behaviors, such as keyboard focus order.</span></span>

<a name="wf471"></a>
### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="b5c26-308">Windows Workflow Foundation (WF) iş akışı Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="b5c26-308">Windows Workflow Foundation (WF) Workflow Designer</span></span>

<span data-ttu-id="b5c26-309">İş akışı tasarımcısında erişilebilirlik değişiklikler şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="b5c26-309">Accessibility changes in the Workflow Designer include the following:</span></span>

- <span data-ttu-id="b5c26-310">Sekme sırası, soldan sağa ve yukarıdan aşağıya bazı denetimlerinde değiştirir:</span><span class="sxs-lookup"><span data-stu-id="b5c26-310">The tab order changes to left to right and top to bottom in some controls:</span></span>

  - <span data-ttu-id="b5c26-311">Upravit data korelace için ayarlamak için Initialize bağıntı penceresi <xref:System.ServiceModel.Activities.InitializeCorrelation> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="b5c26-311">The initialize correlation window for setting correlation data for the <xref:System.ServiceModel.Activities.InitializeCorrelation> activity.</span></span>

  - <span data-ttu-id="b5c26-312">İçerik tanımı penceresi <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="b5c26-312">The content definition window for the <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply> activities.</span></span>

- <span data-ttu-id="b5c26-313">Daha fazla işlev klavye mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="b5c26-313">More functions are available via the keyboard:</span></span>

  - <span data-ttu-id="b5c26-314">Bir etkinliğin özelliklerini düzenlerken, özellik grupları tarafından klavye odaklı ilk kez daraltılabilirler.</span><span class="sxs-lookup"><span data-stu-id="b5c26-314">When editing the properties of an activity, property groups can be collapsed by keyboard the first time they are focused.</span></span>

  - <span data-ttu-id="b5c26-315">Uyarı simgeleri klavye tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="b5c26-315">Warning icons are accessible by keyboard.</span></span>

  - <span data-ttu-id="b5c26-316">**Daha özellikleri** düğmesine **özellikleri** pencere, klavye tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="b5c26-316">The **More Properties** button in the **Properties** window is accessible by keyboard.</span></span>

  - <span data-ttu-id="b5c26-317">Klavye kullanıcılarının üstbilgi öğeleri erişebileceği **bağımsız değişkenleri** ve **değişkenleri** iş akışı Tasarımcısı bölmelerini.</span><span class="sxs-lookup"><span data-stu-id="b5c26-317">Keyboard users can access the header items in the **Arguments** and **Variables** panes of the Workflow Designer.</span></span>

- <span data-ttu-id="b5c26-318">Geliştirilmiş görünürlük odaklanılan ne zaman gibi öğeleri:</span><span class="sxs-lookup"><span data-stu-id="b5c26-318">Improved visibility of items with focus, such as when:</span></span>

  - <span data-ttu-id="b5c26-319">İş Akışı Tasarımcısı ve etkinlik tasarımcıları tarafından kullanılan veri kılavuzları için satırlar ekleme.</span><span class="sxs-lookup"><span data-stu-id="b5c26-319">Adding rows to data grids used by the Workflow Designer and activity designers.</span></span>

  - <span data-ttu-id="b5c26-320">Alanları arasında sekmeyle gitmeyi <xref:System.ServiceModel.Activities.ReceiveReply> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="b5c26-320">Tabbing through fields in the <xref:System.ServiceModel.Activities.ReceiveReply> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>

  - <span data-ttu-id="b5c26-321">Değişken veya bağımsız değişkenleri için varsayılan değerleri ayarlama</span><span class="sxs-lookup"><span data-stu-id="b5c26-321">Setting default values for variables or arguments</span></span>

- <span data-ttu-id="b5c26-322">Artık ekran okuyucular düzgün tanıyabilmesi:</span><span class="sxs-lookup"><span data-stu-id="b5c26-322">Screen readers can now correctly recognize:</span></span>

  - <span data-ttu-id="b5c26-323">İş Akışı Tasarımcısı'nda kesme noktalarını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b5c26-323">Breakpoints set in the workflow designer.</span></span>

  - <span data-ttu-id="b5c26-324"><xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, Ve <xref:System.ServiceModel.Activities.CorrelationScope> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="b5c26-324">The <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, and <xref:System.ServiceModel.Activities.CorrelationScope> activities.</span></span>
  - <span data-ttu-id="b5c26-325">İçeriğini <xref:System.ServiceModel.Activities.Receive> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="b5c26-325">The contents of the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>

  - <span data-ttu-id="b5c26-326">Hedef türü için <xref:System.Activities.Statements.InvokeMethod> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="b5c26-326">The Target Type for the <xref:System.Activities.Statements.InvokeMethod> activity.</span></span>

  - <span data-ttu-id="b5c26-327">Özel durum birleşik giriş kutusu ve son olarak konusundaki <xref:System.Activities.Statements.TryCatch> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="b5c26-327">The Exception combo box and the Finally section in the <xref:System.Activities.Statements.TryCatch> activity.</span></span>

  - <span data-ttu-id="b5c26-328">İleti türü açılan kutusu, bağıntı başlatıcılar Ekle penceresi, içerik tanım penceresini ve mesajlaşma etkinlikleri CorrelatesOn tanımı penceresinde ayırıcı (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, ve <xref:System.ServiceModel.Activities.ReceiveReply>).</span><span class="sxs-lookup"><span data-stu-id="b5c26-328">The Message Type combo box, the splitter in the Add Correlation Initializers window, the Content Definition window, and the CorrelatesOn Definition window in the messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>

  - <span data-ttu-id="b5c26-329">Durum makinesi geçişler ve hedeflere geçer.</span><span class="sxs-lookup"><span data-stu-id="b5c26-329">State machine transitions and transitions destinations.</span></span>

  - <span data-ttu-id="b5c26-330">Ek açıklamalar ve bağlayıcılarda <xref:System.Activities.Statements.FlowDecision> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="b5c26-330">Annotations and connectors on <xref:System.Activities.Statements.FlowDecision> activities.</span></span>

  - <span data-ttu-id="b5c26-331">Etkinlikler için (sağ tıklama) bağlam menüleri.</span><span class="sxs-lookup"><span data-stu-id="b5c26-331">The context (right-click) menus for activities.</span></span>

  - <span data-ttu-id="b5c26-332">Özellik değer düzenleyicileri, aramayı Temizle düğmesi, kategoriye göre ve alfabetik sıralama düğmeler ve Özellikler kılavuzundaki ifade Düzenleyicisi iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="b5c26-332">The property value editors, the Clear Search button, the By Category and Alphabetical sort buttons, and the Expression Editor dialog in the properties grid.</span></span>

  - <span data-ttu-id="b5c26-333">İş akışı tasarımcısında yakınlaştırma yüzdesi.</span><span class="sxs-lookup"><span data-stu-id="b5c26-333">The zoom percentage in the Workflow Designer.</span></span>

  - <span data-ttu-id="b5c26-334">Ayırıcı <xref:System.Activities.Statements.Parallel> ve <xref:System.Activities.Statements.Pick> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="b5c26-334">The separator in <xref:System.Activities.Statements.Parallel> and <xref:System.Activities.Statements.Pick> activities.</span></span>

  - <span data-ttu-id="b5c26-335"><xref:System.Activities.Statements.InvokeDelegate> Etkinlik.</span><span class="sxs-lookup"><span data-stu-id="b5c26-335">The <xref:System.Activities.Statements.InvokeDelegate> activity.</span></span>

  - <span data-ttu-id="b5c26-336">Sözlük etkinlikler için seçim türlerinin penceresi (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`vb..).</span><span class="sxs-lookup"><span data-stu-id="b5c26-336">The Select Types window for dictionary activities (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`, etc.).</span></span>

  - <span data-ttu-id="b5c26-337">Göz atma ve .NET türünü seç penceresi.</span><span class="sxs-lookup"><span data-stu-id="b5c26-337">The Browse and Select .NET Type window.</span></span>

  - <span data-ttu-id="b5c26-338">İş akışı tasarımcısında içerik haritaları.</span><span class="sxs-lookup"><span data-stu-id="b5c26-338">Breadcrumbs in the Workflow Designer.</span></span>

- <span data-ttu-id="b5c26-339">Yüksek karşıtlıklı tema seçen kullanıcılar, iş akışı Tasarımcısı gibi öğeleri ve odak öğeleri için kullanılan daha belirgin seçim kutuları arasında daha iyi kontrast, Denetim ve görünürlüğü içindeki birçok geliştirmeden görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="b5c26-339">Users who choose High Contrast themes will see many improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5c26-340">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5c26-340">See also</span></span>

- [<span data-ttu-id="b5c26-341">.NET Framework'teki yenilikler</span><span class="sxs-lookup"><span data-stu-id="b5c26-341">What's new in the .NET Framework</span></span>](whats-new.md)

