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
ms.openlocfilehash: f0e5ccf999b6aa96b6317b88e25f3cd9d9fbc899
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279886"
---
# <a name="best-practices-for-developing-world-ready-applications"></a>Dünya çapında kullanmaya yönelik uygulamalar geliştirmek için en iyi uygulamalar

Bu bölümde, dünya çapında kullanılabilecek uygulamalar geliştirirken izlenecek en iyi uygulamalar açıklanmaktadır.

## <a name="globalization-best-practices"></a>Genelleştirme en iyi uygulamaları

1. Uygulamanızı dahili olarak Unicode yapın.

2. <xref:System.Globalization>Veri değiştirmek ve biçimlendirmek için ad alanı tarafından sunulan kültür kullanan sınıfları kullanın.

    - Sıralama için <xref:System.Globalization.SortKey> sınıfını ve <xref:System.Globalization.CompareInfo> sınıfını kullanın.

    - Dize karşılaştırmaları için <xref:System.Globalization.CompareInfo> sınıfını kullanın.

    - Tarih ve saat biçimlendirmesi için <xref:System.Globalization.DateTimeFormatInfo> sınıfını kullanın.

    - Sayısal biçimlendirme için <xref:System.Globalization.NumberFormatInfo> sınıfını kullanın.

    - Gregoryen ve Gregoryen olmayan takvimler için, <xref:System.Globalization.Calendar> sınıfı veya belirli takvim uygulamalarından birini kullanın.

3. Uygun durumlarda sınıfı tarafından sunulan kültür özelliği ayarlarını kullanın <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> . <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>Tarih ve saat veya sayısal biçimlendirme gibi biçimlendirme görevleri için özelliğini kullanın. <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType>Kaynakları almak için özelliğini kullanın. `CurrentCulture`Ve `CurrentUICulture` özelliklerinin iş parçacığı başına ayarlanabileceğini unutmayın.

4. Ad alanındaki kodlama sınıflarını kullanarak, uygulamanızın çeşitli kodlara ve verileri okumasını ve veri yazmasını sağlar <xref:System.Text> . ASCII verilerini kabul etmez. Bir kullanıcının metin girebileceği her yerde Uluslararası karakterlerin sağlanma kabul edilir. Örneğin, uygulama sunucu adları, dizinler, dosya adları, Kullanıcı adları ve URL 'lerde uluslararası karakterleri kabul etmelidir.

5. <xref:System.Text.UTF8Encoding>Sınıfı kullanırken, güvenlik nedenleriyle, bu sınıf tarafından sunulan hata algılama özelliğini kullanın. Hata algılama özelliğini etkinleştirmek için, bir `throwOnInvalidBytes` parametre alan ve bu parametrenin değerini olarak ayarlanan oluşturucuyu kullanarak sınıfının bir örneğini oluşturun `true` .

6. Mümkün olduğunda, dizeleri tek bir dizi karakter yerine tüm dizeler olarak işleyin. Bu, alt dizeleri sıralarken veya ararken özellikle önemlidir. Bu, Birleşik karakterlerin ayrıştırılmasından ilişkili sorunları engeller. Sınıfını kullanarak, tek karakterler yerine metin birimleriyle da çalışabilirsiniz <xref:System.Globalization.StringInfo?displayProperty=nameWithType> .

7. Ad alanı tarafından sunulan sınıfları kullanarak metni görüntüler <xref:System.Drawing> .

8. İşletim sistemleri arasında tutarlılık için, Kullanıcı ayarlarının geçersiz kılınmasına izin vermeyin <xref:System.Globalization.CultureInfo> . `CultureInfo`Bir parametreyi kabul eden oluşturucuyu kullanın `useUserOverride` ve olarak ayarlayın `false` .

9. Uluslararası verileri kullanarak, uygulama işlevselliklerinizi Uluslararası işletim sistemi sürümlerinde test edin.

10. Bir güvenlik kararı bir dize karşılaştırma veya örnek değişikliği işleminin sonucunu temel alıyorsa, kültüre duyarsız bir dize işlemi kullanın. Bu uygulama, sonucun değerinden etkilenmemesini sağlar `CultureInfo.CurrentCulture` . Kültüre duyarlı dize karşılaştırmalarının nasıl tutarsız sonuçlar üretediğini gösteren bir örnek için [dizeleri kullanmak Için En Iyi Yöntemler](../base-types/best-practices-strings.md) konusunun ["geçerli kültürü kullanan dize karşılaştırmaları"](../base-types/best-practices-strings.md#string-comparisons-that-use-the-current-culture) bölümüne bakın.

## <a name="localization-best-practices"></a>Yerelleştirme en iyi uygulamaları

1. Tüm yerelleştirilebilir kaynakları yalnızca kaynak dll 'Lerine taşıyın. Yerelleştirilebilir kaynaklar, dizeler, hata iletileri, iletişim kutuları, menüler ve katıştırılmış nesne kaynakları gibi kullanıcı arabirimi öğelerini içerir.

2. Dizeleri veya Kullanıcı arabirimi kaynaklarını hardmayın.

3. Yerelleştirilemeyen kaynakları yalnızca kaynak dll 'Lerine yerleştirmeyin. Bu, çevirmenler için karışıklık oluşmasına neden olur.

4. Birleştirilmiş ifadelerden çalışma zamanında oluşturulan bileşik dizeleri kullanmayın. Birleşik dizelerin yerelleştirilmesi zordur, çünkü genellikle tüm diller için uygun olmayan Ingilizce dilbilgisi sırasını varsayar.

5. Dizelerin, dize bileşenlerinin dilbilgisi rollerine bağlı olarak farklı çevrilebileceği "boş klasör" gibi belirsiz yapıların kaçının. Örneğin, "boş" bir fiil veya sıfata olabilir. Bu, Italyanca veya Fransızca gibi dillerdeki farklı çevirilerine yol açabilir.

6. Uygulamanızda metin içeren görüntüleri ve simgeleri kullanmaktan kaçının. Yerelleştirmeye pahalıdır.

7. Kullanıcı arabiriminde genişleyebilir dizelerin uzunluğu için çok sayıda odaya izin verin. Bazı dillerde, deyimler diğer dillerde gereksinimlerden daha fazla yüzde 50-75 sürebilir.

8. Kültür temelinde <xref:System.Resources.ResourceManager?displayProperty=nameWithType> kaynakları almak için sınıfını kullanın.

9. [Windows Forms Kaynak Düzenleyicisi (Winres. exe)](../../framework/tools/winres-exe-windows-forms-resource-editor.md)kullanılarak yerelleştirilebilecek Windows Forms iletişim kutusu oluşturmak Için [Visual Studio 'yu](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) kullanın. Windows Forms iletişim kutularını el ile kodlayın.

10. Profesyonel yerelleştirme için düzenleyin (çeviri).

11. Kaynakları oluşturma ve yerelleştirme hakkında ayrıntılı bir açıklama için bkz. [uygulamalardaki kaynaklar](../../framework/resources/index.md).

## <a name="globalization-best-practices-for-aspnet-applications"></a>ASP.NET uygulamaları için Genelleştirme en iyi yöntemleri

1. <xref:System.Globalization.CultureInfo.CurrentUICulture%2A>Uygulamanızda ve özelliklerini açık olarak ayarlayın <xref:System.Globalization.CultureInfo.CurrentCulture%2A> . Varsayılanlara güvenmeyin.

2. ASP.NET uygulamalarının yönetilen uygulamalar olduğunu ve bu nedenle, kültürü temel alan bilgileri alma, görüntüleme ve düzenleme için diğer yönetilen uygulamalarla aynı sınıfları kullanabileceğini unutmayın.

3. ASP.NET içinde aşağıdaki üç tür kodlamayı belirtabilin farkında olun:

    - requestEncoding, istemcinin tarayıcısından alınan kodlamayı belirtir.

    - responseEncoding, istemci tarayıcısına göndermek için kodlamayı belirtir. Çoğu durumda, bu kodlama requestEncoding için belirtilen ile aynı olmalıdır.

    - fileEncoding,. aspx,. asmx ve. asax dosya ayrıştırması için varsayılan kodlamayı belirtir.

4. Bir ASP.NET uygulamasında aşağıdaki üç yerde requestEncoding, responseEncoding, fileEncoding, Culture ve UICulture özniteliklerinin değerlerini belirtin:

    - Bir Web. config dosyasının Genelleştirme bölümünde. Bu dosya ASP.NET uygulamasının dışında. Daha fazla bilgi için bkz. [ \<globalization> öğesi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hy4kkhe0(v=vs.100)).

    - Bir sayfa yönergesinde. Bir uygulama bir sayfada olduğunda, dosyanın zaten okunup okunmadığını unutmayın. Bu nedenle, fileEncoding ve requestEncoding belirtmek için çok geç. Bir sayfa yönergesinde yalnızca UICulture, Culture ve responseEncoding belirtilebilir.

    - Uygulama kodunda programlı olarak. Bu ayar, istek başına farklılık gösterebilir. Bir sayfa yönergesinde olduğu gibi, uygulamanın koduna ulaşıldığında, fileEncoding ve requestEncoding belirtmek için çok geç olur. Uygulama kodunda yalnızca UICulture, Culture ve responseEncoding belirtilebilir.

5. UICulture değerinin tarayıcı kabul diline ayarlanbileceğini unutmayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Genelleştirme ve yerelleştirme](index.md)
- [Masaüstü uygulamalarındaki kaynaklar](../../framework/resources/index.md)
