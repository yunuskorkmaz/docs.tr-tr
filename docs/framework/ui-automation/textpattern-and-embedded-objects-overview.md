---
title: TextPattern ve Katıştırılmış Nesnelere Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, TextPattern class
- embedded objects, accessing
- accessing embedded objects
- embedded objects, UI Automation
ms.assetid: 93fdfbb9-0025-4b72-8ca0-0714adbb70d5
ms.openlocfilehash: e577b9d221760544e95b1d6098d0becbf5d776b0
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042675"
---
# <a name="textpattern-and-embedded-objects-overview"></a>TextPattern ve Katıştırılmış Nesnelere Genel Bakış
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu genel bakışta, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] katıştırılmış nesneleri veya bir metin belgesi veya kapsayıcısı içinde alt öğeleri ortaya çıkaran açıklanır.  
  
 Gömülü bir nesne, metinsel olmayan sınırlara sahip herhangi bir öğedir; Örneğin, bir resim, köprü, tablo veya [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] elektronik tablo veya [!INCLUDE[TLA#tla_winmedia](../../../includes/tlasharptla-winmedia-md.md)] dosya gibi belge türü. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Bu, bir uygulamanın bir uygulamada oluşturulduğu, başka bir uygulamada oluşturulduğu ya da bağlandığı standart tanımdan farklıdır. Nesnenin özgün uygulama içinde düzenlenip düzenlenemeyeceğini, bağlamında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ilgisiz olup olmadığı.  
  
<a name="Embedded_Objects_and_the_UI_Automation_Tree"></a>   
## <a name="embedded-objects-and-the-ui-automation-tree"></a>Katıştırılmış nesneler ve UI Otomasyon ağacı  
 Katıştırılmış nesneler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın denetim görünümü içinde tek tek öğeler olarak değerlendirilir. Bunlar, içindeki [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]diğer denetimlerle erişilebilmesi için metin kapsayıcısının alt öğesi olarak gösterilir.  
  
 ![Metin kapsayıcısındaki görüntüyle birlikte katıştırılmış tablo](./media/uia-textpattern-embedded-objects-overview-example1.png "UIA_TextPattern_Embedded_Objects_Overview_Example1")  
Tablo, resim ve köprü katıştırılmış nesneleri olan bir metin kapsayıcısına örnek  
  
 ![Önceki örnek Için içerik görünümü](./media/uia-textpattern-embedded-objects-overview-example2.PNG "UIA_TextPattern_Embedded_Objects_Overview_Example2")  
Önceki metin kapsayıcısının bir bölümü için Içerik görünümü örneği  
  
<a name="Expose_Embedded_Objects_Using_TextPattern_and"></a>   
## <a name="expose-embedded-objects-using-textpattern-and-textpatternrange"></a>TextModel ve TextPatternRange kullanarak gömülü nesneleri kullanıma sunma  
 Birlikte <xref:System.Windows.Automation.TextPattern> kullanıldığında denetim deseninin sınıfı <xref:System.Windows.Automation.Text.TextPatternRange> ve sınıfı, katıştırılmış nesnelerin gezinmesini ve sorgulanmasını kolaylaştıran Yöntemler ve özellikler sunar.  
  
 Metin kapsayıcısının ve köprü ya da tablo hücresi gibi bir katıştırılmış nesnenin metinsel içeriği (veya iç metni), hem denetim görünümünde hem de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın içerik görünümünde tek bir sürekli metin akışı olarak sunulur; nesne sınırları yok sayılır. Bir UI Otomasyon istemcisi bir şekilde yeniden oluşturma, yorumlama veya çözümleme amacıyla metni alıyorsa, metin aralığı, metinsel içeriğe veya diğer katıştırılmış nesnelere sahip bir tablo gibi özel durumlar için denetlenmelidir. Bu, her <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> katıştırılmışnesne<xref:System.Windows.Automation.AutomationElement> için bir ve sonra herbiröğeiçinbirmetinaralığıeldeetmeküzereçağırarakçağırarakgerçekleştirilebilir.<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> Bu, tüm metin içeriği alınana kadar yinelemeli olarak yapılır.  
  
 ![Gömülü nesnelere yayılmış metin aralıkları.](./media/uia-textpattern-embeddedobjecttextranges.png "UIA_TextPattern_EmbeddedObjectTextRanges")  
Katıştırılmış nesneler ve bunların Aralık Yayılmalarına sahip bir metin akışı örneği  
  
 Bir metin aralığının içeriğine çapraz geçiş yapmak gerektiğinde, <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> yöntemin başarıyla yürütülmesi için bir dizi adım arka planda yer alır.  
  
1. Metin aralığı normalleştirilmelidir; diğer bir deyişle, metin aralığı <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> uç noktada bir bozuk aralığına daraltılır ve bu da <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> uç noktayı gereksiz hale getirir. Bu adım bir metin aralığının sınırlara yaydığı <xref:System.Windows.Automation.Text.TextUnit> durumlarda belirsizliğin kaldırılması için gereklidir: Örneğin, `{The URL https://www.microsoft.com is embedded in text` burada "{" ve "}" metin aralığı uç noktalardır.  
  
2. Elde edilen Aralık, <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> öğesinde istenen <xref:System.Windows.Automation.Text.TextUnit> sınırın başına doğru taşınır.  
  
3. Aralık, <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> istenen <xref:System.Windows.Automation.Text.TextUnit> sınır sayısına göre ileri veya geri taşınır.  
  
4. Aralık daha sonra, <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> uç noktayı istenen <xref:System.Windows.Automation.Text.TextUnit> bir sınır ile taşıyarak bir bozuk aralığı durumundan genişletilir.  
  
 ![& ExpandToEnclosingUnit taşıyarak Aralık ayarlamaları](./media/uia-textpattern-moveandexpand-examples.png "UIA_TextPattern_MoveAndExpand_Examples")  
Taşıma () ve ExpandToEnclosingUnit () için metin aralığı ayarlamasının örnekleri  
  
<a name="Common_Scenarios"></a>   
## <a name="common-scenarios"></a>Yaygın senaryolar  
 Aşağıdaki bölümler, katıştırılmış nesneleri içeren en yaygın senaryoların örneklerini sunmaktadır.  
  
 Gösterilen örneklerin göstergesi:  
  
 { = <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start>  
  
 } = <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End>  
  
### <a name="hyperlink"></a>Köprü  

**Örnek 1-gömülü metin Köprüsü içeren bir metin aralığı**
  
`{The URL https://www.microsoft.com is embedded in text}.`
  
|Çağrılan yöntem|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Dizeyi `The URL https://www.microsoft.com is embedded in text`döndürür.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Metin aralığını kapsayan <xref:System.Windows.Automation.AutomationElement> en içteki döndürür; bu durumda <xref:System.Windows.Automation.AutomationElement> , metin sağlayıcısının kendisini temsil eder.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Hyperlink denetimini <xref:System.Windows.Automation.AutomationElement> temsil eden bir döndürür.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A><xref:System.Windows.Automation.AutomationElement> , önceki`GetChildren` yöntem tarafından döndürülen nesnedir.|"https://www.microsoft.com" Temsil eden aralığı döndürür.|  
  
 **Örnek 2-gömülü metin köprüsünü kısmen yayan bir metin aralığı**  
  
 URL `https://{[www]}` , metne eklenmiş.  
  
|Çağrılan yöntem|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|"Www" dizesini döndürür.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Metin aralığını kapsayan <xref:System.Windows.Automation.AutomationElement> en içteki döndürür; bu durumda köprü denetimi.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Metin `null` aralığı URL dizesinin tamamına yayılmadığı için döndürür.|  
  
**Örnek 3-metin kapsayıcısının içeriğini kısmen kapsayan bir metin aralığı. Metin kapsayıcısının metin aralığının parçası olmayan bir katıştırılmış metin köprüsü vardır.**  
  
`{The URL} [https://www.microsoft.com](https://www.microsoft.com) is embedded in text.`
  
|Çağrılan yöntem|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|"URL" dizesini döndürür.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Metin aralığını kapsayan <xref:System.Windows.Automation.AutomationElement> en içteki döndürür; bu durumda <xref:System.Windows.Automation.AutomationElement> , metin sağlayıcısının kendisini temsil eder.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A>parametreleriyle (TextUnit. Word, 1).|Köprünün metni tek sözcüklerde bulunduğundan metin aralığı aralığını "http" olarak kaydırır. Bu durumda, köprü tek bir nesne olarak kabul edilmez.<br /><br /> {[Http]} URL 'SI metne eklenmiş.|  
  
<a name="Image"></a>   
### <a name="image"></a>Görüntü  
 **Örnek 1-gömülü görüntü içeren bir metin aralığı**  
  
 {Resim ![gömülü görüntü örneği](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") metin içine eklenmiş.  
  
|Çağrılan yöntem|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|"Metin içine katıştırılmış" dizesini döndürür. Görüntüyle ilişkili ALT metinlerin metin akışına eklenmesi beklenmez.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Metin aralığını kapsayan <xref:System.Windows.Automation.AutomationElement> en içteki döndürür; bu durumda <xref:System.Windows.Automation.AutomationElement> , metin sağlayıcısının kendisini temsil eder.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Görüntü denetimini <xref:System.Windows.Automation.AutomationElement> temsil eden bir döndürür.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A><xref:System.Windows.Automation.AutomationElement> , önceki<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> yöntem tarafından döndürülen nesnedir.|"![Embedded Image example](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")" öğesini temsil eden bozuk aralığını döndürür.|  
  
 **Örnek 2-bir metin kapsayıcısının içeriğini kısmen yaydığı bir metin aralığı. Metin kapsayıcısının metin aralığının parçası olmayan gömülü bir görüntüsü vardır.**  
  
 {Görüntü} ![Katıştırılmış resim örneği](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") metin içine katıştırılır.  
  
|Çağrılan yöntem|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|"Görüntü" dizesini döndürür.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Metin aralığını kapsayan <xref:System.Windows.Automation.AutomationElement> en içteki döndürür; bu durumda <xref:System.Windows.Automation.AutomationElement> , metin sağlayıcısının kendisini temsil eder.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A>parametreleriyle (TextUnit. Word, 1).|Metin aralığı aralığını "." olarak kaydırır. Yalnızca metin tabanlı katıştırılmış nesneler metin akışının bir parçası olarak kabul edildiği için, bu örnekteki görüntü Move veya Return değerini etkilemez (Bu durumda 1).|  
  
<a name="Table"></a>   
### <a name="table"></a>Tablo  
  
### <a name="table-used-for-examples"></a>Örnekler için kullanılan tablo  
  
|Resim içeren hücre|Metin içeren hücre|  
|---------------------|--------------------|  
|![Katıştırılmış resim örneği](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")|X|  
|![Gömülü görüntü örneği 2](./media/uia-textpattern-embedded-objects-overview-imageexample2.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample2")|Y|  
|![Katıştırılmış resim örneği 3](./media/uia-textpattern-embedded-objects-overview-imageexample3.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample3")<br /><br /> Z görüntüsü|Z|  
  
 **Örnek 1-metin kapsayıcısını bir hücrenin içeriğinden alın.**  
  
|Çağrılan yöntem|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A>parametreler ile (0, 0)|Tablo hücresinin içeriğini temsil eden döndürür; bu durumda, öğe bir metin denetimidir. <xref:System.Windows.Automation.AutomationElement>|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A><xref:System.Windows.Automation.AutomationElement> , önceki`GetItem` yöntem tarafından döndürülen nesnedir.|Image ![Embedded Image example](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")ile yayılan aralığı döndürür.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>önceki `RangeFromChild` yöntem tarafından döndürülen nesne için.|Tablo hücresini <xref:System.Windows.Automation.AutomationElement> temsil eden döndürür; bu durumda, öğesi tableitempattern 'yi destekleyen bir metin denetimidir.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>önceki `GetEnclosingElement` yöntem tarafından döndürülen nesne için.|<xref:System.Windows.Automation.AutomationElement> Tabloyu temsil eden döndürür.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>önceki `GetEnclosingElement` yöntem tarafından döndürülen nesne için.|Metin sağlayıcısının kendisini temsil edenöğesinidöndürür.<xref:System.Windows.Automation.AutomationElement>|  
  
 **Örnek 2-bir hücrenin metin içeriğini alın.**  
  
|Çağrılan yöntem|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A>parametreleri (1, 1) ile.|Tablo hücresinin içeriğini temsil eden döndürür; bu durumda, öğe bir metin denetimidir. <xref:System.Windows.Automation.AutomationElement>|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A><xref:System.Windows.Automation.AutomationElement> , önceki`GetItem` yöntem tarafından döndürülen nesnedir.|"Y" döndürür.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.TextPattern>
- <xref:System.Windows.Automation.Text.TextPatternRange>
- <xref:System.Windows.Automation.Provider.ITextProvider>
- <xref:System.Windows.Automation.Provider.ITextRangeProvider>
- [UI Otomasyonu Kullanarak Katıştırılmış Nesnelere Erişme](access-embedded-objects-using-ui-automation.md)
- [UI Otomasyonu Kullanarak Tablo İçeriğini Kullanıma Sunma](expose-the-content-of-a-table-using-ui-automation.md)
- [UI Otomasyonunu Kullanarak Çapraz Geçiş Yapma](traverse-text-using-ui-automation.md)
- [TextModel arama ve seçim örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FindText)
