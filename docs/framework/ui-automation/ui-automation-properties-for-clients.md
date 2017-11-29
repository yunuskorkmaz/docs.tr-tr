---
title: "İstemciler İçin UI Otomasyon Özellikleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, UI Automation clients
- UI Automation, client properties
ms.assetid: 255905af-0b17-485c-93d4-8a2db2a6524b
caps.latest.revision: "17"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 0c9a007d88189172e6331c6876f2a18f341cd5cc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ui-automation-properties-for-clients"></a>İstemciler İçin UI Otomasyon Özellikleri
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu genel bakışta size tanıtır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri UI otomasyon istemci uygulamaları için sunulan gibi.  
  
 Özellikleri <xref:System.Windows.Automation.AutomationElement> nesneleri hakkında bilgi içeren [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] öğeleri, genellikle denetimleri. Özelliklerini bir <xref:System.Windows.Automation.AutomationElement> olan genel; olduğundan, bir denetim türü için belirli. Bu özelliklerin çoğu sunulan <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation> yapısı.  
  
 Denetim desenleri de özelliklere sahiptir. Denetim desenleri özelliklerini desen özgüdür. Örneğin, <xref:System.Windows.Automation.ScrollPattern> bir pencere dikey veya yatay olarak kaydırılabilir olup ve geçerli görünümü boyutları ve kaydırma konumlar neler olduğunu bulmak bir istemci uygulamasını etkinleştirecek özelliklere sahiptir. Denetim desenleri tüm özelliklerinin bir yapı aracılığıyla kullanıma; Örneğin, <xref:System.Windows.Automation.ScrollPattern.ScrollPatternInformation>.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]özellikleri salt okunurdur. Bir denetimin özelliklerini ayarlamak için uygun denetim düzeni yöntemlerini kullanmanız gerekir. Örneğin, <xref:System.Windows.Automation.ScrollPattern.Scroll%2A> kayan bir pencere konumunu değerlerini değiştirmek için.  
  
 Performans, özellik değerlerini denetimler ve denetim desenlerini geliştirmek için ne zaman önbelleğe alınabilir <xref:System.Windows.Automation.AutomationElement> nesneleri alınır. Daha fazla bilgi için bkz: [UI otomasyonda önbelleğe alma](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md).  
  
<a name="Property_IDs"></a>   
## <a name="property-ids"></a>Özellik kimlikleri  
 Özellik [!INCLUDE[TLA#tla_id#plural](../../../includes/tlasharptla-idsharpplural-md.md)] içinde kapsüllenmiş benzersiz, sabit değerler <xref:System.Windows.Automation.AutomationProperty> nesneleri. UI Otomasyonu istemci uygulamalarının bu alma [!INCLUDE[TLA2#tla_id#plural](../../../includes/tla2sharptla-idsharpplural-md.md)] gelen <xref:System.Windows.Automation.AutomationElement> sınıf veya uygun düzeni sınıfı gibi denetim <xref:System.Windows.Automation.ScrollPattern>. UI Otomasyon sağlayıcıları Al onlardan <xref:System.Windows.Automation.AutomationElementIdentifiers> veya denetim birinden gibi tanımlayıcıları sınıfların desen <xref:System.Windows.Automation.ScrollPatternIdentifiers>.  
  
 Sayısal <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> , bir <xref:System.Windows.Automation.AutomationProperty> sağlayıcıları tarafından için de sorgulanan özelliklerini tanımlamak için kullanılan <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPropertyValue%2A?displayProperty=nameWithType> yöntemi. Genel olarak, istemci uygulamaları inceleyin gerekmez <xref:System.Windows.Automation.AutomationIdentifier.Id%2A>. <xref:System.Windows.Automation.AutomationIdentifier.ProgrammaticName%2A> Yalnızca hata ayıklama ve tanılama amaçları için kullanılır.  
  
<a name="Property_Conditions"></a>   
## <a name="property-conditions"></a>Özellik koşulları  
 Özellik [!INCLUDE[TLA2#tla_id#plural](../../../includes/tla2sharptla-idsharpplural-md.md)] oluştururken kullanılan <xref:System.Windows.Automation.PropertyCondition> nesneleri bulmak için kullanılan <xref:System.Windows.Automation.AutomationElement> nesneleri. Örneğin, bulmak istediğiniz bir <xref:System.Windows.Automation.AutomationElement> belirli bir ad ya da etkin tüm denetimler içeriyor. Her <xref:System.Windows.Automation.PropertyCondition> belirten bir <xref:System.Windows.Automation.AutomationProperty> tanımlayıcısı ve özellik eşleşmelidir bir değer.  
  
 Daha fazla bilgi için aşağıdaki başvuru konularına bakın:  
  
-   <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.FindAll%2A>  
  
-   <xref:System.Windows.Automation.TreeWalker.Condition%2A>  
  
<a name="Retrieving_Properties"></a>   
## <a name="retrieving-properties"></a>Özelliklerini alma  
 Bazı özellikleri <xref:System.Windows.Automation.AutomationElement> ve bir denetim düzeni sınıfın tüm özellikleri iç içe geçmiş özellikleri olarak sunulan `Current` veya `Cached` özelliği <xref:System.Windows.Automation.AutomationElement> veya denetim düzeni nesnesi.  
  
 Ayrıca, tüm <xref:System.Windows.Automation.AutomationElement> veya denetim deseni özelliği, kullanılabilir olmayan bir özellik de dahil olmak üzere, <xref:System.Windows.Automation.AutomationElement.Cached%2A> veya <xref:System.Windows.Automation.AutomationElement.Current%2A> yapısı, aşağıdaki yöntemlerden biri kullanılarak alınabilir:  
  
-   <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>  
  
 Bu yöntemler, özellikler tam aralığını erişimin yanı sıra biraz daha iyi performans sunar.  
  
 Aşağıdaki kod örneği üzerinde bir özellik alma iki yolunu gösterir bir <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIAClient_snip#121](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#121)]
 [!code-vb[UIAClient_snip#121](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#121)]  
  
 Denetim desenleri tarafından desteklenen özelliklerini almak için <xref:System.Windows.Automation.AutomationElement>, Denetim düzeni nesnesini almak gerekmez. Yalnızca bir desen özellik tanımlayıcılarının yönteme geçirin.  
  
 Aşağıdaki kod örneğinde bir denetim düzeni bir özellik alma iki yolunu gösterir.  
  
 [!code-csharp[UIAClient_snip#122](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#122)]
 [!code-vb[UIAClient_snip#122](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#122)]  
  
 `Get` Yöntemleri döndürür bir <xref:System.Object>. Uygulama, değer kullanmadan önce uygun türde döndürülen nesneyi dönüştürmeniz gerekir.  
  
<a name="_Default_Property_Values"></a>   
## <a name="default-property-values"></a>Varsayılan özellik değerleri  
 UI Otomasyon sağlayıcı bir özellik uygulamadığında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sistemidir varsayılan bir değer sağlamak kullanabilirsiniz. Örneğin, bir denetim için sağlayıcısı tarafından tanımlanan özelliğini desteklemiyorsa <xref:System.Windows.Automation.AutomationElement.HelpTextProperty>, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] boş bir dize döndürür. Benzer şekilde, sağlayıcı tarafından tanımlanan özelliğini desteklemiyor, <xref:System.Windows.Automation.AutomationElement.IsDockPatternAvailableProperty>, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] döndürür `false`.  
  
 Kullanarak bu davranışı değiştirebilirsiniz <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> ve <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> yöntemi aşırı. Belirttiğinizde `true` ikinci parametre olarak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] varsayılan bir değer döndürmüyor, ancak bunun yerine özel değer döndürüyor <xref:System.Windows.Automation.AutomationElement.NotSupported>.  
  
 Aşağıdaki örnek kod bir özelliği bir öğeyi almayı dener ve uygulama tanımlı bir değer özelliği desteklenmiyorsa, bunun yerine kullanılır.  
  
 [!code-csharp[UIAClient_snip#123](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#123)]
 [!code-vb[UIAClient_snip#123](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#123)]  
  
 Hangi özelliklerin bir öğesi tarafından desteklenen keşfetmek için <xref:System.Windows.Automation.AutomationElement.GetSupportedProperties%2A>. Bu bir dizi döndürür <xref:System.Windows.Automation.AutomationProperty> tanımlayıcıları.  
  
<a name="Property_changed_Events"></a>   
## <a name="property-changed-events"></a>Özellik değişti olayları  
 Bir özellik değeri, bir <xref:System.Windows.Automation.AutomationElement> veya denetim düzeni değişiklikleri, bir olay oluşturulur. Bir uygulama bu gibi olaylar çağırarak abone olabilirsiniz <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>, bir dizi sağladığını <xref:System.Windows.Automation.AutomationProperty> tanımlayıcılar ilgi özelliklerini belirtmek için son parametre olarak.  
  
 İçinde <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>, denetleyerek değişti özelliği tanımlayabilirsiniz <xref:System.Windows.Automation.AutomationPropertyChangedEventArgs.Property%2A> olay değişkenlerini üyesi. Bağımsız değişkenler de eski ve yeni değerlerini içeren [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değişti özelliği. Bu değerleri türlerinin <xref:System.Object> ve doğru kullanılmadan önce türe gerekir.  
  
<a name="Additional_AutomationElement_Properties"></a>   
## <a name="additional-automationelement-properties"></a>Ek AutomationElement özellikleri  
 Ek olarak <xref:System.Windows.Automation.AutomationElement.Current%2A> ve <xref:System.Windows.Automation.AutomationElement.Cached%2A> özelliği yapıları <xref:System.Windows.Automation.AutomationElement> basit özellik erişimcisi alınan aşağıdaki özelliklere sahiptir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Windows.Automation.AutomationElement.CachedChildren%2A>|Bir alt koleksiyonunu <xref:System.Windows.Automation.AutomationElement> önbelleğinde bulunan nesneleri.|  
|<xref:System.Windows.Automation.AutomationElement.CachedParent%2A>|Bir <xref:System.Windows.Automation.AutomationElement> önbelleğinde üst nesne.|  
|<xref:System.Windows.Automation.AutomationElement.FocusedElement%2A>|(Statik özelliği) <xref:System.Windows.Automation.AutomationElement> Giriş odağını sahip.|  
|<xref:System.Windows.Automation.AutomationElement.RootElement%2A>|(Statik özelliği) Kök <xref:System.Windows.Automation.AutomationElement>.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI otomasyonda önbelleğe alma](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)  
 [Sunucu tarafı UI Otomasyon sağlayıcıyı uygulama](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)  
 [UI Otomasyon olaylarına abone olma](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md)
