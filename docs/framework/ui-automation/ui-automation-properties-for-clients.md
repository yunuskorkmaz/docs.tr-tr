---
title: İstemciler İçin UI Otomasyon Özellikleri
description: UI Automation istemci uygulamalarına sunulduklarında UI Otomasyon özelliklerine genel bakış konusunu okuyun.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, UI Automation clients
- UI Automation, client properties
ms.assetid: 255905af-0b17-485c-93d4-8a2db2a6524b
ms.openlocfilehash: fe78d7da154d79a5f66ee6c190b199065675841f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163137"
---
# <a name="ui-automation-properties-for-clients"></a>İstemciler İçin UI Otomasyon Özellikleri
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu genel bakış, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Kullanıcı Arabirimi Otomasyonu istemci uygulamalarına sunulduklarında özellikleri size tanıtır.  
  
 Nesnelerdeki Özellikler <xref:System.Windows.Automation.AutomationElement> [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] , genellikle denetimleri gibi öğeler hakkında bilgiler içerir. Öğesinin özellikleri <xref:System.Windows.Automation.AutomationElement> geneldir; diğer bir deyişle, bir denetim türüne özgü değildir. Bu özelliklerin birçoğu yapıda kullanıma sunulur <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation> .  
  
 Denetim desenleri de özelliklere sahiptir. Denetim desenlerinin özellikleri desenine özgüdür. Örneğin, <xref:System.Windows.Automation.ScrollPattern> bir istemci uygulamanın bir pencerenin dikey veya yatay kaydırılabilir olduğunu ve geçerli görünüm boyutları ile kaydırma konumlarını bulmasını sağlayan özellikleri vardır. Denetim desenleri, tüm özelliklerini bir yapı aracılığıyla kullanıma sunar; Örneğin, <xref:System.Windows.Automation.ScrollPattern.ScrollPatternInformation> .  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özellikler salt okunurdur. Bir denetimin özelliklerini ayarlamak için uygun denetim deseninin yöntemlerini kullanmanız gerekir. Örneğin, <xref:System.Windows.Automation.ScrollPattern.Scroll%2A> bir kayan pencerenin konum değerlerini değiştirmek için kullanın.  
  
 Performansı artırmak için, denetimler ve denetim desenlerinin özellik değerleri, <xref:System.Windows.Automation.AutomationElement> nesneler alındığında önbelleğe alınabilir. Daha fazla bilgi için bkz. [UI Otomasyonu Istemcilerinde önbelleğe alma](caching-in-ui-automation-clients.md).  
  
## <a name="property-ids"></a>Özellik kimlikleri  
 Özellik tanımlayıcıları (kimlikler), nesnelerde kapsüllenmiş benzersiz, sabit değerlerdir <xref:System.Windows.Automation.AutomationProperty> . UI Otomasyonu istemci uygulamaları, bu kimlikleri <xref:System.Windows.Automation.AutomationElement> sınıfından veya gibi uygun denetim deseninin sınıfından alır <xref:System.Windows.Automation.ScrollPattern> . UI Otomasyon sağlayıcıları <xref:System.Windows.Automation.AutomationElementIdentifiers> , gibi denetim deseninin tanımlayıcı sınıflarından veya bunlardan birinden alırlar <xref:System.Windows.Automation.ScrollPatternIdentifiers> .  
  
 , <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> <xref:System.Windows.Automation.AutomationProperty> Yöntemi içinde için sorgulanmakta olan özellikleri tanımlamak üzere sağlayıcılar tarafından kullanılır <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPropertyValue%2A?displayProperty=nameWithType> . Genel olarak, istemci uygulamalarının ' i incelemesi gerekmez <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> . <xref:System.Windows.Automation.AutomationIdentifier.ProgrammaticName%2A>Yalnızca hata ayıklama ve tanılama amaçları için kullanılır.  
  
## <a name="property-conditions"></a>Özellik koşulları  
 Özellik kimlikleri, <xref:System.Windows.Automation.PropertyCondition> nesneleri bulmak için kullanılan nesneleri oluşturmak için kullanılır <xref:System.Windows.Automation.AutomationElement> . Örneğin, <xref:System.Windows.Automation.AutomationElement> belirli bir ada veya etkin olan tüm denetimlere sahip olan bir öğesini bulmak isteyebilirsiniz. Her biri <xref:System.Windows.Automation.PropertyCondition> bir <xref:System.Windows.Automation.AutomationProperty> tanımlayıcıyı ve özelliğin eşleşmesi gereken değeri belirtir.  
  
 Daha fazla bilgi için aşağıdaki başvuru konularına bakın:  
  
- <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.FindAll%2A>  
  
- <xref:System.Windows.Automation.TreeWalker.Condition%2A>  
  
## <a name="retrieving-properties"></a>Özellikler alınıyor  
 <xref:System.Windows.Automation.AutomationElement>Bir denetim model sınıfının bazı özellikleri ve tüm özellikleri `Current` `Cached` , <xref:System.Windows.Automation.AutomationElement> veya denetim deseninin nesnesinin veya özelliğinin iç içe geçmiş özellikleri olarak sunulur.  
  
 Ayrıca, <xref:System.Windows.Automation.AutomationElement> veya yapısında kullanılamayan bir özellik dahil olmak üzere herhangi bir veya denetim deseninin özelliği, <xref:System.Windows.Automation.AutomationElement.Cached%2A> <xref:System.Windows.Automation.AutomationElement.Current%2A> aşağıdaki yöntemlerden biri kullanılarak alınabilir:  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>  
  
 Bu yöntemler, özelliklerin tam aralığına erişimin yanı sıra biraz daha iyi performans sunar.  
  
 Aşağıdaki kod örneğinde, bir özelliği bir üzerinde almanın iki yolu gösterilmektedir <xref:System.Windows.Automation.AutomationElement> .  
  
 [!code-csharp[UIAClient_snip#121](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#121)]
 [!code-vb[UIAClient_snip#121](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#121)]  
  
 Tarafından desteklenen denetim desenlerinin özelliklerini almak için <xref:System.Windows.Automation.AutomationElement> Denetim deseni nesnesini almanız gerekmez. Yalnızca bir model özelliği tanımlayıcılarından birini yönteme geçirin.  
  
 Aşağıdaki kod örneği, bir denetim düzenine bir özelliği almanın iki yolunu gösterir.  
  
 [!code-csharp[UIAClient_snip#122](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#122)]
 [!code-vb[UIAClient_snip#122](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#122)]  
  
 `Get`Yöntemler bir döndürür <xref:System.Object> . Uygulamanın, değeri kullanmadan önce döndürülen nesneyi doğru türe ataması gerekir.  
  
## <a name="default-property-values"></a>Varsayılan özellik değerleri  
 Bir UI Otomasyon sağlayıcısı bir özelliği uygulamadıysanız, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sistem varsayılan bir değer sağlayabilir. Örneğin, bir denetimin sağlayıcısı tarafından tanımlanan özelliği desteklemiyorsa <xref:System.Windows.Automation.AutomationElement.HelpTextProperty> , [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] boş bir dize döndürür. Benzer şekilde, sağlayıcı tarafından tanımlanan özelliği desteklemiyorsa <xref:System.Windows.Automation.AutomationElement.IsDockPatternAvailableProperty> , [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] döndürür `false` .  
  
 <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType>Ve yöntem aşırı yüklerini kullanarak bu davranışı değiştirebilirsiniz <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> . `true`İkinci parametre olarak belirttiğinizde, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] varsayılan bir değer döndürmez, ancak bunun yerine özel değeri döndürür <xref:System.Windows.Automation.AutomationElement.NotSupported> .  
  
 Aşağıdaki örnek kod bir öğesinden bir özelliği almaya çalışır ve özellik desteklenmiyorsa, bunun yerine uygulama tanımlı bir değer kullanılır.  
  
 [!code-csharp[UIAClient_snip#123](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#123)]
 [!code-vb[UIAClient_snip#123](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#123)]  
  
 Bir öğesi tarafından desteklenen özellikleri saptamak için kullanın <xref:System.Windows.Automation.AutomationElement.GetSupportedProperties%2A> . Bu, bir dizi <xref:System.Windows.Automation.AutomationProperty> tanımlayıcı döndürür.  
  
## <a name="property-changed-events"></a>Özellik değiştirme olayları  
 Bir veya denetim deseninin Özellik değeri değiştiğinde bir <xref:System.Windows.Automation.AutomationElement> olay tetiklenir. Bir uygulama, bu tür olaylara abone olabilir <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> ve <xref:System.Windows.Automation.AutomationProperty> ilgilendiğiniz özellikleri belirtmek için son parametre olarak bir dizi tanımlayıcı sağlar.  
  
 İçinde <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler> , <xref:System.Windows.Automation.AutomationPropertyChangedEventArgs.Property%2A> olay bağımsız değişkenlerinin üyesini denetleyerek değiştirilen özelliği belirleyebilirsiniz. Bağımsız değişkenler, değiştirilen özelliğinin eski ve yeni değerlerini de içerir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Bu değerler türündedir <xref:System.Object> ve kullanılmadan önce doğru türe yayınlanmalıdır.  
  
## <a name="additional-automationelement-properties"></a>Ek AutomationElement özellikleri  
 <xref:System.Windows.Automation.AutomationElement.Current%2A>Ve özellik yapılarına ek olarak <xref:System.Windows.Automation.AutomationElement.Cached%2A> , <xref:System.Windows.Automation.AutomationElement> basit özellik erişimcileri aracılığıyla alınan aşağıdaki özelliklere sahiptir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|<xref:System.Windows.Automation.AutomationElement.CachedChildren%2A>|Önbellekte olan alt <xref:System.Windows.Automation.AutomationElement> nesnelerin koleksiyonu.|  
|<xref:System.Windows.Automation.AutomationElement.CachedParent%2A>|<xref:System.Windows.Automation.AutomationElement>Önbellekte olan bir üst nesne.|  
|<xref:System.Windows.Automation.AutomationElement.FocusedElement%2A>|(Statik özellik) <xref:System.Windows.Automation.AutomationElement>Giriş odağa sahiptir.|  
|<xref:System.Windows.Automation.AutomationElement.RootElement%2A>|(Statik özellik) Kök <xref:System.Windows.Automation.AutomationElement> .|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonda Önbelleğe Alma](caching-in-ui-automation-clients.md)
- [Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Uygulama](server-side-ui-automation-provider-implementation.md)
- [UI Otomasyon Olaylarına Abone Olma](subscribe-to-ui-automation-events.md)
