---
title: Yerelleştirme Öznitelikleri ve Yorumlar
ms.date: 03/30/2017
helpviewer_keywords:
- localization [WPF], attributes
- localization [WPF], comments
ms.assetid: ead2d9ac-b709-4ec1-a924-39927a29d02f
ms.openlocfilehash: 7281ca6d76f0d2ffb5020feba236b4e4cf948bdd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141594"
---
# <a name="localization-attributes-and-comments"></a>Yerelleştirme Öznitelikleri ve Yorumlar
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]yerelleştirme yorumları, xaml kaynak kodu içinde, kurallar ve yerelleştirme için ipuçları sağlamak için geliştiriciler tarafından sağlanan özellikleri vardır. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]yerelleştirme yorumları iki bilgi kümesi içerir: yerelleştirilebilirlik öznitelikleri ve serbest biçimli yerelleştirme açıklamaları. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Yerelleştirilebilirlik öznitelikleri, yerelleştirme API'si tarafından hangi kaynakların yerelleştirilen olduğunu belirtmek için kullanılır. Serbest biçimli yorumlar, uygulama yazarının eklemek istediği bilgilerdir.  

<a name="Localizer_Comments_"></a>
## <a name="localization-comments"></a>Yerelleştirme Yorumları  
 Biçimlendirme uygulaması yazarlarının XAML'de metin uzunluğu, yazı tipi ailesi veya yazı tipi boyutundaki kısıtlamalar gibi belirli öğeler için gereksinimleri varsa, bu bilgileri XAML kodundaki açıklamalarla yerelleştiricilere iletebilirler. Kaynak koduna açıklama ekleme işlemi aşağıdaki gibidir:  
  
1. Uygulama geliştiricisi XAML kaynak koduna yerelleştirme açıklamaları ekler.  
  
2. Oluşturma işlemi sırasında, .proj dosyasında, derlemede serbest biçimli yerelleştirme yorumlarını bırakıp bırakmayacağınızı, yorumların bir kısmını söküp atamayacağınızı veya tüm yorumları çıkarıp çıkarmayacağınızı belirtebilirsiniz. Çıkarılan açıklamalar ayrı bir dosyaya yerleştirilir. Bir `LocalizationDirectivesToLocFile` etiket kullanarak seçeneğinizi belirtirsiniz, örneğin:  
  
     `<LocalizationDirectivesToLocFile>`*değer*`</LocalizationDirectivesToLocFile>`  
  
3. Atanabilecek değerler şunlardır:  
  
    - **Yok** - Hem açıklamalar hem de öznitelikler derlemeiçinde kalır ve ayrı bir dosya oluşturulamaz.  
  
    - **CommentsOnly** - Yalnızca derlemedeki yorumları sıyırR ve bunları ayrı LocFile'a yerleştirir.  
  
    - **Tüm** - Derlemedeki yorumları ve öznitelikleri şeritler ve her ikisini de ayrı bir LocFile'a yerleştirir.  
  
4. Yerelleştirilebilir kaynaklar BAML'den çıkarıldığında, yerelleştirilebilirlik öznitelikleri BAML Yerelleştirme API'si tarafından saygı duyulur.  
  
5. Yalnızca serbest biçimli açıklamalar içeren yerelleştirme yorum dosyaları daha sonra yerelleştirme işlemine dahil edilir.  
  
 Aşağıdaki örnek, bir XAML dosyasına yerelleştirme açıklamalarının nasıl ekleyeceğini gösterir.  
  
 `<TextBlock x:Id = "text01"`  
  
 `FontFamily = "Microsoft Sans Serif"`  
  
 `FontSize = "12"`  
  
 `Localization.Attributes = "$Content (Unmodifiable Readable Text)`  
  
 `FontFamily (Unmodifiable Readable)"`  
  
 `Localization.Comments = "$Content (Trademark)`  
  
 `FontSize (Trademark font size)" >`  
  
 `Microsoft`  
  
 `</TextBlock>`  
  
 Önceki örnekte Localization.Öznitelikler bölümünde yerelleştirme öznitelikleri ve Localization.Comments bölümünde serbest form açıklamaları içerir. Aşağıdaki tablolar da öznitelikleri ve yorumları ve bunların yerelleştiriciye anlamlarını gösterir.  
  
|Yerelleştirme öznitelikleri|Anlamı|  
|-----------------------------|-------------|  
|$Content (Değiştirilemez Okunabilir Metin)|TextBlock öğesinin içeriği değiştirilemez. Yerelleştiriciler "Microsoft" sözcüğüdeğiştiremez. İçerik yerelleştirici tarafından görülebilir (Okunabilir). İçeriğin kategorisi metindir.|  
|FontFamily (Değiştirilemez Okunabilir)|TextBlock öğesinin yazı tipi aile özelliği değiştirilemez, ancak yerelleştirici tarafından görülebilir.|  
  
|Yerelleştirme serbest biçimli yorumlar|Anlamı|  
|--------------------------------------|-------------|  
|$Content (Ticari Marka)|Uygulama yazarı yerelleştiriciye TextBlock öğesindeki içeriğin bir ticari marka olduğunu söyler.|  
|FontSize (Ticari marka yazı tipi boyutu)|Uygulama yazarı, yazı tipi boyutu özelliğinin standart ticari marka boyutunu izlemesi gerektiğini belirtir.|  
  
### <a name="localizability-attributes"></a>Yerelleştirilebilirlik Öznitelikleri  
 Localization.Öznitelikleri'ndeki bilgiler çiftlerin listesini içerir: hedeflenen değer adı ve ilişkili yerelleştirilebilirlik değerleri. Hedef ad bir özellik adı veya özel $Content adı olabilir. Bir özellik adıysa, hedeflenen değer özelliğin değeridir. $Content ise, hedef değer öğenin içeriğidir.  
  
 Üç tür öznitelik vardır:  
  
- **Kategori**. Bu, bir değerin bir yerelleştirici araçtan değiştirilebilir olup olmadığını belirtir. Bkz. <xref:System.Windows.LocalizabilityAttribute.Category%2A>.  
  
- **Okunabilirlik**. Bu, bir yerelleştirici aracın bir değeri okuyup okumayacağını (ve görüntülemesi mi) gerektiğini belirtir. Bkz. <xref:System.Windows.LocalizabilityAttribute.Readability%2A>.  
  
- **Değiştirilebilirlik**. Bu, yerelleştirici bir aracın bir değerin değiştirilmesine izin verip vermeyeceğini belirtir. Bkz. <xref:System.Windows.LocalizabilityAttribute.Modifiability%2A>.  
  
 Bu öznitelikler, bir boşlukla sınırlandırılmış herhangi bir sırada belirtilebilir. Yinelenen özniteliklerin belirtilmiş olması durumunda, son öznitelik eskilerini geçersiz kılar. Örneğin, Localization.Öznitelikler = "Değiştirilemez Değiştirilebilir" son değer olduğundan Değiştirilebilirayarlar.  
  
 Değiştirilebilirlik ve Okunabilirlik kendi kendini açıklar. Kategori özniteliği, metni çevirirken yerelleştiriciye yardımcı olan önceden tanımlanmış kategoriler sağlar. Metin, Etiket ve Başlık gibi kategoriler, yerelleştiriciye metnin nasıl çevrildiği hakkında bilgi verir. Özel kategoriler de vardır: Yok, Devralma, Yoksay ve NeverLocalize.  
  
 Aşağıdaki tablo, özel kategorilerin anlamını gösterir.  
  
|Kategori|Anlamı|  
|--------------|-------------|  
|None|Hedeflenen değerin tanımlı bir kategorisi yoktur.|  
|Devralır|Hedeflenen değer, kategorisini üst öğesinden devralır.|  
|Yoksayma|Hedeflenen değer yerelleştirme işleminde yoksayılır. Yoksayma yalnızca geçerli değeri etkiler. Alt düğümleri etkilemez.|  
|NeverLocalize|Geçerli değer yerelleştirilemez. Bu kategori, bir öğenin alt tarafından devralır.|  
  
<a name="Localization_Comments"></a>
## <a name="localization-comments"></a>Yerelleştirme Yorumları  
 Localization.Comments, hedeflenen değerle ilgili serbest biçimli dizeleri içerir. Uygulama geliştiricileri, yerelleştiricilere uygulama metninin nasıl çevrilmesi gerektiği hakkında ipuçları vermek için bilgi ekleyebilir. Yorumların biçimi "()" ile çevrili herhangi bir dize olabilir. Karakterlerden\\kaçmak için ' ' ' kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF için Genelleştirme](globalization-for-wpf.md)
- [Düğme Oluşturmak için Otomatik Düzeni Kullanma](how-to-use-automatic-layout-to-create-a-button.md)
- [Otomatik Düzen için Kılavuz Kullanma](how-to-use-a-grid-for-automatic-layout.md)
- [Bir Uygulamayı Yerelleştirme](how-to-localize-an-application.md)
