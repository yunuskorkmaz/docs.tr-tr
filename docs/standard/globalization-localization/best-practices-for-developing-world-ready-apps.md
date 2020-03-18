---
title: Dünyaya Hazır Uygulamalar Geliştirmek için En İyi Yöntemler
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- global applications, best practices
- world-ready applications, best practices
- globalization [.NET Framework], best practices
- international applications [.NET Framework], best practices
ms.assetid: f08169c7-aad8-4ec3-9a21-9ebd3b89986c
ms.openlocfilehash: a2cd1039f95a763002922fc2fa24eff77838de80
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141291"
---
# <a name="best-practices-for-developing-world-ready-applications"></a>Dünyaya hazır uygulamalar geliştirmek için en iyi uygulamalar

Bu bölümde, dünyaya hazır uygulamalar geliştirirken izlenmeyen en iyi uygulamalar açıklanmaktadır.

## <a name="globalization-best-practices"></a>Küreselleşme en iyi uygulamalar

1. Uygulamanızı dahili olarak Unicode yapın.

2. Verileri işlemek ve biçimlendirmek <xref:System.Globalization> için ad alanı tarafından sağlanan kültüre duyarlı sınıfları kullanın.

    - Sıralama için <xref:System.Globalization.SortKey> sınıfı ve <xref:System.Globalization.CompareInfo> sınıfı kullanın.

    - Dize karşılaştırmaları için <xref:System.Globalization.CompareInfo> sınıfı kullanın.

    - Tarih ve saat biçimlendirmesi için <xref:System.Globalization.DateTimeFormatInfo> sınıfı kullanın.

    - Sayısal biçimlendirme için <xref:System.Globalization.NumberFormatInfo> sınıfı kullanın.

    - Gregoryen ve Gregoryen olmayan takvimler <xref:System.Globalization.Calendar> için sınıfı veya belirli takvim uygulamalarından birini kullanın.

3. <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> Uygun durumlarda sınıf tarafından sağlanan kültür özelliği ayarlarını kullanın. Tarih <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> ve saat veya sayısal biçimlendirme gibi görevleri biçimlendirmek için özelliği kullanın. Kaynakları <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> almak için özelliği kullanın. Ve `CurrentCulture` `CurrentUICulture` özelliklerinin iş parçacığı başına ayarlanabileceğini unutmayın.

4. Ad alanındaki kodlama sınıflarını kullanarak uygulamanızın çeşitli kodlamalara veri okumasını <xref:System.Text> ve yazmasını etkinleştirin. ASCII verilerini varsaymayın. Uluslararası karakterlerin, kullanıcının metin girebileceği her yerde sağlanacağını varsayalım. Örneğin, uygulama sunucu adlarında, dizinlerde, dosya adlarında, kullanıcı adlarında ve URL'lerde uluslararası karakterleri kabul etmelidir.

5. <xref:System.Text.UTF8Encoding> Sınıfı kullanırken, güvenlik nedenleriyle, bu sınıfın sunduğu hata algılama özelliğini kullanın. Hata algılama özelliğini açmak için, bir parametre alan ve `throwOnInvalidBytes` bu parametrenin değerini `true`'ye ayarlayan oluşturucuyu kullanarak sınıfın bir örneğini oluşturun.

6. Mümkün olduğunda, dizeleri tek tek karakter dizisi yerine tüm dizeleri olarak işleyebilir. Bu, özellikle alt dizeleri sıralarken veya ararken önemlidir. Bu, birleştirilmiş karakterleri ayrıştırma ile ilişkili sorunları önler. Ayrıca <xref:System.Globalization.StringInfo?displayProperty=nameWithType> sınıfı kullanarak tek karakterler yerine metin birimleri yle de çalışabilirsiniz.

7. Ad alanı tarafından sağlanan <xref:System.Drawing> sınıfları kullanarak metni görüntüleyin.

8. İşletim sistemleri arasında tutarlılık için, kullanıcı ayarlarının geçersiz kılınmasını <xref:System.Globalization.CultureInfo>izin vermez. Parametre `CultureInfo` `useUserOverride` kabul eden ve '' olarak `false`ayarlayan oluşturucuyu kullanın.

9. Uluslararası verileri kullanarak uygulama işlevselliğinizi uluslararası işletim sistemi sürümlerinde test edin.

10. Bir güvenlik kararı dize karşılaştırması veya büyük/küçük harf değiştirme işleminin sonucuna dayanıyorsa, kültüre duyarlı bir dize işlemi kullanın. Bu uygulama, sonucun değeri etkilenmemesini `CultureInfo.CurrentCulture`sağlar. Kültüre duyarlı dize karşılaştırmalarının tutarsız sonuçlar üretebileceğini gösteren bir örnek için [Dizeleri Kullanmak için En İyi Uygulamalar'ın](../../../docs/standard/base-types/best-practices-strings.md) ["Geçerli Kültürü Kullanan Dize Karşılaştırmaları"](../../../docs/standard/base-types/best-practices-strings.md#string-comparisons-that-use-the-current-culture) bölümüne bakın.

## <a name="localization-best-practices"></a>Yerelleştirme en iyi uygulamaları

1. Tüm yerelleştirilebilir kaynakları yalnızca kaynak DL'lerini ayırmak için taşıyın. Yerelleştirilebilir kaynaklar, dizeleri, hata iletileri, iletişim kutuları, menüler ve katıştırılmış nesne kaynakları gibi kullanıcı arabirimi öğelerini içerir.

2. Dizeleri veya kullanıcı arabirimi kaynaklarını kodlamayın.

3. Yalnızca kaynak DL'lerine yerelleştirilebilir olmayan kaynakları koymayın. Bu çevirmenler için karışıklığa neden olur.

4. Concatenated tümceciklerden çalışma zamanında oluşturulmuş bileşik dizeleri kullanmayın. Bileşik dizeleri yerelleştirmek zordur, çünkü genellikle tüm diller için geçerli olmayan bir İngilizce dilbilgisi sırasını varsayarlar.

5. Dize bileşenlerinin dilbilgisi rollerine bağlı olarak dizelerin farklı çevrilebileceği "Boş Klasör" gibi belirsiz yapılardan kaçının. Örneğin, "boş" bir fiil veya İtalyanca veya Fransızca gibi dillerde farklı çevirilere yol açabilir bir sıfat olabilir.

6. Uygulamanızda metin içeren resimler ve simgeler kullanmaktan kaçının. Onlar yerelleştirmek için pahalıdır.

7. Kullanıcı arabiriminde genişletmek için dizeleri uzunluğu için bol yer izin verin. Bazı dillerde, tümcecikler diğer dillerde gereksinim duyduklarından yüzde 50-75 daha fazla alan gerektirebilir.

8. Kültüre <xref:System.Resources.ResourceManager?displayProperty=nameWithType> dayalı kaynakları almak için sınıfı kullanın.

9. Windows Forms [Kaynak Düzenleyicisi (Winres.exe)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)kullanılarak yerelleştirilebilmeleri için Windows Forms iletişim kutuları oluşturmak için [Visual Studio'yu](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) kullanın. Windows Forms iletişim kutularını elle kodlamayın.

10. Profesyonel yerelleştirme (çeviri) için düzenleme.

11. Kaynak oluşturma ve yerelleştirmenin tam açıklaması [için, Uygulamalardaki Kaynaklar'a](../../../docs/framework/resources/index.md)bakın.

## <a name="globalization-best-practices-for-aspnet-applications"></a>ASP.NET uygulamalar için küreselleşme en iyi uygulamalar

1. Uygulamanızdaki <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> özellikleri <xref:System.Globalization.CultureInfo.CurrentCulture%2A> ve özelliklerini açıkça ayarlayın. Varsayılanlara güvenmeyin.

2. ASP.NET uygulamaların yönetildiğini ve bu nedenle kültüre dayalı bilgileri almak, görüntülemek ve işlemek için diğer yönetilen uygulamalarla aynı sınıfları kullanabileceğini unutmayın.

3. ASP.NET aşağıdaki üç tür kodlamayı belirtebileceğinizi unutmayın:

    - requestEncoding, istemcinin tarayıcısından alınan kodlamayı belirtir.

    - responseKodlama istemci tarayıcıya göndermek için kodlama belirtir. Çoğu durumda, bu kodlama requestEncoding için belirtilen aynı olmalıdır.

    - fileEncoding ,aspx, .asmx ve .asax dosya ayrıştma için varsayılan kodlama belirtir.

4. İstek için değerleri belirtinKodlama, yanıtKodlama, fileEncoding, kültür ve uiCulture öznitelikleri ASP.NET bir uygulamada aşağıdaki üç yerde:

    - Bir Web.config dosyasının genelleştirme bölümünde. Bu dosya ASP.NET uygulamasının dışındadır. Daha fazla bilgi [ \<için, küreselleşme> Öğesi'ne](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hy4kkhe0(v=vs.100))bakın.

    - Bir sayfa yönergesinde. Bir uygulama bir sayfadayken, dosyanın zaten okunduğunu unutmayın. Bu nedenle, fileEncoding ve requestEncoding belirtmek için çok geç. Yalnızca uiCulture, Culture ve responseEncoding bir sayfa yönergesinde belirtilebilir.

    - Uygulama kodunda programlı olarak. Bu ayar istek başına değişebilir. Bir sayfa yönergesi olduğu gibi, uygulamanın koduna ulaşılıncaya kadar dosyakodlama ve requestEncoding belirtmek için çok geç. Uygulama kodunda yalnızca uiCulture, Culture ve responseEncoding belirtilebilir.

5. UiCulture değerinin tarayıcı kabul dili olarak ayarlanabileceğini unutmayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Genelleştirme ve Yerelleştirme](../../../docs/standard/globalization-localization/index.md)
- [Masaüstü Uygulamalarında Kaynaklar](../../../docs/framework/resources/index.md)
