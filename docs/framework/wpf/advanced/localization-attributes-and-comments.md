---
title: Yerelleştirme Öznitelikleri ve Yorumlar
ms.date: 03/30/2017
helpviewer_keywords:
- localization [WPF], attributes
- localization [WPF], comments
ms.assetid: ead2d9ac-b709-4ec1-a924-39927a29d02f
ms.openlocfilehash: 4e4c4891a905a5e4458ad5fc21a512c1dfe6f74e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092922"
---
# <a name="localization-attributes-and-comments"></a>Yerelleştirme Öznitelikleri ve Yorumlar
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Yerelleştirme açıklamalarını olan özellikleri içinde [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] kaynak kodu, kurallar ve ipuçları için yerelleştirme sağlamak için geliştiriciler tarafından sağlanan. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Yerelleştirme açıklamalarını iki bilgi kümesi içerir: Yerelleştirme öznitelikleri ve serbest biçimli yerelleştirme yorumlar. Yerelleştirme öznitelikleri tarafından kullanılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerelleştirme hangi kaynakların yerelleştirilmesi belirtmek için API. Serbest biçimli, uygulama yazarı eklemek isteyen herhangi bir bilgi yorumlardır.  

<a name="Localizer_Comments_"></a>   
## <a name="localization-comments"></a>Yerelleştirme açıklamalarını  
 Biçimlendirme uygulama yazarları belirli öğeleri için gereksinimler varsa [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)], metin uzunluğu, yazı tipi ailesi veya yazı tipi boyutu gibi kısıtlamalar, bu bilgileri yerelleştiriciler açıklamalar ile ifade edebilir [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] kod. Kaynak koda açıklama ekleme işlemi aşağıdaki gibidir:  
  
1.  Uygulama geliştiricileri için yerelleştirme açıklamalarını ekler [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] kaynak kodu.  
  
2.  Derleme işlemi sırasında .proj dosyasında serbest biçimli yerelleştirme derleme, Yorumlar parçası atmak veya tüm yorumları atmak yorumlarında verilip verilmeyeceğini belirtebilirsiniz. Çıkarılan yorumlar, ayrı bir dosyada yer alır. Seçeneğini kullanarak belirttiğiniz bir `LocalizationDirectivesToLocFile` etiketi, örneğin:  
  
     `<LocalizationDirectivesToLocFile>` *value* `</LocalizationDirectivesToLocFile>`  
  
3.  Atanabilecek değerleri şunlardır:  
  
    -   **Hiçbiri** -hem açıklamalarını ve özniteliklerini derleme içinde kalır, hem de ayrı bir dosya oluşturulur.  
  
    -   **CommentsOnly** - derleme yalnızca açıklamalardan ve bunları ayrı LocFile içine yerleştirir.  
  
    -   **Tüm** - açıklamaları hem de derleme öznitelikleri ve bunları iki ayrı bir LocFile içine yerleştirir.  
  
4.  Gelen yerelleştirilebilir kaynaklar ayıklanırken [!INCLUDE[TLA2#tla_baml](../../../../includes/tla2sharptla-baml-md.md)], Yerelleştirme öznitelikleri tarafından uymaya [!INCLUDE[TLA2#tla_baml](../../../../includes/tla2sharptla-baml-md.md)] yerelleştirme API'si.  
  
5.  Yalnızca serbest biçimli açıklamalar içeren yerelleştirme yorum dosyaları daha sonraki bir zamanda yerelleştirme işlemine dahil edilir.  
  
 Aşağıdaki örnek, yerelleştirme açıklamalarını ekleme işlemi gösterilmektedir bir [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] dosya.  
  
 `<TextBlock x:Id = "text01"`  
  
 `FontFamily = "Microsoft Sans Serif"`  
  
 `FontSize = "12"`  
  
 `Localization.Attributes = "$Content (Unmodifiable Readable Text)`  
  
 `FontFamily (Unmodifiable Readable)"`  
  
 `Localization.Comments = "$Content (Trademark)`  
  
 `FontSize (Trademark font size)" >`  
  
 `Microsoft`  
  
 `</TextBlock>`  
  
 Önceki örnekte Localization.Attributes Yerelleştirme öznitelikleri ve Localization.Comments bölüm serbest biçimli Açıklamalar bölümü içerir. Aşağıdaki tablolarda, öznitelikleri ve yorumlar ve bunların anlamları yerelleştiriciye gösterilmektedir.  
  
|Yerelleştirme öznitelikleri|Açıklama|  
|-----------------------------|-------------|  
|$Content (değiştirilemeyen okunabilir metin)|TextBlock öğe içeriklerinin değiştirilemez. "Microsoft" sözcüğünü yerelleştiriciler değiştiremezsiniz. İçeriği yerelleştiriciye görünür (okunabilir) olur. Metin içeriği kategorisidir.|  
|FontFamily (değiştirilemeyen okunabilir)|TextBlock öğesinin yazı tipi ailesi özelliği değiştirilemez, ancak yerelleştiriciye görünür olur.|  
  
|Yerelleştirme serbest biçimli açıklamalar|Açıklama|  
|--------------------------------------|-------------|  
|$Content (ticari)|Uygulama yazarı TextBlock öğe içeriğinde ticari markasıdır yerelleştiriciye söyler.|  
|FontSize (ticari marka yazı tipi boyutu)|Uygulama yazarı, yazı tipi boyutu özelliğinin standart ticari marka boyutu izlemesi gerektiğini gösterir.|  
  
### <a name="localizability-attributes"></a>Yerelleştirme öznitelikleri  
 Çiftlerinin listesini Localization.Attributes bilgileri içerir: hedef değer adını ve ilişkili yerelleştirme değerleri. Hedef adı, özellik adı veya özel $Content adı olabilir. Bir özellik adı ise, hedeflenen özelliğinin değeri değerdir. $Content ise, hedef öğenin içeriğini değerdir.  
  
 Öznitelik üç tür vardır:  
  
-   **Kategori**. Bu değer bir yerelleştiriciye aracından değiştirilebilir olup olmayacağını belirtir. Bkz. <xref:System.Windows.LocalizabilityAttribute.Category%2A>.  
  
-   **Okunabilirlik**. Bu bir yerelleştiriciye aracı gerekip gerekmediğini belirten bir değer okuma (ve görüntüleme). Bkz. <xref:System.Windows.LocalizabilityAttribute.Readability%2A>.  
  
-   **Modifiability'e göre**. Bu, bir yerelleştiriciye aracı değiştirilmesi için bir değer izin verip vermediğini belirtir. Bkz. <xref:System.Windows.LocalizabilityAttribute.Modifiability%2A>.  
  
 Bu öznitelikler, boşlukla ayrılmış herhangi bir sırada belirtilebilir. Yinelenen öznitelikleri belirtilmesi durumunda, son özniteliğini eski olanları geçersiz kılar. Örneğin, Localization.Attributes son değeri olduğundan "Değiştirilemeyen değiştirilebilir" kümeleri Modifiability'i Modifiable =.  
  
 Modifiability'e göre ve okunabilirliği kendinden açıklamalıdır. Category özniteliği metin çevirme yerelleştiriciye yardımcı tanımlanmış kategorilerle sağlar. Kategorileri gibi metin, etiket ve başlık metni çevirmek nasıl yerelleştiriciye bilgi verin. Özel kategori vardır: None, devralma, Ignore ve NeverLocalize.  
  
 Aşağıdaki tabloda özel kategoriler anlamını gösterilmektedir.  
  
|Kategori|Açıklama|  
|--------------|-------------|  
|Yok.|Hedeflenen değeri tanımlı hiçbir kategori vardır.|  
|Devral|Hedeflenen değeri, kategori, üst öğeden devralır.|  
|Yoksayma|Hedeflenen değeri yerelleştirme işleminde göz ardı edilir. Yoksay yalnızca geçerli değer etkiler. Alt düğümleri etkilemez.|  
|NeverLocalize|Geçerli değer yerelleştirilemez. Bu kategori, öğenin alt gruplar tarafından devralınır.|  
  
<a name="Localization_Comments"></a>   
## <a name="localization-comments"></a>Yerelleştirme açıklamalarını  
 Localization.Comments hedeflenen değeri ile ilgili serbest biçimli dizeleri içerir. Uygulama geliştiricileri, çevirmenlerin vermek için bilgi ekleyebileceğiniz uygulamaların metnin nasıl çevrileceği hakkında ipuçları. Yorumları biçimi arasına "(") tarafından herhangi bir dize olabilir. Kullanım '\\' kaçış karakterleri için.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF için Genelleştirme](globalization-for-wpf.md)
- [Düğme Oluşturmak için Otomatik Düzeni Kullanma](how-to-use-automatic-layout-to-create-a-button.md)
- [Otomatik Düzen için Kılavuz Kullanma](how-to-use-a-grid-for-automatic-layout.md)
- [Bir Uygulamayı Yerelleştirme](how-to-localize-an-application.md)
