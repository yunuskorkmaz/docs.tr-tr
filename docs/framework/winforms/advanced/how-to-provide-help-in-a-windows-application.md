---
title: 'Nasıl yapılır: Bir Windows Uygulamasında Yardım Sağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- Help [Windows Forms], Windows applications
- HTML Help [Windows Forms], Windows Forms
- Windows applications [Windows Forms], providing Help
- HelpProvider component [Windows Forms]
- forms [Windows Forms], providing Help
ms.assetid: 7c4e5cec-2bd2-4f0b-8d75-c2b88929bd61
ms.openlocfilehash: 405de333ce936a864047e827e60f56a930059e26
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84143634"
---
# <a name="how-to-provide-help-in-a-windows-application"></a>Nasıl yapılır: Bir Windows Uygulamasında Yardım Sağlama

<xref:System.Windows.Forms.HelpProvider>Windows Forms, bir yardım dosyası içindeki belirli denetimlere yardım konuları eklemek için bileşeni kullanabilirsiniz. Yardım dosyası HTML ya da HTMLHelp 1. x veya daha büyük bir biçimde olabilir.

## <a name="provide-help"></a>Yardım sağlama

1. Visual Studio 'da, **araç kutusundan**bir <xref:System.Windows.Forms.HelpProvider> bileşeni formunuza sürükleyin.

     Bileşen Windows Form Tasarımcısı alt kısmındaki tepside yer alır.

2. **Özellikler** penceresinde, <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> özelliği. chm,. col veya. htm yardım dosyası olarak ayarlayın.

3. Formunuzda bulunan başka bir denetim seçin ve **Özellikler** penceresinde <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> özelliğini ayarlayın.

     Bu, <xref:System.Windows.Forms.HelpProvider> uygun yardım konusunu toplaa eklemek için bileşen aracılığıyla yardım dosyanıza geçirilen dizedir.

4. **Özellikler** penceresinde, <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> özelliği numaralandırmanın bir değeri olarak ayarlayın <xref:System.Windows.Forms.HelpNavigator> .

     Bu, **Helpanahtar sözcük** özelliğinin yardım sistemine geçirilme şeklini belirler. Aşağıdaki tabloda olası ayarlar ve bunların açıklamaları gösterilmektedir.

    |Üye Adı|Açıklama|
    |-----------------|-----------------|
    |AssociateIndex|Belirtilen bir konunun dizininin belirtilen URL 'de gerçekleştirildiğini belirtir.|
    |Bul|Belirtilen URL 'nin arama sayfasının görüntülendiğini belirtir.|
    |Dizin oluşturma|Belirtilen URL 'nin dizininin görüntülendiğini belirtir.|
    |KeywordIndex|Aranacak anahtar sözcüğü ve belirtilen URL 'de gerçekleştirilecek eylemi belirtir.|
    |Tablo Içerikleri|HTML 1,0 Yardım dosyasının içindekiler tablosunun görüntülendiğini belirtir.|
    |Konu başlığı|Belirtilen URL tarafından başvurulan konunun görüntülendiğini belirtir.|

 Çalışma zamanında, yardım için **Helpsözcüðünü** ve **HelpNavigator** özelliklerini ayarladığınız denetim için F1 tuşuna basın. odak, bu bileşenle ilişkilendirdiğiniz yardım dosyasını açar <xref:System.Windows.Forms.HelpProvider> .

 Şu anda **HelpNamespace** özelliği şu üç biçimdeki yardım dosyalarını destekler: HTMLHelp 1. x, HTMLHelp 2,0 ve HTML. Bu nedenle, **HelpNamespace** özelliğini `http://` bir Web sayfası gibi bir adrese ayarlayabilirsiniz. Bu işlem yapıldıktan sonra, bağlantı olarak kullanılan **Helpanahtar sözcük** özelliğinde belirtilen dizeyle Web sayfasına varsayılan tarayıcıyı açar. Tutturucu, HTML sayfasının belirli bir kısmına geçmek için kullanılır.

> [!IMPORTANT]
> Uygulamanızda kullanmadan önce bir istemciden gönderilen tüm bilgileri denetlememeye dikkat edin. Kötü amaçlı kullanıcılar yürütülebilir betiği, SQL deyimlerini veya diğer kodları göndermeye veya eklemeye çalışabilir. Bir kullanıcının girişini görüntülemeden, bir veritabanında saklamadan veya onunla çalışmadan önce, güvenli olmayabilecek bilgiler içermediğinden emin olun. Bir kullanıcıdan giriş aldığınızda "komut dosyası" gibi anahtar sözcükleri aramak için normal bir ifade kullanmanın yaygın bir yoludur.

Ayrıca <xref:System.Windows.Forms.HelpProvider> bileşeni, Windows Forms denetimleri Için yardım dosyalarını görüntülemek üzere yapılandırılmış olsa bile açılır Yardımı göstermek için de kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: açılan menü yardımını görüntüleme](how-to-display-pop-up-help.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Açılır Yardımı Görüntüleme](how-to-display-pop-up-help.md)
- [ToolTips Kullanarak Denetim Yardımı](control-help-using-tooltips.md)
- [Windows Forms'ta Kullanıcı Yardımını Tümleştirme](integrating-user-help-in-windows-forms.md)
- [Windows Forms](../index.md)
