---
title: "UI Otomasyon Özelliklerine Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, properties
- properties, UI Automation
ms.assetid: a6c31d7b-b33e-49b3-b5c1-31a345f9b7c8
caps.latest.revision: "17"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: a6fec422e235413bd76d86cdcb5a72a351bb3f97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ui-automation-properties-overview"></a><span data-ttu-id="1f215-102">UI Otomasyon Özelliklerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1f215-102">UI Automation Properties Overview</span></span>
> [!NOTE]
>  <span data-ttu-id="1f215-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="1f215-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="1f215-104">Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="1f215-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="1f215-105">UI Otomasyon sağlayıcılar üzerindeki özellikleri kullanıma [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] öğeleri.</span><span class="sxs-lookup"><span data-stu-id="1f215-105">UI Automation providers expose properties on [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements.</span></span> <span data-ttu-id="1f215-106">UI otomasyon istemci uygulamaları parçalarını hakkında bilgi bulmak bu özellikleri etkinleştirmek [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], özellikle, statik ve dinamik veriler de dahil olmak üzere kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="1f215-106">These properties enable UI Automation client applications to discover information about pieces of the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], especially controls, including both static and dynamic data.</span></span>  
  
 <span data-ttu-id="1f215-107">Bu bölümde geniş kapsamlı bir genel bakışını sunan [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] özellikleri.</span><span class="sxs-lookup"><span data-stu-id="1f215-107">This section gives a broad overview of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] properties.</span></span> <span data-ttu-id="1f215-108">Daha ayrıntılı bilgi aşağıdaki konularda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="1f215-108">More specific information is given in the following topics:</span></span>  
  
-   [<span data-ttu-id="1f215-109">İstemciler için UI Otomasyon özellikleri</span><span class="sxs-lookup"><span data-stu-id="1f215-109">UI Automation Properties for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)  
  
-   [<span data-ttu-id="1f215-110">Sunucu tarafı UI Otomasyon sağlayıcıyı uygulama</span><span class="sxs-lookup"><span data-stu-id="1f215-110">Server-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)  
  
<a name="Property_Identifiers"></a>   
## <a name="property-identifiers"></a><span data-ttu-id="1f215-111">Özellik tanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="1f215-111">Property Identifiers</span></span>  
 <span data-ttu-id="1f215-112">Her özellik, bir sayı ve bir ad tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="1f215-112">Every property is identified by a number and a name.</span></span> <span data-ttu-id="1f215-113">Özellik adlarını yalnızca hata ayıklama ve tanılama için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1f215-113">The names of properties are used only for debugging and diagnosis.</span></span> <span data-ttu-id="1f215-114">Sağlayıcıları kullanan sayısal [!INCLUDE[TLA2#tla_id#plural](../../../includes/tla2sharptla-idsharpplural-md.md)] gelen özellik istekleri belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="1f215-114">Providers use the numeric [!INCLUDE[TLA2#tla_id#plural](../../../includes/tla2sharptla-idsharpplural-md.md)] to identify incoming property requests.</span></span> <span data-ttu-id="1f215-115">İstemci uygulamaları, ancak yalnızca kullanmanız <xref:System.Windows.Automation.AutomationProperty>sayısını ve ad saklar, özellikleri belirlemek için alınacak istedikleri.</span><span class="sxs-lookup"><span data-stu-id="1f215-115">Client applications, however, only use <xref:System.Windows.Automation.AutomationProperty>, which encapsulates the number and name, to identify properties they wish to retrieve.</span></span>  
  
 <span data-ttu-id="1f215-116"><xref:System.Windows.Automation.AutomationProperty>belirli özellikleri temsil eden nesneler, çeşitli sınıfları alanlar olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1f215-116"><xref:System.Windows.Automation.AutomationProperty> objects representing particular properties are available as fields in various classes.</span></span> <span data-ttu-id="1f215-117">Güvenlik nedenleriyle, UI Otomasyon sağlayıcılar UIAutomationTypes.dll içinde bulunan sınıflar ayrı kümesinden bu nesneler edinin.</span><span class="sxs-lookup"><span data-stu-id="1f215-117">For security reasons, UI Automation providers obtain these objects from a separate set of classes that are contained in Uiautomationtypes.dll.</span></span>  
  
 <span data-ttu-id="1f215-118">Aşağıdaki tabloda özellikleri içeren sınıfları tarafından kategorilere ayıran <xref:System.Windows.Automation.AutomationProperty> [!INCLUDE[TLA2#tla_id#plural](../../../includes/tla2sharptla-idsharpplural-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1f215-118">The following table categorizes properties by the classes that contain the <xref:System.Windows.Automation.AutomationProperty>[!INCLUDE[TLA2#tla_id#plural](../../../includes/tla2sharptla-idsharpplural-md.md)].</span></span>  
  
|<span data-ttu-id="1f215-119">Tür özellikleri</span><span class="sxs-lookup"><span data-stu-id="1f215-119">Kinds of properties</span></span>|<span data-ttu-id="1f215-120">İstemcileri kimlikleri alma</span><span class="sxs-lookup"><span data-stu-id="1f215-120">Clients get IDs from</span></span>|<span data-ttu-id="1f215-121">Sağlayıcıları kimlikleri alma</span><span class="sxs-lookup"><span data-stu-id="1f215-121">Providers get IDs from</span></span>|  
|-------------------------|--------------------------|----------------------------|  
|<span data-ttu-id="1f215-122">Tüm öğeleri (tablolar aşağıdaki bakın) ortak özellikler</span><span class="sxs-lookup"><span data-stu-id="1f215-122">Properties common to all elements (see following tables)</span></span>|<xref:System.Windows.Automation.AutomationElement>|<xref:System.Windows.Automation.AutomationElementIdentifiers>|  
|<span data-ttu-id="1f215-123">Yerleşik bir pencere konumunu</span><span class="sxs-lookup"><span data-stu-id="1f215-123">Position of a docking window</span></span>|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.DockPatternIdentifiers>|  
|<span data-ttu-id="1f215-124">Öğenin genişletme ve daraltma durumu</span><span class="sxs-lookup"><span data-stu-id="1f215-124">State of an element that can expand and collapse</span></span>|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers>|  
|<span data-ttu-id="1f215-125">Bir kılavuzdaki bir öğenin özellikleri</span><span class="sxs-lookup"><span data-stu-id="1f215-125">Properties of an item in a grid</span></span>|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.GridItemPatternIdentifiers>|  
|<span data-ttu-id="1f215-126">Bir kılavuz özellikleri</span><span class="sxs-lookup"><span data-stu-id="1f215-126">Properties of a grid</span></span>|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.GridPatternIdentifiers>|  
|<span data-ttu-id="1f215-127">Birden çok görünüm olan bir öğeyi geçerli ve desteklenen görünümü</span><span class="sxs-lookup"><span data-stu-id="1f215-127">Current and supported view of an element that has multiple views</span></span>|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers>|  
|<span data-ttu-id="1f215-128">Bir kaydırıcının gibi değerleri aralığı üzerinden taşınan bir öğenin özellikleri</span><span class="sxs-lookup"><span data-stu-id="1f215-128">Properties of an element that moves over a range of values, such as a slider</span></span>|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.RangeValuePatternIdentifiers>|  
|<span data-ttu-id="1f215-129">Kayan bir pencere özellikleri</span><span class="sxs-lookup"><span data-stu-id="1f215-129">Properties of a scrolling window</span></span>|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.ScrollPatternIdentifiers>|  
|<span data-ttu-id="1f215-130">Durum ve kapsayıcı öğenin listesini olduğu gibi seçilebilir</span><span class="sxs-lookup"><span data-stu-id="1f215-130">Status and container of an item that can be selected, as in a list</span></span>|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers>|  
|<span data-ttu-id="1f215-131">Seçim öğelerini içeren bir denetim özellikleri</span><span class="sxs-lookup"><span data-stu-id="1f215-131">Properties of a control that contains selection items</span></span>|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.SelectionPatternIdentifiers>|  
|<span data-ttu-id="1f215-132">Bir öğenin bir tablodaki sütun ve satır başlıklarının</span><span class="sxs-lookup"><span data-stu-id="1f215-132">Column and row headers of an item in a table</span></span>|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.TableItemPatternIdentifiers>|  
|<span data-ttu-id="1f215-133">Sütun ve satır başlıklarının ve bir tablonun yönü</span><span class="sxs-lookup"><span data-stu-id="1f215-133">Column and row headers, and orientation, of a table</span></span>|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.TablePatternIdentifiers>|  
|<span data-ttu-id="1f215-134">İki durumlu düğme denetim durumu</span><span class="sxs-lookup"><span data-stu-id="1f215-134">State of a toggle control</span></span>|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.TogglePatternIdentifiers>|  
|<span data-ttu-id="1f215-135">Taşınabilir, bir öğenin özelliklerini Döndürülmüş veya yeniden boyutlandırılabilir</span><span class="sxs-lookup"><span data-stu-id="1f215-135">Capabilities of an element that can be moved, rotated, or resized</span></span>|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.TransformPatternIdentifiers>|  
|<span data-ttu-id="1f215-136">Değerine sahip bir öğenin değeri ve okuma/yazma özellikleri</span><span class="sxs-lookup"><span data-stu-id="1f215-136">Value and read/write capabilities of an element that has a value</span></span>|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.ValuePatternIdentifiers>|  
|<span data-ttu-id="1f215-137">Özellikleri ve bir pencere durumu</span><span class="sxs-lookup"><span data-stu-id="1f215-137">Capabilities and state of a window</span></span>|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.WindowPatternIdentifiers>|  
  
<a name="Properties_by_Category"></a>   
## <a name="properties-by-category"></a><span data-ttu-id="1f215-138">Kategoriye göre özellikleri</span><span class="sxs-lookup"><span data-stu-id="1f215-138">Properties by Category</span></span>  
 <span data-ttu-id="1f215-139">Aşağıdaki tablolarda özellikleri kategorilere ayırma, [!INCLUDE[TLA2#tla_id#plural](../../../includes/tla2sharptla-idsharpplural-md.md)] bulunan <xref:System.Windows.Automation.AutomationElement> ve <xref:System.Windows.Automation.AutomationElementIdentifiers>.</span><span class="sxs-lookup"><span data-stu-id="1f215-139">The following tables categorize the properties whose [!INCLUDE[TLA2#tla_id#plural](../../../includes/tla2sharptla-idsharpplural-md.md)] are found in <xref:System.Windows.Automation.AutomationElement> and <xref:System.Windows.Automation.AutomationElementIdentifiers>.</span></span> <span data-ttu-id="1f215-140">Bu özellikleri tüm denetimler için yaygındır.</span><span class="sxs-lookup"><span data-stu-id="1f215-140">These properties are common to all controls.</span></span> <span data-ttu-id="1f215-141">Birkaç tanesi dışındaki tüm sağlayıcısı uygulama ömrü boyunca statik büyük olasılıkla; Çoğu dinamik Özellikler Denetim düzenleri ile ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="1f215-141">All but a few of them are likely to be static over the lifetime of the provider application; most dynamic properties are associated with control patterns.</span></span>  
  
 <span data-ttu-id="1f215-142">**Özellik erişimi** sütunu ek olarak her bir özellik için başka bir erişimciler listeler <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> ve <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f215-142">The **Property Access** column lists any other accessors for each property, in addition to <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> and <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>.</span></span> <span data-ttu-id="1f215-143">Bir istemci uygulamasında özelliklerini alma ile ilgili daha fazla bilgi için bkz: [istemciler için UI Otomasyon özellikleri](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).</span><span class="sxs-lookup"><span data-stu-id="1f215-143">For more information on getting properties in a client application, see [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1f215-144">Her bir özellik hakkında ayrıntılı bilgi için bağlantıdaki izleyin **özellik erişimi** sütun.</span><span class="sxs-lookup"><span data-stu-id="1f215-144">For specific information about each property, follow the link in the **Property Access** column.</span></span>  
  
### <a name="display-characteristics"></a><span data-ttu-id="1f215-145">Görüntü Özellikleri</span><span class="sxs-lookup"><span data-stu-id="1f215-145">Display Characteristics</span></span>  
  
|<span data-ttu-id="1f215-146">Özellik tanımlayıcısı</span><span class="sxs-lookup"><span data-stu-id="1f215-146">Property identifier</span></span>|<span data-ttu-id="1f215-147">Özellik erişimi</span><span class="sxs-lookup"><span data-stu-id="1f215-147">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>|  
|<xref:System.Windows.Automation.AutomationElement.CultureProperty>|<span data-ttu-id="1f215-148">yok</span><span class="sxs-lookup"><span data-stu-id="1f215-148">n/a</span></span>|  
|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsOffscreen%2A>|  
|<xref:System.Windows.Automation.AutomationElement.OrientationProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Orientation%2A>|  
  
### <a name="element-type"></a><span data-ttu-id="1f215-149">Öğe türü</span><span class="sxs-lookup"><span data-stu-id="1f215-149">Element Type</span></span>  
  
|<span data-ttu-id="1f215-150">Özellik tanımlayıcısı</span><span class="sxs-lookup"><span data-stu-id="1f215-150">Property identifier</span></span>|<span data-ttu-id="1f215-151">Özellik erişimi</span><span class="sxs-lookup"><span data-stu-id="1f215-151">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsContentElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsControlElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LocalizedControlType%2A>|  
  
### <a name="identification"></a><span data-ttu-id="1f215-152">Tanımlama</span><span class="sxs-lookup"><span data-stu-id="1f215-152">Identification</span></span>  
  
|<span data-ttu-id="1f215-153">Özellik tanımlayıcısı</span><span class="sxs-lookup"><span data-stu-id="1f215-153">Property identifier</span></span>|<span data-ttu-id="1f215-154">Özellik erişimi</span><span class="sxs-lookup"><span data-stu-id="1f215-154">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClassNameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ClassName%2A>|  
|<xref:System.Windows.Automation.AutomationElement.FrameworkIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.FrameworkId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LabeledByProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LabeledBy%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ProcessIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ProcessId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.RuntimeIdProperty>|<xref:System.Windows.Automation.AutomationElement.GetRuntimeId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NativeWindowHandleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.NativeWindowHandle%2A>|  
  
### <a name="interaction"></a><span data-ttu-id="1f215-155">Etkileşim</span><span class="sxs-lookup"><span data-stu-id="1f215-155">Interaction</span></span>  
  
|<span data-ttu-id="1f215-156">Özellik tanımlayıcısı</span><span class="sxs-lookup"><span data-stu-id="1f215-156">Property identifier</span></span>|<span data-ttu-id="1f215-157">Özellik erişimi</span><span class="sxs-lookup"><span data-stu-id="1f215-157">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AcceleratorKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AccessKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>|<xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>|  
|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HasKeyboardFocus%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsEnabled%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsKeyboardFocusable%2A>|  
  
### <a name="support-for-patterns"></a><span data-ttu-id="1f215-158">Desenler için destek</span><span class="sxs-lookup"><span data-stu-id="1f215-158">Support for Patterns</span></span>  
  
|<span data-ttu-id="1f215-159">Özellik tanımlayıcısı</span><span class="sxs-lookup"><span data-stu-id="1f215-159">Property identifier</span></span>|<span data-ttu-id="1f215-160">Özellik erişimi</span><span class="sxs-lookup"><span data-stu-id="1f215-160">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsDockPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsExpandCollapsePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsGridItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsGridPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsInvokePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsMultipleViewPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsRangeValuePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsScrollItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsScrollPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsSelectionItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsSelectionPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTableItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTablePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTogglePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTransformPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsValuePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsWindowPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
  
### <a name="miscellaneous"></a><span data-ttu-id="1f215-161">Diğer</span><span class="sxs-lookup"><span data-stu-id="1f215-161">Miscellaneous</span></span>  
  
|<span data-ttu-id="1f215-162">Özellik tanımlayıcısı</span><span class="sxs-lookup"><span data-stu-id="1f215-162">Property identifier</span></span>|<span data-ttu-id="1f215-163">Özellik erişimi</span><span class="sxs-lookup"><span data-stu-id="1f215-163">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsRequiredForFormProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsRequiredForForm%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsPassword%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemStatusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemStatus%2A>|  
  
<a name="Localization"></a>   
## <a name="localization"></a><span data-ttu-id="1f215-164">Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="1f215-164">Localization</span></span>  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="1f215-165">Aşağıdaki özellikler işletim sisteminin dilinde sağlayıcılardan:</span><span class="sxs-lookup"><span data-stu-id="1f215-165"> providers should present the following properties in the language of the operating system:</span></span>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>  
  
<a name="Properties_and_Events"></a>   
## <a name="properties-and-events"></a><span data-ttu-id="1f215-166">Özellikleri ve olayları</span><span class="sxs-lookup"><span data-stu-id="1f215-166">Properties and Events</span></span>  
 <span data-ttu-id="1f215-167">Özelliklerinde oturum yakından bağlı [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değişti olayları kavramdır.</span><span class="sxs-lookup"><span data-stu-id="1f215-167">Closely tied in with the properties in [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is the concept of property-changed events.</span></span> <span data-ttu-id="1f215-168">Dinamik özellikler için istemci uygulaması bilgileri önbelleğini güncelleştirin veya başka bir şekilde yeni bilgilere tepki bir özellik değeri, değiştiğini bilmenin bir yolu gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="1f215-168">For dynamic properties, the client application needs a way to know that a property value has changed, so that it can update its cache of information or react to the new information in some other way.</span></span>  
  
 <span data-ttu-id="1f215-169">Sağlayıcıları olaylar şeyin zaman oluşturma [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="1f215-169">Providers raise events when something in the [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] changes.</span></span> <span data-ttu-id="1f215-170">Örneğin, bir onay kutusu seçili ya da işaretli bir özellik değişti olayı değiştirme düzenini sağlayıcının uygulaması tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1f215-170">For example, if a check box is selected or cleared, a property-changed event is raised by the provider's implementation of the Toggle pattern.</span></span> <span data-ttu-id="1f215-171">Sağlayıcıları olayları seçerek, veya bağlı olarak tüm istemcileri olaylar için dinleme, belirli olaylar için dinleme yükseltebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f215-171">Providers can raise events selectively, depending on whether any clients are listening for events, or listening for specific events.</span></span>  
  
 <span data-ttu-id="1f215-172">Tüm özellik değişikliği olayları Yükselt; öğesi için UI Otomasyon sağlayıcı uyarlamasını kadar tamamen olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="1f215-172">Not all property changes raise events; that is entirely up to the implementation of the UI Automation provider for the element.</span></span> <span data-ttu-id="1f215-173">Örneğin, standart proxy sağlayıcıları liste kutuları için bir olay yükseltmeyin zaman <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="1f215-173">For example, the standard proxy providers for list boxes do not raise an event when the <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> changes.</span></span> <span data-ttu-id="1f215-174">Bu durumda, uygulamanın yerine dinlemeye devam etmesi gereken bir <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>.</span><span class="sxs-lookup"><span data-stu-id="1f215-174">In this case, the application instead must listen for an <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>.</span></span>  
  
 <span data-ttu-id="1f215-175">İstemciler, bunlara abone olarak olaylarını dinler.</span><span class="sxs-lookup"><span data-stu-id="1f215-175">Clients listen for events by subscribing to them.</span></span> <span data-ttu-id="1f215-176">Olaylara abone olma anlamına olayları işlemek temsilci yöntemlerini oluşturma ve yöntemlere geçirme [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ile bu yöntemleri ele belirli olayları yanı sıra.</span><span class="sxs-lookup"><span data-stu-id="1f215-176">Subscribing to events means creating delegate methods that can handle the events, and then passing the methods to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] along with the specific events that will be dealt with in those methods.</span></span> <span data-ttu-id="1f215-177">Özellik değişti olayları için özel olarak, istemciler uygulamalıdır <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="1f215-177">For property-changed events in particular, clients must implement <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f215-178">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1f215-178">See Also</span></span>  
 [<span data-ttu-id="1f215-179">UI otomasyonda önbelleğe alma</span><span class="sxs-lookup"><span data-stu-id="1f215-179">Caching in UI Automation Clients</span></span>](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)  
 [<span data-ttu-id="1f215-180">İstemciler için UI Otomasyon özellikleri</span><span class="sxs-lookup"><span data-stu-id="1f215-180">UI Automation Properties for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)  
 [<span data-ttu-id="1f215-181">Sunucu tarafı UI Otomasyon sağlayıcıyı uygulama</span><span class="sxs-lookup"><span data-stu-id="1f215-181">Server-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)  
 [<span data-ttu-id="1f215-182">Özellik koşulunu temel alan UI Otomasyon öğesi bulma</span><span class="sxs-lookup"><span data-stu-id="1f215-182">Find a UI Automation Element Based on a Property Condition</span></span>](../../../docs/framework/ui-automation/find-a-ui-automation-element-based-on-a-property-condition.md)  
 [<span data-ttu-id="1f215-183">UI Otomasyon sağlayıcı dönüş özellikleri</span><span class="sxs-lookup"><span data-stu-id="1f215-183">Return Properties from a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/return-properties-from-a-ui-automation-provider.md)  
 [<span data-ttu-id="1f215-184">UI Otomasyon sağlayıcı olayları Yükselt</span><span class="sxs-lookup"><span data-stu-id="1f215-184">Raise Events from a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/raise-events-from-a-ui-automation-provider.md)
