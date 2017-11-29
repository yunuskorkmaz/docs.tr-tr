---
title: "UI Otomasyonda Önbelleğe Almayı Kullanma"
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
- caching, UI Automation
- UI Automation, caching
ms.assetid: ec722dff-6009-4279-b86a-e18d3fa94ebf
caps.latest.revision: "14"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 9576389c7245810eeef3c86926e479dedfdfbb69
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="use-caching-in-ui-automation"></a>UI Otomasyonda Önbelleğe Almayı Kullanma
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu bölümde, önbelleğe alınmasını uygulamak gösterilmiştir <xref:System.Windows.Automation.AutomationElement> özellikleri ve denetim düzenleri.  
  
### <a name="activate-a-cache-request"></a>Bir önbellek isteği etkinleştirme  
  
1.  Oluşturma bir <xref:System.Windows.Automation.CacheRequest>.  
  
2.  Kullanarak özellikleri ve önbellek desenlerini belirtin <xref:System.Windows.Automation.CacheRequest.Add%2A>.  
  
3.  Ayarlayarak önbelleğe alma kapsamını belirtin <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> özelliği.  
  
4.  Alt ağaç görünümünü ayarlayarak belirtin <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> özelliği.  
  
5.  Ayarlama <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> özelliğine <xref:System.Windows.Automation.AutomationElementMode.None> nesneleri için tam bir başvuru almadığınızdan verimliliğini artırmak istiyorsanız. (Bu, geçerli değerleri bu nesnelerden almak mümkün hale getirir.)  
  
6.  İstek kullanarak etkinleştirme <xref:System.Windows.Automation.CacheRequest.Activate%2A> içinde bir `using` blok (`Using` içinde [!INCLUDE[TLA#tla_visualbnet](../../../includes/tlasharptla-visualbnet-md.md)]).  
  
 Alma sonra <xref:System.Windows.Automation.AutomationElement> nesneleri veya olaylara abone olma devre dışı bırakma isteği kullanarak <xref:System.Windows.Automation.CacheRequest.Pop%2A> (varsa <xref:System.Windows.Automation.CacheRequest.Push%2A> kullanılan) veya tarafından oluşturulan nesne atma <xref:System.Windows.Automation.CacheRequest.Activate%2A>. (Kullanım <xref:System.Windows.Automation.CacheRequest.Activate%2A> içinde bir `using` blok (`Using` içinde [!INCLUDE[TLA#tla_visualbnet](../../../includes/tlasharptla-visualbnet-md.md)]).  
  
### <a name="cache-automationelement-properties"></a>Önbellek AutomationElement özellikleri  
  
1.  Sırada bir <xref:System.Windows.Automation.CacheRequest> etkindir elde <xref:System.Windows.Automation.AutomationElement> kullanarak nesneleri <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> veya <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; veya elde bir <xref:System.Windows.Automation.AutomationElement> için ne zaman kayıtlı bir olay kaynağı olarak <xref:System.Windows.Automation.CacheRequest> etkin olduğu. (Bir önbellek geçirerek oluşturabilirsiniz bir <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache veya birini <xref:System.Windows.Automation.TreeWalker> yöntemleri.)  
  
2.  Kullanım <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> veya bir özellikten almak <xref:System.Windows.Automation.AutomationElement.Cached%2A> özelliği <xref:System.Windows.Automation.AutomationElement>.  
  
### <a name="obtain-cached-patterns-and-their-properties"></a>Önbelleğe alınan desenleri ve bunların özelliklerini alın  
  
1.  Sırada bir <xref:System.Windows.Automation.CacheRequest> etkindir elde <xref:System.Windows.Automation.AutomationElement> kullanarak nesneleri <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> veya <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; veya elde bir <xref:System.Windows.Automation.AutomationElement> için ne zaman kayıtlı bir olay kaynağı olarak <xref:System.Windows.Automation.CacheRequest> etkin olduğu. (Bir önbellek geçirerek oluşturabilirsiniz bir <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache veya birini <xref:System.Windows.Automation.TreeWalker> yöntemleri.)  
  
2.  Kullanım <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> veya <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> önbelleğe alınmış desen alınamadı.  
  
3.  Özellik değerleri almak `Cached` denetim düzeni özelliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği kullanarak önbelleğe alma, çeşitli yönlerini gösterir <xref:System.Windows.Automation.CacheRequest.Activate%2A> etkinleştirmek için <xref:System.Windows.Automation.CacheRequest>.  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği kullanarak önbelleğe alma, çeşitli yönlerini gösterir <xref:System.Windows.Automation.CacheRequest.Push%2A> etkinleştirmek için <xref:System.Windows.Automation.CacheRequest>. Önbellek isteği iç içe istediğinizde, kullanmak için tercih edilir dışında <xref:System.Windows.Automation.CacheRequest.Activate%2A>.  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI otomasyonda önbelleğe alma](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
