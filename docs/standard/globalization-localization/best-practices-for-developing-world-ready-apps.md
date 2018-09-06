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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 35b8e062c9f207eba19bcee5593425095de2e267
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44041476"
---
# <a name="best-practices-for-developing-world-ready-applications"></a>Dünyaya Hazır Uygulamalar Geliştirmek için En İyi Yöntemler
Bu bölümde dünya çapında kullanılmaya hazır uygulamalar geliştirirken izlenecek en iyi uygulamaları açıklar.  
  
## <a name="globalization-best-practices"></a>En iyi Genelleştirme pratikleri  
  
1.  Dahili olarak Unicode uygulamanızı olun.  
  
2.  Tarafından sağlanan kültüre duyarlı sınıfları kullanın <xref:System.Globalization> veri işlemek ve biçimlendirmek için ad alanı.  
  
    -   Sıralamada kullanmak <xref:System.Globalization.SortKey> sınıfı ve <xref:System.Globalization.CompareInfo> sınıfı.  
  
    -   Dize karşılaştırmaları için kullanma <xref:System.Globalization.CompareInfo> sınıfı.  
  
    -   Tarih ve saat biçimlendirme için kullanma <xref:System.Globalization.DateTimeFormatInfo> sınıfı.  
  
    -   Sayısal biçimlendirme için <xref:System.Globalization.NumberFormatInfo> sınıfı.  
  
    -   Miladi ve Miladi olmayan takvimlerde kullanın <xref:System.Globalization.Calendar> sınıf ya da belirli Takvim uygulamalarından birini.  
  
3.  Tarafından sağlanan kültür özellik ayarlarını kullanın <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> uygun durumlarda sınıfı. Kullanım <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> tarih ve saat veya sayısal biçimlendirme gibi biçimlendirme özelliği görevler. Kullanım <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> kaynakları almak için özellik. Unutmayın `CurrentCulture` ve `CurrentUICulture` başına iş parçacığı özellikleri ayarlanabilir.  
  
4.  Uygulamanızın Okuma ve kodlama sınıflarını kullanarak Kodlamalar çeşitli gelen ve giden veri yazma <xref:System.Text> ad alanı. ASCII verisini varsaymayın. Uluslararası karakterler sağlanması varsayar herhangi bir kullanıcının metin girebileceği. Örneğin, uygulama, sunucu adları, dizin, dosya adları, kullanıcı adları ve URL'leri uluslararası karakterleri kabul etmelidir.  
  
5.  Kullanırken <xref:System.Text.UTF8Encoding> sınıfı, güvenlik nedeniyle, bu sınıfın sunduğu hata algılama özelliğini kullanın. Uygulama hata algılama özelliğini açmak için alan oluşturucu kullanılarak sınıfının bir örneğini oluşturur bir `throwOnInvalidBytes` parametresi ve bu parametrenin değerini ayarlar `true`.  
  
6.  Mümkün olduğunda, bir tek karakter dizisi olarak yerine bütün dizeler olarak tanıtıcı dizeleri. Sıralama veya alt dizeleri için arama yaparken bu özellikle önemlidir. Bu, birleşik karakterleri ayrıştırmayla ilgili sorunları önler.  
  
7.  Ekran tarafından sağlanan sınıfları kullanarak metni <xref:System.Drawing> ad alanı.  
  
8.  İşletim sistemleri arasında tutarlılık sağlamak için kullanıcı ayarlarını geçersiz kılmak izin verme <xref:System.Globalization.CultureInfo>. Kullanım `CultureInfo` kabul eden Oluşturucu bir `useUserOverride` parametresi ve `false`.  
  
9. Uygulamanızın işlevselliğini uluslararası işletim sistemi sürümlerinde, uluslararası veriler kullanarak test edin.  
  
10. Bir güvenlik kararı bir dize karşılaştırmasının sonucuna bağlı ya da vaka değişim işleminin, uygulamanın kültüre duyarlı bir işlem gerçekleştirmek vardır. Bu yöntem, sonuç değeri tarafından etkilenmemesini sağlar `CultureInfo.CurrentCulture`. "Dize karşılaştırmaları geçerli kültürü kullanan" bölümüne bakın [kullanarak dizeleri için en iyi](../../../docs/standard/base-types/best-practices-strings.md) nasıl kültüre duyarlı dize gösteren bir örnek için karşılaştırmalar tutarsız sonuçlara neden olabilir.  
  
## <a name="localization-best-practices"></a>Yen iyi yerelleştirme pratikleri  
  
1.  Tüm yerelleştirilebilir kaynakları ayrı yalnızca kaynak DLL'lerine taşıyın. Yerelleştirilebilir kaynaklar, dizeler, hata iletileri, iletişim kutuları, menüler ve katıştırılmış nesne kaynakları gibi kullanıcı arabirimi öğelerini içerir.  
  
2.  Sabit kodlamayın dizesi değil ya da kullanıcı arabirimi kaynaklarını yapın.  
  
3.  Yerelleştirilemez kaynakları salt kaynak DLL'leri koymayın. Bu, çevirmenler için karışıklığa neden olur.  
  
4.  Yan tümcelerden çalışma zamanında oluşturulan bileşik dizeleri yapın. Bileşik dizeler, bunlar genellikle, tüm diller için geçerli olmayan bir İngilizce gramer olduğunu varsaydığından yerelleştirmek zordur.  
  
5.  "Boş yere dizeleri farklı dize bileşenlerinin gramer rollerine bağlı olarak çevrilebilir klasör" gibi belirsiz yapıları kaçının. Örneğin, "boş" bir fiil ya da İtalyanca ya da Fransızca gibi dillerde farklı çevirilere yol açabilir bir sıfat olabilir.  
  
6.  Görüntüler ve uygulamanızda metin içeren simgeler kullanmaktan kaçının. Bunlar yerelleştirmek pahalıdır.  
  
7.  Kullanıcı arabiriminde, genişletme amacıyla dizelerin uzunluğu için yeterli izin verir. Bazı dillerde tümcecikleri 50-75 daha fazla alan gereken diğer dillerde yüzde gerektirebilir.  
  
8.  Kullanım <xref:System.Resources.ResourceManager?displayProperty=nameWithType> kaynakları almak için sınıf tabanlı kültürü üzerinde.  
  
9. Windows Forms iletişim kutuları oluşturmak için Visual Studio kullanarak yerelleştirilebilen böylece kullanın [Windows Forms Kaynak Düzenleyicisi'ni (Winres.exe)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md). Windows Forms iletişim kutuları ile kodlamayın.  
  
10. Profesyonel yerelleştirme (çeviri) için düzenleyin.  
  
11. Oluşturma ve kaynakları yerelleştirme tam açıklaması için bkz. [uygulamalardaki kaynaklar](../../../docs/framework/resources/index.md).  
  
## <a name="globalization-best-practices-for-aspnet-applications"></a>ASP.NET uygulamaları için en iyi Genelleştirme pratikleri  
  
1.  Açıkça <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> ve <xref:System.Globalization.CultureInfo.CurrentCulture%2A> uygulamanızdaki özellikleri. Varsayılanlara güvenmeyin.  
  
2.  ASP.NET uygulamalarının yönetilen uygulamalar olduğuna ve almak için aynı sınıf yönetilen diğer uygulamalar bu nedenle kullanabilir Not kültüre göre görüntülemek ve bilgi düzenleme temel.  
  
3.  ASP.NET'te aşağıdaki üç tür kodlamayı belirtebilirsiniz dikkat edin:  
  
    -   requestEncoding, kodlamanın istemcinin tarayıcısından alındığını belirtir.  
  
    -   responseEncoding, istemci tarayıcıya göndermek için kodlamasını belirtir. Çoğu durumda, bu kodlama requestEncoding için belirtilen ile aynı olmalıdır.  
  
    -   fileEncoding .aspx, .asmx ve .asax dosya ayrıştırması için varsayılan belirtir.  
  
4.  RequestEncoding, responseEncoding, fileEncoding, culture ve uiCulture özniteliklerinin değerlerini bir ASP.NET uygulamasında aşağıdaki üç yerde belirtin:  
  
    -   Web.config dosyasının Genelleştirme bölümünde. Bu dosya, ASP.NET uygulamasının dışındadır. Daha fazla bilgi için [ \<Genelleştirme > öğesi](https://msdn.microsoft.com/library/e2dffc8e-ebd2-439b-a2fd-e3ac5e620da7).  
  
    -   Bir sayfa yönergesinde. Bir uygulama bir sayfada olduğunda, dosyanın zaten okunmuş olduğuna dikkat edin. Bu nedenle, çok geç fileEncoding ve Requestencoding'i belirtmek için gereklidir. Bir sayfa yönergesinde yalnızca uiCulture, Culture ve responseEncoding belirtilebilir.  
  
    -   Uygulama kodunda programlı olarak. Bu ayar isteğe göre değişebilir. Bir sayfa yönergesi ile zaman uygulama kodunun olduğu gibi fileEncoding ve Requestencoding'i belirtmek için çok geç olduğu. Uygulama kodunda yalnızca uiCulture, Culture ve responseEncoding belirtilebilir.  
  
5.  UiCulture değerinin tarayıcı ayarlanabilir Not dil kabul edin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Genelleştirme ve Yerelleştirme](../../../docs/standard/globalization-localization/index.md)  
- [Masaüstü Uygulamalarındaki Kaynaklar](../../../docs/framework/resources/index.md)
