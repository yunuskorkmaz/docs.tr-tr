---
title: UI Otomasyon Özelliklerine Genel Bakış
description: Bkz. Microsoft UI Otomasyon özelliklerine ilişkin geniş bir genel bakış. Özellik tanımlayıcıları, kategoriye göre özellikler, yerelleştirme ve Özellikler ve olaylar hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, properties
- properties, UI Automation
ms.assetid: a6c31d7b-b33e-49b3-b5c1-31a345f9b7c8
ms.openlocfilehash: 17d780c059530be8c91890302ea4066de2d4aa73
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163214"
---
# <a name="ui-automation-properties-overview"></a><span data-ttu-id="8d807-104">UI Otomasyon Özelliklerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8d807-104">UI Automation Properties Overview</span></span>
> [!NOTE]
> <span data-ttu-id="8d807-105">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="8d807-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="8d807-106">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="8d807-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="8d807-107">UI Otomasyon sağlayıcıları öğeleri üzerinde özellikler sunar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="8d807-107">UI Automation providers expose properties on [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements.</span></span> <span data-ttu-id="8d807-108">Bu özellikler, UI Otomasyonu istemci uygulamalarının [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] hem statik hem de dinamik veriler de dahil olmak üzere, özellikle denetimlerin parçaları hakkında bilgi bulmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8d807-108">These properties enable UI Automation client applications to discover information about pieces of the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], especially controls, including both static and dynamic data.</span></span>  
  
 <span data-ttu-id="8d807-109">Bu bölüm özelliklere kapsamlı bir genel bakış sunar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="8d807-109">This section gives a broad overview of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] properties.</span></span> <span data-ttu-id="8d807-110">Aşağıdaki konularda daha ayrıntılı bilgiler verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="8d807-110">More specific information is given in the following topics:</span></span>  
  
- [<span data-ttu-id="8d807-111">İstemciler İçin UI Otomasyon Özellikleri</span><span class="sxs-lookup"><span data-stu-id="8d807-111">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)  
  
- [<span data-ttu-id="8d807-112">Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Uygulama</span><span class="sxs-lookup"><span data-stu-id="8d807-112">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)  
  
<a name="Property_Identifiers"></a>
## <a name="property-identifiers"></a><span data-ttu-id="8d807-113">Özellik tanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="8d807-113">Property Identifiers</span></span>  
 <span data-ttu-id="8d807-114">Her özellik bir sayı ve bir ad ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="8d807-114">Every property is identified by a number and a name.</span></span> <span data-ttu-id="8d807-115">Özelliklerin adları yalnızca hata ayıklama ve Tanılama için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8d807-115">The names of properties are used only for debugging and diagnosis.</span></span> <span data-ttu-id="8d807-116">Sağlayıcılar gelen özellik isteklerini tanımlamak için sayısal kimlikleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="8d807-116">Providers use the numeric IDs to identify incoming property requests.</span></span> <span data-ttu-id="8d807-117">Ancak, istemci uygulamaları, <xref:System.Windows.Automation.AutomationProperty> almak istedikleri özellikleri tanımlamak için yalnızca sayıyı ve adı kapsülleyen kullanın.</span><span class="sxs-lookup"><span data-stu-id="8d807-117">Client applications, however, only use <xref:System.Windows.Automation.AutomationProperty>, which encapsulates the number and name, to identify properties they wish to retrieve.</span></span>  
  
 <span data-ttu-id="8d807-118"><xref:System.Windows.Automation.AutomationProperty>belirli özellikleri temsil eden nesneler çeşitli sınıflarda alanlar olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8d807-118"><xref:System.Windows.Automation.AutomationProperty> objects representing particular properties are available as fields in various classes.</span></span> <span data-ttu-id="8d807-119">Güvenlik nedenleriyle, UI Otomasyon sağlayıcıları bu nesneleri Uiautomationtypes.dll bulunan ayrı bir sınıf kümesinden alır.</span><span class="sxs-lookup"><span data-stu-id="8d807-119">For security reasons, UI Automation providers obtain these objects from a separate set of classes that are contained in Uiautomationtypes.dll.</span></span>  
  
 <span data-ttu-id="8d807-120">Aşağıdaki tablo, kimlikleri içeren sınıfların özelliklerini kategorilere ayırır <xref:System.Windows.Automation.AutomationProperty> .</span><span class="sxs-lookup"><span data-stu-id="8d807-120">The following table categorizes properties by the classes that contain the <xref:System.Windows.Automation.AutomationProperty>IDs.</span></span>  
  
|<span data-ttu-id="8d807-121">Özellik türleri</span><span class="sxs-lookup"><span data-stu-id="8d807-121">Kinds of properties</span></span>|<span data-ttu-id="8d807-122">İstemcilerin kimlikleri alması</span><span class="sxs-lookup"><span data-stu-id="8d807-122">Clients get IDs from</span></span>|<span data-ttu-id="8d807-123">Sağlayıcılar kimlik al</span><span class="sxs-lookup"><span data-stu-id="8d807-123">Providers get IDs from</span></span>|  
|-------------------------|--------------------------|----------------------------|  
|<span data-ttu-id="8d807-124">Tüm öğelerde ortak olan Özellikler (aşağıdaki tablolara bakın)</span><span class="sxs-lookup"><span data-stu-id="8d807-124">Properties common to all elements (see following tables)</span></span>|<xref:System.Windows.Automation.AutomationElement>|<xref:System.Windows.Automation.AutomationElementIdentifiers>|  
|<span data-ttu-id="8d807-125">Yerleştirme penceresinin konumu</span><span class="sxs-lookup"><span data-stu-id="8d807-125">Position of a docking window</span></span>|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.DockPatternIdentifiers>|  
|<span data-ttu-id="8d807-126">Genişleyebilir ve daraltılabilen bir öğenin durumu</span><span class="sxs-lookup"><span data-stu-id="8d807-126">State of an element that can expand and collapse</span></span>|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers>|  
|<span data-ttu-id="8d807-127">Kılavuzdaki bir öğenin özellikleri</span><span class="sxs-lookup"><span data-stu-id="8d807-127">Properties of an item in a grid</span></span>|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.GridItemPatternIdentifiers>|  
|<span data-ttu-id="8d807-128">Kılavuzun özellikleri</span><span class="sxs-lookup"><span data-stu-id="8d807-128">Properties of a grid</span></span>|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.GridPatternIdentifiers>|  
|<span data-ttu-id="8d807-129">Birden çok görünümü olan bir öğenin geçerli ve desteklenen görünümü</span><span class="sxs-lookup"><span data-stu-id="8d807-129">Current and supported view of an element that has multiple views</span></span>|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers>|  
|<span data-ttu-id="8d807-130">Kaydırıcı gibi bir değer aralığı üzerinde taşınan bir öğenin özellikleri</span><span class="sxs-lookup"><span data-stu-id="8d807-130">Properties of an element that moves over a range of values, such as a slider</span></span>|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.RangeValuePatternIdentifiers>|  
|<span data-ttu-id="8d807-131">Kaydırılan pencerenin özellikleri</span><span class="sxs-lookup"><span data-stu-id="8d807-131">Properties of a scrolling window</span></span>|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.ScrollPatternIdentifiers>|  
|<span data-ttu-id="8d807-132">Bir listede olduğu gibi, seçilebir öğenin durumu ve kapsayıcısı</span><span class="sxs-lookup"><span data-stu-id="8d807-132">Status and container of an item that can be selected, as in a list</span></span>|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers>|  
|<span data-ttu-id="8d807-133">Seçim öğelerini içeren bir denetimin özellikleri</span><span class="sxs-lookup"><span data-stu-id="8d807-133">Properties of a control that contains selection items</span></span>|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.SelectionPatternIdentifiers>|  
|<span data-ttu-id="8d807-134">Tablodaki bir öğenin sütun ve satır üst bilgileri</span><span class="sxs-lookup"><span data-stu-id="8d807-134">Column and row headers of an item in a table</span></span>|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.TableItemPatternIdentifiers>|  
|<span data-ttu-id="8d807-135">Bir tablonun sütun ve satır başlıkları ve yönü</span><span class="sxs-lookup"><span data-stu-id="8d807-135">Column and row headers, and orientation, of a table</span></span>|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.TablePatternIdentifiers>|  
|<span data-ttu-id="8d807-136">İki durumlu denetimin durumu</span><span class="sxs-lookup"><span data-stu-id="8d807-136">State of a toggle control</span></span>|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.TogglePatternIdentifiers>|  
|<span data-ttu-id="8d807-137">Taşınabilecek, döndürülebilen veya yeniden boyutlandırılan bir öğenin özellikleri</span><span class="sxs-lookup"><span data-stu-id="8d807-137">Capabilities of an element that can be moved, rotated, or resized</span></span>|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.TransformPatternIdentifiers>|  
|<span data-ttu-id="8d807-138">Değer içeren bir öğenin değeri ve okuma/yazma özellikleri</span><span class="sxs-lookup"><span data-stu-id="8d807-138">Value and read/write capabilities of an element that has a value</span></span>|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.ValuePatternIdentifiers>|  
|<span data-ttu-id="8d807-139">Pencerenin özellikleri ve durumu</span><span class="sxs-lookup"><span data-stu-id="8d807-139">Capabilities and state of a window</span></span>|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.WindowPatternIdentifiers>|  
  
<a name="Properties_by_Category"></a>
## <a name="properties-by-category"></a><span data-ttu-id="8d807-140">Kategoriye göre Özellikler</span><span class="sxs-lookup"><span data-stu-id="8d807-140">Properties by Category</span></span>  
 <span data-ttu-id="8d807-141">Aşağıdaki tablolar, kimlikleri ve içinde bulunan özellikleri sınıflandırmıştır <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.AutomationElementIdentifiers> .</span><span class="sxs-lookup"><span data-stu-id="8d807-141">The following tables categorize the properties whose IDs are found in <xref:System.Windows.Automation.AutomationElement> and <xref:System.Windows.Automation.AutomationElementIdentifiers>.</span></span> <span data-ttu-id="8d807-142">Bu özellikler tüm denetimlerde ortaktır.</span><span class="sxs-lookup"><span data-stu-id="8d807-142">These properties are common to all controls.</span></span> <span data-ttu-id="8d807-143">Ancak, bir kaç tane, sağlayıcı uygulamasının ömrü boyunca statik olması olasıdır; çoğu dinamik özellik denetim desenleriyle ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="8d807-143">All but a few of them are likely to be static over the lifetime of the provider application; most dynamic properties are associated with control patterns.</span></span>  
  
 <span data-ttu-id="8d807-144">**Özellik erişim** sütunu, ve ' a ek olarak her bir özellik için diğer erişimcileri <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> listeler <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> .</span><span class="sxs-lookup"><span data-stu-id="8d807-144">The **Property Access** column lists any other accessors for each property, in addition to <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> and <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>.</span></span> <span data-ttu-id="8d807-145">İstemci uygulamasında Özellikler alma hakkında daha fazla bilgi için bkz. [istemciler Için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).</span><span class="sxs-lookup"><span data-stu-id="8d807-145">For more information on getting properties in a client application, see [UI Automation Properties for Clients](ui-automation-properties-for-clients.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8d807-146">Her özellik hakkında belirli bilgiler için, **özellik erişim** sütunundaki bağlantıyı izleyin.</span><span class="sxs-lookup"><span data-stu-id="8d807-146">For specific information about each property, follow the link in the **Property Access** column.</span></span>  
  
### <a name="display-characteristics"></a><span data-ttu-id="8d807-147">Görüntü özellikleri</span><span class="sxs-lookup"><span data-stu-id="8d807-147">Display Characteristics</span></span>  
  
|<span data-ttu-id="8d807-148">Özellik tanımlayıcısı</span><span class="sxs-lookup"><span data-stu-id="8d807-148">Property identifier</span></span>|<span data-ttu-id="8d807-149">Özellik erişimi</span><span class="sxs-lookup"><span data-stu-id="8d807-149">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>|  
|<xref:System.Windows.Automation.AutomationElement.CultureProperty>|<span data-ttu-id="8d807-150">yok</span><span class="sxs-lookup"><span data-stu-id="8d807-150">n/a</span></span>|  
|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsOffscreen%2A>|  
|<xref:System.Windows.Automation.AutomationElement.OrientationProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Orientation%2A>|  
  
### <a name="element-type"></a><span data-ttu-id="8d807-151">Öğe türü</span><span class="sxs-lookup"><span data-stu-id="8d807-151">Element Type</span></span>  
  
|<span data-ttu-id="8d807-152">Özellik tanımlayıcısı</span><span class="sxs-lookup"><span data-stu-id="8d807-152">Property identifier</span></span>|<span data-ttu-id="8d807-153">Özellik erişimi</span><span class="sxs-lookup"><span data-stu-id="8d807-153">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsContentElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsControlElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LocalizedControlType%2A>|  
  
### <a name="identification"></a><span data-ttu-id="8d807-154">Kimlik</span><span class="sxs-lookup"><span data-stu-id="8d807-154">Identification</span></span>  
  
|<span data-ttu-id="8d807-155">Özellik tanımlayıcısı</span><span class="sxs-lookup"><span data-stu-id="8d807-155">Property identifier</span></span>|<span data-ttu-id="8d807-156">Özellik erişimi</span><span class="sxs-lookup"><span data-stu-id="8d807-156">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClassNameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ClassName%2A>|  
|<xref:System.Windows.Automation.AutomationElement.FrameworkIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.FrameworkId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LabeledByProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LabeledBy%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ProcessIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ProcessId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.RuntimeIdProperty>|<xref:System.Windows.Automation.AutomationElement.GetRuntimeId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NativeWindowHandleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.NativeWindowHandle%2A>|  
  
### <a name="interaction"></a><span data-ttu-id="8d807-157">Etkileşim</span><span class="sxs-lookup"><span data-stu-id="8d807-157">Interaction</span></span>  
  
|<span data-ttu-id="8d807-158">Özellik tanımlayıcısı</span><span class="sxs-lookup"><span data-stu-id="8d807-158">Property identifier</span></span>|<span data-ttu-id="8d807-159">Özellik erişimi</span><span class="sxs-lookup"><span data-stu-id="8d807-159">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AcceleratorKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AccessKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>|<xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>|  
|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HasKeyboardFocus%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsEnabled%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsKeyboardFocusable%2A>|  
  
### <a name="support-for-patterns"></a><span data-ttu-id="8d807-160">Desenler için destek</span><span class="sxs-lookup"><span data-stu-id="8d807-160">Support for Patterns</span></span>  
  
|<span data-ttu-id="8d807-161">Özellik tanımlayıcısı</span><span class="sxs-lookup"><span data-stu-id="8d807-161">Property identifier</span></span>|<span data-ttu-id="8d807-162">Özellik erişimi</span><span class="sxs-lookup"><span data-stu-id="8d807-162">Property access</span></span>|  
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
  
### <a name="miscellaneous"></a><span data-ttu-id="8d807-163">Çeşitli</span><span class="sxs-lookup"><span data-stu-id="8d807-163">Miscellaneous</span></span>  
  
|<span data-ttu-id="8d807-164">Özellik tanımlayıcısı</span><span class="sxs-lookup"><span data-stu-id="8d807-164">Property identifier</span></span>|<span data-ttu-id="8d807-165">Özellik erişimi</span><span class="sxs-lookup"><span data-stu-id="8d807-165">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsRequiredForFormProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsRequiredForForm%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsPassword%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemStatusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemStatus%2A>|  
  
<a name="Localization"></a>
## <a name="localization"></a><span data-ttu-id="8d807-166">Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="8d807-166">Localization</span></span>  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="8d807-167">sağlayıcılar, işletim sisteminin dilinde aşağıdaki özellikleri sunmalıdır:</span><span class="sxs-lookup"><span data-stu-id="8d807-167">providers should present the following properties in the language of the operating system:</span></span>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>  
  
<a name="Properties_and_Events"></a>
## <a name="properties-and-events"></a><span data-ttu-id="8d807-168">Özellikler ve olaylar</span><span class="sxs-lookup"><span data-stu-id="8d807-168">Properties and Events</span></span>  
 <span data-ttu-id="8d807-169">İçindeki özellikleriyle yakından birlikte, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değiştirme olaylarının kavramıdır.</span><span class="sxs-lookup"><span data-stu-id="8d807-169">Closely tied in with the properties in [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is the concept of property-changed events.</span></span> <span data-ttu-id="8d807-170">Dinamik özellikler için, istemci uygulamanın bir özellik değerinin değiştiğini bilmesi için bir yol gerekir, böylece bilgi önbelleğini güncelleştirebilir veya yeni bilgilere başka bir şekilde tepki verebilir.</span><span class="sxs-lookup"><span data-stu-id="8d807-170">For dynamic properties, the client application needs a way to know that a property value has changed, so that it can update its cache of information or react to the new information in some other way.</span></span>  
  
 <span data-ttu-id="8d807-171">Sağlayıcılar, değişikliklere bir şeyler olduğunda olaylar yükseltir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="8d807-171">Providers raise events when something in the [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] changes.</span></span> <span data-ttu-id="8d807-172">Örneğin, bir onay kutusu seçiliyse veya silinirse, sağlayıcının Iki durumlu düzenin uygulamasıyla bir özellik değiştirildi olayı tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="8d807-172">For example, if a check box is selected or cleared, a property-changed event is raised by the provider's implementation of the Toggle pattern.</span></span> <span data-ttu-id="8d807-173">Sağlayıcılar, herhangi bir istemcinin olayları dinleyip dinlemediğini veya belirli olayları dinlemediğine bağlı olarak olayları seçerek oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="8d807-173">Providers can raise events selectively, depending on whether any clients are listening for events, or listening for specific events.</span></span>  
  
 <span data-ttu-id="8d807-174">Tüm özellik değişiklikleri olay oluşturmaz; Bu, öğesi için UI Otomasyon sağlayıcısının uygulamasına tamamıyla çalışır.</span><span class="sxs-lookup"><span data-stu-id="8d807-174">Not all property changes raise events; that is entirely up to the implementation of the UI Automation provider for the element.</span></span> <span data-ttu-id="8d807-175">Örneğin, liste kutuları için standart ara sunucu sağlayıcıları, değişiklikler sırasında bir olay oluşturmaz <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> .</span><span class="sxs-lookup"><span data-stu-id="8d807-175">For example, the standard proxy providers for list boxes do not raise an event when the <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> changes.</span></span> <span data-ttu-id="8d807-176">Bu durumda, bunun yerine uygulamanın dinlemesi gerekir <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent> .</span><span class="sxs-lookup"><span data-stu-id="8d807-176">In this case, the application instead must listen for an <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>.</span></span>  
  
 <span data-ttu-id="8d807-177">İstemciler bu olaylara abone olarak olay dinler.</span><span class="sxs-lookup"><span data-stu-id="8d807-177">Clients listen for events by subscribing to them.</span></span> <span data-ttu-id="8d807-178">Olaylara abone olmak, olayları işleyebilen temsilci yöntemleri oluşturma ve ardından yöntemlerini [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Bu yöntemlerle ele alacak belirli olaylarla birlikte geçirme anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8d807-178">Subscribing to events means creating delegate methods that can handle the events, and then passing the methods to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] along with the specific events that will be dealt with in those methods.</span></span> <span data-ttu-id="8d807-179">Özellikle, özellik tarafından değiştirilen olaylar için, istemcilerin uygulaması gerekir <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler> .</span><span class="sxs-lookup"><span data-stu-id="8d807-179">For property-changed events in particular, clients must implement <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d807-180">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d807-180">See also</span></span>

- [<span data-ttu-id="8d807-181">UI Otomasyonda Önbelleğe Alma</span><span class="sxs-lookup"><span data-stu-id="8d807-181">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
- [<span data-ttu-id="8d807-182">İstemciler İçin UI Otomasyon Özellikleri</span><span class="sxs-lookup"><span data-stu-id="8d807-182">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)
- [<span data-ttu-id="8d807-183">Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Uygulama</span><span class="sxs-lookup"><span data-stu-id="8d807-183">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
- [<span data-ttu-id="8d807-184">Özellik Koşulunu Temel Alan UI Otomasyon Öğesi Bulma</span><span class="sxs-lookup"><span data-stu-id="8d807-184">Find a UI Automation Element Based on a Property Condition</span></span>](find-a-ui-automation-element-based-on-a-property-condition.md)
- [<span data-ttu-id="8d807-185">UI Otomasyon Sağlayıcı Dönüş Özellikleri</span><span class="sxs-lookup"><span data-stu-id="8d807-185">Return Properties from a UI Automation Provider</span></span>](return-properties-from-a-ui-automation-provider.md)
- [<span data-ttu-id="8d807-186">UI Otomasyon Sağlayıcıda Olay Tetikleme</span><span class="sxs-lookup"><span data-stu-id="8d807-186">Raise Events from a UI Automation Provider</span></span>](raise-events-from-a-ui-automation-provider.md)
