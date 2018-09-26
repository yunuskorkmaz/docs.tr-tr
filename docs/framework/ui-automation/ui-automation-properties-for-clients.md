---
title: İstemciler İçin UI Otomasyon Özellikleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, UI Automation clients
- UI Automation, client properties
ms.assetid: 255905af-0b17-485c-93d4-8a2db2a6524b
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 2e0c2764f96a2592ad0a4dfe5caa46536373eb80
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193284"
---
# <a name="ui-automation-properties-for-clients"></a>İstemciler İçin UI Otomasyon Özellikleri
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu genel bakışta, tanıtır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri için UI otomasyon istemci uygulamaları açık olarak.  
  
 Özelliklerde <xref:System.Windows.Automation.AutomationElement> nesneler hakkında bilgi içeren [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] öğeler, genellikle denetimleri. Özellikleri bir <xref:System.Windows.Automation.AutomationElement> olan genel; olan, bir denetim türü için belirli. Bu özelliklerin çoğu sunulan <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation> yapısı.  
  
 Denetim desenlerini özelliklere de sahiptir. Denetim desenlerini özelliklerini desen özgüdür. Örneğin, <xref:System.Windows.Automation.ScrollPattern> bir pencereyi yatay veya dikey olarak kaydırılabilir olup ve geçerli görünümü boyutları ve pozisyonları kaydırma nelerdir bulmak bir istemci uygulamanın sağlayan özellikleri vardır. Denetim desenlerini bir yapısı üzerinden tüm özellikleri açığa; Örneğin, <xref:System.Windows.Automation.ScrollPattern.ScrollPatternInformation>.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] salt okunur özelliklerdir. Bir denetimin özelliklerini ayarlamak için uygun denetim düzeni yöntemlerini kullanmanız gerekir. Örneğin, <xref:System.Windows.Automation.ScrollPattern.Scroll%2A> kayan pencere konumu değerleri değiştirmek için.  
  
 Performans, denetimler ve denetim düzenleri özellik değerlerini artırmak için ne zaman önbelleğe alınabilir <xref:System.Windows.Automation.AutomationElement> nesneleri alınır. Daha fazla bilgi için [UI otomasyonda önbelleğe alma](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md).  
  
<a name="Property_IDs"></a>   
## <a name="property-ids"></a>Özellik kimliği  
 Özellik [!INCLUDE[TLA#tla_id#plural](../../../includes/tlasharptla-idsharpplural-md.md)] içinde kapsanan benzersiz, sabit değerler <xref:System.Windows.Automation.AutomationProperty> nesneleri. UI Otomasyonu istemci uygulamaları bu alma [!INCLUDE[TLA2#tla_id#plural](../../../includes/tla2sharptla-idsharpplural-md.md)] gelen <xref:System.Windows.Automation.AutomationElement> sınıfı veya uygun desen sınıfı gibi denetim <xref:System.Windows.Automation.ScrollPattern>. UI Otomasyonu sağlayıcıları Al bunları <xref:System.Windows.Automation.AutomationElementIdentifiers> veya bir denetim noktasından tanımlayıcıları sınıflar gibi desen <xref:System.Windows.Automation.ScrollPatternIdentifiers>.  
  
 Sayısal <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> , bir <xref:System.Windows.Automation.AutomationProperty> sağlayıcıları tarafından için sorgulanan özellikleri tanımlamak için kullanılan <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPropertyValue%2A?displayProperty=nameWithType> yöntemi. Genel olarak, istemci uygulamaları incelemek gerekmez <xref:System.Windows.Automation.AutomationIdentifier.Id%2A>. <xref:System.Windows.Automation.AutomationIdentifier.ProgrammaticName%2A> Yalnızca hata ayıklama ve tanılama amacıyla kullanılır.  
  
<a name="Property_Conditions"></a>   
## <a name="property-conditions"></a>Özellik koşullarına  
 Özellik [!INCLUDE[TLA2#tla_id#plural](../../../includes/tla2sharptla-idsharpplural-md.md)] oluşturulmasında kullanılan <xref:System.Windows.Automation.PropertyCondition> bulmak için kullanılan nesneleri <xref:System.Windows.Automation.AutomationElement> nesneleri. Örneğin, bulmak istediğiniz bir <xref:System.Windows.Automation.AutomationElement> belirli bir ada veya etkinleştirilmiş olan tüm denetimler vardır. Her <xref:System.Windows.Automation.PropertyCondition> belirtir bir <xref:System.Windows.Automation.AutomationProperty> tanımlayıcısı ve özellik eşleşmelidir bir değer.  
  
 Daha fazla bilgi için aşağıdaki başvuru konularına bakın:  
  
-   <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.FindAll%2A>  
  
-   <xref:System.Windows.Automation.TreeWalker.Condition%2A>  
  
<a name="Retrieving_Properties"></a>   
## <a name="retrieving-properties"></a>Özellikleri alınıyor  
 Bazı özellikleri <xref:System.Windows.Automation.AutomationElement> ve tüm özelliklerinin bir denetim düzeni sınıfı iç içe özellikleri olarak gösterilen `Current` veya `Cached` özelliği <xref:System.Windows.Automation.AutomationElement> veya denetim düzeni nesnesi.  
  
 Ayrıca, tüm <xref:System.Windows.Automation.AutomationElement> veya denetim düzeni özelliği bulunmayan bir özelliği de dahil olmak üzere, <xref:System.Windows.Automation.AutomationElement.Cached%2A> veya <xref:System.Windows.Automation.AutomationElement.Current%2A> yapısı, aşağıdaki yöntemlerden biri kullanılarak alınabilir:  
  
-   <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>  
  
 Bu yöntemlerin, özelliklerin tam aralığına erişimin yanı sıra biraz daha iyi performans sunar.  
  
 Aşağıdaki kod örneği üzerinde bir özelliği almanın iki yolu gösteren bir <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIAClient_snip#121](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#121)]
 [!code-vb[UIAClient_snip#121](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#121)]  
  
 Tarafından desteklenen denetim düzenleri özelliklerini almak için <xref:System.Windows.Automation.AutomationElement>, Denetim düzeni nesneyi almak gerekmez. Yalnızca bir desen özellik tanımlayıcılarının yönteme geçirin.  
  
 Aşağıdaki kod örneği, bir denetim düzeni özellik alma iki yolunu gösterir.  
  
 [!code-csharp[UIAClient_snip#122](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#122)]
 [!code-vb[UIAClient_snip#122](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#122)]  
  
 `Get` Yöntemleri döndürür bir <xref:System.Object>. Uygulama, değer kullanmadan önce döndürülen nesneyi doğru türe dönüştürmeniz gerekir.  
  
<a name="_Default_Property_Values"></a>   
## <a name="default-property-values"></a>Varsayılan özellik değerleri  
 UI Otomasyon sağlayıcısında bir özellik uygulamıyorsa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sistemidir varsayılan değeri sağlamak kullanabilirsiniz. Örneğin, bir denetim için sağlayıcı tarafından tanımlanan özelliğini desteklemiyorsa <xref:System.Windows.Automation.AutomationElement.HelpTextProperty>, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] boş bir dize döndürür. Benzer şekilde, sağlayıcı tarafından tanımlanan özelliğini desteklemiyor, <xref:System.Windows.Automation.AutomationElement.IsDockPatternAvailableProperty>, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] döndürür `false`.  
  
 Kullanarak bu davranışı değiştirebilirsiniz <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> ve <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> yöntemi aşırı yüklemeleri. Belirttiğinizde `true` ikinci parametre olarak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] varsayılan bir değer döndürmez ama bunun yerine özel değeri döndürür <xref:System.Windows.Automation.AutomationElement.NotSupported>.  
  
 Aşağıdaki kod örneği, bir özelliği bir öğeyi almayı dener ve özelliği desteklenmiyor, bunun yerine bir uygulama tanımlı değeri kullanılır.  
  
 [!code-csharp[UIAClient_snip#123](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#123)]
 [!code-vb[UIAClient_snip#123](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#123)]  
  
 Hangi özellikler bir öğe tarafından desteklenen bulmak için kullanmak <xref:System.Windows.Automation.AutomationElement.GetSupportedProperties%2A>. Bu bir dizi döndürür <xref:System.Windows.Automation.AutomationProperty> tanımlayıcıları.  
  
<a name="Property_changed_Events"></a>   
## <a name="property-changed-events"></a>Özellik değişti olayları  
 Bir özellik değeri, bir <xref:System.Windows.Automation.AutomationElement> veya denetim desen değişiklikleri, bir olay oluşturulur. Çağırarak, bir uygulamanın böyle olaylara abone olabilirsiniz <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>, bir dizi sağlama <xref:System.Windows.Automation.AutomationProperty> tanımlayıcı ilgi özelliklerini belirtmek için son parametre olarak.  
  
 İçinde <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>, kontrol ederek değişen özelliği tanımlayabilirsiniz <xref:System.Windows.Automation.AutomationPropertyChangedEventArgs.Property%2A> olay bağımsız değişkenleri üyesi. Bağımsız değişkenler de eski ve yeni değerlerini içeren [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değişen özelliği. Bu değerler türünü <xref:System.Object> ve kullanılmadan önce doğru türe dönüştürmeniz gerekir.  
  
<a name="Additional_AutomationElement_Properties"></a>   
## <a name="additional-automationelement-properties"></a>Ek AutomationElement özellikleri  
 Ek olarak <xref:System.Windows.Automation.AutomationElement.Current%2A> ve <xref:System.Windows.Automation.AutomationElement.Cached%2A> özellik yapıları <xref:System.Windows.Automation.AutomationElement> basit özellik erişimcileri alınan aşağıdaki özelliklere sahiptir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Windows.Automation.AutomationElement.CachedChildren%2A>|Alt koleksiyonu <xref:System.Windows.Automation.AutomationElement> önbellekte olan nesneler.|  
|<xref:System.Windows.Automation.AutomationElement.CachedParent%2A>|Bir <xref:System.Windows.Automation.AutomationElement> , önbellekte üst nesne.|  
|<xref:System.Windows.Automation.AutomationElement.FocusedElement%2A>|(Statik özelliği) <xref:System.Windows.Automation.AutomationElement> Giriş odağı olan.|  
|<xref:System.Windows.Automation.AutomationElement.RootElement%2A>|(Statik özelliği) Kök <xref:System.Windows.Automation.AutomationElement>.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyonu İstemcilerinde Önbelleğe Alma](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)  
 [Sunucu Tarafı UI Otomasyonu Sağlayıcısı Uygulama](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)  
 [UI Otomasyonu Olaylarına Abone Olma](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md)
