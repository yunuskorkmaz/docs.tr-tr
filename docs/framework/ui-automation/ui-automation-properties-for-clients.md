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
ms.openlocfilehash: 6f02a4825206da0dd4949083cc54f555a8ae40b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914453"
---
# <a name="ui-automation-properties-for-clients"></a>İstemciler İçin UI Otomasyon Özellikleri
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu genel bakış, Kullanıcı [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Arabirimi Otomasyonu istemci uygulamalarına sunulduklarında özellikleri size tanıtır.  
  
 Nesnelerdeki özellikler, genellikle denetimleri gibi [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] öğeler hakkında bilgiler içerir. <xref:System.Windows.Automation.AutomationElement> Öğesinin <xref:System.Windows.Automation.AutomationElement> özellikleri geneldir; diğer bir deyişle, bir denetim türüne özgü değildir. Bu özelliklerin birçoğu <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation> yapıda kullanıma sunulur.  
  
 Denetim desenleri de özelliklere sahiptir. Denetim desenlerinin özellikleri desenine özgüdür. Örneğin, <xref:System.Windows.Automation.ScrollPattern> bir istemci uygulamanın bir pencerenin dikey veya yatay kaydırılabilir olduğunu ve geçerli görünüm boyutları ile kaydırma konumlarını bulmasını sağlayan özellikleri vardır. Denetim desenleri, tüm özelliklerini bir yapı aracılığıyla kullanıma sunar; Örneğin, <xref:System.Windows.Automation.ScrollPattern.ScrollPatternInformation>.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özellikler salt okunurdur. Bir denetimin özelliklerini ayarlamak için uygun denetim deseninin yöntemlerini kullanmanız gerekir. Örneğin, bir kayan <xref:System.Windows.Automation.ScrollPattern.Scroll%2A> pencerenin konum değerlerini değiştirmek için kullanın.  
  
 Performansı artırmak için, denetimler ve denetim desenlerinin özellik değerleri, <xref:System.Windows.Automation.AutomationElement> nesneler alındığında önbelleğe alınabilir. Daha fazla bilgi için bkz. [UI Otomasyonu Istemcilerinde önbelleğe alma](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md).  
  
## <a name="property-ids"></a>Özellik kimlikleri  
 Özellik tanımlayıcıları (kimlikler), <xref:System.Windows.Automation.AutomationProperty> nesnelerde kapsüllenmiş benzersiz, sabit değerlerdir. UI Otomasyonu istemci uygulamaları, <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.ScrollPattern>bu kimlikleri sınıfından veya gibi uygun denetim deseninin sınıfından alır. UI Otomasyon sağlayıcıları, <xref:System.Windows.Automation.AutomationElementIdentifiers> <xref:System.Windows.Automation.ScrollPatternIdentifiers>gibi denetim deseninin tanımlayıcı sınıflarından veya bunlardan birinden alırlar.  
  
 , Yöntemi içinde<xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPropertyValue%2A?displayProperty=nameWithType> için sorgulanmakta olan özellikleri tanımlamak üzere sağlayıcılar tarafından kullanılır. <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> <xref:System.Windows.Automation.AutomationProperty> Genel olarak, istemci uygulamalarının ' i incelemesi <xref:System.Windows.Automation.AutomationIdentifier.Id%2A>gerekmez. <xref:System.Windows.Automation.AutomationIdentifier.ProgrammaticName%2A> Yalnızca hata ayıklama ve tanılama amaçları için kullanılır.  
  
## <a name="property-conditions"></a>Özellik koşulları  
 Özellik kimlikleri, nesneleri bulmak <xref:System.Windows.Automation.PropertyCondition> <xref:System.Windows.Automation.AutomationElement> için kullanılan nesneleri oluşturmak için kullanılır. Örneğin, belirli bir ada veya etkin olan tüm <xref:System.Windows.Automation.AutomationElement> denetimlere sahip olan bir öğesini bulmak isteyebilirsiniz. Her <xref:System.Windows.Automation.PropertyCondition> biri bir <xref:System.Windows.Automation.AutomationProperty> tanımlayıcıyı ve özelliğin eşleşmesi gereken değeri belirtir.  
  
 Daha fazla bilgi için aşağıdaki başvuru konularına bakın:  
  
- <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.FindAll%2A>  
  
- <xref:System.Windows.Automation.TreeWalker.Condition%2A>  
  
## <a name="retrieving-properties"></a>Özellikler alınıyor  
 Bir denetim model <xref:System.Windows.Automation.AutomationElement> sınıfının bazı özellikleri ve tüm özellikleri, <xref:System.Windows.Automation.AutomationElement> veya denetim deseninin nesnesinin `Current` veya `Cached` özelliğinin iç içe geçmiş özellikleri olarak sunulur.  
  
 Ayrıca, <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.AutomationElement.Cached%2A> veya yapısındakullanılamayanbirözellikdahilolmaküzereherhangibirveyadenetimdesenininözelliği,aşağıdakiyöntemlerdenbirikullanılarakalınabilir:<xref:System.Windows.Automation.AutomationElement.Current%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>  
  
 Bu yöntemler, özelliklerin tam aralığına erişimin yanı sıra biraz daha iyi performans sunar.  
  
 Aşağıdaki kod örneğinde, bir özelliği bir <xref:System.Windows.Automation.AutomationElement>üzerinde almanın iki yolu gösterilmektedir.  
  
 [!code-csharp[UIAClient_snip#121](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#121)]
 [!code-vb[UIAClient_snip#121](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#121)]  
  
 Tarafından <xref:System.Windows.Automation.AutomationElement>desteklenen denetim desenlerinin özelliklerini almak için denetim deseni nesnesini almanız gerekmez. Yalnızca bir model özelliği tanımlayıcılarından birini yönteme geçirin.  
  
 Aşağıdaki kod örneği, bir denetim düzenine bir özelliği almanın iki yolunu gösterir.  
  
 [!code-csharp[UIAClient_snip#122](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#122)]
 [!code-vb[UIAClient_snip#122](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#122)]  
  
 `Get` Yöntemler bir<xref:System.Object>döndürür. Uygulamanın, değeri kullanmadan önce döndürülen nesneyi doğru türe ataması gerekir.  
  
## <a name="default-property-values"></a>Varsayılan özellik değerleri  
 Bir UI Otomasyon sağlayıcısı bir özelliği uygulamadıysanız, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sistem varsayılan bir değer sağlayabilir. Örneğin, bir denetimin sağlayıcısı tarafından <xref:System.Windows.Automation.AutomationElement.HelpTextProperty>tanımlanan özelliği desteklemiyorsa, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] boş bir dize döndürür. Benzer şekilde, sağlayıcı tarafından <xref:System.Windows.Automation.AutomationElement.IsDockPatternAvailableProperty>tanımlanan özelliği desteklemiyorsa, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] döndürür `false`.  
  
 <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> Ve<xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> yöntem aşırı yüklerini kullanarak bu davranışı değiştirebilirsiniz. İkinci parametre olarak `true` belirttiğinizde, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] varsayılan bir değer döndürmez, ancak bunun yerine özel değeri <xref:System.Windows.Automation.AutomationElement.NotSupported>döndürür.  
  
 Aşağıdaki örnek kod bir öğesinden bir özelliği almaya çalışır ve özellik desteklenmiyorsa, bunun yerine uygulama tanımlı bir değer kullanılır.  
  
 [!code-csharp[UIAClient_snip#123](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#123)]
 [!code-vb[UIAClient_snip#123](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#123)]  
  
 Bir öğesi tarafından desteklenen özellikleri saptamak için kullanın <xref:System.Windows.Automation.AutomationElement.GetSupportedProperties%2A>. Bu, <xref:System.Windows.Automation.AutomationProperty> bir dizi tanımlayıcı döndürür.  
  
## <a name="property-changed-events"></a>Özellik değiştirme olayları  
 Bir <xref:System.Windows.Automation.AutomationElement> veya denetim deseninin Özellik değeri değiştiğinde bir olay tetiklenir. Bir uygulama <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>, bu tür olaylara abone olabilir ve ilgilendiğiniz özellikleri belirtmek için son <xref:System.Windows.Automation.AutomationProperty> parametre olarak bir dizi tanımlayıcı sağlar.  
  
 İçinde, olay bağımsız değişkenlerinin <xref:System.Windows.Automation.AutomationPropertyChangedEventArgs.Property%2A> üyesini denetleyerek değiştirilen özelliği belirleyebilirsiniz. <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler> Bağımsız değişkenler, değiştirilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliğinin eski ve yeni değerlerini de içerir. Bu değerler türündedir <xref:System.Object> ve kullanılmadan önce doğru türe yayınlanmalıdır.  
  
## <a name="additional-automationelement-properties"></a>Ek AutomationElement özellikleri  
 <xref:System.Windows.Automation.AutomationElement.Current%2A> <xref:System.Windows.Automation.AutomationElement> Ve özellikyapılarınaekolarak,basitözellikerişimcileriaracılığıylaalınanaşağıdakiözellikleresahiptir.<xref:System.Windows.Automation.AutomationElement.Cached%2A>  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Windows.Automation.AutomationElement.CachedChildren%2A>|Önbellekte olan alt <xref:System.Windows.Automation.AutomationElement> nesnelerin koleksiyonu.|  
|<xref:System.Windows.Automation.AutomationElement.CachedParent%2A>|Önbellekte <xref:System.Windows.Automation.AutomationElement> olan bir üst nesne.|  
|<xref:System.Windows.Automation.AutomationElement.FocusedElement%2A>|(Statik özellik) <xref:System.Windows.Automation.AutomationElement> Giriş odağa sahiptir.|  
|<xref:System.Windows.Automation.AutomationElement.RootElement%2A>|(Statik özellik) Kök <xref:System.Windows.Automation.AutomationElement>.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu İstemcilerinde Önbelleğe Alma](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
- [Sunucu Tarafı UI Otomasyonu Sağlayıcısı Uygulama](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
- [UI Otomasyonu Olaylarına Abone Olma](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md)
