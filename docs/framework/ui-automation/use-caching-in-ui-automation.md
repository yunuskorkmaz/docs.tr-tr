---
title: UI Otomasyonda Önbelleğe Almayı Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- caching, UI Automation
- UI Automation, caching
ms.assetid: ec722dff-6009-4279-b86a-e18d3fa94ebf
ms.openlocfilehash: 679192b611a423e095ee9acc956d247364940edf
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800802"
---
# <a name="use-caching-in-ui-automation"></a>UI Otomasyonda Önbelleğe Almayı Kullanma
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu bölümde, <xref:System.Windows.Automation.AutomationElement> özelliklerinin ve denetim desenlerinin önbelleğe alınmasının nasıl uygulanacağı gösterilmektedir.  
  
### <a name="activate-a-cache-request"></a>Önbellek Isteğini etkinleştirme  
  
1. Oluşturma bir <xref:System.Windows.Automation.CacheRequest>.  
  
2. <xref:System.Windows.Automation.CacheRequest.Add%2A>kullanarak önbelleğe almak için özellikleri ve desenleri belirtin.  
  
3. <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> özelliğini ayarlayarak önbelleğe alma kapsamını belirtin.  
  
4. <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> özelliğini ayarlayarak alt ağacın görünümünü belirtin.  
  
5. Nesnelere tam bir başvuru almadıkça verimliliği artırmak istiyorsanız, <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> özelliğini <xref:System.Windows.Automation.AutomationElementMode.None> olarak ayarlayın. (Bu, bu nesnelerden geçerli değerleri almayı olanaksız hale getirir.)  
  
6. `using` bloğunda <xref:System.Windows.Automation.CacheRequest.Activate%2A> kullanarak isteği etkinleştirin (Microsoft Visual Basic .NET 'te`Using`).  
  
 <xref:System.Windows.Automation.AutomationElement> nesneleri aldıktan veya olaylara abone olduktan sonra, <xref:System.Windows.Automation.CacheRequest.Pop%2A> kullanarak (<xref:System.Windows.Automation.CacheRequest.Push%2A> kullanıldıysa) veya <xref:System.Windows.Automation.CacheRequest.Activate%2A>tarafından oluşturulan nesneyi elden kaldırarak isteği devre dışı bırakın. (Microsoft Visual Basic .NET 'te <xref:System.Windows.Automation.CacheRequest.Activate%2A> `using` bloğunda kullanın (`Using`).  
  
### <a name="cache-automationelement-properties"></a>Önbellek AutomationElement özellikleri  
  
1. <xref:System.Windows.Automation.CacheRequest> etkinken, <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> veya <xref:System.Windows.Automation.AutomationElement.FindAll%2A>kullanarak <xref:System.Windows.Automation.AutomationElement> nesneleri elde edin; veya <xref:System.Windows.Automation.CacheRequest> etkinken için kaydettiğiniz bir olayın kaynağı olarak bir <xref:System.Windows.Automation.AutomationElement> edinin. (Ayrıca bir <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache 'e geçirerek veya <xref:System.Windows.Automation.TreeWalker> metotlarından birine bir önbellek oluşturabilirsiniz.)  
  
2. <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> kullanın veya <xref:System.Windows.Automation.AutomationElement><xref:System.Windows.Automation.AutomationElement.Cached%2A> özelliğinden bir özellik alın.  
  
### <a name="obtain-cached-patterns-and-their-properties"></a>Önbelleğe alınmış desenleri ve bunların özelliklerini alma  
  
1. <xref:System.Windows.Automation.CacheRequest> etkinken, <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> veya <xref:System.Windows.Automation.AutomationElement.FindAll%2A>kullanarak <xref:System.Windows.Automation.AutomationElement> nesneleri elde edin; veya <xref:System.Windows.Automation.CacheRequest> etkinken için kaydettiğiniz bir olayın kaynağı olarak bir <xref:System.Windows.Automation.AutomationElement> edinin. (Ayrıca bir <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache 'e geçirerek veya <xref:System.Windows.Automation.TreeWalker> metotlarından birine bir önbellek oluşturabilirsiniz.)  
  
2. Önbelleğe alınmış bir model almak için <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> veya <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> kullanın.  
  
3. Denetim deseninin `Cached` özelliğinden özellik değerlerini alın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, <xref:System.Windows.Automation.CacheRequest>etkinleştirmek için <xref:System.Windows.Automation.CacheRequest.Activate%2A> kullanarak önbelleğe alma işleminin çeşitli yönlerini gösterir.  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, <xref:System.Windows.Automation.CacheRequest>etkinleştirmek için <xref:System.Windows.Automation.CacheRequest.Push%2A> kullanarak önbelleğe alma işleminin çeşitli yönlerini gösterir. Önbellek isteklerini iç içe aktarmak istediğiniz durumlar dışında <xref:System.Windows.Automation.CacheRequest.Activate%2A>kullanmak tercih edilir.  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu İstemcilerinde Önbelleğe Alma](caching-in-ui-automation-clients.md)
