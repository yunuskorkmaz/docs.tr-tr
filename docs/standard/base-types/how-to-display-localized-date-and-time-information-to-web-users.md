---
title: "Nasıl yapılır: Web Kullanıcılarına Yerelleştirilmiş Tarih ve Saat Bilgilerini Görüntüleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- formatting [.NET Framework], dates
- parsing strings [.NET Framework], date and time strings
- localization [.NET Framework], date and time displays
- formatting [.NET Framework], localized data
- displaying date and time data
- localized date displays [.NET Framework]
ms.assetid: 377fe93c-32be-421a-a30a-be639a46ede8
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 21493e0e0c9e42cf5efc42d86c8f126fbae9b392
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-localized-date-and-time-information-to-web-users"></a>Nasıl yapılır: Web Kullanıcılarına Yerelleştirilmiş Tarih ve Saat Bilgilerini Görüntüleme
Bir Web sayfası dünyanın her yerden görüntülenebilir olduğundan, ayrıştırma ve tarih ve saat değerlerini biçimlendirmek işlemleri (genellikle Web sunucusunun yerel kültür biçimi) bir varsayılan biçimi üzerinde güvenmemelisiniz kullanıcıyla kullanılırken. Bunun yerine, işleyen tarih ve saat dizeleri giriş kullanıcı tarafından Web forms kullanıcının tercih edilen kültürü kullanarak dizeleri ayrıştırma. Benzer şekilde, tarih ve saat verilerini kullanıcıya kullanıcının kültürü için uyumlu bir biçimde görüntülenmesi gerekir. Bu konuda, bunun nasıl yapılacağı gösterilmektedir.  
  
### <a name="to-parse-date-and-time-strings-input-by-the-user"></a>Tarih ve saat ayrıştırmak için kullanıcı tarafından Giriş dizeleri  
  
1.  Dize dizisi tarafından döndürülen olup olmadığını belirlemek <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> özelliği doldurulur. Değilse, 6. adıma geçin.  
  
2.  Dize dizisi olarak döndürülürse <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği doldurulur, ilk alt öğesi alın. İlk öğesi, kullanıcının varsayılan veya tercih edilen dil ve bölge gösterir.  
  
3.  Örneği bir <xref:System.Globalization.CultureInfo> kullanıcıyı temsil eden nesne tercih edilen kültür çağırarak <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> Oluşturucusu.  
  
4.  Ya da çağrısı `TryParse` veya `Parse` yöntemi <xref:System.DateTime> veya <xref:System.DateTimeOffset> türüne dönüştürmeyi deneyin. Bir aşırı yüklemesini kullanın `TryParse` veya `Parse` yöntemi ile bir `provider` parametresi ve aşağıdakilerden birini geçirin:  
  
    -   <xref:System.Globalization.CultureInfo> 3. adımda oluşturulan nesne.  
  
    -   <xref:System.Globalization.DateTimeFormatInfo> Tarafından döndürülen nesne <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> özelliği <xref:System.Globalization.CultureInfo> 3. adımda oluşturulan nesne.  
  
5.  Dönüştürme başarısız olursa, tarafından döndürülen 2 ile 4 dize dizisi kalan her öğe için adımları yineleyin <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği.  
  
6.  Dönüştürme yine başarısız olursa veya dize dizisi olarak döndürülürse <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği boşsa, dize sabit kültür tarafından döndürülen kullanarak XML'in <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> özelliği.  
  
### <a name="to-parse-the-local-date-and-time-of-the-users-request"></a>Yerel tarih ve saat kullanıcının isteği ayrıştırılamıyor  
  
1.  Ekleme bir <xref:System.Web.UI.WebControls.HiddenField> Web formu denetimi.  
  
2.  İşleme bir JavaScript işlevi oluşturma `onClick` olayı bir `Submit` gelen Eşgüdümlü Evrensel Saat (UTC) için geçerli tarih ve saat ile yerel saat diliminin uzaklığı yazarak düğmesi <xref:System.Web.UI.WebControls.HiddenField.Value%2A> özelliği. Dize, iki bileşeni birbirinden ayırmak için sınırlayıcı (örneğin, noktalı virgül) kullanın.  
  
3.  Web formun kullanmak <xref:System.Web.UI.Control.PreRender> HTML'e işlevi eklemesine olay çıkış akışı komut dosyasına metin geçirerek <xref:System.Web.UI.ClientScriptManager.RegisterClientScriptBlock%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType> yöntemi.  
  
4.  Olay işleyicisine bağlanmak `Submit` düğmenin `onClick` için JavaScript işlevinin adı sağlayarak olay `OnClientClick` özniteliği `Submit` düğmesi.  
  
5.  İçin bir işleyici oluşturmak `Submit` düğmenin <xref:System.Web.UI.WebControls.Button.Click> olay.  
  
6.  Olay işleyicisinin dize dizisi tarafından döndürülen olup olmadığını belirlemek <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> özelliği doldurulur. Değilse, 14. adıma geçin.  
  
7.  Dize dizisi olarak döndürülürse <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği doldurulur, ilk alt öğesi alın. İlk öğesi, kullanıcının varsayılan veya tercih edilen dil ve bölge gösterir.  
  
8.  Örneği bir <xref:System.Globalization.CultureInfo> kullanıcıyı temsil eden nesne tercih edilen kültür çağırarak <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> Oluşturucusu.  
  
9. Atanmış bir dizeyi geçirmek <xref:System.Web.UI.WebControls.HiddenField.Value%2A> özelliğine <xref:System.String.Split%2A> kullanıcının yerel tarih ve saat dize gösterimini ve kullanıcının yerel saat dilimi uzaklığı dize gösterimini ayrı dizi öğeleri depolamak için yöntem.  
  
10. Ya da çağrısı <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> veya <xref:System.DateTime.TryParse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%2CSystem.DateTime%40%29?displayProperty=nameWithType> kullanıcının isteğine saat ve tarih biçimine dönüştürecek şekilde bir <xref:System.DateTime> değeri. Bir yöntemle kullanın bir `provider` parametresi ve aşağıdakilerden birini geçirin:  
  
    -   <xref:System.Globalization.CultureInfo> 8. adımda oluşturduğunuz nesne.  
  
    -   <xref:System.Globalization.DateTimeFormatInfo> Tarafından döndürülen nesne <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> özelliği <xref:System.Globalization.CultureInfo> 8. adımda oluşturduğunuz nesne.  
  
11. 10 adımda ayrıştırma işlemi başarısız olursa, 13. adıma gidin. Aksi halde çağrı <xref:System.UInt32.Parse%28System.String%29?displayProperty=nameWithType> kullanıcının saat dilimi konumu dize gösterimini bir tamsayıya dönüştürmek için yöntem.  
  
12. Örneği bir <xref:System.DateTimeOffset> kullanıcının yerel saat çağırarak temsil eden <xref:System.DateTimeOffset.%23ctor%28System.DateTime%2CSystem.TimeSpan%29?displayProperty=nameWithType> Oluşturucusu.  
  
13. 10 adımda dönüştürme başarısız olursa, tarafından döndürülen 7 arasındaki adımları ile 12 dize dizisi kalan her öğe için yineleyin <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği.  
  
14. Dönüştürme yine başarısız olursa veya dize dizisi olarak döndürülürse <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği boşsa, dize sabit kültür tarafından döndürülen kullanarak XML'in <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> özelliği. Ardından 7 ile 12 arasında adımları yineleyin.  
  
 Sonuç bir <xref:System.DateTimeOffset> Web sayfanızın kullanıcı yerel saatini temsil eden nesne. Ardından çağırarak eşdeğer UTC belirleyebilirsiniz <xref:System.DateTimeOffset.ToUniversalTime%2A> yöntemi. Ayrıca eşdeğer tarih ve saat Web sunucunuzda çağırarak belirleyebilirsiniz <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> yöntemi ve değerini geçirme <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> süresi dönüştürmek için saat dilimi olarak.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, HTML kaynağını ve bir tarih ve saat değeri giriş için kullanıcıdan bir ASP.NET Web formu kodunu içerir. İstemci tarafı komut dosyası, gizli bir alan için UTC yerel tarih ve saat kullanıcının isteğinin ve kullanıcının saat dilimi uzaklığını hakkında bilgi de yazar. Bu bilgiler daha sonra kullanıcının giriş görüntüleyen bir Web sayfası döndürür sunucunun tarafından ayrıştırılır. Ayrıca kullanıcının isteği kullanıcının yerel saat, saat, sunucu ve UTC kullanılarak saat ve tarihi görüntüler.  
  
 [!code-aspx-csharp[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/cs/GetDateInfo.aspx#1)]
 [!code-aspx-vb[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/vb/GetDateInfo.aspx#1)]
  
 İstemci tarafı komut dosyası JavaScript çağrılarını `toLocaleString` yöntemi. Bu sunucu üzerinde başarıyla ayrıştırılması olasılığı daha yüksektir kullanıcının yerel ayarı biçimlendirme kuralları izleyen bir dize oluşturur.  
  
 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> Özelliği bulunan kültür adlarından doldurulur `Accept-Language` bir HTTP isteğine dahil üstbilgileri. Ancak, tüm tarayıcılar dahil `Accept-Language` üstbilgileri kendi isteklerini ve kullanıcılar da bastırmak üstbilgileri tamamen. Bu, kullanıcı girişi ayrıştırırken bir geri dönüş kültür sağlamak önemli kolaylaştırır. Genellikle geri dönüş tarafından döndürülen sabit kültür kültürdür <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Kullanıcılar ayrıca Internet Explorer kültür adlarıyla kültür adları geçerli olmayabilir olasılığı oluşturan bir metin kutusunda giriş sağlayabilirsiniz. Bu örneği oluşturulurken özel durum işleme kullanmak önemli kılar bir <xref:System.Globalization.CultureInfo> nesnesi.  
  
 Internet Explorer tarafından gönderilen HTTP isteğinden alınırken <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> dizi kullanıcı tercih sırasına göre doldurulur. Dizinin ilk öğesi, kullanıcının birincil kültür/bölge adını içerir. Dizi ek öğeler içeriyorsa, Internet Explorer bunları rasgele kültür adı noktalı virgülle ayrılmış bir kalite belirticisi atar. Örneğin, fr-FR kültür için bir giriş form alabilir `fr-FR;q=0.7`.  
  
 Örnek aramalar <xref:System.Globalization.CultureInfo.%23ctor%2A> Oluşturucu kendi `useUserOverride` parametre kümesine `false` yeni <xref:System.Globalization.CultureInfo> nesnesi. Kültür adı sunucusundaki varsayılan kültür adı ise bu, sağlar yeni <xref:System.Globalization.CultureInfo> sınıfı oluşturucusu tarafından oluşturulan nesne bir kültürün varsayılan ayarları içerir ve sunucunun kullanarak geçersiz kılınmış herhangi bir ayarı yansıtmaz  **Bölge ve Dil Seçenekleri** uygulama. Sunucudaki tüm geçersiz kılınmış ayarları değerleri, kullanıcının sistemde yok veya kullanıcının giriş yansıtılması düşüktür.  
  
 Bu örnek bir tarih ve saat (kullanıcı tarafından diğer gizli alan depolanan bir giriş) iki dize sunumu ayrıştırması nedeniyle olası tanımlar <xref:System.Globalization.CultureInfo> önceden gerekebilecek nesneleri. Bir dizi oluşturur <xref:System.Globalization.CultureInfo> tarafından döndürülen öğe sayısından daha büyük bir nesneleri <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> özelliği. Ardından başlatır bir <xref:System.Globalization.CultureInfo> nesne her bir dil/bölge dize için ve ayrıca başlatır bir <xref:System.Globalization.CultureInfo> temsil eden nesnesi <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.  
  
 Kodunuzu ya da çağırabilirsiniz <xref:System.DateTime.Parse%2A> veya <xref:System.DateTime.TryParse%2A> kullanıcının dize gösterimini bir tarih ve zaman yöntemi bir <xref:System.DateTime> değeri. Parse yöntemi yinelenen çağrıları için tek bir ayrıştırma işlemi gerekli olabilir. Sonuç olarak, <xref:System.DateTime.TryParse%2A> yöntemi olduğundan daha iyi döndürdüğü `false` ayrıştırma işlemi başarısız olursa. Buna karşılık, tarafından oluşturulan yinelenen özel durumları işleme <xref:System.DateTime.Parse%2A> yöntemi, bir Web uygulaması çok pahalı bir teklifinde olabilir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Kodu derlemek için oluşturma bir [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] bir arka plan kodu olmadan Web sayfası. Böylece tüm var olan kodu yerini örneği Web sayfasına kopyalayın. [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web sayfası aşağıdaki denetimleri içermelidir:  
  
-   A <xref:System.Web.UI.WebControls.Label> kodunda başvurulmuyor denetim. Ayarlama, <xref:System.Web.UI.WebControls.TextBox.Text%2A> özelliğine "bir sayı girin:".  
  
-   A <xref:System.Web.UI.WebControls.TextBox> adlı Denetim `DateString`.  
  
-   A <xref:System.Web.UI.WebControls.Button> adlı Denetim `OKButton`. Ayarlama, <xref:System.Web.UI.WebControls.Button.Text%2A> "Tamam" özelliğine.  
  
-   A <xref:System.Web.UI.WebControls.HiddenField> adlı Denetim `DateInfo`.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bir kullanıcının HTML akışa betik injecting önlemek için kullanıcı girişi hiçbir zaman doğrudan sunucu yanıtta yansıtılması gerekir. Bunun yerine, bunu kullanarak kodlanması gereken <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType> yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Biçimlendirme işlemlerini gerçekleştirme](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [Standart tarih ve saat biçim dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)  
 [Özel tarih ve saat biçim dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)  
 [Tarih ve saat dizelerini ayrıştırma](../../../docs/standard/base-types/parsing-datetime.md)
