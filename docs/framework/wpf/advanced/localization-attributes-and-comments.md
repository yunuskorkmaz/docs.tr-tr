---
title: Yerelleştirme Öznitelikleri ve Yorumlar
ms.date: 03/30/2017
helpviewer_keywords:
- localization [WPF], attributes
- localization [WPF], comments
ms.assetid: ead2d9ac-b709-4ec1-a924-39927a29d02f
ms.openlocfilehash: 7cfcc9fa4dc3bc1450febb39500b7d96f92beac6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="localization-attributes-and-comments"></a>Yerelleştirme Öznitelikleri ve Yorumlar
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Yerelleştirme açıklamalarını özelliklerdir, içinde [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] kaynak kod yerelleştirme için kurallar ve ipuçları sağlamak için geliştiriciler tarafından sağlanan,. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Yerelleştirme açıklamalarını içeren iki bilgi kümesi: Yerelleştirme öznitelikleri ve serbest biçimli yerelleştirme açıklamalarını. Yerelleştirme öznitelikleri tarafından kullanılan [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerelleştirme hangi kaynakların yerelleştirilmesi belirtmek için API. Serbest biçimli açıklamalar dahil etmek için uygulama yazarı istediği herhangi bilgilerdir.  
  

  
<a name="Localizer_Comments_"></a>   
## <a name="localization-comments"></a>Yerelleştirme yorumları  
 Biçimlendirme uygulaması yazarları içindeki belirli öğeler için gereksinimleri olup olmadığını [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)], metin uzunluğu, yazı tipi ailesi veya yazı tipi boyutu kısıtlamaları gibi çevirmenler açıklamaları ile bu bilgileri iletmek [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] kodu. Kaynak kodu açıklamaları ekleme işlemi aşağıdaki gibidir:  
  
1.  Uygulama geliştiricisi yerelleştirme açıklamalarını ekler [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] kaynak kodu.  
  
2.  Derleme işlemi sırasında derleme, Yorumlar parçası çıkışı Şerit ya da tüm açıklamaları Şerit serbest biçimli yerelleştirme açıklamalarını bırakmak mı yoksa .proj dosyasında belirtebilirsiniz. Çıkarılan yorumlar ayrı bir dosyada yer alır. Seçeneğini kullanarak belirttiğiniz bir `LocalizationDirectivesToLocFile` etiketi, örneğin:  
  
     `<LocalizationDirectivesToLocFile>` *Değer* `</LocalizationDirectivesToLocFile>`  
  
3.  Atanabilir değerler şunlardır:  
  
    -   **Hiçbiri** -hem açıklamaları ve öznitelikleri derleme içinde kalır ve ayrı bir dosya oluşturulur.  
  
    -   **CommentsOnly** - derleme yalnızca açıklamalardan ve bunları ayrı bir LocFile içine yerleştirir.  
  
    -   **Tüm** - açıklamaları ve öznitelikleri derlemesinden kaldırır ve bunları ayrı bir LocFile içine yerleştirir.  
  
4.  Gelen yerelleştirilebilir kaynakları ayıklanırken [!INCLUDE[TLA2#tla_baml](../../../../includes/tla2sharptla-baml-md.md)], Yerelleştirme öznitelikleri tarafından kullanılır [!INCLUDE[TLA2#tla_baml](../../../../includes/tla2sharptla-baml-md.md)] yerelleştirme API'si.  
  
5.  Yalnızca serbest biçimli açıklamalar içeren yerelleştirme yorumları dosyaları daha sonraki bir zamanda yerelleştirme işlemi içine birleştirilir.  
  
 Aşağıdaki örnek, yerelleştirme açıklama eklemek gösterilmiştir bir [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] dosyası.  
  
 `<TextBlock x:Id = "text01"`  
  
 `FontFamily = "Microsoft Sans Serif"`  
  
 `FontSize = "12"`  
  
 `Localization.Attributes = "$Content (Unmodifiable Readable Text)`  
  
 `FontFamily (Unmodifiable Readable)"`  
  
 `Localization.Comments = "$Content (Trademark)`  
  
 `FontSize (Trademark font size)" >`  
  
 `Microsoft`  
  
 `</TextBlock>`  
  
 Önceki örnekte Localization.Attributes Yerelleştirme öznitelikleri ve Localization.Comments bölümü serbest biçimli açıklamalar bölüm içerir. Aşağıdaki tablolarda, öznitelikleri ve yorumları ve anlamları yerelleştiriciye gösterilmektedir.  
  
|Yerelleştirme öznitelikleri|Açıklama|  
|-----------------------------|-------------|  
|$Content (değiştirilemeyen okunabilir metin)|TextBlock öğesinin içeriği değiştirilemez. Çevirmenler "Microsoft" sözcüğünü değiştiremezsiniz. İçeriği yerelleştiriciye görünür (okunabilir) olur. İçerik kategorisi metindir.|  
|FontFamily (değiştirilemeyen okunabilir)|TextBlock öğesinin yazı tipi ailesi özelliği değiştirilemez, ancak yerelleştiriciye görünür olur.|  
  
|Yerelleştirme serbest biçimli açıklamalar|Açıklama|  
|--------------------------------------|-------------|  
|$Content (ticari marka)|Uygulama yazarı yerelleştiriciye TextBlock öğe içeriğinde bir ticari marka olduğunu söyler.|  
|FontSize (ticari marka yazı tipi boyutu)|Uygulama yazarı yazı tipi boyutu özelliğinin standart ticari marka boyutunu izlenmesi gerektiğini gösterir.|  
  
### <a name="localizability-attributes"></a>Yerelleştirme öznitelikleri  
 Çiftlerinin listesini Localization.Attributes bilgileri içerir: hedeflenen değer adını ve ilişkili yerelleştirme değerleri. Hedef adı, bir özellik adı veya özel $Content adı olabilir. Bir özellik adı ise, hedeflenen özelliğinin değeri değerdir. $Content ise, hedef değer öğesi içeriktir.  
  
 Üç tür öznitelik vardır:  
  
-   **Kategori**. Bu, bir değer yerelleştirici araçtan değiştirilebilir olup olmayacağını belirtir. Bkz: <xref:System.Windows.LocalizabilityAttribute.Category%2A>.  
  
-   **Okunabilirlik**. Bu yerelleştirici aracın gerekip gerekmediğini belirten bir değer okuma (ve görüntüleme). Bkz: <xref:System.Windows.LocalizabilityAttribute.Readability%2A>.  
  
-   **Modifiability'e göre**. Bu, yerelleştirici aracın bir değerin değiştirilmesine izin verip vermeyeceğini belirtir. Bkz: <xref:System.Windows.LocalizabilityAttribute.Modifiability%2A>.  
  
 Bu öznitelikler, boşlukla ayrılmış herhangi bir sırada belirtilebilir. Yinelenen öznitelikler belirtilmesi durumunda, son özniteliğini eski olanları geçersiz kılar. Örneğin, Localization.Attributes son değeri olduğundan = Modifiability'i Modifiable "Değiştirilemeyen değiştirilebilir" belirler.  
  
 Modifiability'e göre ve okunabilirliği niteliktedir. Kategori özniteliği metni çevirirken yerelleştiriciye yardım tanımlanmış kategorilerle sağlar. Örneğin, metin, etiket ve başlık verin metin çevirme hakkında yerelleştiriciye bilgi kategoriler. Ayrıca özel kategoriye ayrılır: None, devralma, yoksay ve NeverLocalize.  
  
 Aşağıdaki tabloda özel kategoriler anlamını gösterir.  
  
|Kategori|Açıklama|  
|--------------|-------------|  
|Yok.|Hedeflenen değer tanımlanmış bir kategorisi yoktur.|  
|Devral|Hedeflenen değer kategorisinin üst öğesinden devralıyor.|  
|Yoksay|Hedeflenen değer yerelleştirme işleminde göz ardı edilir. Yoksay yalnızca geçerli değeri etkiler. Alt düğümler etkilemez.|  
|NeverLocalize|Geçerli değer yerelleştirilmiş olamaz. Bu kategori, bir öğenin gruplar tarafından devralınır.|  
  
<a name="Localization_Comments"></a>   
## <a name="localization-comments"></a>Yerelleştirme yorumları  
 Localization.Comments hedeflenen değeri ile ilgili serbest biçimli dizeleri içerir. Uygulama geliştiricilerinin çevirmenler vermek için bilgi ekleyebileceğiniz uygulama metninin nasıl çevrilen hakkında ipuçları. Açıklamaları biçimi çevrelenen "(") tarafından herhangi bir dize olabilir. Kullanım '\\' kaçış karakterleri için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF için Genelleştirme](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)  
 [Düğme Oluşturmak için Otomatik Düzeni Kullanma](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)  
 [Otomatik Düzen için Kılavuz Kullanma](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)  
 [Bir Uygulamayı Yerelleştirme](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)
