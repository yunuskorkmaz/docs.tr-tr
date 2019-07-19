---
title: Yerelleştirme Öznitelikleri ve Yorumlar
ms.date: 03/30/2017
helpviewer_keywords:
- localization [WPF], attributes
- localization [WPF], comments
ms.assetid: ead2d9ac-b709-4ec1-a924-39927a29d02f
ms.openlocfilehash: 1ef18802ab3568df00e29eb4ccaf717f4bdf4863
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68330988"
---
# <a name="localization-attributes-and-comments"></a>Yerelleştirme Öznitelikleri ve Yorumlar
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Yerelleştirme Yorumları, geliştiriciler tarafından yerelleştirme [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] için kurallar ve ipuçları sağlamak üzere sağlanan kaynak kodu içindeki özelliklerdir. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]yerelleştirme açıklamaları iki bilgi kümesi içerir: Yerelleştirilebilirlik öznitelikleri ve serbest biçimli yerelleştirme açıklamaları. Yerelleştirilebilirlik öznitelikleri, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] yerelleştirme API 'si tarafından hangi kaynakların yerelleştirileceğini göstermek için kullanılır. Serbest biçimli açıklamalar, uygulama yazarının eklemek istediği herhangi bir bilgi.  

<a name="Localizer_Comments_"></a>   
## <a name="localization-comments"></a>Yerelleştirme açıklamaları  
 Biçimlendirme uygulaması yazarları, ' deki [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]belirli öğeler için, metin uzunluğu, yazı tipi ailesi veya yazı tipi boyutu kısıtlamaları gibi gereksinimlere sahip olursa, bu bilgileri [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] koddaki yorumlarla birlikte yerellere iletirler. Kaynak koda yorum ekleme işlemi aşağıdaki gibidir:  
  
1. Uygulama geliştiricisi, [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] kaynak koduna yerelleştirme açıklamaları ekler.  
  
2. Oluşturma işlemi sırasında,. proj dosyasında, serbest biçimli yerelleştirme açıklamalarını derlemede bırakıp, yorumların bir kısmını bırakarak veya tüm yorumların dışına çıkaramayacağını belirtebilirsiniz. Açılan Yorumlar ayrı bir dosyaya yerleştirilir. Bir `LocalizationDirectivesToLocFile` etiket kullanarak seçeneğinizi belirtirsiniz, örneğin:  
  
     `<LocalizationDirectivesToLocFile>`*değer*`</LocalizationDirectivesToLocFile>`  
  
3. Atanabileceği değerler şunlardır:  
  
    - **Hiçbiri** -yorumların ve özniteliklerin her ikisi de derlemenin içinde kalır ve ayrı bir dosya oluşturulmaz.  
  
    - **CommentsOnly** -yalnızca derlemeden açıklamaları kaldırır ve ayrı bir LocFile içine yerleştirir.  
  
    - **All** -derlemeden hem açıklamaları hem de öznitelikleri şeritler ve bunları ayrı bir LocFile içine yerleştirir.  
  
4. Yerelleştirilebilir kaynaklar BAML 'den ayıklandığında, Yerelleştirilebilirlik öznitelikleri BAML yerelleştirme API 'SI tarafından dikkate alınır.  
  
5. Yalnızca ücretsiz form açıklamalarını içeren Yerelleştirme açıklama dosyaları, yerelleştirme sürecine daha sonra dahil edilir.  
  
 Aşağıdaki örnek, bir [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] dosyaya yerelleştirme açıklamalarının nasıl ekleneceğini gösterir.  
  
 `<TextBlock x:Id = "text01"`  
  
 `FontFamily = "Microsoft Sans Serif"`  
  
 `FontSize = "12"`  
  
 `Localization.Attributes = "$Content (Unmodifiable Readable Text)`  
  
 `FontFamily (Unmodifiable Readable)"`  
  
 `Localization.Comments = "$Content (Trademark)`  
  
 `FontSize (Trademark font size)" >`  
  
 `Microsoft`  
  
 `</TextBlock>`  
  
 Önceki örnekte, yerelleştirme. Öznitelikler bölümünde, ücretsiz form açıklamaları olan yerelleştirme öznitelikleri ve yerelleştirme. Comments bölümü bulunur. Aşağıdaki tablolarda öznitelikleri ve açıklamaları ve yerelleştiriciye ilişkin anlamı gösterilmektedir.  
  
|Yerelleştirme öznitelikleri|Açıklama|  
|-----------------------------|-------------|  
|$Content (değiştirilemeyen okunabilir metin)|TextBlock öğesinin içeriği değiştirilemez. Yerelleştiriciler "Microsoft" sözcüğünü değiştiremiyor. İçerik, yerelleştirici için görünür (okunabilir). İçerik kategorisi metindir.|  
|FontFamily (değiştirilemez okunabilir)|TextBlock öğesinin yazı tipi ailesi özelliği değiştirilemez, ancak Localizer tarafından görülebilir.|  
  
|Yerelleştirme serbest form açıklamaları|Açıklama|  
|--------------------------------------|-------------|  
|$Content (ticari marka)|Uygulama yazarı, yerelleştiriciye TextBlock öğesindeki içeriğin bir ticari marka olduğunu söyler.|  
|FontSize (ticari marka yazı tipi boyutu)|Uygulama yazarı, yazı tipi boyutu özelliğinin standart ticari marka boyutunu izlemesi gerektiğini gösterir.|  
  
### <a name="localizability-attributes"></a>Yerelleştirilebilirlik öznitelikleri  
 Yerelleştirme. Attributes içindeki bilgiler, çiftler listesini içerir: hedeflenen değer adı ve ilişkili Yerelleştirilebilirlik değerleri. Hedef adı bir özellik adı veya özel $Content adı olabilir. Özellik adı ise, hedeflenen değer özelliğin değeridir. $Content, hedef değer öğenin içeridir.  
  
 Üç tür öznitelik vardır:  
  
- **Kategori**. Bu, bir değerin yerelleştirici aracından değiştirilebilir olup olmadığını belirtir. Bkz. <xref:System.Windows.LocalizabilityAttribute.Category%2A>.  
  
- **Okunabilirlik**. Bu, bir yorumdur aracının bir değeri okuyup okumayacağını (ve görüntülemesini) belirler. Bkz. <xref:System.Windows.LocalizabilityAttribute.Readability%2A>.  
  
- **Modifibeceri**. Bu, bir yorumdur aracının bir değerin değiştirilmesini izin verip içermediğini belirtir. Bkz. <xref:System.Windows.LocalizabilityAttribute.Modifiability%2A>.  
  
 Bu öznitelikler, boşlukla ayrılmış herhangi bir sıraya göre belirtilebilir. Yinelenen öznitelikler belirtilirse, son öznitelik eski olanları geçersiz kılar. Örneğin, yerelleştirme. Attributes = "değiştirilemez değiştirilebilir" değeri, son değer olduğundan, Modifibilirliği değiştirilebilir olarak ayarlar.  
  
 Modifibilme ve okunabilirlik kendi kendine açıklayıcıdır. Kategori özniteliği, metin çevrilirken yerelleştiriciye yardımcı olan önceden tanımlanmış kategoriler sağlar. Metin, etiket ve başlık gibi kategoriler, metin çevirme hakkında yerelleştirici bilgilerini verir. Ayrıca özel kategoriler de vardır: None, Inherit, yoksay ve Neveryerelleştirin.  
  
 Aşağıdaki tabloda özel kategorilerin anlamı gösterilmektedir.  
  
|Kategori|Açıklama|  
|--------------|-------------|  
|Yok.|Hedeflenen değerin tanımlı bir kategorisi yok.|  
|Devralınır|Hedeflenen değer kendi üst öğesinden kategorisini devralır.|  
|Yoksayma|Hedeflenen değer, yerelleştirme sürecinde yok sayılır. Ignore yalnızca geçerli değeri etkiler. Alt düğümleri etkilemez.|  
|Neveryerelleştirin|Geçerli değer yerelleştirilemez. Bu kategori bir öğenin alt öğeleri tarafından devralınır.|  
  
<a name="Localization_Comments"></a>   
## <a name="localization-comments"></a>Yerelleştirme açıklamaları  
 Yerelleştirme. Comments hedeflenen değerle ilgili serbest biçimli dizeler içerir. Uygulama geliştiricileri, uygulamalar metninin nasıl çevrilmesi gerektiği hakkında yerelleştiriciler ipuçlarına izin vermek için bilgi ekleyebilir. Yorumların biçimi "()" ile çevrelenen herhangi bir dize olabilir. Kaçış karakterleri\\için ' ' kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WPF için Genelleştirme](globalization-for-wpf.md)
- [Düğme Oluşturmak için Otomatik Düzeni Kullanma](how-to-use-automatic-layout-to-create-a-button.md)
- [Otomatik Düzen için Kılavuz Kullanma](how-to-use-a-grid-for-automatic-layout.md)
- [Bir Uygulamayı Yerelleştirme](how-to-localize-an-application.md)
