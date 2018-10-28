---
title: TextPattern ve Katıştırılmış Nesnelere Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, TextPattern class
- embedded objects, accessing
- accessing embedded objects
- embedded objects, UI Automation
ms.assetid: 93fdfbb9-0025-4b72-8ca0-0714adbb70d5
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 78c511555065528d1ab34ee3ec9f8859a15bbc61
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194110"
---
# <a name="textpattern-and-embedded-objects-overview"></a>TextPattern ve Katıştırılmış Nesnelere Genel Bakış
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu genel bakış açıklar nasıl [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] kullanıma sunan katıştırılmış nesneler veya bir metin belgesi veya kapsayıcı içinde alt öğeleri.  
  
 İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] katıştırılmış nesne metinsel olmayan sınırları olan herhangi bir öğenin; Örneğin, bir görüntü, köprü, tablo veya belge türü gibi bir [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] elektronik tablo veya [!INCLUDE[TLA#tla_winmedia](../../../includes/tlasharptla-winmedia-md.md)] dosya. Bu, burada bir öğe bir uygulamada oluşturulduğunda ve gömülü veya bağlantılı, içinde başka bir standart tanımlı farklıdır. Nesne özgün uygulamasına içinde düzenlenebilir olup olmadığını bağlamında ilgisizdir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Embedded_Objects_and_the_UI_Automation_Tree"></a>   
## <a name="embedded-objects-and-the-ui-automation-tree"></a>Katıştırılmış nesneler ve UI Otomasyon ağacı  
 Katıştırılmış nesneler kontrol görünümündeki tek tek öğeleri olarak kabul edilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç. Bunlar aynı erişilebilir olduğunu metin kapsayıcısını alt diğer denetimleri model olarak sunulan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
 ![Bir metin kapsayıcıda görüntü tabloyla katıştırılmış](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-example1.png "UIA_TextPattern_Embedded_Objects_Overview_Example1")  
Tablo, görüntü ve köprü metni kapsayıcıyla örneği katıştırılmış nesneler  
  
 ![İçerik görünümü önceki örneğin](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-example2.PNG "UIA_TextPattern_Embedded_Objects_Overview_Example2")  
Önceki metin kapsayıcı bir kısmı için içerik görünümü örneği  
  
<a name="Expose_Embedded_Objects_Using_TextPattern_and"></a>   
## <a name="expose-embedded-objects-using-textpattern-and-textpatternrange"></a>TextPattern ve TextPatternRange kullanarak katıştırılmış nesnelere kullanıma sunma  
 Birlikte kullanılan <xref:System.Windows.Automation.TextPattern> denetim düzeni sınıfı ve <xref:System.Windows.Automation.Text.TextPatternRange> sınıfı yöntemleri ve özellikleri, gezinti ve katıştırılmış nesnelerin sorgulama işlemlerini gerçekleştiren kullanıma sunar.  
  
 Denetim ve içerik görünümünde hem tek, sürekli bir metin akışında olarak metin kapsayıcısını ve katıştırılmış nesne, köprü veya tablo hücresi gibi metinsel içeriği (veya iç metni) gösterilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç; nesne, sınırlar yok sayılır. UI Otomasyonu istemci reciting, yorumlama veya herhangi bir biçimde çözümleme amacıyla metin alıyorsa, metinsel içerik veya katıştırılmış nesneleri içeren bir tablo gibi özel durumlar için metin aralığı denetlenmelidir. Bu çağrı yaparak da gerçekleştirilebilir <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> almak için bir <xref:System.Windows.Automation.AutomationElement> her nesne ve ardından arama embedded için <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> her öğe için bir metin aralığını elde edilir. Tüm metin içeriği alınıncaya kadar bu yinelemeli olarak gerçekleştirilir.  
  
 ![Katıştırılmış nesneler tarafından kaplanan metin aralıkları ](../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjecttextranges.png "UIA_TextPattern_EmbeddedObjectTextRanges")  
Katıştırılmış nesneler ve onların aralığı yayılma ile metin akışına örneği  
  
 Bir metin aralığını içeriğini geçirmek gerekli olduğunda, bir dizi adım söz konusu sırasını arka planda <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> yöntemi başarıyla yürütülemedi.  
  
1.  Metin aralığı normalleştirilmiş; diğer bir deyişle, metin aralığı bozuk bir aralıkta için daraltılmış <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> getiren endpoint <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> gereksiz uç noktası. Bir metin aralığını nereden yayılan durumlarda belirsizliğini kaldırmak bu adım gereklidir <xref:System.Windows.Automation.Text.TextUnit> sınırları: Örneğin, `{The URL https://www.microsoft.com is embedded in text` burada "{" ve "}" metin aralığı noktalarıdır.  
  
2.  Elde edilen aralığın geriye taşınır <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> istenen başlangıcına <xref:System.Windows.Automation.Text.TextUnit> sınır.  
  
3.  Aralığın ileriye veya geriye doğru de taşınır <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> istenen sayısına göre <xref:System.Windows.Automation.Text.TextUnit> sınırlar.  
  
4.  Aralığın taşıyarak bozuk aralığı durumundan ardından Genişletilmiş <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> uç noktası tarafından istenen bir <xref:System.Windows.Automation.Text.TextUnit> sınır.  
  
 ![Aralık & Yukarı Taşı göe tarafından ayarlamalar](../../../docs/framework/ui-automation/media/uia-textpattern-moveandexpand-examples.png "UIA_TextPattern_MoveAndExpand_Examples")  
Bir metin aralığını Move() ve ExpandToEnclosingUnit() için nasıl ayarlandığını örnekleri  
  
<a name="Common_Scenarios"></a>   
## <a name="common-scenarios"></a>Yaygın senaryolar  
 Aşağıdaki bölümlerde, katıştırılmış nesneleri içeren en yaygın senaryoları örnekleri sunar.  
  
 Gösterge gösterilen örneklerden için:  
  
 { = <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start>  
  
 } = <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End>  
  
### <a name="hyperlink"></a>Köprü  

**Örnek 1 - katıştırılmış bir köprü içeren bir metin aralığı**
  
`{The URL https://www.microsoft.com is embedded in text}.`
  
|Yöntemi|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Dizeyi döndürür `The URL https://www.microsoft.com is embedded in text`.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|En içteki döndürür <xref:System.Windows.Automation.AutomationElement> , metin aralığı alır; bu durumda, <xref:System.Windows.Automation.AutomationElement> temsil eden metin sağlayıcısı.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Döndürür bir <xref:System.Windows.Automation.AutomationElement> köprü denetimini temsil eden.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> Burada <xref:System.Windows.Automation.AutomationElement> önceki tarafından döndürülen nesne `GetChildren` yöntemi.|Gösteren aralığını döndürür "https://www.microsoft.com".|  
  
 **Örnek 2 - katıştırılmış bir köprü kısmen yayılan bir metin aralığı**  
  
 URL `https://{[www]}` metinde katıştırılır.  
  
|Yöntemi|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|"Www" dizesini döndürür.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|En içteki döndürür <xref:System.Windows.Automation.AutomationElement> , metin aralığı alır; bu durumda, köprü denetim.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Döndürür `null` olduğundan tüm URL dizesi metin aralığını kapsayan değil.|  
  
**Örnek 3 - bir metin kapsayıcı içeriğini kısmen yayılan bir metin aralığı. Metin aralığı bir parçası olmayan bir ekli metinleri köprü metin kapsayıcı vardır.**  
  
`{The URL} [https://www.microsoft.com](https://www.microsoft.com) is embedded in text.`
  
|Yöntemi|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|"URL" dizesini döndürür.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|En içteki döndürür <xref:System.Windows.Automation.AutomationElement> , metin aralığı alır; bu durumda, <xref:System.Windows.Automation.AutomationElement> temsil eden metin sağlayıcısı.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> (TextUnit.Word, 1) parametreleriyle.|Köprü metni tek sözcüklük oluşan bu yana metin aralığı yayılma "http" taşır. Bu durumda, köprüyü tek bir nesne olarak işlenmez.<br /><br /> {[Http]} URL metin olarak eklenir.|  
  
<a name="Image"></a>   
### <a name="image"></a>Görüntü  
 **Örnek 1 - bir katıştırılmış resim içeren bir metin aralığı**  
  
 {Görüntü ![katıştırılmış resim örneği](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") metinde katıştırılmış}.  
  
|Yöntemi|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Dizeyi döndürür "metninde katıştırılmış". Görüntüyle ilişkilendirilen herhangi bir ALT metin metin akışında dahil edilecek beklenen olamaz.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|En içteki döndürür <xref:System.Windows.Automation.AutomationElement> , metin aralığı alır; bu durumda, <xref:System.Windows.Automation.AutomationElement> temsil eden metin sağlayıcısı.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Döndürür bir <xref:System.Windows.Automation.AutomationElement> görüntü denetimini temsil eden.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> Burada <xref:System.Windows.Automation.AutomationElement> önceki tarafından döndürülen nesne <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> yöntemi.|Gösteren bozuk aralığını döndürür "![katıştırılmış resim örneği](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")".|  
  
 **Örnek 2 - bir metin kapsayıcı içeriğini kısmen yayılan bir metin aralığı. Metin aralığı bir parçası olmayan bir katıştırılmış resim metin kapsayıcı vardır.**  
  
 {} Görüntüsü ![Katıştırılmış resim örneği](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") metinde katıştırılır.  
  
|Yöntemi|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|"İmage" dizesini döndürür.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|En içteki döndürür <xref:System.Windows.Automation.AutomationElement> , metin aralığı alır; bu durumda, <xref:System.Windows.Automation.AutomationElement> temsil eden metin sağlayıcısı.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> (TextUnit.Word, 1) parametreleriyle.|"İs" için metin aralığı aralık taşır. Yalnızca metin tabanlı katıştırılmış nesneler metin akışına bir parçası olarak kabul edilir, çünkü bu örnekte görüntü taşıma veya dönüş değerini (Bu durumda 1) etkilemez.|  
  
<a name="Table"></a>   
### <a name="table"></a>Tablo  
  
### <a name="table-used-for-examples"></a>Örnekler için kullanılan tablo  
  
|Hücre resmi|Metin hücresi|  
|---------------------|--------------------|  
|![Katıştırılmış Resim örneği](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")|X|  
|![Katıştırılmış Resim örneği 2](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample2.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample2")|Y|  
|![Katıştırılmış Resim örneği 3](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample3.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample3")<br /><br /> Görüntü için Z|Z|  
  
 **Örnek 1 - bir hücrenin içeriğini metin kapsayıcıya alın.**  
  
|Adlı yöntemi|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A> parametrelerle (0,0)|Döndürür <xref:System.Windows.Automation.AutomationElement> ; tablo hücresi içeriğini temsil eden bu durumda, bir metin denetimi öğedir.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> Burada <xref:System.Windows.Automation.AutomationElement> önceki tarafından döndürülen nesne `GetItem` yöntemi.|Görüntü yayılan bir aralık verir ![katıştırılmış resim örneği](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample").|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A> Önceki tarafından döndürülen nesne için `RangeFromChild` yöntemi.|Döndürür <xref:System.Windows.Automation.AutomationElement> ; tablo hücresi temsil eden bu durumda, TableItemPattern destekleyen bir metin denetimi öğedir.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A> Önceki tarafından döndürülen nesne için `GetEnclosingElement` yöntemi.|Döndürür <xref:System.Windows.Automation.AutomationElement> tablosunu temsil eden.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A> Önceki tarafından döndürülen nesne için `GetEnclosingElement` yöntemi.|Döndürür <xref:System.Windows.Automation.AutomationElement> temsil eden metin sağlayıcısı.|  
  
 **Örnek 2 - bir hücre metin içeriğini alır.**  
  
|Adlı yöntemi|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A> (1,1) parametreleriyle.|Döndürür <xref:System.Windows.Automation.AutomationElement> ; tablo hücresi içeriğini temsil eden bu durumda, bir metin denetimi öğedir.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> Burada <xref:System.Windows.Automation.AutomationElement> önceki tarafından döndürülen nesne `GetItem` yöntemi.|Döndürür "Y".|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Automation.TextPattern>  
 <xref:System.Windows.Automation.Text.TextPatternRange>  
 <xref:System.Windows.Automation.Provider.ITextProvider>  
 <xref:System.Windows.Automation.Provider.ITextRangeProvider>  
 [UI Otomasyonu Kullanarak Katıştırılmış Nesnelere Erişme](../../../docs/framework/ui-automation/access-embedded-objects-using-ui-automation.md)  
 [UI Otomasyonu Kullanarak Tablo İçeriğini Kullanıma Sunma](../../../docs/framework/ui-automation/expose-the-content-of-a-table-using-ui-automation.md)  
 [UI Otomasyonunu Kullanarak Çapraz Geçiş Yapma](../../../docs/framework/ui-automation/traverse-text-using-ui-automation.md)  
 [TextPattern arama ve seçim örneği](https://msdn.microsoft.com/library/0a3bca57-8b72-489d-a57c-da85b7a22c7f)
