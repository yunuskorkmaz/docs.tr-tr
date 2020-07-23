---
title: UI Otomasyonda Önbelleğe Almayı Kullanma
description: Bkz. Kullanıcı Arabirimi Otomasyonu 'nda önbelleğe alma kullanma. Önbellek isteğini etkinleştirme, AutomationElement özelliklerini önbelleğe alma ve önbelleğe alınmış desenler alma adımlarını gözden geçirin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- caching, UI Automation
- UI Automation, caching
ms.assetid: ec722dff-6009-4279-b86a-e18d3fa94ebf
ms.openlocfilehash: 8dff9db77e39dc66a16b6a7b395c76a3c768d48e
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924493"
---
# <a name="use-caching-in-ui-automation"></a>UI Otomasyonda Önbelleğe Almayı Kullanma
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu bölümde, <xref:System.Windows.Automation.AutomationElement> özelliklerin ve denetim desenlerinin önbelleğe alınmasının nasıl uygulanacağı gösterilmektedir.  
  
### <a name="activate-a-cache-request"></a>Önbellek Isteğini etkinleştirme  
  
1. Oluşturun <xref:System.Windows.Automation.CacheRequest> .  
  
2. Kullanarak önbelleğe almak için özellikleri ve desenleri belirtin <xref:System.Windows.Automation.CacheRequest.Add%2A> .  
  
3. Özelliği ayarlayarak önbelleğe alma kapsamını belirtin <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> .  
  
4. Özelliği ayarlayarak alt ağacın görünümünü belirtin <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> .  
  
5. <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> <xref:System.Windows.Automation.AutomationElementMode.None> Nesnelere tam başvuru almadıkça verimliliği artırmak istiyorsanız, özelliğini olarak ayarlayın. (Bu, bu nesnelerden geçerli değerleri almayı olanaksız hale getirir.)  
  
6. <xref:System.Windows.Automation.CacheRequest.Activate%2A>Bir blok içinde kullanarak isteği etkinleştirin `using` ( `Using` Microsoft Visual Basic .net 'te).  
  
 Nesneleri aldıktan <xref:System.Windows.Automation.AutomationElement> veya olaylara abone olduktan sonra <xref:System.Windows.Automation.CacheRequest.Pop%2A> ( <xref:System.Windows.Automation.CacheRequest.Push%2A> kullanıldıysa) veya tarafından oluşturulan nesneyi elden kaldırarak isteği devre dışı bırakın <xref:System.Windows.Automation.CacheRequest.Activate%2A> . ( <xref:System.Windows.Automation.CacheRequest.Activate%2A> Bir bloğunda kullanın `using` ( `Using` Microsoft Visual Basic .net 'te).  
  
### <a name="cache-automationelement-properties"></a>Önbellek AutomationElement özellikleri  
  
1. Etkin olsa <xref:System.Windows.Automation.CacheRequest> da, <xref:System.Windows.Automation.AutomationElement> veya kullanarak nesneleri elde edin <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> <xref:System.Windows.Automation.AutomationElement.FindAll%2A> ya da <xref:System.Windows.Automation.AutomationElement> , etkin olduğunda için kaydettiğiniz bir olayın kaynağı olarak elde edin <xref:System.Windows.Automation.CacheRequest> . (Bir <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache 'e veya yöntemlerinden birine geçirerek de bir önbellek oluşturabilirsiniz <xref:System.Windows.Automation.TreeWalker> .)  
  
2. <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>Öğesinin özelliğinden bir özelliği kullanın veya alın <xref:System.Windows.Automation.AutomationElement.Cached%2A> <xref:System.Windows.Automation.AutomationElement> .  
  
### <a name="obtain-cached-patterns-and-their-properties"></a>Önbelleğe alınmış desenleri ve bunların özelliklerini alma  
  
1. Etkin olsa <xref:System.Windows.Automation.CacheRequest> da, <xref:System.Windows.Automation.AutomationElement> veya kullanarak nesneleri elde edin <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> <xref:System.Windows.Automation.AutomationElement.FindAll%2A> ya da <xref:System.Windows.Automation.AutomationElement> , etkin olduğunda için kaydettiğiniz bir olayın kaynağı olarak elde edin <xref:System.Windows.Automation.CacheRequest> . (Bir <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache 'e veya yöntemlerinden birine geçirerek de bir önbellek oluşturabilirsiniz <xref:System.Windows.Automation.TreeWalker> .)  
  
2. <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> Önbelleğe alınmış bir model almak için veya kullanın.  
  
3. `Cached`Denetim deseninin özelliğinden özellik değerlerini alın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, öğesini etkinleştirmek için kullanarak, önbelleğe alma işleminin çeşitli yönlerini gösterir <xref:System.Windows.Automation.CacheRequest.Activate%2A> <xref:System.Windows.Automation.CacheRequest> .  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, öğesini etkinleştirmek için kullanarak, önbelleğe alma işleminin çeşitli yönlerini gösterir <xref:System.Windows.Automation.CacheRequest.Push%2A> <xref:System.Windows.Automation.CacheRequest> . Önbellek isteklerini iç içe aktarmak istediğiniz durumlar dışında, kullanılması tercih edilir <xref:System.Windows.Automation.CacheRequest.Activate%2A> .  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonda Önbelleğe Alma](caching-in-ui-automation-clients.md)
