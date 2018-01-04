---
title: "Dünyaya Hazır Uygulamalar Geliştirmek için En İyi Yöntemler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- global applications, best practices
- world-ready applications, best practices
- globalization [.NET Framework], best practices
- international applications [.NET Framework], best practices
ms.assetid: f08169c7-aad8-4ec3-9a21-9ebd3b89986c
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 367da11fd0af9673a60d9acff20aef5969c98aae
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="best-practices-for-developing-world-ready-applications"></a>Dünyaya Hazır Uygulamalar Geliştirmek için En İyi Yöntemler
Bu bölümde, dünya çapında kullanılmaya hazır uygulamalar geliştirirken izlemek için en iyi uygulamaları açıklar.  
  
## <a name="globalization-best-practices"></a>Genelleştirme en iyi uygulamalar  
  
1.  Uygulamanızı Unicode dahili olun.  
  
2.  Tarafından sağlanan kültür duyarlı sınıfları kullanan <xref:System.Globalization> değiştirmek ve verilerin biçimlendirilmesi için ad alanı.  
  
    -   Sıralama için kullanmak <xref:System.Globalization.SortKey> sınıfı ve <xref:System.Globalization.CompareInfo> sınıfı.  
  
    -   Dize karşılaştırmaları için kullanma <xref:System.Globalization.CompareInfo> sınıfı.  
  
    -   Tarih ve saat biçimlendirmesi için kullanmak <xref:System.Globalization.DateTimeFormatInfo> sınıfı.  
  
    -   Sayısal biçimlendirme için <xref:System.Globalization.NumberFormatInfo> sınıfı.  
  
    -   Gregoryen ve Miladi olmayan takvimleri kullanın <xref:System.Globalization.Calendar> sınıf veya belirli Takvim uygulamaları biri.  
  
3.  Tarafından sağlanan kültür özellik ayarları kullanmak <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> uygun durumlarda sınıfı. Kullanım <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> biçimlendirme özelliği görevler, tarih ve saat veya sayısal biçimlendirme gibi. Kullanım <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> kaynakları almak için özellik. Unutmayın `CurrentCulture` ve `CurrentUICulture` başına iş parçacığı özellikleri ayarlanabilir.  
  
4.  Okuma ve Kodlamalar çeşitli gelen ve şifreleme sınıflarını kullanarak veri yazmak uygulamanızı etkinleştirme <xref:System.Text> ad alanı. ASCII veri varsayalım değil. Uluslararası karakterler sağlanması varsayın kullanıcı metin herhangi bir yere girebilirsiniz. Örneğin, uygulama, sunucu adları, dizinleri, dosya adları, kullanıcı adları ve URL'leri uluslararası karakterler kabul etmelidir.  
  
5.  Kullanırken <xref:System.Text.UTF8Encoding> sınıfı, güvenlik nedeniyle, bu sınıf tarafından sunulan hata algılama özelliğini kullanın. Uygulama hatası algılama özelliği etkinleştirmek için alan oluşturucu kullanılarak sınıfının bir örneğini oluşturur bir `throwOnInvalidBytes` parametresi ve değeri bu parametrenin ayarlar `true`.  
  
6.  Mümkün olduğunda, tek tek karakter dizisi olarak yerine tüm dizeleri olarak tanıtıcı dizeleri. Sıralama veya alt dizeler için arama bu özellikle önemlidir. Bu ayrıştırma birleşik karakterlerle ilişkili sorunları önler.  
  
7.  Tarafından sağlanan sınıfları kullanarak metin görüntüleme <xref:System.Drawing> ad alanı.  
  
8.  İşletim sistemleri genelinde tutarlılık sağlamak için kullanıcı ayarlarını geçersiz kılmak izin verme <xref:System.Globalization.CultureInfo>. Kullanım `CultureInfo` kabul Oluşturucusu bir `useUserOverride` parametre ve ayarlamak `false`.  
  
9. Uluslararası veri kullanarak uluslararası işletim sistemi sürümlerinde, uygulamanın işlevselliğini test etmek.  
  
10. Güvenlik kararı dize karşılaştırmasının sonucuna dayalı veya durum değiştirme işlemi, kültüre duyarsız bir işlemi uygulama vardır. Bu yöntem sonuç değeri tarafından etkilenmez sağlar `CultureInfo.CurrentCulture`. "Dize karşılaştırmaları kullanma geçerli kültür" bölümüne bakın [kullanarak dizeleri için en iyi uygulamaları](../../../docs/standard/base-types/best-practices-strings.md) nasıl kültüre duyarlı dize gösteren bir örnek için karşılaştırmaları tutarsız sonuçlara yol açabilir.  
  
## <a name="localization-best-practices"></a>Yerelleştirme en iyi uygulamalar  
  
1.  Yalnızca kaynak DLL'ler ayırmak için tüm yerelleştirilebilir kaynakları taşıyın. Yerelleştirilebilir kaynaklar dizeler, hata iletileri, iletişim kutularını, menüleri ve katıştırılmış nesne kaynakları gibi kullanıcı arabirimi öğeleri içerir.  
  
2.  Değil stillerinizin dizeleri veya kullanıcı arabirimi kaynakları yapın.  
  
3.  Nonlocalizable kaynaklar yalnızca kaynak DLL'ler koymayın. Bu, çevirmenler için karışıklığa neden olur.  
  
4.  Birleştirilmiş tümcecikleri gelen çalışma zamanında oluşturulan değil kullanın composite dizeleri yapın. Bileşik dizeleri bunlar genellikle, tüm diller için geçerli değildir İngilizce dilbilgisi sipariş varsayar çünkü yerelleştirme zordur.  
  
5.  "Boş burada dizeleri farklı dize bileşenleri dilbilgisi rollerine bağlı olarak çevrilebilir klasörü" gibi belirsiz yapıları kaçının. Örneğin, "boş" bir fiil veya İtalyanca veya Fransızca gibi dillerde farklı çevirileri açabilir bir gelen olabilir.  
  
6.  Görüntüleri ve uygulamanızda metin içeren simgeleri kullanmaktan kaçının. Bunlar yerelleştirme maliyetlidir.  
  
7.  Kullanıcı arabiriminde genişletmek için dize uzunluğu için yeterli izin verir. Bazı dillerde, bunlar daha fazla alan gereken diğer dillerde yüzde 50 75 tümcecikleri gerektirebilir.  
  
8.  Kullanım <xref:System.Resources.ResourceManager?displayProperty=nameWithType> kaynakları almak için sınıf tabanlı kültürü üzerinde.  
  
9. Böylece kullanarak yerelleştirilebilir Windows Forms iletişim kutuları oluşturmak için Visual Studio'yu kullanın [Windows Forms Kaynak Düzenleyici (Winres.exe)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md). Windows Forms iletişim kutuları el ile kodu değil.  
  
10. Profesyonel yerelleştirme (çevirisi) düzenleyin.  
  
11. Oluşturma ve kaynakları yerelleştirme tam bir açıklaması için bkz: [uygulamalarında kaynakları](../../../docs/framework/resources/index.md).  
  
## <a name="globalization-best-practices-for-aspnet-applications"></a>ASP.NET uygulamaları için genelleştirme en iyi yöntemler  
  
1.  Açık olarak ayarlanıp <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> ve <xref:System.Globalization.CultureInfo.CurrentCulture%2A> uygulamanızda özellikleri. Varsayılanlara kullanmayın.  
  
2.  ASP.NET uygulamaları yönetilen uygulamaları ve almak için aynı sınıflar yönetilen diğer uygulamalar bu nedenle kullanabilirsiniz Not görüntüleme ve bilgi düzenleme kültür üzerinde temel.  
  
3.  ASP.NET Kodlamalar aşağıdaki üç tür belirtebilirsiniz dikkat edin:  
  
    -   requestEncoding istemcinin tarayıcıdan alınan kodlamasını belirtir.  
  
    -   responseEncoding istemci tarayıcıya göndermek için kodlamasını belirtir. Çoğu durumda bu kodlama için requestEncoding belirtilen ile aynı olmalıdır.  
  
    -   fileEncoding varsayılan .aspx, .asmx ve .asax dosya ayrıştırması için kodlamayı belirtir.  
  
4.  Bir ASP.NET uygulamasında aşağıdaki üç yerde requestEncoding, responseEncoding, fileEncoding, kültür ve UICulture öznitelikleri için değerleri belirtin:  
  
    -   Web.config dosyasının Genelleştirme bölümünde. Bu ASP.NET uygulamasını dış dosyasıdır. Daha fazla bilgi için bkz: [ \<Genelleştirme > öğesi](http://msdn.microsoft.com/en-us/e2dffc8e-ebd2-439b-a2fd-e3ac5e620da7).  
  
    -   Bir sayfa yönergesinde. Bir uygulama içinde bir sayfa olduğunda, dosyanın daha önce Okunmuş, unutmayın. Bu nedenle, bu çok geç fileEncoding ve requestEncoding belirtmektir. Yalnızca UICulture, kültür ve responseEncoding bir sayfa yönergesinde belirtilebilir.  
  
    -   Program aracılığıyla uygulama kodunda. Bu ayar, istek başına farklılık gösterebilir. Sayfa yönergesi ile zamanına göre uygulama kodunun ulaşıldığında çok geç fileEncoding ve requestEncoding belirtmek için aynıdır. Yalnızca UICulture, kültür ve responseEncoding uygulama kodunda belirtilebilir.  
  
5.  Tarayıcıya UICulture değer ayarlanabilir Not dil kabul edin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Genelleştirme ve Yerelleştirme](../../../docs/standard/globalization-localization/index.md)  
 [Masaüstü Uygulamalarındaki Kaynaklar](../../../docs/framework/resources/index.md)
