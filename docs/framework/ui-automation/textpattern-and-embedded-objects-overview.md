---
title: TextPattern ve Katıştırılmış Nesnelere Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, TextPattern class
- embedded objects, accessing
- accessing embedded objects
- embedded objects, UI Automation
ms.assetid: 93fdfbb9-0025-4b72-8ca0-0714adbb70d5
ms.openlocfilehash: 635c06a03107b33134b015e2643c5281dd86798b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180008"
---
# <a name="textpattern-and-embedded-objects-overview"></a>TextPattern ve Katıştırılmış Nesnelere Genel Bakış
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu genel [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] bakış, katışılmış nesneleri veya alt öğeleri bir metin belgesi veya kapsayıcıda nasıl ortaya çıkardığını açıklar.  
  
 Katıştırılmış bir nesnede [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] metin selüloitleri olmayan herhangi bir öğe vardır; örneğin, Microsoft Excel elektronik tablosu veya Microsoft Windows Media dosyası gibi bir resim, köprü, tablo veya belge türü. Bu, bir öğenin bir uygulamada oluşturulduğu ve başka bir uygulamada gömülü veya bağlantılı olduğu standart tanımdan farklıdır. Nesnenin özgün uygulaması içinde düzenlenip düzenlenemeyeceği, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]'' bağlamında önemsizdir.  
  
<a name="Embedded_Objects_and_the_UI_Automation_Tree"></a>
## <a name="embedded-objects-and-the-ui-automation-tree"></a>Gömülü Nesneler ve UI Otomasyon Ağacı  
 Katıştılmış [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nesneler, ağacın denetim görünümü içinde tek tek öğeler olarak kabul edilir. Metin kapsayıcısının çocukları olarak ortaya çıkarırlar, böylece diğer denetimlerle aynı [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]model üzerinden erişilebilsinler.  
  
 ![Metin Kapsayıcısında Görüntü ile Gömülü Tablo](./media/uia-textpattern-embedded-objects-overview-example1.png "UIA_TextPattern_Embedded_Objects_Overview_Example1")  
Tablo, Resim ve Köprü Gömülü Nesneleri olan Metin Kapsayıcısı Örneği  
  
 ![Önceki örnek için içerik görünümü](./media/uia-textpattern-embedded-objects-overview-example2.PNG "UIA_TextPattern_Embedded_Objects_Overview_Example2")  
Önceki Metin Kapsayıcısının Bir Bölümü Için İçerik Görünümü Örneği  
  
<a name="Expose_Embedded_Objects_Using_TextPattern_and"></a>
## <a name="expose-embedded-objects-using-textpattern-and-textpatternrange"></a>TextPattern ve TextPatternRange kullanarak Gömülü Nesneleri Açığa  
 Birlikte kullanıldığında, <xref:System.Windows.Automation.TextPattern> denetim deseni <xref:System.Windows.Automation.Text.TextPatternRange> sınıfı ve sınıf, katışmış nesnelerin gezinmesini ve sorgulanmasını kolaylaştıran yöntem ve özellikleri ortaya çıkarır.  
  
 Bir metin kapsayıcısının ve köprü veya tablo hücresi gibi katıştırılmış bir nesnenin metin içeriği (veya iç metni), [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hem denetim görünümünde hem de ağacın içerik görünümünde tek ve sürekli bir metin akışı olarak ortaya çıkar; nesne sınırları yoksayılır. Bir Kullanıcı Arabirimi Otomasyon istemcisi metni ezberden okumak, yorumlamak veya bir şekilde çözümlemek amacıyla alıyorsa, metin aralığı metin içeriği veya diğer katıştırılmış nesneleriçeren bir tablo gibi özel durumlar için denetlenmelidir. Bu, katıştılanan <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> her <xref:System.Windows.Automation.AutomationElement> nesne için bir tane <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> almak için arayarak ve sonra her öğe için bir metin aralığı elde etmek için arayarak gerçekleştirilebilir. Tüm metin içeriği alınana kadar bu işlem özyinelemeli olarak yapılır.  
  
 ![Katıştırılmış nesneler tarafından yayılan metin aralıkları.](./media/uia-textpattern-embeddedobjecttextranges.png "UIA_TextPattern_EmbeddedObjectTextRanges")  
Katıştırılmış nesneler ve aralık aralıkları ile bir metin akışı örneği  
  
 Bir metin aralığının içeriğini geçiş yapmak gerektiğinde, <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> yöntemin başarılı bir şekilde yürütülmesi için arka planda bir dizi adım yer almaktadır.  
  
1. Metin aralığı normalleştirilmiştir; diğer bir tarihte, metin aralığı <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> bitiş noktasında dejenere bir <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> aralıkta daraltılır ve bu da bitiş noktasını gereksiz kılar. Bu adım, metin aralığının <xref:System.Windows.Automation.Text.TextUnit> sınırları kapsadığı durumlarda belirsizliği gidermek için `{The URL https://www.microsoft.com is embedded in text` gereklidir: örneğin, "{" ve "}" metin aralığı uç noktalarıdır.  
  
2. Elde edilen aralık, istenen <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> <xref:System.Windows.Automation.Text.TextUnit> sınırın başına geriye doğru taşınır.  
  
3. Aralık, istenen <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> <xref:System.Windows.Automation.Text.TextUnit> sınır sayısına göre ileri veya geri hareket ettirilir.  
  
4. Aralık daha sonra <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> bitiş noktasını istenen <xref:System.Windows.Automation.Text.TextUnit> bir sınıra taşıyarak dejenere aralık durumundan genişletilir.  
  
 ![Move & ExpandToEnclosingUnit ile aralık ayarlamaları](./media/uia-textpattern-moveandexpand-examples.png "UIA_TextPattern_MoveAndExpand_Examples")  
Bir metin aralığının Move() ve ExpandToEnclosingUnit() için nasıl ayarlanabildiğini örnekler  
  
<a name="Common_Scenarios"></a>
## <a name="common-scenarios"></a>Genel Senaryolar  
 Aşağıdaki bölümlerde katışılmış nesneleri içeren en yaygın senaryoörnekleri bulunur.  
  
 Gösterilen örnekler için gösterge:  
  
 { =<xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start>  
  
 } =<xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End>  
  
### <a name="hyperlink"></a>Köprü  

**Örnek 1 - Katışılmış metin köprüiçeren bir metin aralığı**
  
`{The URL https://www.microsoft.com is embedded in text}.`
  
|Adlı yöntem|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Dizeyi `The URL https://www.microsoft.com is embedded in text`döndürür.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Metin aralığını <xref:System.Windows.Automation.AutomationElement> içine alan en içte döndürür; bu durumda, <xref:System.Windows.Automation.AutomationElement> metin sağlayıcısının kendisini temsil eder.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Köprü <xref:System.Windows.Automation.AutomationElement> denetimini temsil eden bir verir.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>önceki <xref:System.Windows.Automation.AutomationElement> `GetChildren` yöntemle döndürülen nesne nerede.|" "'https://www.microsoft.comyi temsil eden aralığı döndürür.|  
  
 **Örnek 2 - Katıştırılmış metin köprülerini kısmen kaplayan bir metin aralığı**  
  
 URL `https://{[www]}` metin de katıştırılmış.  
  
|Adlı yöntem|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|"www" dizesini döndürür.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Metin aralığını <xref:System.Windows.Automation.AutomationElement> içine alan en içte döndürür; bu durumda, köprü kontrolü.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Metin `null` aralığı TÜM URL dizesini kapsamadığından döndürür.|  
  
**Örnek 3 - Metin kapsayıcısının içeriğini kısmen kapsayan bir metin aralığı. Metin kapsayıcısı, metin aralığının bir parçası olmayan katıştırılmış bir metin köprüye sahiptir.**  
  
`{The URL} [https://www.microsoft.com](https://www.microsoft.com) is embedded in text.`
  
|Adlı yöntem|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|"URL" dizesini döndürür.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Metin aralığını <xref:System.Windows.Automation.AutomationElement> içine alan en içte döndürür; bu durumda, <xref:System.Windows.Automation.AutomationElement> metin sağlayıcısının kendisini temsil eder.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A>parametreleri ile (TextUnit.Word, 1).|Köprü metni tek tek sözcüklerden oluştuğundan metin aralığı aralığını "http" olarak taşır. Bu durumda, köprü tek bir nesne olarak kabul edilmez.<br /><br /> {[http]} URL'si metne katıştırılmıştır.|  
  
<a name="Image"></a>
### <a name="image"></a>Görüntü  
 **Örnek 1 - Katışılmış bir resim içeren bir metin aralığı**  
  
 {Görüntü ![Gömülü Resim Örneği](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") metine katıştırılmış}.  
  
|Adlı yöntem|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|"Metine katıştırılmış" dizesini döndürür. Görüntüyle ilişkili herhangi bir ALT metninin metin akışına eklenmesi beklenemez.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Metin aralığını <xref:System.Windows.Automation.AutomationElement> içine alan en içte döndürür; bu durumda, <xref:System.Windows.Automation.AutomationElement> metin sağlayıcısının kendisini temsil eder.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Görüntü <xref:System.Windows.Automation.AutomationElement> denetimini temsil eden bir döndürür.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>önceki <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> yöntemle döndürülen nesne nerede.|" Gömülü Görüntü Örneği " ni temsil eden dejenere aralığı![döndürür.](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")|  
  
 **Örnek 2 - Metin kapsayıcısının içeriğini kısmen kapsayan bir metin aralığı. Metin kapsayıcısı, metin aralığının bir parçası olmayan katıştırılmış bir görüntüye sahiptir.**  
  
 {Resim} ![Gömülü Resim Örneği](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") metine katıştırılmış.  
  
|Adlı yöntem|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|"Görüntü" dizesini döndürür.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|Metin aralığını <xref:System.Windows.Automation.AutomationElement> içine alan en içte döndürür; bu durumda, <xref:System.Windows.Automation.AutomationElement> metin sağlayıcısının kendisini temsil eder.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A>parametreleri ile (TextUnit.Word, 1).|Metin aralığı aralığını "is" olarak taşır. Yalnızca metin tabanlı katıştirilen nesneler metin akışının bir parçası olarak kabul edilir, bu örnekteki görüntü Taşı veya dönüş değerini etkilemez (bu durumda 1).|  
  
<a name="Table"></a>
### <a name="table"></a>Tablo  
  
### <a name="table-used-for-examples"></a>Örnekler için kullanılan tablo  
  
|Görüntü ile Hücre|Metinli Hücre|  
|---------------------|--------------------|  
|![Gömülü Resim Örneği](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")|X|  
|![Gömülü Resim Örneği 2](./media/uia-textpattern-embedded-objects-overview-imageexample2.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample2")|E|  
|![Gömülü Resim Örnek 3](./media/uia-textpattern-embedded-objects-overview-imageexample3.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample3")<br /><br /> Z için resim|Z|  
  
 **Örnek 1 - Metin kapsayıcısını bir hücrenin içeriğinden alın.**  
  
|Yöntem Called|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A>parametreleri ile (0,0)|Tablo <xref:System.Windows.Automation.AutomationElement> hücresinin içeriğini temsil eden iverir; bu durumda, öğe bir metin denetimidir.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>önceki <xref:System.Windows.Automation.AutomationElement> `GetItem` yöntemle döndürülen nesne nerede.|![Görüntü Gömülü Resim Örneği'ni](./media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")kapsayan aralığı döndürür.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>önceki `RangeFromChild` yöntemle döndürülen nesne için.|Tablo <xref:System.Windows.Automation.AutomationElement> hücresini temsil edeni döndürür; Bu durumda, öğe TableItemPattern destekleyen bir metin denetimidir.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>önceki `GetEnclosingElement` yöntemle döndürülen nesne için.|Tabloyu <xref:System.Windows.Automation.AutomationElement> temsil edeni döndürür.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>önceki `GetEnclosingElement` yöntemle döndürülen nesne için.|Metin <xref:System.Windows.Automation.AutomationElement> sağlayıcısının kendisini temsil edeni döndürür.|  
  
 **Örnek 2 - Bir hücrenin metin içeriğini alın.**  
  
|Yöntem Called|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A>parametreleri ile (1,1).|Tablo <xref:System.Windows.Automation.AutomationElement> hücresinin içeriğini temsil eden iverir; bu durumda, öğe bir metin denetimidir.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>önceki <xref:System.Windows.Automation.AutomationElement> `GetItem` yöntemle döndürülen nesne nerede.|"Y"yi döndürür.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.TextPattern>
- <xref:System.Windows.Automation.Text.TextPatternRange>
- <xref:System.Windows.Automation.Provider.ITextProvider>
- <xref:System.Windows.Automation.Provider.ITextRangeProvider>
- [UI Otomasyonu Kullanarak Katıştırılmış Nesnelere Erişme](access-embedded-objects-using-ui-automation.md)
- [UI Otomasyonu Kullanarak Tablo İçeriğini Kullanıma Sunma](expose-the-content-of-a-table-using-ui-automation.md)
- [UI Otomasyonunu Kullanarak Çapraz Geçiş Yapma](traverse-text-using-ui-automation.md)
- [TextPattern Arama ve Seçim Örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FindText)
