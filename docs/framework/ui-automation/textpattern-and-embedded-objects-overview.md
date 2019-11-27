---
title: TextPattern ve Katıştırılmış Nesnelere Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, TextPattern class
- embedded objects, accessing
- accessing embedded objects
- embedded objects, UI Automation
ms.assetid: 93fdfbb9-0025-4b72-8ca0-0714adbb70d5
ms.openlocfilehash: afcb7f282b222d377c4b04db7c91db062ffe4b2a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446842"
---
# <a name="textpattern-and-embedded-objects-overview"></a>TextPattern ve Katıştırılmış Nesnelere Genel Bakış
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu genel bakışta, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] katıştırılmış nesneleri veya bir metin belgesi veya kapsayıcısı içinde alt öğeleri nasıl kullanıma sunduğunu açıklar.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], gömülü bir nesne, metinsel olmayan sınırlara sahip herhangi bir öğedir; Örneğin, bir resim, köprü, tablo veya Microsoft Excel elektronik tablosu veya Microsoft Windows medya dosyası gibi belge türü. Bu, bir uygulamanın bir uygulamada oluşturulduğu, başka bir uygulamada oluşturulduğu ya da bağlandığı standart tanımdan farklıdır. Nesnenin özgün uygulama içinde düzenlenip düzenlenemeyeceğini [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bağlamında ilgisiz olup olmadığı.  
  
<a name="Embedded_Objects_and_the_UI_Automation_Tree"></a>   
## <a name="embedded-objects-and-the-ui-automation-tree"></a>Katıştırılmış nesneler ve UI Otomasyon ağacı  
 Katıştırılmış nesneler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının denetim görünümü içinde tek tek öğeler olarak değerlendirilir. Bunlar, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]' deki diğer denetimlerle erişilebilmesi için metin kapsayıcısının alt öğesi olarak gösterilir.  
  
 ![Metin kapsayıcısındaki görüntüyle birlikte katıştırılmış tablo](./media/uia-textpattern-embedded-objects-overview-example1.png "UIA_TextPattern_Embedded_Objects_Overview_Example1")  
Tablo, resim ve köprü katıştırılmış nesneleri olan bir metin kapsayıcısına örnek  
  
 ![Önceki örnek için içerik görünümü](./media/uia-textpattern-embedded-objects-overview-example2.PNG "UIA_TextPattern_Embedded_Objects_Overview_Example2")  
Önceki metin kapsayıcısının bir bölümü için Içerik görünümü örneği  
  
<a name="Expose_Embedded_Objects_Using_TextPattern_and"></a>   
## <a name="expose-embedded-objects-using-textpattern-and-textpatternrange"></a>TextModel ve TextPatternRange kullanarak gömülü nesneleri kullanıma sunma  
 Birlikte kullanıldığında, <xref:System.Windows.Automation.TextPattern> denetim deseninin sınıfı ve <xref:System.Windows.Automation.Text.TextPatternRange> sınıfı, katıştırılmış nesnelerin gezinmesini ve sorgulanmasını kolaylaştıran Yöntemler ve özellikler sunar.  
  
 Bir metin kapsayıcısının ve köprü ya da tablo hücresi gibi bir katıştırılmış nesnenin metinsel içeriği (veya iç metni), hem denetim görünümünde hem de [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının içerik görünümünde tek bir sürekli metin akışı olarak sunulur; nesne sınırları yoksayıldı. Bir UI Otomasyon istemcisi bir şekilde yeniden oluşturma, yorumlama veya çözümleme amacıyla metni alıyorsa, metin aralığı, metinsel içeriğe veya diğer katıştırılmış nesnelere sahip bir tablo gibi özel durumlar için denetlenmelidir. Bu, her katıştırılmış nesne için bir <xref:System.Windows.Automation.AutomationElement> elde etmek üzere <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> çağırarak ve sonra her öğe için bir metin aralığı elde <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> çağırarak gerçekleştirilebilir. Bu, tüm metin içeriği alınana kadar yinelemeli olarak yapılır.  
  
 ![Gömülü nesnelere yayılmış metin aralıkları.](./media/uia-textpattern-embeddedobjecttextranges.png "UIA_TextPattern_EmbeddedObjectTextRanges")  
Katıştırılmış nesneler ve bunların Aralık Yayılmalarına sahip bir metin akışı örneği  
  
 Bir metin aralığının içeriğinde geçiş yapmak gerektiğinde, <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> yönteminin başarıyla yürütülmesi için bir dizi adım arka planda yer alır.  
  
1. Metin aralığı normalleştirilmelidir; diğer bir deyişle, metin aralığı <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> uç noktasında bir bozuk aralığına daraltılır ve bu da <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> uç noktasını gereksiz hale getirir. Bu adım, bir metin aralığının <xref:System.Windows.Automation.Text.TextUnit> sınırlara yaydığı durumlarda belirsizliğin kaldırılması için gereklidir: Örneğin, "{" ve "}" metin aralığı uç noktaları olan `{The URL https://www.microsoft.com is embedded in text`.  
  
2. Elde edilen Aralık <xref:System.Windows.Automation.TextPattern.DocumentRange%2A>, istenen <xref:System.Windows.Automation.Text.TextUnit> sınırının başlangıcına doğru taşınır.  
  
3. Aralık, istenen <xref:System.Windows.Automation.Text.TextUnit> sınır sayısına göre <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> ileri veya geri taşınır.  
  
4. Aralık daha sonra, <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> uç noktasını istenen bir <xref:System.Windows.Automation.Text.TextUnit> sınırına taşıyarak bir bozuk Aralık durumundan genişletilir.  
  
 ![& ExpandToEnclosingUnit taşıyarak Aralık ayarlamaları](./media/uia-textpattern-moveandexpand-examples.png "UIA_TextPattern_MoveAndExpand_Examples")  
Taşıma () ve ExpandToEnclosingUnit () için metin aralığı ayarlamasının örnekleri  
  
<a name="Common_Scenarios"></a>   
## <a name="common-scenarios"></a>Yaygın Senaryolar  
 Aşağıdaki bölümler, katıştırılmış nesneleri içeren en yaygın senaryoların örneklerini sunmaktadır.  
  
 Gösterilen örneklerin göstergesi:  
  
 {= <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start>  
  
 } = <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End>  
  
### <a name="hyperlink"></a>Köprü  

**Örnek 1-gömülü metin Köprüsü içeren bir metin aralığı**
  
`{The URL https://www.microsoft.com is embedded in text}.`
  
|Çağrılan yöntem|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|`The URL https://www.microsoft.com is embedded in text`dize döndürür.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Metin aralığını kapsayan en içteki <xref:System.Windows.Automation.AutomationElement> döndürür; Bu durumda, metin sağlayıcısının kendisini temsil eden <xref:System.Windows.Automation.AutomationElement>.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Köprü denetimini temsil eden bir <xref:System.Windows.Automation.AutomationElement> döndürür.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>, önceki `GetChildren` yönteminin döndürdüğü nesne <xref:System.Windows.Automation.AutomationElement>.|"https://www.microsoft.com" temsil eden aralığı döndürür.|  
  
 **Örnek 2-gömülü metin köprüsünü kısmen yayan bir metin aralığı**  
  
 `https://{[www]}` URL 'SI metne eklenmiş.  
  
|Çağrılan yöntem|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|"Www" dizesini döndürür.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Metin aralığını kapsayan en içteki <xref:System.Windows.Automation.AutomationElement> döndürür; Bu durumda, HyperLink denetimi.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Metin aralığı URL dizesinin tamamına yayılmadığı için `null` döndürür.|  
  
**Örnek 3-metin kapsayıcısının içeriğini kısmen kapsayan bir metin aralığı. Metin kapsayıcısının metin aralığının parçası olmayan bir katıştırılmış metin köprüsü vardır.**  
  
`{The URL} [https://www.microsoft.com](https://www.microsoft.com) is embedded in text.`
  
|Çağrılan yöntem|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|"URL" dizesini döndürür.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Metin aralığını kapsayan en içteki <xref:System.Windows.Automation.AutomationElement> döndürür; Bu durumda, metin sağlayıcısının kendisini temsil eden <xref:System.Windows.Automation.AutomationElement>.|  
|parametreleriyle <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> (TextUnit. Word, 1).|Köprünün metni tek sözcüklerde bulunduğundan metin aralığı aralığını "http" olarak kaydırır. Bu durumda, köprü tek bir nesne olarak kabul edilmez.<br /><br /> {[Http]} URL 'SI metne eklenmiş.|  
  
<a name="Image"></a>   
### <a name="image"></a>Görüntü  
 **Örnek 1-gömülü görüntü içeren bir metin aralığı**  
  
 {Resim ![katıştırılmış görüntü örneği](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") , metne eklenmiş.  
  
|Çağrılan yöntem|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|"Metin içine katıştırılmış" dizesini döndürür. Görüntüyle ilişkili ALT metinlerin metin akışına eklenmesi beklenmez.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Metin aralığını kapsayan en içteki <xref:System.Windows.Automation.AutomationElement> döndürür; Bu durumda, metin sağlayıcısının kendisini temsil eden <xref:System.Windows.Automation.AutomationElement>.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Görüntü denetimini temsil eden bir <xref:System.Windows.Automation.AutomationElement> döndürür.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>, önceki <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> yönteminin döndürdüğü nesne <xref:System.Windows.Automation.AutomationElement>.|"![Embedded Image example](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")" öğesini temsil eden bozuk aralığını döndürür.|  
  
 **Örnek 2-bir metin kapsayıcısının içeriğini kısmen yaydığı bir metin aralığı. Metin kapsayıcısının metin aralığının parçası olmayan gömülü bir görüntüsü vardır.**  
  
 {Görüntü} ![Katıştırılmış görüntü örneği](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") metne eklenmiş.  
  
|Çağrılan yöntem|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|"Görüntü" dizesini döndürür.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Metin aralığını kapsayan en içteki <xref:System.Windows.Automation.AutomationElement> döndürür; Bu durumda, metin sağlayıcısının kendisini temsil eden <xref:System.Windows.Automation.AutomationElement>.|  
|parametreleriyle <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> (TextUnit. Word, 1).|Metin aralığı aralığını "." olarak kaydırır. Yalnızca metin tabanlı katıştırılmış nesneler metin akışının bir parçası olarak kabul edildiği için, bu örnekteki görüntü Move veya Return değerini etkilemez (Bu durumda 1).|  
  
<a name="Table"></a>   
### <a name="table"></a>Tablo  
  
### <a name="table-used-for-examples"></a>Örnekler için kullanılan tablo  
  
|Resim içeren hücre|Metin içeren hücre|  
|---------------------|--------------------|  
|![Katıştırılmış resim örneği](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")|X|  
|![Gömülü görüntü örneği 2](./media/uia-textpattern-embedded-objects-overview-imageexample2.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample2")|E|  
|![Katıştırılmış resim örneği 3](./media/uia-textpattern-embedded-objects-overview-imageexample3.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample3")<br /><br /> Z görüntüsü|Z|  
  
 **Örnek 1-metin kapsayıcısını bir hücrenin içeriğinden alın.**  
  
|Çağrılan yöntem|Sonuç|  
|-------------------|------------|  
|parametrelerle <xref:System.Windows.Automation.GridPattern.GetItem%2A> (0, 0)|Tablo hücresinin içeriğini temsil eden <xref:System.Windows.Automation.AutomationElement> döndürür; Bu durumda, öğe bir metin denetimidir.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>, önceki `GetItem` yönteminin döndürdüğü nesne <xref:System.Windows.Automation.AutomationElement>.|Resim ![gömülü görüntü örneğine](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")yayılan aralığı döndürür.|  
|önceki `RangeFromChild` yöntemi tarafından döndürülen nesne için <xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>.|Tablo hücresini temsil eden <xref:System.Windows.Automation.AutomationElement> döndürür; Bu durumda, öğesi TableItemPattern 'yi destekleyen bir metin denetimidir.|  
|önceki `GetEnclosingElement` yöntemi tarafından döndürülen nesne için <xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>.|Tabloyu temsil eden <xref:System.Windows.Automation.AutomationElement> döndürür.|  
|önceki `GetEnclosingElement` yöntemi tarafından döndürülen nesne için <xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>.|Metin sağlayıcısının kendisini temsil eden <xref:System.Windows.Automation.AutomationElement> döndürür.|  
  
 **Örnek 2-bir hücrenin metin içeriğini alın.**  
  
|Çağrılan yöntem|Sonuç|  
|-------------------|------------|  
|(1, 1) parametreleriyle <xref:System.Windows.Automation.GridPattern.GetItem%2A>.|Tablo hücresinin içeriğini temsil eden <xref:System.Windows.Automation.AutomationElement> döndürür; Bu durumda, öğe bir metin denetimidir.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>, önceki `GetItem` yönteminin döndürdüğü nesne <xref:System.Windows.Automation.AutomationElement>.|"Y" döndürür.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.TextPattern>
- <xref:System.Windows.Automation.Text.TextPatternRange>
- <xref:System.Windows.Automation.Provider.ITextProvider>
- <xref:System.Windows.Automation.Provider.ITextRangeProvider>
- [UI Otomasyonu Kullanarak Katıştırılmış Nesnelere Erişme](access-embedded-objects-using-ui-automation.md)
- [UI Otomasyonu Kullanarak Tablo İçeriğini Kullanıma Sunma](expose-the-content-of-a-table-using-ui-automation.md)
- [UI Otomasyonunu Kullanarak Çapraz Geçiş Yapma](traverse-text-using-ui-automation.md)
- [TextModel arama ve seçim örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FindText)
