---
title: "AutomationID Özelliğini Kullanma"
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
- AutomationId property
- UI Automation, AutomationId property
- properties, AutomationId
ms.assetid: a24e807b-d7c3-4e93-ac48-80094c4e1c90
caps.latest.revision: "21"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 969ab4f3c63571488c66c8a505df3969fcd788e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="use-the-automationid-property"></a>AutomationID Özelliğini Kullanma
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, senaryolarını ve ne zaman ve nasıl Göster örnek kod içerir <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> bir öğenin içine bulmak için kullanılan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı.  
  
 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>UI Otomasyon öğesi eşdüzey düğümünden benzersiz olarak tanımlar. Kimlik denetlemek için ilgili özellik tanımlayıcıları hakkında daha fazla bilgi için bkz: [UI Otomasyon özelliklerine genel bakış](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>Ağaç genelinde benzersiz bir kimlik garanti etmez; Genellikle, kapsayıcı ve kullanışlı olması için kapsam bilgileri de gerekir. Örneğin, bir uygulama olan, buna karşılık, birden çok alt menü öğesi birden çok üst düzey menü öğesi ile bir menü denetimi içerebilir. Bu ikincil menü öğeleri, "Item1", "2 öğesinin" gibi genel bir şema tarafından tanımlanan ve benzeri, yinelenen tanımlayıcıları çocuklar için üst düzey menü öğeleri arasında izin verme.  
  
## <a name="scenarios"></a>Senaryolar  
 Üç birincil UI Otomasyonu istemci uygulaması senaryoları kullanımını gerektiren belirlenmiştir <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> için öğeleri ararken doğru ve tutarlı sonuçlar elde etmek için.  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>Denetim görünümünde üst düzey uygulama windows, türetilen UI Otomasyon öğeleri dışındaki tüm UI Otomasyon öğeleri tarafından desteklenen [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] bir kimlik veya x: Uid ve türetilen UI Otomasyon öğeleri yok denetimleri [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] denetleyen bir denetim kimliği yok  
  
#### <a name="use-a-unique-and-discoverable-automationid-to-locate-a-specific-element-in-the-ui-automation-tree"></a>UI Otomasyonu ağacında belirli bir öğeyi bulmak için benzersiz ve bulunabilirlik Automationıd kullanın  
  
-   Gibi bir araç kullanın [!INCLUDE[TLA#tla_uispy](../../../includes/tlasharptla-uispy-md.md)] raporuna <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> , bir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] ilgi öğesi. Bu değer kopyalanır ve sonraki otomatikleştirilmiş testleri için test komut dosyası gibi bir istemci uygulaması içine yapıştırdığınız. Bu yaklaşım azaltır ve tanımlamak ve çalışma zamanında bir öğeyi bulmak gerekli kod basitleştirir.  
  
> [!CAUTION]
>  Genel olarak, sadece doğrudan alt edinme denemelisiniz <xref:System.Windows.Automation.AutomationElement.RootElement%2A>. Alt öğeleri için bir arama yüzlerce veya binlerce büyük olasılıkla bir yığın taşması kaynaklanan öğelerinin bile yinelemek. Belirli bir öğenin alt düzeyde edinme çalışıyorsanız, Uygulama penceresinden veya daha düşük düzeydeki bir kapsayıcı aramanızı başlamanız gerekir.  
  
 [!code-csharp[UIAAutomationID_snip#100](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#100)]
 [!code-vb[UIAAutomationID_snip#100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#100)]  
  
#### <a name="use-a-persistent-path-to-return-to-a-previously-identified-automationelement"></a>Kalıcı bir yol için önceden tanımlanmış bir AutomationElement döndürmek için kullanın  
  
-   İstemci uygulamalarından sağlam kaydı ve kayıttan yürütme yardımcı programlar, basit bir sınama komut dosyaları gibi bir dosya iletişim kutusu veya menü öğesini açın ve bu nedenle UI Otomasyonu ağacında yok, şu anda, örneği oluşturulmadan değil öğelere erişim gerektirebilir. Bu öğeler yalnızca örneği yeniden oluşturma, veya "tekrar oynatma", belirli bir dizi tarafından [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] eylemleri kullanılarak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Automationıd, Denetim desenleri ve olay dinleyicileri gibi özellikleri. Bkz: [Test komut Oluşturucu örnek](http://msdn.microsoft.com/en-us/028467fd-2980-4691-9522-0131dcef23a0) kullanan bir örnek [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] ile kullanıcı etkileşimi dayalı test komut dosyaları oluşturmak için [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)].  
  
 [!code-csharp[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#uiaworkerthread)]
 [!code-vb[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#uiaworkerthread)]  
[!code-csharp[UIAAutomationID_snip#Playback](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#playback)]
[!code-vb[UIAAutomationID_snip#Playback](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#playback)]  
  
#### <a name="use-a-relative-path-to-return-to-a-previously-identified-automationelement"></a>Önceden tanımlanmış AutomationElement için döndürmek için göreli bir yol kullanın  
  
-   Bazı durumlarda Automationıd yalnızca eşdüzey arasında benzersiz olması garanti bu yana UI Otomasyonu ağacında birden çok öğe aynı Automationıd özelliği değerlerine sahip olabilir. Bu durumlarda öğeleri benzersiz olarak bir üst öğede göre tanımlanabilir ve gerekirse, bir iki üst varlık. Örneğin, bir geliştirici alt sıralı Automationıd 's "Item1", "Item2" vb. gibi ile burada tanımlanan menü öğeleri birden çok menü öğeleriyle her birden çok alt ile bir menü çubuğu sağlayabilir. Her bir menü öğesi sonra benzersiz olarak kendi üst Automationıd yanı sıra kendi Automationıd tarafından tanımlanamadı ve gerekirse, kendi iki üst varlık.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>  
 [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Özellik Koşulunu Temel Alan UI Otomasyonu Öğesi Bulma](../../../docs/framework/ui-automation/find-a-ui-automation-element-based-on-a-property-condition.md)
