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
ms.openlocfilehash: 3ef1e7c6e21f30c5bdea096003f192c38059ab2e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441368"
---
# <a name="ui-automation-properties-for-clients"></a>İstemciler İçin UI Otomasyon Özellikleri
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu genel bakış, Kullanıcı Arabirimi Otomasyonu istemci uygulamalarına sunulduklarında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri tanıtır.  
  
 <xref:System.Windows.Automation.AutomationElement> nesnelerdeki özellikler, genellikle denetimleri olan [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] öğeler hakkında bilgiler içerir. <xref:System.Windows.Automation.AutomationElement> özellikleri geneldir; Yani, bir denetim türüne özgü değildir. Bu özelliklerin birçoğu <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation> yapısında kullanıma sunulur.  
  
 Denetim desenleri de özelliklere sahiptir. Denetim desenlerinin özellikleri desenine özgüdür. Örneğin <xref:System.Windows.Automation.ScrollPattern>, bir istemci uygulamanın bir pencerenin dikey veya yatay kaydırılabilir olduğunu ve geçerli görünüm boyutları ile kaydırma konumlarını bulmasını sağlayan özelliklere sahiptir. Denetim desenleri, tüm özelliklerini bir yapı aracılığıyla kullanıma sunar; Örneğin, <xref:System.Windows.Automation.ScrollPattern.ScrollPatternInformation>.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikler salt okunurdur. Bir denetimin özelliklerini ayarlamak için uygun denetim deseninin yöntemlerini kullanmanız gerekir. Örneğin, bir kayan pencerenin konum değerlerini değiştirmek için <xref:System.Windows.Automation.ScrollPattern.Scroll%2A> kullanın.  
  
 Performansı artırmak için, <xref:System.Windows.Automation.AutomationElement> nesneler alındığında denetimlerin ve denetim desenlerinin özellik değerleri önbelleğe alınabilir. Daha fazla bilgi için bkz. [UI Otomasyonu Istemcilerinde önbelleğe alma](caching-in-ui-automation-clients.md).  
  
## <a name="property-ids"></a>Özellik kimlikleri  
 Özellik tanımlayıcıları (kimlikler), <xref:System.Windows.Automation.AutomationProperty> nesnelerinde kapsüllenmiş benzersiz, sabit değerlerdir. UI Otomasyonu istemci uygulamaları, bu kimlikleri <xref:System.Windows.Automation.AutomationElement> sınıfından veya <xref:System.Windows.Automation.ScrollPattern>gibi uygun denetim deseninin sınıfından alırlar. UI Otomasyon sağlayıcıları, <xref:System.Windows.Automation.ScrollPatternIdentifiers>gibi denetim deseninin tanımlayıcı sınıflarından veya <xref:System.Windows.Automation.AutomationElementIdentifiers> onlardan alırlar.  
  
 Bir <xref:System.Windows.Automation.AutomationProperty> sayısal <xref:System.Windows.Automation.AutomationIdentifier.Id%2A>, sağlayıcılar tarafından <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPropertyValue%2A?displayProperty=nameWithType> yönteminde sorgulanmakta olan özellikleri belirlemek için kullanılır. Genel olarak, istemci uygulamalarının <xref:System.Windows.Automation.AutomationIdentifier.Id%2A>incelemesi gerekmez. <xref:System.Windows.Automation.AutomationIdentifier.ProgrammaticName%2A> yalnızca hata ayıklama ve tanılama amaçları için kullanılır.  
  
## <a name="property-conditions"></a>Özellik koşulları  
 Özellik kimlikleri, <xref:System.Windows.Automation.AutomationElement> nesneleri bulmak için kullanılan <xref:System.Windows.Automation.PropertyCondition> nesneleri oluşturmak için kullanılır. Örneğin, belirli bir ada veya etkin olan tüm denetimlere sahip bir <xref:System.Windows.Automation.AutomationElement> bulmak isteyebilirsiniz. Her <xref:System.Windows.Automation.PropertyCondition>, bir <xref:System.Windows.Automation.AutomationProperty> tanımlayıcıyı ve özelliğin eşleşmesi gereken değeri belirtir.  
  
 Daha fazla bilgi için aşağıdaki başvuru konularına bakın:  
  
- <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.FindAll%2A>  
  
- <xref:System.Windows.Automation.TreeWalker.Condition%2A>  
  
## <a name="retrieving-properties"></a>Özellikler alınıyor  
 <xref:System.Windows.Automation.AutomationElement> özellikleri ve bir denetim deseninin tüm özellikleri, <xref:System.Windows.Automation.AutomationElement> veya denetim deseninin nesnesinin `Current` veya `Cached` özelliğinin iç içe geçmiş özellikleri olarak sunulur.  
  
 Ayrıca, <xref:System.Windows.Automation.AutomationElement.Cached%2A> veya <xref:System.Windows.Automation.AutomationElement.Current%2A> yapısında kullanılamayan bir özellik dahil olmak üzere herhangi bir <xref:System.Windows.Automation.AutomationElement> veya denetim deseninin özelliği aşağıdaki yöntemlerden biri kullanılarak alınabilir:  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>  
  
 Bu yöntemler, özelliklerin tam aralığına erişimin yanı sıra biraz daha iyi performans sunar.  
  
 Aşağıdaki kod örneği, <xref:System.Windows.Automation.AutomationElement>bir özelliği almanın iki yolunu gösterir.  
  
 [!code-csharp[UIAClient_snip#121](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#121)]
 [!code-vb[UIAClient_snip#121](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#121)]  
  
 <xref:System.Windows.Automation.AutomationElement>tarafından desteklenen denetim desenlerinin özelliklerini almak için denetim deseni nesnesini almanız gerekmez. Yalnızca bir model özelliği tanımlayıcılarından birini yönteme geçirin.  
  
 Aşağıdaki kod örneği, bir denetim düzenine bir özelliği almanın iki yolunu gösterir.  
  
 [!code-csharp[UIAClient_snip#122](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#122)]
 [!code-vb[UIAClient_snip#122](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#122)]  
  
 `Get` yöntemleri bir <xref:System.Object>döndürür. Uygulamanın, değeri kullanmadan önce döndürülen nesneyi doğru türe ataması gerekir.  
  
## <a name="default-property-values"></a>Varsayılan özellik değerleri  
 Bir UI Otomasyon sağlayıcısı bir özelliği uygulamadıysanız, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sistem varsayılan bir değer sağlayabilir. Örneğin, bir denetimin sağlayıcısı <xref:System.Windows.Automation.AutomationElement.HelpTextProperty>tarafından tanımlanan özelliği desteklemiyorsa, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] boş bir dize döndürür. Benzer şekilde, sağlayıcı <xref:System.Windows.Automation.AutomationElement.IsDockPatternAvailableProperty>tarafından tanımlanan özelliği desteklemiyorsa, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] `false`döndürür.  
  
 <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> ve <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> yöntemi aşırı yüklerini kullanarak bu davranışı değiştirebilirsiniz. İkinci parametre olarak `true` belirttiğinizde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] varsayılan bir değer döndürmez, bunun yerine <xref:System.Windows.Automation.AutomationElement.NotSupported>özel değeri döndürür.  
  
 Aşağıdaki örnek kod bir öğesinden bir özelliği almaya çalışır ve özellik desteklenmiyorsa, bunun yerine uygulama tanımlı bir değer kullanılır.  
  
 [!code-csharp[UIAClient_snip#123](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#123)]
 [!code-vb[UIAClient_snip#123](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#123)]  
  
 Bir öğe tarafından desteklenen özellikleri saptamak için <xref:System.Windows.Automation.AutomationElement.GetSupportedProperties%2A>kullanın. Bu, <xref:System.Windows.Automation.AutomationProperty> tanımlayıcılarından oluşan bir dizi döndürür.  
  
## <a name="property-changed-events"></a>Özellik değiştirme olayları  
 Bir <xref:System.Windows.Automation.AutomationElement> veya denetim düzenindeki bir özellik değeri değiştiğinde bir olay tetiklenir. Bir uygulama, <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>çağırarak söz konusu olaylara abone olabilir ve ilgilendiğiniz özellikleri belirtmek için son parametre olarak bir dizi <xref:System.Windows.Automation.AutomationProperty> tanımlayıcısı sağlayabilir.  
  
 <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>, olay bağımsız değişkenlerinin <xref:System.Windows.Automation.AutomationPropertyChangedEventArgs.Property%2A> üyesini denetleyerek değiştirilen özelliği belirleyebilirsiniz. Bağımsız değişkenler, değişen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliğinin eski ve yeni değerlerini de içerir. Bu değerler <xref:System.Object> türündedir ve kullanılmadan önce doğru türe yayınlanmalıdır.  
  
## <a name="additional-automationelement-properties"></a>Ek AutomationElement özellikleri  
 <xref:System.Windows.Automation.AutomationElement.Current%2A> ve <xref:System.Windows.Automation.AutomationElement.Cached%2A> Özellik yapılarına ek olarak, <xref:System.Windows.Automation.AutomationElement> basit özellik erişimcileri aracılığıyla alınan aşağıdaki özelliklere sahiptir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Windows.Automation.AutomationElement.CachedChildren%2A>|Önbellekte olan bir alt <xref:System.Windows.Automation.AutomationElement> nesneleri koleksiyonu.|  
|<xref:System.Windows.Automation.AutomationElement.CachedParent%2A>|Önbellekte olan bir <xref:System.Windows.Automation.AutomationElement> üst nesnesi.|  
|<xref:System.Windows.Automation.AutomationElement.FocusedElement%2A>|(Statik özellik) Giriş odaklı <xref:System.Windows.Automation.AutomationElement>.|  
|<xref:System.Windows.Automation.AutomationElement.RootElement%2A>|(Statik özellik) Kök <xref:System.Windows.Automation.AutomationElement>.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu İstemcilerinde Önbelleğe Alma](caching-in-ui-automation-clients.md)
- [Sunucu Tarafı UI Otomasyonu Sağlayıcısı Uygulama](server-side-ui-automation-provider-implementation.md)
- [UI Otomasyonu Olaylarına Abone Olma](subscribe-to-ui-automation-events.md)
