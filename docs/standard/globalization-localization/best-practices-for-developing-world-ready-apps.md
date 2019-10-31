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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141291"
---
# <a name="best-practices-for-developing-world-ready-applications"></a>Dünya çapında kullanmaya yönelik uygulamalar geliştirmek için en iyi uygulamalar

Bu bölümde, dünya çapında kullanılabilecek uygulamalar geliştirirken izlenecek en iyi uygulamalar açıklanmaktadır.

## <a name="globalization-best-practices"></a>Genelleştirme en iyi uygulamaları

1. Uygulamanızı dahili olarak Unicode yapın.

2. Verileri yönetmek ve biçimlendirmek için <xref:System.Globalization> ad alanı tarafından sunulan kültür kullanan sınıfları kullanın.

    - Sıralama için <xref:System.Globalization.SortKey> sınıfını ve <xref:System.Globalization.CompareInfo> sınıfını kullanın.

    - Dize karşılaştırmaları için <xref:System.Globalization.CompareInfo> sınıfını kullanın.

    - Tarih ve saat biçimlendirmesi için <xref:System.Globalization.DateTimeFormatInfo> sınıfını kullanın.

    - Sayısal biçimlendirme için <xref:System.Globalization.NumberFormatInfo> sınıfını kullanın.

    - Gregoryen ve Gregoryen olmayan takvimler için <xref:System.Globalization.Calendar> sınıfını veya belirli takvim uygulamalarından birini kullanın.

3. Uygun durumlarda <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> sınıfı tarafından sunulan kültür özelliği ayarlarını kullanın. Tarih ve saat veya sayısal biçimlendirme gibi biçimlendirme görevleri için <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> özelliğini kullanın. Kaynakları almak için <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> özelliğini kullanın. `CurrentCulture` ve `CurrentUICulture` özelliklerinin iş parçacığı başına ayarlanabileceğini unutmayın.

4. <xref:System.Text> ad alanındaki kodlama sınıflarını kullanarak, uygulamanızın çeşitli kodlara ve verileri okumasını ve veri yazmasını sağlar. ASCII verilerini kabul etmez. Bir kullanıcının metin girebileceği her yerde Uluslararası karakterlerin sağlanma kabul edilir. Örneğin, uygulama sunucu adları, dizinler, dosya adları, Kullanıcı adları ve URL 'lerde uluslararası karakterleri kabul etmelidir.

5. <xref:System.Text.UTF8Encoding> sınıfını kullanırken, güvenlik nedenleriyle, bu sınıf tarafından sunulan hata algılama özelliğini kullanın. Hata algılama özelliğini etkinleştirmek için, bir `throwOnInvalidBytes` parametresi alan oluşturucuyu kullanarak sınıfın bir örneğini oluşturun ve bu parametrenin değerini `true`olarak ayarlayın.

6. Mümkün olduğunda, dizeleri tek bir dizi karakter yerine tüm dizeler olarak işleyin. Bu, alt dizeleri sıralarken veya ararken özellikle önemlidir. Bu, Birleşik karakterlerin ayrıştırılmasından ilişkili sorunları engeller. <xref:System.Globalization.StringInfo?displayProperty=nameWithType> sınıfını kullanarak, tek karakterler yerine metin birimleriyle da çalışabilirsiniz.

7. <xref:System.Drawing> ad alanı tarafından sunulan sınıfları kullanarak metin görüntüler.

8. İşletim sistemleri arasında tutarlılık için, Kullanıcı ayarlarının <xref:System.Globalization.CultureInfo>geçersiz kılmasına izin vermeyin. Bir `useUserOverride` parametresini kabul eden `CultureInfo` oluşturucusunu kullanın ve `false`olarak ayarlayın.

9. Uluslararası verileri kullanarak, uygulama işlevselliklerinizi Uluslararası işletim sistemi sürümlerinde test edin.

10. Bir güvenlik kararı bir dize karşılaştırma veya örnek değişikliği işleminin sonucunu temel alıyorsa, kültüre duyarsız bir dize işlemi kullanın. Bu uygulama, sonucun `CultureInfo.CurrentCulture`değerden etkilenmemesini sağlar. Kültüre duyarlı dize karşılaştırmalarının nasıl tutarsız sonuçlar üretediğini gösteren bir örnek için [dizeleri kullanmak Için En Iyi Yöntemler](../../../docs/standard/base-types/best-practices-strings.md) konusunun ["geçerli kültürü kullanan dize karşılaştırmaları"](../../../docs/standard/base-types/best-practices-strings.md#string-comparisons-that-use-the-current-culture) bölümüne bakın.

## <a name="localization-best-practices"></a>Yerelleştirme en iyi uygulamaları

1. Tüm yerelleştirilebilir kaynakları yalnızca kaynak dll 'Lerine taşıyın. Yerelleştirilebilir kaynaklar, dizeler, hata iletileri, iletişim kutuları, menüler ve katıştırılmış nesne kaynakları gibi kullanıcı arabirimi öğelerini içerir.

2. Dizeleri veya Kullanıcı arabirimi kaynaklarını hardmayın.

3. Yerelleştirilemeyen kaynakları yalnızca kaynak dll 'Lerine yerleştirmeyin. Bu, çevirmenler için karışıklık oluşmasına neden olur.

4. Birleştirilmiş ifadelerden çalışma zamanında oluşturulan bileşik dizeleri kullanmayın. Birleşik dizelerin yerelleştirilmesi zordur, çünkü genellikle tüm diller için uygun olmayan Ingilizce dilbilgisi sırasını varsayar.

5. Dizelerin, dize bileşenlerinin dilbilgisi rollerine bağlı olarak farklı çevrilebileceği "boş klasör" gibi belirsiz yapıların kaçının. Örneğin, "boş" bir fiil veya sıfata olabilir. Bu, Italyanca veya Fransızca gibi dillerdeki farklı çevirilerine yol açabilir.

6. Uygulamanızda metin içeren görüntüleri ve simgeleri kullanmaktan kaçının. Yerelleştirmeye pahalıdır.

7. Kullanıcı arabiriminde genişleyebilir dizelerin uzunluğu için çok sayıda odaya izin verin. Bazı dillerde, deyimler diğer dillerde gereksinimlerden daha fazla yüzde 50-75 sürebilir.

8. Kültürü temel alan kaynakları almak için <xref:System.Resources.ResourceManager?displayProperty=nameWithType> sınıfını kullanın.

9. [Windows Forms Kaynak Düzenleyicisi (Winres. exe)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)kullanılarak yerelleştirilebilecek Windows Forms iletişim kutusu oluşturmak Için [Visual Studio 'yu](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) kullanın. Windows Forms iletişim kutularını el ile kodlayın.

10. Profesyonel yerelleştirme için düzenleyin (çeviri).

11. Kaynakları oluşturma ve yerelleştirme hakkında ayrıntılı bir açıklama için bkz. [uygulamalardaki kaynaklar](../../../docs/framework/resources/index.md).

## <a name="globalization-best-practices-for-aspnet-applications"></a>ASP.NET uygulamaları için Genelleştirme en iyi yöntemleri

1. Uygulamanızda <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> ve <xref:System.Globalization.CultureInfo.CurrentCulture%2A> özelliklerini açık olarak ayarlayın. Varsayılanlara güvenmeyin.

2. ASP.NET uygulamalarının yönetilen uygulamalar olduğunu ve bu nedenle, kültürü temel alan bilgileri alma, görüntüleme ve düzenleme için diğer yönetilen uygulamalarla aynı sınıfları kullanabileceğini unutmayın.

3. ASP.NET içinde aşağıdaki üç tür kodlamayı belirtabilin farkında olun:

    - requestEncoding, istemcinin tarayıcısından alınan kodlamayı belirtir.

    - responseEncoding, istemci tarayıcısına göndermek için kodlamayı belirtir. Çoğu durumda, bu kodlama requestEncoding için belirtilen ile aynı olmalıdır.

    - fileEncoding,. aspx,. asmx ve. asax dosya ayrıştırması için varsayılan kodlamayı belirtir.

4. Bir ASP.NET uygulamasında aşağıdaki üç yerde requestEncoding, responseEncoding, fileEncoding, Culture ve UICulture özniteliklerinin değerlerini belirtin:

    - Bir Web. config dosyasının Genelleştirme bölümünde. Bu dosya ASP.NET uygulamasının dışında. Daha fazla bilgi için bkz. [\<genelleştirme > öğesi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hy4kkhe0(v=vs.100)).

    - Bir sayfa yönergesinde. Bir uygulama bir sayfada olduğunda, dosyanın zaten okunup okunmadığını unutmayın. Bu nedenle, fileEncoding ve requestEncoding belirtmek için çok geç. Bir sayfa yönergesinde yalnızca UICulture, Culture ve responseEncoding belirtilebilir.

    - Uygulama kodunda programlı olarak. Bu ayar, istek başına farklılık gösterebilir. Bir sayfa yönergesinde olduğu gibi, uygulamanın koduna ulaşıldığında, fileEncoding ve requestEncoding belirtmek için çok geç olur. Uygulama kodunda yalnızca UICulture, Culture ve responseEncoding belirtilebilir.

5. UICulture değerinin tarayıcı kabul diline ayarlanbileceğini unutmayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Genelleştirme ve Yerelleştirme](../../../docs/standard/globalization-localization/index.md)
- [Masaüstü Uygulamalarındaki Kaynaklar](../../../docs/framework/resources/index.md)
