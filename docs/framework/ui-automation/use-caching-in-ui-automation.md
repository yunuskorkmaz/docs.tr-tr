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
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 12d101b3cd8b7c387cb37b62bc0e777d7294affc
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47236325"
---
# <a name="use-caching-in-ui-automation"></a>UI Otomasyonda Önbelleğe Almayı Kullanma
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu bölümde, önbelleğe almayı uygulayın gösterilmektedir <xref:System.Windows.Automation.AutomationElement> özellikleri ve denetim desenleri.  
  
### <a name="activate-a-cache-request"></a>Bir önbellek isteği'ni etkinleştirin  
  
1.  Oluşturma bir <xref:System.Windows.Automation.CacheRequest>.  
  
2.  Özellikler ve önbellek desenlerini kullanarak belirtin <xref:System.Windows.Automation.CacheRequest.Add%2A>.  
  
3.  Ayarlayarak önbelleğe alma kapsamı belirle <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> özelliği.  
  
4.  Alt ağaç görünümünü belirtmek <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> özelliği.  
  
5.  Ayarlama <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> özelliğini <xref:System.Windows.Automation.AutomationElementMode.None> nesneleri için tam bir başvuru almayarak verimliliği artırmak istiyorsanız. (Bu, bu nesnelerden geçerli değerleri almak imkansız hale getirir.)  
  
6.  Etkinleştirme isteği kullanarak <xref:System.Windows.Automation.CacheRequest.Activate%2A> içinde bir `using` blok (`Using` Microsoft Visual Basic. NET'te).  
  
 Aldıktan sonra <xref:System.Windows.Automation.AutomationElement> nesneleri veya olaylara abone olma devre dışı bırakma isteği kullanarak <xref:System.Windows.Automation.CacheRequest.Pop%2A> (varsa <xref:System.Windows.Automation.CacheRequest.Push%2A> kullanıldı) ya da tarafından oluşturulan nesne disposing <xref:System.Windows.Automation.CacheRequest.Activate%2A>. (Kullanım <xref:System.Windows.Automation.CacheRequest.Activate%2A> içinde bir `using` blok (`Using` Microsoft Visual Basic. NET'te).  
  
### <a name="cache-automationelement-properties"></a>Önbellek AutomationElement özellikleri  
  
1.  Sırasında bir <xref:System.Windows.Automation.CacheRequest> etkin olup elde <xref:System.Windows.Automation.AutomationElement> kullanarak nesneleri <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> veya <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; veya bir <xref:System.Windows.Automation.AutomationElement> için kayıtlı bir olay kaynağı olarak <xref:System.Windows.Automation.CacheRequest> etkindi. (Geçirerek bir önbellek oluşturabilirsiniz bir <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache ya da birini <xref:System.Windows.Automation.TreeWalker> yöntemler.)  
  
2.  Kullanım <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> veya bir özelliği almak <xref:System.Windows.Automation.AutomationElement.Cached%2A> özelliği <xref:System.Windows.Automation.AutomationElement>.  
  
### <a name="obtain-cached-patterns-and-their-properties"></a>Önbelleğe alınan desenleri ve bunların özelliklerini alın  
  
1.  Sırasında bir <xref:System.Windows.Automation.CacheRequest> etkin olup elde <xref:System.Windows.Automation.AutomationElement> kullanarak nesneleri <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> veya <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; veya bir <xref:System.Windows.Automation.AutomationElement> için kayıtlı bir olay kaynağı olarak <xref:System.Windows.Automation.CacheRequest> etkindi. (Geçirerek bir önbellek oluşturabilirsiniz bir <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache ya da birini <xref:System.Windows.Automation.TreeWalker> yöntemler.)  
  
2.  Kullanım <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> veya <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> önbelleğe alınmış bir deseni alınamıyor.  
  
3.  Özellik değerleri almak `Cached` denetim düzeni özelliğidir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği kullanarak önbelleğe alma, çeşitli yönlerini gösteren <xref:System.Windows.Automation.CacheRequest.Activate%2A> etkinleştirmek için <xref:System.Windows.Automation.CacheRequest>.  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği kullanarak önbelleğe alma, çeşitli yönlerini gösteren <xref:System.Windows.Automation.CacheRequest.Push%2A> etkinleştirmek için <xref:System.Windows.Automation.CacheRequest>. Önbellek isteği'iç içe istediklerinde kullanmak tercih edilir dışında <xref:System.Windows.Automation.CacheRequest.Activate%2A>.  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyonu İstemcilerinde Önbelleğe Alma](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
