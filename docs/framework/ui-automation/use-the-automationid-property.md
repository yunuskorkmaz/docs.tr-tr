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
ms.openlocfilehash: 13ad6c85bbde57cd6ad19848de71dabc23ed8f49
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953915"
---
# <a name="use-the-automationid-property"></a>AutomationID Özelliğini Kullanma
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç içindeki bir öğeyi bulmak için nasıl ve ne zaman kullanılabileceğini gösteren senaryolar ve örnek kod içerir.  
  
 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>bir UI Otomasyon öğesini eşlerinden bağımsız olarak tanımlar. Denetim kimliğiyle ilgili özellik tanımlayıcıları hakkında daha fazla bilgi için bkz. [UI Automation özelliklerine genel bakış](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
> [!NOTE]
> <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>ağacın tamamında benzersiz bir kimlik garantisi vermez; genellikle kapsayıcı ve kapsam bilgilerinin yararlı olması gerekir. Örneğin, bir uygulama birden çok üst düzey menü öğesi olan bir menü denetimi içerebilir, buna karşılık birden çok alt menü öğesi vardır. Bu ikincil menü öğeleri, "Item1", "Item 2" gibi genel bir düzen tarafından tanımlanabilir ve üst düzey menü öğelerinde alt öğeler için yinelenen tanımlayıcılara izin verebilir.  
  
## <a name="scenarios"></a>Senaryolar  
 Öğeleri ararken doğru ve tutarlı sonuçlar elde <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> etmek için kullanımını gerektiren üç birincil UI Otomasyonu istemci uygulama senaryosu tanımlandı.  
  
> [!NOTE]
> <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>, üst düzey uygulama pencereleri haricinde denetim görünümündeki tüm UI Otomasyon öğeleri, ID veya x:Uid olmayan [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] denetimlerden türetilmiş UI Otomasyonu öğeleri ve bu denetimden [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] türetilmiş Kullanıcı Arabirimi Otomasyonu öğeleri tarafından desteklenir Denetim KIMLIĞI yok.  
  
#### <a name="use-a-unique-and-discoverable-automationid-to-locate-a-specific-element-in-the-ui-automation-tree"></a>UI Otomasyon ağacındaki belirli bir öğeyi bulmak için benzersiz ve bulunabilir bir AutomationId kullanın  
  
- İlgilendiğiniz bir [!INCLUDE[TLA#tla_uispy](../../../includes/tlasharptla-uispy-md.md)] öğeyi[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] raporlamak için gibi bir <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> araç kullanın. Bu değer daha sonra, sonraki otomatikleştirilmiş test için test betiği gibi bir istemci uygulamasına kopyalanabilir ve yapıştırılabilir. Bu yaklaşım, çalışma zamanında bir öğeyi tanımlamak ve bulmak için gereken kodu azaltır ve basitleştirir.  
  
> [!CAUTION]
>  Genel olarak, yalnızca kendi doğrudan alt öğelerini <xref:System.Windows.Automation.AutomationElement.RootElement%2A>edinmeye çalışırsınız. Alt öğeler için arama yüzlerce veya hatta binlerce öğe aracılığıyla yineleyebilir ve muhtemelen yığın taşmasına neden olabilir. Daha düşük bir düzeyde belirli bir öğe edinmeye çalışıyorsanız, aramanızı uygulama penceresinden veya bir kapsayıcıdan daha düşük bir düzeyde başlatmanız gerekir.  
  
 [!code-csharp[UIAAutomationID_snip#100](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#100)]
 [!code-vb[UIAAutomationID_snip#100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#100)]  
  
#### <a name="use-a-persistent-path-to-return-to-a-previously-identified-automationelement"></a>Daha önce tanımlanan bir AutomationElement öğesine dönmek için kalıcı bir yol kullanın  
  
- Basit test betiklerinden güçlü kayıt ve kayıttan yürütme yardımcı programlarına istemci uygulamaları, dosya açma iletişim kutusu veya menü öğesi gibi şu anda örneği bulunmayan öğelere erişim gerektirebilir ve bu nedenle UI Otomasyon ağacında yok. Bu öğeler yalnızca bir çoğaltma veya "kayıttan yürütme" ile örnek olarak, AutomationId, Denetim desenleri ve olay dinleyicileri gibi UI Otomasyon özelliklerinin kullanımı aracılığıyla belirli bir Kullanıcı Arabirimi eylemleri dizisi aracılığıyla oluşturulabilir.
  
 [!code-csharp[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#uiaworkerthread)]
 [!code-vb[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#uiaworkerthread)]  
[!code-csharp[UIAAutomationID_snip#Playback](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#playback)]
[!code-vb[UIAAutomationID_snip#Playback](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#playback)]  
  
#### <a name="use-a-relative-path-to-return-to-a-previously-identified-automationelement"></a>Daha önce tanımlanan bir AutomationElement öğesine dönmek için göreli yol kullanın  
  
- Bazı durumlarda, AutomationId yalnızca eşdüzey öğeler arasında benzersiz olduğundan garantilenmiş olduğundan, UI Otomasyon ağacındaki birden çok öğe aynı AutomationId özellik değerlerine sahip olabilir. Bu durumlarda, öğeler bir üst öğeye göre benzersiz şekilde tanımlanabilir ve gerekirse, bir üst öğe. Örneğin, bir geliştirici birden çok alt menü öğesi olan, her biri "Item1", "Item2" gibi sıralı AutomationId ile tanımlanmış olan birden çok menü öğesiyle bir menü çubuğu sağlayabilir. Daha sonra her menü öğesi, kendi AutomationId 'si ile birlikte kendi üst öğesinin AutomationId 'si ile ve gerekirse kendi üst öğesi ile benzersiz şekilde tanımlanabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>
- [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Özellik Koşulunu Temel Alan UI Otomasyonu Öğesi Bulma](../../../docs/framework/ui-automation/find-a-ui-automation-element-based-on-a-property-condition.md)
