---
title: AutomationID Özelliğini Kullanma
description: UI Otomasyon ağacı içinde bir öğe bulmak için AutomationId özelliğinin nasıl ve ne zaman kullanılacağını gösteren senaryoları ve örnek kodu gözden geçirin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutomationId property
- UI Automation, AutomationId property
- properties, AutomationId
ms.assetid: a24e807b-d7c3-4e93-ac48-80094c4e1c90
ms.openlocfilehash: 9e6dd3935a1b4d15690e1dfecd73e9b07330ec6c
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924532"
---
# <a name="use-the-automationid-property"></a>AutomationID Özelliğini Kullanma
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> ağaç içindeki bir öğeyi bulmak için nasıl ve ne zaman kullanılabileceğini gösteren senaryolar ve örnek kod içerir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>bir UI Otomasyon öğesini eşlerinden bağımsız olarak tanımlar. Denetim kimliğiyle ilgili özellik tanımlayıcıları hakkında daha fazla bilgi için bkz. [UI Automation özelliklerine genel bakış](ui-automation-properties-overview.md).  
  
> [!NOTE]
> <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>ağacın tamamında benzersiz bir kimlik garantisi vermez; genellikle kapsayıcı ve kapsam bilgilerinin yararlı olması gerekir. Örneğin, bir uygulama birden çok üst düzey menü öğesi olan bir menü denetimi içerebilir, buna karşılık birden çok alt menü öğesi vardır. Bu ikincil menü öğeleri, "Item1", "Item 2" gibi genel bir düzen tarafından tanımlanabilir ve üst düzey menü öğelerinde alt öğeler için yinelenen tanımlayıcılara izin verebilir.  
  
## <a name="scenarios"></a>Senaryolar  
 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>Öğeleri ararken doğru ve tutarlı sonuçlar elde etmek için kullanımını gerektiren üç BIRINCIL UI Otomasyonu istemci uygulama senaryosu tanımlandı.  
  
> [!NOTE]
> <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>, üst düzey uygulama pencereleri hariç denetim görünümündeki tüm UI Otomasyon öğeleri, bir [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] ID veya x:Uid olmayan denetimlerden TÜRETILMIŞ UI Otomasyon öğeleri ve bir DENETIM kimliği olmayan Win32 denetimlerinden TÜRETILMIŞ UI Otomasyonu öğeleri tarafından desteklenir.  
  
#### <a name="use-a-unique-and-discoverable-automationid-to-locate-a-specific-element-in-the-ui-automation-tree"></a>UI Otomasyon ağacındaki belirli bir öğeyi bulmak için benzersiz ve bulunabilir bir AutomationId kullanın  
  
- İlgilendiğiniz bir öğenin raporunu raporlamak için UI Spy gibi bir araç kullanın <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Bu değer daha sonra, sonraki otomatikleştirilmiş test için test betiği gibi bir istemci uygulamasına kopyalanabilir ve yapıştırılabilir. Bu yaklaşım, çalışma zamanında bir öğeyi tanımlamak ve bulmak için gereken kodu azaltır ve basitleştirir.  
  
> [!CAUTION]
> Genel olarak, yalnızca kendi doğrudan alt öğelerini edinmeye çalışırsınız <xref:System.Windows.Automation.AutomationElement.RootElement%2A> . Alt öğeler için arama yüzlerce veya hatta binlerce öğe aracılığıyla yineleyebilir ve muhtemelen yığın taşmasına neden olabilir. Daha düşük bir düzeyde belirli bir öğe edinmeye çalışıyorsanız, aramanızı uygulama penceresinden veya bir kapsayıcıdan daha düşük bir düzeyde başlatmanız gerekir.  
  
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
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
- [Özellik Koşulunu Temel Alan UI Otomasyon Öğesi Bulma](find-a-ui-automation-element-based-on-a-property-condition.md)
