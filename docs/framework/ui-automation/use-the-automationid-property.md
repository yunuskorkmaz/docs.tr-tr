---
title: AutomationID Özelliğini Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutomationId property
- UI Automation, AutomationId property
- properties, AutomationId
ms.assetid: a24e807b-d7c3-4e93-ac48-80094c4e1c90
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 9f2f5b157d8999cd254d6b389cdf7a2ca8ca1f8f
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48840538"
---
# <a name="use-the-automationid-property"></a>AutomationID Özelliğini Kullanma
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, senaryoları ve nasıl ve ne zaman gösteren örnek kodu içerir <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> içindeki bir öğeyi bulmak için kullanılan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç.  
  
 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> bir eşdüzey UI Otomasyonu öğesinden benzersiz olarak tanımlar. Kimlik denetimi ile ilgili özellik tanımlayıcıları hakkında daha fazla bilgi için bkz. [UI Otomasyon özelliklerine genel bakış](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> Ağaç genelinde benzersiz bir kimlik garanti etmez. Genellikle, kapsayıcı ve kullanışlı olması için kapsam bilgileri de gerekir. Örneğin, bir uygulama, buna karşılık, birden çok alt menü öğeleri sahip birden çok üst düzey menü öğeleri ile bir menü denetimi içerebilir. Bu ikincil menü öğeleri "Item1", "2 öğe" gibi genel bir şema belirtilebileceği vb. üst düzey menü öğeleri arasında yinelenen tanımlayıcıları alt öğeleri için izin verme.  
  
## <a name="scenarios"></a>Senaryolar  
 Üç birincil UI Otomasyonu istemci uygulama senaryoları kullanımını gerektiren belirlenmiştir <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> öğeleri için arama yaparken doğru ve tutarlı sonuçlar elde etmek için.  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> Denetim görünümünde en üst düzey uygulama windows, UI Otomasyonu öğeleri türetilen dışındaki tüm UI Otomasyonu öğeleri tarafından desteklenen [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] bir kimlik veya x: Uid ve türetilen UI Otomasyonu öğeleri olmayan denetimleri [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] denetleyen Denetim kimliği yok  
  
#### <a name="use-a-unique-and-discoverable-automationid-to-locate-a-specific-element-in-the-ui-automation-tree"></a>UI Otomasyonu ağaçta belirli bir öğeyi bulmak için benzersiz ve bulunabilirlik Automationıd kullanın  
  
-   Gibi bir araç kullanın [!INCLUDE[TLA#tla_uispy](../../../includes/tlasharptla-uispy-md.md)] rapora <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> , bir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] ilgi öğesi. Bu değer kopyalanır ve sonraki otomatik testi için test betiği gibi bir istemci uygulamasına yapıştırıldı. Bu yaklaşım azaltır ve tanımlamak ve çalışma zamanında bir öğeyi bulmak için gereken kodu basitleştirir.  
  
> [!CAUTION]
>  Genel olarak, yalnızca doğrudan alt öğeleri almak denemelisiniz <xref:System.Windows.Automation.AutomationElement.RootElement%2A>. Alt öğeleri için arama, yüzlerce veya binlerce büyük olasılıkla bir yığın taşması ile elde edilen öğelerin bile aracılığıyla yineleme. Daha düşük bir düzeyde belirli bir öğeyi edinme çalışıyorsanız, uygulama penceresinin veya daha düşük bir düzeyde bir kapsayıcı aramanızı başlamanız gerekir.  
  
 [!code-csharp[UIAAutomationID_snip#100](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#100)]
 [!code-vb[UIAAutomationID_snip#100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#100)]  
  
#### <a name="use-a-persistent-path-to-return-to-a-previously-identified-automationelement"></a>Önceden tanımlanmış bir AutomationElement için döndürülecek kalıcı bir yol kullanın  
  
-   İstemci uygulamalarından sağlam kaydı ve kayıttan yürütme yardımcı programlar, basit bir test betikleri gibi bir dosya iletişim kutusu veya menü öğesini açın ve UI Otomasyonu ağaçta yok, şu anda, örneği oluşturulur değil öğelere erişim gerektirebilir. Bu öğeleri yalnızca oluşturulabilir yeniden oluşturma, veya "kayıttan", belirli bir dizi tarafından [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] eylemleri kullanımının [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Automationıd, Denetim düzenleri ve olay dinleyicileri gibi özellikleri. Bkz: [Test betiği oluşturucu örneği](https://msdn.microsoft.com/library/028467fd-2980-4691-9522-0131dcef23a0) kullanan bir örnek için [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] kullanıcı etkileşimi olmadan dayalı test betikleri oluşturmak için [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)].  
  
 [!code-csharp[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#uiaworkerthread)]
 [!code-vb[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#uiaworkerthread)]  
[!code-csharp[UIAAutomationID_snip#Playback](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#playback)]
[!code-vb[UIAAutomationID_snip#Playback](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#playback)]  
  
#### <a name="use-a-relative-path-to-return-to-a-previously-identified-automationelement"></a>Önceden tanımlanmış bir AutomationElement için döndürülecek göreli bir yol kullanın  
  
-   Automationıd yalnızca eş değerleri arasında benzersiz olması garanti olduğundan bazı durumlarda, UI Otomasyonu ağacında birden çok öğe aynı Automationıd özelliği değerlerine sahip olabilir. Bu durumlarda öğeleri benzersiz bir üst öğede göre tanımlanabilir ve gerekirse bir doya. Örneğin, bir geliştirici menü öğeleri ile sıralı Automationıd 's "Item1", "Item2" vb. gibi alt burada tanımlanan birden çok menü öğeleri ile her ile birden çok alt menü çubuğu sağlayabilir. Her bir menü öğesi sonra benzersiz üst Automationıd yanı sıra kendi Automationıd tarafından tanımlanabilir ve gerekirse kendi dizinleriyle.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>  
 [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Özellik Koşulunu Temel Alan UI Otomasyonu Öğesi Bulma](../../../docs/framework/ui-automation/find-a-ui-automation-element-based-on-a-property-condition.md)
