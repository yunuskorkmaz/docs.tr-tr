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
manager: markl
ms.openlocfilehash: ab732ffedfbe05b1b246d8d8eef1c374e223eb39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="textpattern-and-embedded-objects-overview"></a>TextPattern ve Katıştırılmış Nesnelere Genel Bakış
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu genel bakış açıklanmaktadır nasıl [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] çıkarır katıştırılmış nesneler veya bir metin belgesi veya kapsayıcı içindeki alt öğe.  
  
 İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] katıştırılmış nesne metinsel olmayan sınırları sahip herhangi bir öğe; örneğin, bir görüntü, köprü, tablo veya belge türü gibi bir [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] elektronik tablo veya [!INCLUDE[TLA#tla_winmedia](../../../includes/tlasharptla-winmedia-md.md)] dosyası. Bu, burada bir öğenin bir uygulama içinde oluşturulan ve katıştırılmış veya bağlantılı, içinde başka bir standart tanımı farklıdır. Nesne özgün uygulamasına içinde düzenlenip düzenlenemeyeceğini bağlamında ilgisiz [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
<a name="Embedded_Objects_and_the_UI_Automation_Tree"></a>   
## <a name="embedded-objects-and-the-ui-automation-tree"></a>Katıştırılmış nesneler ve UI Otomasyon ağacı  
 Katıştırılmış nesneler denetim görünümü içinde ayrı ayrı öğeler olarak kabul edilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı. Böylece bunlar aynı erişilebilen diğer denetimlerinde metin kapsayıcı alt model olarak kullanıma sunulan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
 ![Bir metin kapsayıcısında görüntü tabloyla katıştırılmış](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-example1.png "UIA_TextPattern_Embedded_Objects_Overview_Example1")  
Tablo, görüntü ve köprü metni kapsayıcıyla örneği katıştırılmış nesneler  
  
 ![İçerik görünümü önceki örnek için](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-example2.PNG "UIA_TextPattern_Embedded_Objects_Overview_Example2")  
Önceki metin kapsayıcı bir kısmı için içerik görünümü örneği  
  
<a name="Expose_Embedded_Objects_Using_TextPattern_and"></a>   
## <a name="expose-embedded-objects-using-textpattern-and-textpatternrange"></a>TextPattern ve TextPatternRange kullanarak katıştırılmış nesnelere kullanıma sunma  
 Birlikte kullanılan <xref:System.Windows.Automation.TextPattern> denetim düzeni sınıfı ve <xref:System.Windows.Automation.Text.TextPatternRange> sınıfı yöntemleri ve gezinti ve katıştırılmış nesnelerin sorgulama kolaylaştırmak özellikleri kullanıma sunar.  
  
 Denetim Görünüm ve içerik görünümünü tek, sürekli metin akışında olarak metin kapsayıcı ve katıştırılmış nesneler, köprü veya tablo hücresinin gibi metinsel içeriği (veya iç metni) sunulan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç; sınırları yoksayılır nesne. UI Otomasyonu istemci reciting, yorumlama veya bazı şekilde çözümleme amacıyla metin alıyorsa, metin aralığını metinsel içerik veya diğer katıştırılmış nesneler içeren bir tablo gibi özel durumlar için denetlenmelidir. Bu çağırarak gerçekleştirilebilir <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> elde etmek için bir <xref:System.Windows.Automation.AutomationElement> her nesne ve ardından çağırma katıştırılmış için <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> her öğe için bir metin aralığını elde edilir. Tüm metin içeriği alınan kadar bu yinelemeli olarak gerçekleştirilir.  
  
 ![Katıştırılmış nesneler tarafından yayılan metin aralıkları. ] (../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjecttextranges.png "UIA_TextPattern_EmbeddedObjectTextRanges")  
Katıştırılmış nesneler ve onların aralığı yayılma olan bir metin akış örneği  
  
 Bir metin aralığını içeriğini çapraz geçiş için gerekli olduğunda, bir dizi adımı söz konusu arka planda sırayla <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> başarıyla yürütülecek yöntem.  
  
1.  Metin aralığını normalleştirilmiş; diğer bir deyişle, bozuk bir aralıkta için metin aralığını daraltılmış <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> yapar uç nokta <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> gereksiz uç noktası. Burada bir metin aralığını kapsayan durumlarda belirsizliğini kaldırmak bu adım gereklidir <xref:System.Windows.Automation.Text.TextUnit> sınırları: Örneğin, "{U} RL [ http://www.microsoft.com ](http://www.microsoft.com) metinde katıştırılmış" burada "{" ve "}" metin aralığı noktalarıdır.  
  
2.  Sonuçta elde edilen aralığı geriye doğru taşınmış <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> istenen başlangıcına <xref:System.Windows.Automation.Text.TextUnit> sınır.  
  
3.  Aralığın ileriye veya geriye doğru olarak taşınır <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> istenen sayısına göre <xref:System.Windows.Automation.Text.TextUnit> sınırlar.  
  
4.  Aralığın taşıyarak bozuk aralığı durumdan sonra Genişletilmiş <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> bitiş noktası tarafından istenen bir <xref:System.Windows.Automation.Text.TextUnit> sınır.  
  
 ![Aralık taşıma & göe tarafından ayarlamalar](../../../docs/framework/ui-automation/media/uia-textpattern-moveandexpand-examples.png "UIA_TextPattern_MoveAndExpand_Examples")  
Bir metin aralığını Move() ve ExpandToEnclosingUnit() için nasıl ayarlanacağını örnekleri  
  
<a name="Common_Scenarios"></a>   
## <a name="common-scenarios"></a>Yaygın senaryolar  
 Aşağıdaki bölümlerde katıştırılmış nesneler ilgili yaygın senaryolar örnekleri sunar.  
  
 Gösterge örneklerde için:  
  
 { = <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start>  
  
 } = <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End>  
  
<a name="Hyperlink"></a>   
### <a name="hyperlink"></a>Köprü  
 **Örnek 1 - katıştırılmış bir köprü içeren bir metin aralığını**  
  
 {URL [ http://www.microsoft.com ](http://www.microsoft.com) metinde katıştırılmış}.  
  
|Adlı yöntemi|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Bir dize döndürür "URL http://www.microsoft.com metinde katıştırılmış".|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|En içteki döndürür <xref:System.Windows.Automation.AutomationElement> metin aralığını alır; bu durumda, <xref:System.Windows.Automation.AutomationElement> , metin sağlayıcısını temsil eder.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Döndürür bir <xref:System.Windows.Automation.AutomationElement> köprü denetimini temsil eden.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> Burada <xref:System.Windows.Automation.AutomationElement> önceki tarafından döndürülen nesne `GetChildren` yöntemi.|Gösteren aralığını döndürür "http://www.microsoft.com".|  
  
 **Örnek 2 - kısmen katıştırılmış bir köprü yayılan bir metin aralığını**  
  
 URL http://{[www]} metin olarak katıştırılır.  
  
|Adlı yöntemi|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|"Www" dizesini döndürür.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|En içteki döndürür <xref:System.Windows.Automation.AutomationElement> metin aralığını alır; bu durumda, köprü denetim.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Döndürür `null` metin aralığını tüm URL dizesi span değil bu yana.|  
  
 **Örnek 3 - bir metin kapsayıcı içeriğini kısmen yayılan bir metin aralığını. Metin kapsayıcısı metin aralığının parçası olmayan bir katıştırılmış köprü metni içerir.**  
  
 {URL} [ http://www.microsoft.com ](http://www.microsoft.com) metin olarak katıştırılır.  
  
|Adlı yöntemi|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|"URL" dizesini döndürür.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|En içteki döndürür <xref:System.Windows.Automation.AutomationElement> metin aralığını alır; bu durumda, <xref:System.Windows.Automation.AutomationElement> , metin sağlayıcısını temsil eder.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> (TextUnit.Word, 1) parametrelerle.|Köprü metni tek tek sözcüklük oluşan bu yana metin aralığı aralık "http" taşır. Bu durumda, köprüyü tek bir nesne olarak işlenmez.<br /><br /> {[Http]} URL metin olarak katıştırılır.|  
  
<a name="Image"></a>   
### <a name="image"></a>Görüntü  
 **Örnek 1 - bir katıştırılmış resim içeren bir metin aralığını**  
  
 {Görüntü ![katıştırılmış resim örneği](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") metinde katıştırılmış}.  
  
|Adlı yöntemi|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|Bir dize döndürür "metinde katıştırılmış". Görüntüsü ile ilişkili herhangi bir ALT metin metin akışında eklenmesi beklenen olamaz.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|En içteki döndürür <xref:System.Windows.Automation.AutomationElement> metin aralığını alır; bu durumda, <xref:System.Windows.Automation.AutomationElement> , metin sağlayıcısını temsil eder.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A>|Döndürür bir <xref:System.Windows.Automation.AutomationElement> resim denetimini temsil eden.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> Burada <xref:System.Windows.Automation.AutomationElement> önceki tarafından döndürülen nesne <xref:System.Windows.Automation.Text.TextPatternRange.GetChildren%2A> yöntemi.|Gösteren bozuk aralığını döndürür "![katıştırılmış resim örneği](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")".|  
  
 **Örnek 2 - bir metin kapsayıcı içeriğini kısmen yayılan bir metin aralığını. Metin kapsayıcısı metin aralığını parçası olmayan bir katıştırılmış resim içerir.**  
  
 {Görüntünün} ![Katıştırılmış resim örneği](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample") metin olarak katıştırılır.  
  
|Adlı yöntemi|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>|"Görüntü" dizesini döndürür.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A>|En içteki döndürür <xref:System.Windows.Automation.AutomationElement> metin aralığını alır; bu durumda, <xref:System.Windows.Automation.AutomationElement> , metin sağlayıcısını temsil eder.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> (TextUnit.Word, 1) parametrelerle.|Metin aralığı aralık "olduğu için" taşır. Yalnızca metin tabanlı katıştırılmış nesneler metin akış parçası olarak kabul edilir çünkü bu örnekte görüntü taşıma veya dönüş değeri (1 Bu durumda) etkilemez.|  
  
<a name="Table"></a>   
### <a name="table"></a>Tablo  
  
### <a name="table-used-for-examples"></a>Örnekler için kullanılan tablo  
  
|Görüntü ile hücre|Metni hücrenin|  
|---------------------|--------------------|  
|![Katıştırılmış Resim örneği](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample")|X|  
|![Katıştırılmış Resim örneği 2](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample2.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample2")|Y|  
|![Görüntü örnek 3 katıştırılmış](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample3.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample3")<br /><br /> Z görüntüsü|Z|  
  
 **Örnek 1 - bir hücre içerikten metin kapsayıcısını alır.**  
  
|Adlı yöntemi|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A> parametrelerle (0,0)|Döndürür <xref:System.Windows.Automation.AutomationElement> ; tablo hücresi içeriğini temsil eden bu durumda, bir metin denetimini öğedir.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> Burada <xref:System.Windows.Automation.AutomationElement> önceki tarafından döndürülen nesne `GetItem` yöntemi.|Görüntü yayılan aralık verir ![katıştırılmış resim örneği](../../../docs/framework/ui-automation/media/uia-textpattern-embedded-objects-overview-imageexample.PNG "UIA_TextPattern_Embedded_Objects_Overview_ImageExample").|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A> Önceki tarafından döndürülen nesne için `RangeFromChild` yöntemi.|Döndürür <xref:System.Windows.Automation.AutomationElement> ; tablo hücresi temsil eden bu durumda, TableItemPattern destekleyen bir metin denetimini öğedir.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A> Önceki tarafından döndürülen nesne için `GetEnclosingElement` yöntemi.|Döndürür <xref:System.Windows.Automation.AutomationElement> tablo temsil eden.|  
|<xref:System.Windows.Automation.Text.TextPatternRange.GetEnclosingElement%2A> Önceki tarafından döndürülen nesne için `GetEnclosingElement` yöntemi.|Döndürür <xref:System.Windows.Automation.AutomationElement> , metin sağlayıcısını temsil eder.|  
  
 **Örnek 2 - bir hücre metin içeriğini alın.**  
  
|Adlı yöntemi|Sonuç|  
|-------------------|------------|  
|<xref:System.Windows.Automation.GridPattern.GetItem%2A> (1,1) parametrelerle.|Döndürür <xref:System.Windows.Automation.AutomationElement> ; tablo hücresi içeriğini temsil eden bu durumda, bir metin denetimini öğedir.|  
|<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> Burada <xref:System.Windows.Automation.AutomationElement> önceki tarafından döndürülen nesne `GetItem` yöntemi.|Döndürür "Y".|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Automation.TextPattern>  
 <xref:System.Windows.Automation.Text.TextPatternRange>  
 <xref:System.Windows.Automation.Provider.ITextProvider>  
 <xref:System.Windows.Automation.Provider.ITextRangeProvider>  
 [UI Otomasyonu Kullanarak Katıştırılmış Nesnelere Erişme](../../../docs/framework/ui-automation/access-embedded-objects-using-ui-automation.md)  
 [UI Otomasyonu Kullanarak Tablo İçeriğini Kullanıma Sunma](../../../docs/framework/ui-automation/expose-the-content-of-a-table-using-ui-automation.md)  
 [UI Otomasyonunu Kullanarak Çapraz Geçiş Yapma](../../../docs/framework/ui-automation/traverse-text-using-ui-automation.md)  
 [TextPattern arama ve seçim örneği](http://msdn.microsoft.com/library/0a3bca57-8b72-489d-a57c-da85b7a22c7f)
