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
ms.openlocfilehash: 38c7742f3e4691f29490e73b05616754415eac58
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953897"
---
# <a name="use-caching-in-ui-automation"></a>UI Otomasyonda Önbelleğe Almayı Kullanma
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu bölümde, <xref:System.Windows.Automation.AutomationElement> özelliklerin ve denetim desenlerinin önbelleğe alınmasının nasıl uygulanacağı gösterilmektedir.  
  
### <a name="activate-a-cache-request"></a>Önbellek Isteğini etkinleştirme  
  
1. Oluşturma bir <xref:System.Windows.Automation.CacheRequest>.  
  
2. Kullanarak <xref:System.Windows.Automation.CacheRequest.Add%2A>önbelleğe almak için özellikleri ve desenleri belirtin.  
  
3. <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> Özelliği ayarlayarak önbelleğe alma kapsamını belirtin.  
  
4. <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> Özelliği ayarlayarak alt ağacın görünümünü belirtin.  
  
5. Nesnelere tam <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> başvuru almadıkça verimliliği artırmak istiyorsanız, özelliğini olarak <xref:System.Windows.Automation.AutomationElementMode.None> ayarlayın. (Bu, bu nesnelerden geçerli değerleri almayı olanaksız hale getirir.)  
  
6. `Using` Bir <xref:System.Windows.Automation.CacheRequest.Activate%2A> blokiçinde`using` kullanarak isteği etkinleştirin (Microsoft Visual Basic .net 'te).  
  
 Nesneleri aldıktan <xref:System.Windows.Automation.AutomationElement> veya olaylara abone olduktan sonra <xref:System.Windows.Automation.CacheRequest.Pop%2A> ( <xref:System.Windows.Automation.CacheRequest.Push%2A> kullanıldıysa) veya tarafından <xref:System.Windows.Automation.CacheRequest.Activate%2A>oluşturulan nesneyi elden kaldırarak isteği devre dışı bırakın. (Bir <xref:System.Windows.Automation.CacheRequest.Activate%2A> `using` bloğunda kullanın (`Using` Microsoft Visual Basic .net 'te).  
  
### <a name="cache-automationelement-properties"></a>Önbellek AutomationElement özellikleri  
  
1. <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.CacheRequest> <xref:System.Windows.Automation.AutomationElement> Etkin olsa da, veya <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> kullanarak<xref:System.Windows.Automation.AutomationElement.FindAll%2A>nesneleri elde edin ya da, etkin olduğunda için kaydettiğiniz bir olayın kaynağı olarak elde edin. <xref:System.Windows.Automation.CacheRequest> (Bir <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache 'e veya <xref:System.Windows.Automation.TreeWalker> yöntemlerinden birine geçirerek de bir önbellek oluşturabilirsiniz.)  
  
2. Öğesinin <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> özelliğindenbir<xref:System.Windows.Automation.AutomationElement.Cached%2A> özelliği kullanın veya alın. <xref:System.Windows.Automation.AutomationElement>  
  
### <a name="obtain-cached-patterns-and-their-properties"></a>Önbelleğe alınmış desenleri ve bunların özelliklerini alma  
  
1. <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.CacheRequest> <xref:System.Windows.Automation.AutomationElement> Etkin olsa da, veya <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> kullanarak<xref:System.Windows.Automation.AutomationElement.FindAll%2A>nesneleri elde edin ya da, etkin olduğunda için kaydettiğiniz bir olayın kaynağı olarak elde edin. <xref:System.Windows.Automation.CacheRequest> (Bir <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache 'e veya <xref:System.Windows.Automation.TreeWalker> yöntemlerinden birine geçirerek de bir önbellek oluşturabilirsiniz.)  
  
2. Önbelleğe <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> alınmış <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> bir model almak için veya kullanın.  
  
3. Denetim deseninin `Cached` özelliğinden özellik değerlerini alın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, öğesini <xref:System.Windows.Automation.CacheRequest.Activate%2A> <xref:System.Windows.Automation.CacheRequest>etkinleştirmek için kullanarak, önbelleğe alma işleminin çeşitli yönlerini gösterir.  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, öğesini <xref:System.Windows.Automation.CacheRequest.Push%2A> <xref:System.Windows.Automation.CacheRequest>etkinleştirmek için kullanarak, önbelleğe alma işleminin çeşitli yönlerini gösterir. Önbellek isteklerini iç içe aktarmak istediğiniz durumlar dışında, kullanılması <xref:System.Windows.Automation.CacheRequest.Activate%2A>tercih edilir.  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu İstemcilerinde Önbelleğe Alma](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
