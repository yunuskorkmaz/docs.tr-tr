---
title: "Erişilebilirlik .NET Framework'teki yenilikler"
ms.custom: updateeachrelease
ms.date: 10/13/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: what's new [.NET Framework]
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9fe4b24f14dd8f08d1168cc26b91e04faa4bf183
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="379e3-102">Erişilebilirlik .NET Framework'teki yenilikler</span><span class="sxs-lookup"><span data-stu-id="379e3-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="379e3-103">.NET Framework uygulamaları, kullanıcılarınızın daha fazla accessibile kolaylaştırmayı amaçlar.</span><span class="sxs-lookup"><span data-stu-id="379e3-103">The .NET Framework aims at making applications more accessibile for your users.</span></span> <span data-ttu-id="379e3-104">Erişilebilirlik Özellikleri yardımcı teknoloji kullanıcılar için uygun bir deneyim sağlamak üzere bir uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="379e3-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="379e3-105">.NET Framework 4.7.1 ile başlayarak, .NET Framework çok sayıda erişilebilir uygulamalar oluşturmak geliştiriciler izin erişilebilirlik geliştirmeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="379e3-105">Starting with the .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span> 

<span data-ttu-id="379e3-106">Yeni erişilebilirlik özellikleri, .NET Framework 4.7.1 hedefleyen uygulamalar için varsayılan olarak etkin veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="379e3-106">The new accessibility features are enabled by default for applications that target the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="379e3-107">Ayrıca, .NET Framework'ün önceki bir sürümünü hedef ancak 4.7.1 .NET Framework üzerinde çalışmakta olan veya daha sonra seçebilirsiniz uygulamalar out eski erişilebilirlik davranışlarını (ve dolayısıyla 4.7.1 .NET Framework'teki erişilebilirlik geliştirmeleri için kabul) tarafından Aşağıdaki anahtar ekleme [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğesinde [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) uygulamanın yapılandırma dosyasının.</span><span class="sxs-lookup"><span data-stu-id="379e3-107">In addition, applications that target an earlier version of the .NET Framework but are running on the .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby opt in to the accessibility improvements in the .NET Framework 4.7.1) by adding the following switch to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="379e3-108">Benzer şekilde, 4.7.1 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar erişilebilirlik özellikleri aşağıdaki anahtara ekleyerek devre dışı bırakabilirsiniz [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğesinde [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) uygulamanın yapılandırma dosyasının.</span><span class="sxs-lookup"><span data-stu-id="379e3-108">Similarly, applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding the following switch to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a><span data-ttu-id="379e3-109">Erişilebilirlik 4.7.1 .NET Framework'teki yenilikler</span><span class="sxs-lookup"><span data-stu-id="379e3-109">What's new in accessibility in the .NET Framework 4.7.1</span></span>

<span data-ttu-id="379e3-110">.NET Framework 4.7.1 aşağıdaki alanlarda yeni erişilebilirlik özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="379e3-110">The .NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="379e3-111">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="379e3-111">Windows Presentation Foundation (WPF)</span></span>](#windows-presentation-foundation-wpf)

- [<span data-ttu-id="379e3-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="379e3-112">Windows Forms</span></span>](#windows-forms-accessibility-improvements)

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="379e3-113">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="379e3-113">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="379e3-114">**Ekran Okuyucusu geliştirmeleri**</span><span class="sxs-lookup"><span data-stu-id="379e3-114">**Screen reader improvements**</span></span>

<span data-ttu-id="379e3-115">Erişilebilirlik geliştirmeleri etkinleştirilirse, .NET Framework 4.7.1 ekran okuyucular etkileyen aşağıdaki geliştirmeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="379e3-115">If accessibility improvements are enabled, the .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="379e3-116">.NET Framework 4.7 ve önceki sürümlerde, <xref:System.Windows.Controls.Expander> denetimleri duyurdu düğmeler olarak ekran okuyucular tarafından.</span><span class="sxs-lookup"><span data-stu-id="379e3-116">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="379e3-117">.NET Framework 4.7.1 ile başlayarak, bunlar Genişletilebilir/daraltılabilir grupları olarak doğru bildirilir.</span><span class="sxs-lookup"><span data-stu-id="379e3-117">Starting with the .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="379e3-118">.NET Framework 4.7 ve önceki sürümlerde, <xref:System.Windows.Controls.DataGridCell> denetimleri ekran okuyucular tarafından bildirilen "özel" olarak</span><span class="sxs-lookup"><span data-stu-id="379e3-118">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="379e3-119">.NET Framework 4.7.1 ile başlayarak, bunlar artık doğru (yerelleştirilmiş) veri kılavuz hücresinin bildirilir.</span><span class="sxs-lookup"><span data-stu-id="379e3-119">Starting with the .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>
 
- <span data-ttu-id="379e3-120">.NET Framework 4.7.1 ile başlayarak, ekran okuyucuların bir düzenlenebilir adını Duyurusu <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="379e3-120">Starting with the .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="379e3-121">.NET Framework 4.7 ve önceki sürümlerde, <xref:System.Windows.Controls.PasswordBox> denetimleri "öğesi görünüm olarak" duyurdu veya vardı Aksi takdirde yanlış bir davranış.</span><span class="sxs-lookup"><span data-stu-id="379e3-121">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="379e3-122">Bu sorun .NET Framework 4.7.1 ile başlayan düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="379e3-122">This issue is fixed starting with the .NET Framework 4.7.1.</span></span>     

<span data-ttu-id="379e3-123">**UIAutomation LiveRegion desteği**</span><span class="sxs-lookup"><span data-stu-id="379e3-123">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="379e3-124">Ekran okuyucular ekran okuyucusu Yardım kişiler gibi bir uygulama kullanıcı Arabirimi içeriğini odaklanmış UI içeriği metin okuma çıktı tarafından genellikle okuyun.</span><span class="sxs-lookup"><span data-stu-id="379e3-124">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="379e3-125">Ancak, bir kullanıcı Arabirimi öğesi değiştirir ve odağı yok, kullanıcı bilgilendirilmez ve önemli bilgiler eksik.</span><span class="sxs-lookup"><span data-stu-id="379e3-125">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="379e3-126">Bu sorunu çözme sırasında dinamik bölgeler hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="379e3-126">Live regions aim at solving this problem.</span></span> <span data-ttu-id="379e3-127">Bir geliştirici ekran okuyucusu veya önemli bir değişiklik bir kullanıcı Arabirimi öğesine yapılan herhangi bir UIAutomation istemcisi hakkında bilgilendirmek için bunları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="379e3-127">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="379e3-128">Ekran Okuyucusu sonra nasıl ve ne zaman karar verebilirsiniz bu değişikliği kullanıcıyı bilgilendirmek üzere.</span><span class="sxs-lookup"><span data-stu-id="379e3-128">The screen reader can then decide how and when to inform the user of this change.</span></span> 

<span data-ttu-id="379e3-129">Canlı bölgeler desteklemek için aşağıdaki API'leri WPF için eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="379e3-129">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="379e3-130"><xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> Ve <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> tanımlamak alanları **LiveSetting** özelliği ve **LiveRegionChanged** olay.</span><span class="sxs-lookup"><span data-stu-id="379e3-130">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="379e3-131">XAML kullanılarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="379e3-131">They can be set by using XAML.</span></span>

- <span data-ttu-id="379e3-132">**AutomationProperties.LiveSetting** kullanıcı için kullanıcı Arabirimi değişiklik önem ekran okuyucusu bildirir özelliği eklenmiş.</span><span class="sxs-lookup"><span data-stu-id="379e3-132">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="379e3-133"><xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> Tanımlayan özellik **AutomationProperties.LiveSetting** özelliği eklenmiş.</span><span class="sxs-lookup"><span data-stu-id="379e3-133">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>
 
- <span data-ttu-id="379e3-134"><xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> Sağlamak üzere geçersiz yöntemi bir **LiveSetting** değeri.</span><span class="sxs-lookup"><span data-stu-id="379e3-134">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="379e3-135"><xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> Ve <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> alma ve ayarlama yöntemleri bir **LiveSetting** değeri.</span><span class="sxs-lookup"><span data-stu-id="379e3-135">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>
 
- <span data-ttu-id="379e3-136"><xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> Aşağıdaki olası tanımlar numaralandırma **LiveSetting** değerler:</span><span class="sxs-lookup"><span data-stu-id="379e3-136">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

   - <span data-ttu-id="379e3-137"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="379e3-137"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="379e3-138">Canlı bölge içeriği değişirse öğesi bildirim göndermez.</span><span class="sxs-lookup"><span data-stu-id="379e3-138">The element does not send notifications if the content of the live region has changed.</span></span>   
   - <span data-ttu-id="379e3-139"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="379e3-139"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="379e3-140">Canlı bölge içeriği değişirse öğesi interruptive olmayan bildirimleri gönderir.</span><span class="sxs-lookup"><span data-stu-id="379e3-140">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>   

  - <span data-ttu-id="379e3-141"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="379e3-141"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="379e3-142">Canlı bölge içeriği değişirse öğesi interruptive bildirimleri gönderir.</span><span class="sxs-lookup"><span data-stu-id="379e3-142">The element sends interruptive notifications if the content of the live region has changed.</span></span>   

<span data-ttu-id="379e3-143">Bir LiveRegion ayarlayarak oluşturabileceğiniz **AutomationProperties.LiveSetting** ilgi, aşağıdaki örnekte gösterildiği gibi öğesindeki özelliği:</span><span class="sxs-lookup"><span data-stu-id="379e3-143">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>   

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="379e3-144">Canlı bölgede veri değişikliklerini ve ekran okuyucusu bildirmek gerektiğinde, açıkça bir olay aşağıdaki örnekte gösterildiği gibi yükseltin.</span><span class="sxs-lookup"><span data-stu-id="379e3-144">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="379e3-145">**Yüksek Karşıtlık**</span><span class="sxs-lookup"><span data-stu-id="379e3-145">**High contrast**</span></span>

<span data-ttu-id="379e3-146">.NET Framework 4.7.1 ile başlayarak, çeşitli WPF denetimleri yüksek karşıtlıklı iyileştirmeler yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="379e3-146">Starting with the .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="379e3-147">Şimdi ne zaman görünür oldukları <xref:System.Windows.SystemParameters.HighContrast%2A> tema ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="379e3-147">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="379e3-148">Bu güncelleştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="379e3-148">These include:</span></span>

- <span data-ttu-id="379e3-149"><xref:System.Windows.Controls.Expander>denetimi</span><span class="sxs-lookup"><span data-stu-id="379e3-149"><xref:System.Windows.Controls.Expander> control</span></span>

    <span data-ttu-id="379e3-150">Görsel için odak <xref:System.Windows.Controls.Expander> denetimidir artık görünür.</span><span class="sxs-lookup"><span data-stu-id="379e3-150">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="379e3-151">Klavye görsellerini <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, ve <xref:System.Windows.Controls.RadioButton> denetimleri görünür de.</span><span class="sxs-lookup"><span data-stu-id="379e3-151">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="379e3-152">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="379e3-152">For example:</span></span>

    <span data-ttu-id="379e3-153">Sonra:</span><span class="sxs-lookup"><span data-stu-id="379e3-153">Before:</span></span> 
    
    ![Erişilebilirlik geliştirmeleri önce odaklanılan genişletici denetimi](media/expander-before.png)

    <span data-ttu-id="379e3-155">Sonra:</span><span class="sxs-lookup"><span data-stu-id="379e3-155">After:</span></span> 

    ![Erişilebilirlik geliştirmeleri sonra odaklanılan genişletici denetimi](media/expander-after.png)

- <span data-ttu-id="379e3-157"><xref:System.Windows.Controls.CheckBox>ve <xref:System.Windows.Controls.RadioButton> denetimleri</span><span class="sxs-lookup"><span data-stu-id="379e3-157"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>
 
    <span data-ttu-id="379e3-158">Metin <xref:System.Windows.Controls.CheckBox> ve <xref:System.Windows.Controls.RadioButton> denetimleri yüksek karşıtlık Temalar seçildiğinde daha kolay şimdi.</span><span class="sxs-lookup"><span data-stu-id="379e3-158">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="379e3-159">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="379e3-159">For example:</span></span>

    <span data-ttu-id="379e3-160">Sonra:</span><span class="sxs-lookup"><span data-stu-id="379e3-160">Before:</span></span> 

    ![Erişilebilirlik geliştirmeleri önce odaklanılan yüksek karşıtlık radyo düğmesi](media/radio-button-before.png)
    
    <span data-ttu-id="379e3-162">Sonra:</span><span class="sxs-lookup"><span data-stu-id="379e3-162">After:</span></span> 

    ![Erişilebilirlik geliştirmeleri sonra odaklanılan yüksek karşıtlık radyo düğmesi](media/radio-button-after.png)

- <span data-ttu-id="379e3-164"><xref:System.Windows.Controls.ComboBox>denetimi</span><span class="sxs-lookup"><span data-stu-id="379e3-164"><xref:System.Windows.Controls.ComboBox> control</span></span>
 
    <span data-ttu-id="379e3-165">.NET Framework ile 4.7.1, bir devre dışı kenarlık başlangıç <xref:System.Windows.Controls.ComboBox> denetimidir devre dışı bırakılmış metin olarak aynı rengi.</span><span class="sxs-lookup"><span data-stu-id="379e3-165">Starting with the .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="379e3-166">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="379e3-166">For example:</span></span>
    
    <span data-ttu-id="379e3-167">Sonra:</span><span class="sxs-lookup"><span data-stu-id="379e3-167">Before:</span></span> 

     ![ComboBox kenarlık ve metin erişilebilirlik geliştirmeleri önce devre dışı](media/combo-disabled-before.png)

    <span data-ttu-id="379e3-169">Sonra:</span><span class="sxs-lookup"><span data-stu-id="379e3-169">After:</span></span>   

     ![ComboBox kenarlık ve metin erişilebilirlik geliştirmeleri sonra devre dışı](media/combo-disabled-after.png)

    <span data-ttu-id="379e3-171">Ayrıca, doğru Tema rengi devre dışı bırakılmış ve odaklanmış düğmelerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="379e3-171">In addition, disabled and focused buttons use the correct theme color.</span></span>

    <span data-ttu-id="379e3-172">Sonra:</span><span class="sxs-lookup"><span data-stu-id="379e3-172">Before:</span></span>

    ![Erişilebilirlik geliştirmeleri önce düğmesi Tema renkleri](media/button-themes-before.png) 
    
    <span data-ttu-id="379e3-174">Sonra:</span><span class="sxs-lookup"><span data-stu-id="379e3-174">After:</span></span> 

    ![Erişilebilirlik geliştirmeleri sonra düğmesi Tema renkleri](media/button-themes-after.png) 

    <span data-ttu-id="379e3-176">Son olarak, .NET Framework 4.7 ve önceki sürümleri, ayarı içinde bir <xref:System.Windows.Controls.ComboBox> denetimin stiline `Toolbar.ComboBoxStyleKey` görünmez olmasını aşağı açılan okunu neden oldu.</span><span class="sxs-lookup"><span data-stu-id="379e3-176">Finally, in the .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="379e3-177">Bu sorun .NET Framework 4.7.1 ile başlayan düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="379e3-177">This issue is fixed starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="379e3-178">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="379e3-178">For example:</span></span>

    <span data-ttu-id="379e3-179">Sonra:</span><span class="sxs-lookup"><span data-stu-id="379e3-179">Before:</span></span> 

    ![Erişilebilirlik geliştirmeleri önce Toolbar.ComboBoxStyleKey](media/comboboxstylekey-before.png) 
    
    <span data-ttu-id="379e3-181">Sonra:</span><span class="sxs-lookup"><span data-stu-id="379e3-181">After:</span></span> 

    ![Erişilebilirlik geliştirmeleri sonra Toolbar.ComboBoxStyleKey](media/comboboxstylekey-after.png) 

- <span data-ttu-id="379e3-183"><xref:System.Windows.Controls.DataGrid>denetimi</span><span class="sxs-lookup"><span data-stu-id="379e3-183"><xref:System.Windows.Controls.DataGrid> control</span></span>

    <span data-ttu-id="379e3-184">.NET Framework 4.7.1, sıralama göstergesi oku başlayarak <xref:System.Windows.Controls.DataGrid> kullandığı Tema renkleri düzeltmek artık denetler.</span><span class="sxs-lookup"><span data-stu-id="379e3-184">Starting with the .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="379e3-185">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="379e3-185">For example:</span></span>

    <span data-ttu-id="379e3-186">Sonra:</span><span class="sxs-lookup"><span data-stu-id="379e3-186">Before:</span></span> 

    ![Erişilebilirlik geliştirmeleri önce sıralama göstergesi oku](media/sort-indicator-before.png) 
    
    <span data-ttu-id="379e3-188">Sonra:</span><span class="sxs-lookup"><span data-stu-id="379e3-188">After:</span></span>   
 
    ![Erişilebilirlik geliştirmeleri sonra sıralama göstergesi oku](media/sort-indicator-after.png) 
    
    <span data-ttu-id="379e3-190">Ayrıca, .NET Framework 4.7 ve önceki sürümlerinde varsayılan bağlantı stilini fare yanlış bir renk yüksek karşıtlık modunda değiştirilip.</span><span class="sxs-lookup"><span data-stu-id="379e3-190">In addition, in the .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="379e3-191">Bu .NET Framework 4.7.1 ile başlayan çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="379e3-191">This is resolved starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="379e3-192">Benzer şekilde, <xref:System.Windows.Controls.DataGrid> onay kutusunu sütunları .NET Framework 4.7.1 ile başlayan klavye odağı geri bildirim için beklenen renkleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="379e3-192">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with the .NET Framework 4.7.1.</span></span>

    <span data-ttu-id="379e3-193">Sonra:</span><span class="sxs-lookup"><span data-stu-id="379e3-193">Before:</span></span> 

    ![DataGrid varsayılan bağlantı stili önce erişilebilirlik geliştirmeleri](media/default-link-style-before.png) 
 
    <span data-ttu-id="379e3-195">Sonra:</span><span class="sxs-lookup"><span data-stu-id="379e3-195">After:</span></span>    
  
    ![DataGrid varsayılan bağlantı stili sonra erişilebilirlik geliştirmeleri](media/default-link-style-after.png)  

<span data-ttu-id="379e3-197">.NET Framework'teki 4.7.1 WPF erişilebilirlik geliştirmeleri hakkında daha fazla bilgi için bkz: [erişilebilirlik geliştirmeleri WPF'de](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span><span class="sxs-lookup"><span data-stu-id="379e3-197">For more information on WPF accessibility improvements in the .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

## <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="379e3-198">Windows Forms erişilebilirlik geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="379e3-198">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="379e3-199">.NET Framework 4.7.1'da, Windows Forms (WinForms) aşağıdaki alanlarda erişilebilirlik değişiklikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="379e3-199">In the .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="379e3-200">**Yüksek karşıtlık modunda geliştirilmiş görüntüleme**</span><span class="sxs-lookup"><span data-stu-id="379e3-200">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="379e3-201">.NET Framework 4.7.1 ile başlayarak, çeşitli WinForms denetimleri işletim sistemi içinde kullanılabilir yüksek karşıtlık modda geliştirilmiş işleme sunar.</span><span class="sxs-lookup"><span data-stu-id="379e3-201">Starting with the .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="379e3-202">Windows 10 bazı yüksek karşıtlık sistem renkleri değerlerini değişti ve Windows Forms Windows 10 Win32 Framework'te temel alır.</span><span class="sxs-lookup"><span data-stu-id="379e3-202">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="379e3-203">En iyi deneyim için en son sürümünü çalıştırın ve en son işletim sistemi değişiklikleri aşağıdaki tanıyarak test uygulaması ve kaydını yorum Windows 10 app.manifest dosyasında OS satırını desteklenen ekleyerek kabul:</span><span class="sxs-lookup"><span data-stu-id="379e3-203">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!– Windows 10 –>
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
<span data-ttu-id="379e3-204">Yüksek Karşıtlık değişiklikler bazı örnekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="379e3-204">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="379e3-205">Açılır menüdeki onay <xref:System.Windows.Forms.MenuStrip> öğeleri görüntülemek daha kolay.</span><span class="sxs-lookup"><span data-stu-id="379e3-205">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="379e3-206">Seçili olduğunda, devre dışı <xref:System.Windows.Forms.MenuStrip> öğeleri görüntülemek daha kolay.</span><span class="sxs-lookup"><span data-stu-id="379e3-206">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="379e3-207">Seçili metni <xref:System.Windows.Forms.Button> Denetim seçim rengi ile çelişir.</span><span class="sxs-lookup"><span data-stu-id="379e3-207">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="379e3-208">Devre dışı bırakılmış metin okumak daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="379e3-208">Disabled text is easier to read.</span></span> <span data-ttu-id="379e3-209">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="379e3-209">For example:</span></span>

    <span data-ttu-id="379e3-210">Sonra:</span><span class="sxs-lookup"><span data-stu-id="379e3-210">Before:</span></span>

    ![Erişilebilirlik geliştirmeleri önce devre dışı bırakılmış metin](media/wf-disabled-before.png) 

    <span data-ttu-id="379e3-212">Sonra:</span><span class="sxs-lookup"><span data-stu-id="379e3-212">After:</span></span>

    ![Devre dışı metinden sonra erişilebilirlik geliştirmeleri](media/wf-disabled-after.png) 

- <span data-ttu-id="379e3-214">İş parçacığı özel durum iletişim kutusunda yüksek karşıtlık geliştirmeleri.</span><span class="sxs-lookup"><span data-stu-id="379e3-214">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="379e3-215">**Ekran Okuyucusu için geliştirilmiş destek**</span><span class="sxs-lookup"><span data-stu-id="379e3-215">**Improved Narrator support**</span></span>

<span data-ttu-id="379e3-216">.NET Framework 4.7.1 Windows Forms'ta ekran okuyucusu için aşağıdaki erişilebilirlik geliştirmeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="379e3-216">Windows Forms in the .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="379e3-217"><xref:System.Windows.Forms.MonthCalendar> Denetimi, ekran okuyucusu tarafından yanı sıra diğer UI Otomasyon araçları tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="379e3-217">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="379e3-218"><xref:System.Windows.Forms.CheckedListBox> Denetim ekran okuyucusu kullanıcıya bir liste öğesinin değeri değiştirdiyseniz bildirimde şekilde öğenin onay durumu değiştiğinde bildirir.</span><span class="sxs-lookup"><span data-stu-id="379e3-218">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>
 
- <span data-ttu-id="379e3-219"><xref:System.Windows.Forms.DataGridViewCell> Denetim ekran okuyucusu için doğru salt okunur durumunu raporlar.</span><span class="sxs-lookup"><span data-stu-id="379e3-219">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>
 
- <span data-ttu-id="379e3-220">Ekran Okuyucusu şimdi devre dışı okuma <xref:System.Windows.Forms.ToolStripMenuItem> metin, daha önce devre dışı bırakılmış menü öğeleri üzerindeki Atla ancak.</span><span class="sxs-lookup"><span data-stu-id="379e3-220">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="379e3-221">**UIAutomation erişilebilirlik desenler için gelişmiş destek**</span><span class="sxs-lookup"><span data-stu-id="379e3-221">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="379e3-222">4.7.1 .NET Framework ile başlayarak, geliştiricilerin erişilebilirlik teknolojisinin Araçları'nın ortak API erişilebilirlik desenleri ve birden çok WinForms denetimi özelliklerini yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="379e3-222">Starting with the .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="379e3-223">Bu erişilebilirlik geliştirmeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="379e3-223">These accessibility improvements include:</span></span>

- <span data-ttu-id="379e3-224"><xref:System.Windows.Forms.ComboBox> Ve <xref:System.Windows.Forms.ToolStripSplitButton> şimdi destek [Genişlet/Daralt düzeni](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="379e3-224">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>
 
- <span data-ttu-id="379e3-225"><xref:System.Windows.Forms.DataGridViewCheckBoxCell> Artık destekliyor [değiştirme düzenini](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="379e3-225">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>
 
- <span data-ttu-id="379e3-226"><xref:System.Windows.Forms.ToolStripItem> Kontrol destekler <xref:System.Windows.Automation.AutomationElement.Name> özelliği ve [Genişlet/Daralt düzeni](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="379e3-226">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="379e3-227"><xref:System.Windows.Forms.NumericUpDown> Ve <xref:System.Windows.Forms.DomainUpDown> denetimleri Destek <xref:System.Windows.Automation.automationElement.Name> özelliği.</span><span class="sxs-lookup"><span data-stu-id="379e3-227">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.automationElement.Name> property.</span></span>

<span data-ttu-id="379e3-228">**Geliştirilmiş özellik tarayıcı deneyimi**</span><span class="sxs-lookup"><span data-stu-id="379e3-228">**Improved property browser experience**</span></span>

<span data-ttu-id="379e3-229">.NET Framework 4.7.1 ile başlayarak, Windows Forms içerir:</span><span class="sxs-lookup"><span data-stu-id="379e3-229">Starting with the .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="379e3-230">Daha iyi klavye gezinmesi çeşitli aşağı açılan seçimi windows sağlar.</span><span class="sxs-lookup"><span data-stu-id="379e3-230">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="379e3-231">Gereksiz sekme durakları azaltma.</span><span class="sxs-lookup"><span data-stu-id="379e3-231">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="379e3-232">Daha iyi denetim türlerini raporlama.</span><span class="sxs-lookup"><span data-stu-id="379e3-232">Better reporting of control types.</span></span>
- <span data-ttu-id="379e3-233">Gelişmiş ekran okuyucusu davranışı.</span><span class="sxs-lookup"><span data-stu-id="379e3-233">Improved narrator behavior.</span></span>
 
## <a name="see-also"></a><span data-ttu-id="379e3-234">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="379e3-234">See Also</span></span>
[<span data-ttu-id="379e3-235">.NET Framework'teki yenilikler</span><span class="sxs-lookup"><span data-stu-id="379e3-235">What's new in the .NET Framework</span></span>](whats-new.md)   
 