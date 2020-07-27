---
title: TextPattern ve Katıştırılmış Nesnelere Genel Bakış
description: Kullanıcı Arabirimi Otomasyonu 'nun katıştırılmış nesneleri veya alt öğeleri, TextModel ve TextPatternRange kullanarak bir metin belgesi veya kapsayıcı içinde nasıl açığa çıkardığı hakkında genel bakış konusunu okuyun.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, TextPattern class
- embedded objects, accessing
- accessing embedded objects
- embedded objects, UI Automation
ms.assetid: 93fdfbb9-0025-4b72-8ca0-0714adbb70d5
ms.openlocfilehash: 0a06fb72b280fc61faeb12f6f2c3a05d957ec7b9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163558"
---
# <a name="textpattern-and-embedded-objects-overview"></a>TextPattern ve Katıştırılmış Nesnelere Genel Bakış
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu genel bakışta [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , katıştırılmış nesneleri veya bir metin belgesi veya kapsayıcısı içinde alt öğeleri ortaya çıkaran açıklanır.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Gömülü bir nesne, metin olmayan sınırlara sahip herhangi bir öğedir; Örneğin, bir resim, köprü, tablo veya Microsoft Excel elektronik tablosu veya Microsoft Windows medya dosyası gibi belge türü. Bu, bir uygulamanın bir uygulamada oluşturulduğu, başka bir uygulamada oluşturulduğu ya da bağlandığı standart tanımdan farklıdır. Nesnenin özgün uygulama içinde düzenlenip düzenlenemeyeceğini, bağlamında ilgisiz olup olmadığı [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
<a name="Embedded_Objects_and_the_UI_Automation_Tree"></a>
## <a name="embedded-objects-and-the-ui-automation-tree"></a>Katıştırılmış nesneler ve UI Otomasyon ağacı  
 Katıştırılmış nesneler, ağacın denetim görünümü içinde tek tek öğeler olarak değerlendirilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Bunlar, içindeki diğer denetimlerle erişilebilmesi için metin kapsayıcısının alt öğesi olarak gösterilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
 ![Metin kapsayıcısındaki görüntüyle birlikte katıştırılmış tablo](./media/uia-textpattern-embedded-objects-overview-example1.png "UIA_TextPattern_Embedded_Objects_Overview_Example1")  
Tablo, resim ve köprü katıştırılmış nesneleri olan bir metin kapsayıcısına örnek  
  
 ![Önceki örnek için içerik görünümü](./media/uia-textpattern-embedded-objects-overview-example2.PNG "UIA_TextPattern_Embedded_Objects_Overview_Example2")  
Önceki metin kapsayıcısının bir bölümü için Içerik görünümü örneği  
  
<a name="Expose_Embedded_Objects_Using_TextPattern_and"></a>
## <a name="expose-embedded-objects-using-textpattern-and-textpatternrange"></a>TextModel ve TextPatternRange kullanarak gömülü nesneleri kullanıma sunma  
 Birlikte kullanıldığında <xref:System.Windows.Automation.TextPattern> Denetim deseninin sınıfı ve <xref:System.Windows.Automation.Text.TextPatternRange> sınıfı, katıştırılmış nesnelerin gezinmesini ve sorgulanmasını kolaylaştıran Yöntemler ve özellikler sunar.  
  
 Metin kapsayıcısının ve köprü ya da tablo hücresi gibi bir katıştırılmış nesnenin metinsel içeriği (veya iç metni), hem denetim görünümünde hem de ağacın içerik görünümünde tek bir sürekli metin akışı olarak sunulur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ; nesne sınırları yok sayılır. Bir UI Otomasyon istemcisi bir şekilde yeniden oluşturma, yorumlama veya çözümleme amacıyla metni alıyorsa, metin aralığı, metinsel içeriğe veya diğer katıştırılmış nesnelere sahip bir tablo gibi özel durumlar için denetlenmelidir. Bu, <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> <xref:System.Windows.Automation.AutomationElement> Her katıştırılmış nesne için bir ve sonra <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> her bir öğe için bir metin aralığı elde etmek üzere çağırarak çağırarak gerçekleştirilebilir. Bu, tüm metin içeriği alınana kadar yinelemeli olarak yapılır.  
  
 ![Gömülü nesnelere yayılmış metin aralıkları.](./media/uia-textpattern-embeddedobjecttextranges.png "UIA_TextPattern_EmbeddedObjectTextRanges")  
Katıştırılmış nesneler ve bunların Aralık Yayılmalarına sahip bir metin akışı örneği  
  
 Bir metin aralığının içeriğine çapraz geçiş yapmak gerektiğinde, yöntemin başarıyla yürütülmesi için bir dizi adım arka planda yer alır <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> .  
  
1. Metin aralığı normalleştirilmelidir; diğer bir deyişle, metin aralığı uç noktada bir bozuk aralığına daraltılır ve bu da <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> uç noktayı gereksiz hale getirir. Bu adım bir metin aralığının sınırlara yaydığı durumlarda belirsizliğin kaldırılması için gereklidir <xref:System.Windows.Automation.Text.TextUnit> : Örneğin, `{The URL https://www.microsoft.com is embedded in text` burada "{" ve "}" metin aralığı uç noktalardır.  
  
2. Elde edilen Aralık, öğesinde <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> istenen sınırın başına doğru taşınır <xref:System.Windows.Automation.Text.TextUnit> .  
  
3. Aralık, <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> İstenen sınır sayısına göre ileri veya geri taşınır <xref:System.Windows.Automation.Text.TextUnit> .  
  
4. Aralık daha sonra, <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> uç noktayı istenen bir sınır ile taşıyarak bir bozuk aralığı durumundan genişletilir <xref:System.Windows.Automation.Text.TextUnit> .  
  
 ![& ExpandToEnclosingUnit taşıyarak Aralık ayarlamaları](./media/uia-textpattern-moveandexpand-examples.png "UIA_TextPattern_MoveAndExpand_Examples")  
Taşıma () ve ExpandToEnclosingUnit () için metin aralığı ayarlamasının örnekleri  
  
<a name="Common_Scenarios"></a>
## <a name="common-scenarios"></a>Genel Senaryolar  
 Aşağıdaki bölümler, katıştırılmış nesneleri içeren en yaygın senaryoların örneklerini sunmaktadır.  
  
 Gösterilen örneklerin göstergesi:  
  
 { =<xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start>  
  
 } =<xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End>  
  
### <a name="hyperlink"></a>Köprü  

**Örnek 1-gömülü metin Köprüsü içeren bir metin aralığı**
  
`{The URL https://www.microsoft.com is embedded in text}.`
  
|Çağrılan yöntem|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Dizeyi döndürür `The URL https://www.microsoft.com is embedded in text` .|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|<xref:System.Windows.Automation.AutomationElement>Metin aralığını kapsayan en içteki döndürür; bu durumda, <xref:System.Windows.Automation.AutomationElement> metin sağlayıcısının kendisini temsil eder.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|<xref:System.Windows.Automation.AutomationElement>Hyperlink denetimini temsil eden bir döndürür.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>, <xref:System.Windows.Automation.AutomationElement> önceki yöntem tarafından döndürülen nesnedir `GetChildren` .|Temsil eden aralığı döndürür `https://www.microsoft.com` .|  
  
 **Örnek 2-gömülü metin köprüsünü kısmen yayan bir metin aralığı**  
  
 URL, `https://{[www]}` metne eklenmiş.  
  
|Çağrılan yöntem|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|"Www" dizesini döndürür.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|<xref:System.Windows.Automation.AutomationElement>Metin aralığını kapsayan en içteki döndürür; bu durumda köprü denetimi.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|`null`Metin ARALıĞı URL dizesinin tamamına yayılmadığı için döndürür.|  
  
**Örnek 3-metin kapsayıcısının içeriğini kısmen kapsayan bir metin aralığı. Metin kapsayıcısının metin aralığının parçası olmayan bir katıştırılmış metin köprüsü vardır.**  
  
`{The URL} [https://www.microsoft.com](https://www.microsoft.com) is embedded in text.`
  
|Çağrılan yöntem|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|"URL" dizesini döndürür.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|<xref:System.Windows.Automation.AutomationElement>Metin aralığını kapsayan en içteki döndürür; bu durumda, <xref:System.Windows.Automation.AutomationElement> metin sağlayıcısının kendisini temsil eder.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A>parametreleriyle (TextUnit. Word, 1).|Köprünün metni tek sözcüklerde bulunduğundan metin aralığı aralığını "http" olarak kaydırır. Bu durumda, köprü tek bir nesne olarak kabul edilmez.<br /><br /> {[Http]} URL 'SI metne eklenmiş.|  
  
<a name="Image"></a>
### <a name="image"></a>Görüntü  
 **Örnek 1-gömülü görüntü içeren bir metin aralığı**  
  
 {Resim ![katıştırılmış görüntü örneği](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") , metne eklenmiş.  
  
|Çağrılan yöntem|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|"Metin içine katıştırılmış" dizesini döndürür. Görüntüyle ilişkili ALT metinlerin metin akışına eklenmesi beklenmez.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|<xref:System.Windows.Automation.AutomationElement>Metin aralığını kapsayan en içteki döndürür; bu durumda, <xref:System.Windows.Automation.AutomationElement> metin sağlayıcısının kendisini temsil eder.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|<xref:System.Windows.Automation.AutomationElement>Görüntü denetimini temsil eden bir döndürür.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>, <xref:System.Windows.Automation.AutomationElement> önceki yöntem tarafından döndürülen nesnedir <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> .|"![Embedded Image example](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")" öğesini temsil eden bozuk aralığını döndürür.|  
  
 **Örnek 2-bir metin kapsayıcısının içeriğini kısmen yaydığı bir metin aralığı. Metin kapsayıcısının metin aralığının parçası olmayan gömülü bir görüntüsü vardır.**  
  
 {Görüntü} ![Katıştırılmış görüntü örneği](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") metne eklenmiş.  
  
|Çağrılan yöntem|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|"Görüntü" dizesini döndürür.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|<xref:System.Windows.Automation.AutomationElement>Metin aralığını kapsayan en içteki döndürür; bu durumda, <xref:System.Windows.Automation.AutomationElement> metin sağlayıcısının kendisini temsil eder.|  
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
|<xref:System.Windows.Automation.GridPattern.GetItem%2A>parametreler ile (0, 0)|<xref:System.Windows.Automation.AutomationElement>Tablo hücresinin içeriğini temsil eden döndürür; bu durumda, öğe bir metin denetimidir.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>, <xref:System.Windows.Automation.AutomationElement> önceki yöntem tarafından döndürülen nesnedir `GetItem` .|Resim ![gömülü görüntü örneğine](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")yayılan aralığı döndürür.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>önceki yöntem tarafından döndürülen nesne için `RangeFromChild` .|<xref:System.Windows.Automation.AutomationElement>Tablo hücresini temsil eden döndürür; bu durumda, öğesi TableItemPattern 'yi destekleyen bir metin denetimidir.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>önceki yöntem tarafından döndürülen nesne için `GetEnclosingElement` .|<xref:System.Windows.Automation.AutomationElement>Tabloyu temsil eden döndürür.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>önceki yöntem tarafından döndürülen nesne için `GetEnclosingElement` .|<xref:System.Windows.Automation.AutomationElement>Metin sağlayıcısının kendisini temsil eden öğesini döndürür.|  
  
 **Örnek 2-bir hücrenin metin içeriğini alın.**  
  
|Çağrılan yöntem|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A>parametreleri (1, 1) ile.|<xref:System.Windows.Automation.AutomationElement>Tablo hücresinin içeriğini temsil eden döndürür; bu durumda, öğe bir metin denetimidir.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>, <xref:System.Windows.Automation.AutomationElement> önceki yöntem tarafından döndürülen nesnedir `GetItem` .|"Y" döndürür.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.TextPattern>
- <xref:System.Windows.Automation.Text.TextPatternRange>
- <xref:System.Windows.Automation.Provider.ITextProvider>
- <xref:System.Windows.Automation.Provider.ITextRangeProvider>
- [UI Otomasyonu Kullanarak Katıştırılmış Nesnelere Erişme](access-embedded-objects-using-ui-automation.md)
- [UI Otomasyonu Kullanarak Tablo İçeriğini Kullanıma Sunma](expose-the-content-of-a-table-using-ui-automation.md)
- [UI Otomasyonunu Kullanarak Çapraz Geçiş Yapma](traverse-text-using-ui-automation.md)
- [TextModel arama ve seçim örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FindText)
