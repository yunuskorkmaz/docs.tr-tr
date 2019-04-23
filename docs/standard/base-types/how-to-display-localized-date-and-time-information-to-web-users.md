---
title: 'Nasıl yapılır: Web Kullanıcılarına Yerelleştirilmiş Tarih ve Saat Bilgilerini Görüntüleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- formatting [.NET Framework], dates
- parsing strings [.NET Framework], date and time strings
- localization [.NET Framework], date and time displays
- formatting [.NET Framework], localized data
- displaying date and time data
- localized date displays [.NET Framework]
ms.assetid: 377fe93c-32be-421a-a30a-be639a46ede8
dev_langs:
- csharp
- vb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e97bc095332e626d79561ab5fdc7bad531e3ba31
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320164"
---
# <a name="how-to-display-localized-date-and-time-information-to-web-users"></a>Nasıl yapılır: Web Kullanıcılarına Yerelleştirilmiş Tarih ve Saat Bilgilerini Görüntüleme
Bir Web sayfası dünyanın herhangi bir yere görüntülenebileceğinden ayrıştırma ve biçimlendirme tarih ve saat değerlerini işlemleri (genellikle Web sunucusunun yerel kültür biçiminde) bir varsayılan biçimi üzerinde doğrulamamalısınız kullanıcıyla etkileşim kurulurken. Bunun yerine, işlemek tarih ve saat dizeleri giriş kullanıcı tarafından Web forms, tercih edilen kullanıcının kültürü kullanarak dizeleri çözümlenmelidir. Benzer şekilde, tarih ve saat verileri kullanıcıya kullanıcının kültürü için uygun bir biçimde görüntülenmesi gerekir. Bu konuda, bunun nasıl yapılacağı gösterilmektedir.  
  
## <a name="to-parse-date-and-time-strings-input-by-the-user"></a>Tarih ve saat ayrıştırılacak giriş kullanıcı tarafından dizeleri  
  
1. Dize dizisi tarafından döndürülen olup olmadığını belirlemek <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> özelliği doldurulur. Yüklü değilse, 6. adıma devam edin.  
  
2. Dize dizisi olarak döndürülürse <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği eklendiğinden, ilk öğesi alın. Kullanıcının varsayılan veya tercih edilen dil ve bölge ilk öğeyi gösterir.  
  
3. Örneği bir <xref:System.Globalization.CultureInfo> kullanıcıyı temsil eden bir nesne tercih edilen kültür çağırarak <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> Oluşturucusu.  
  
4. Çağırın ya da `TryParse` veya `Parse` yöntemi <xref:System.DateTime> veya <xref:System.DateTimeOffset> türü dönüştürmeyi deneyin. Bir aşırı yüklemesini kullanmanız `TryParse` veya `Parse` yöntemi ile bir `provider` parametresi, aşağıdakilerden birini geçirin:  
  
    -   <xref:System.Globalization.CultureInfo> 3. adımda oluşturulan nesne.  
  
    -   <xref:System.Globalization.DateTimeFormatInfo> Tarafından döndürülen nesne <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> özelliği <xref:System.Globalization.CultureInfo> 3. adımda oluşturulan nesne.  
  
5. Dönüştürme başarısız olursa tarafından döndürülen 2 dize dizisi kalan her öğe için 4 arasındaki adımları yineleyin <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği.  
  
6. Dönüştürme yine başarısız olursa veya dize dizisi tarafından döndürülen <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği boşsa, tarafından döndürülen sabit kültür kullanarak dizeyi ayrıştırmak <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> özelliği.  
  
## <a name="to-parse-the-local-date-and-time-of-the-users-request"></a>Yerel tarih ve saat kullanıcının isteği ayrıştırılamıyor  
  
1. Ekleme bir <xref:System.Web.UI.WebControls.HiddenField> Web formu denetimi.  
  
2. İşleme bir JavaScript işlevi oluşturmak `onClick` olayı bir `Submit` düğmesi ile eşgüdümlü evrensel saat (UTC) için geçerli tarih ve saat ile yerel saat diliminin uzaklığı yazarak <xref:System.Web.UI.WebControls.HiddenField.Value%2A> özelliği. Dizenin iki bileşeni birbirinden ayırmak için sınırlayıcı (örneğin, noktalı virgül) kullanın.  
  
3. Web form denetiminin kullanın <xref:System.Web.UI.Control.PreRender> HTML'e işlevi eklemesine olay çıkış akışı için betiğin metnini geçirerek <xref:System.Web.UI.ClientScriptManager.RegisterClientScriptBlock%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType> yöntemi.  
  
4. Olay işleyicisine bağlamanız `Submit` düğmenin `onClick` olayı için JavaScript işlevinin adı sağlayarak `OnClientClick` özniteliği `Submit` düğmesi.  
  
5. Oluşturmak için bir işleyici `Submit` düğmenin <xref:System.Web.UI.WebControls.Button.Click> olay.  
  
6. Olay işleyicisi, dize dizisi tarafından döndürülen olup olmadığını belirlemek <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> özelliği doldurulur. Yüklü değilse, 14 adıma devam edin.  
  
7. Dize dizisi olarak döndürülürse <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği eklendiğinden, ilk öğesi alın. Kullanıcının varsayılan veya tercih edilen dil ve bölge ilk öğeyi gösterir.  
  
8. Örneği bir <xref:System.Globalization.CultureInfo> kullanıcıyı temsil eden bir nesne tercih edilen kültür çağırarak <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> Oluşturucusu.  
  
9. Atanmış bir dizeyi geçirmek <xref:System.Web.UI.WebControls.HiddenField.Value%2A> özelliğini <xref:System.String.Split%2A> kullanıcının yerel tarih ve saat dize gösterimini ve kullanıcının yerel saat dilimi uzaklığı dize gösterimini ayrı dizi öğelerinde depolamak için yöntemi.  
  
10. Çağırın ya da <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> veya <xref:System.DateTime.TryParse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%2CSystem.DateTime%40%29?displayProperty=nameWithType> tarih ve saat için kullanıcının isteği dönüştürmek için yöntemi bir <xref:System.DateTime> değeri. Bir yöntemi aşırı yüklemesini kullanın bir `provider` parametresi, aşağıdakilerden birini geçirin:  
  
    -   <xref:System.Globalization.CultureInfo> 8. adımda oluşturulan nesne.  
  
    -   <xref:System.Globalization.DateTimeFormatInfo> Tarafından döndürülen nesne <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> özelliği <xref:System.Globalization.CultureInfo> 8. adımda oluşturulan nesne.  
  
11. Adımda 10 ayrıştırma işlemi başarısız olursa, 13. adıma gidin. Aksi takdirde, çağrı <xref:System.UInt32.Parse%28System.String%29?displayProperty=nameWithType> kullanıcının saat dilimi uzaklığı dize gösterimini bir tamsayıya dönüştürmek için yöntemi.  
  
12. Örneği bir <xref:System.DateTimeOffset> kullanıcının yerel saati çağırarak temsil eden <xref:System.DateTimeOffset.%23ctor%28System.DateTime%2CSystem.TimeSpan%29?displayProperty=nameWithType> Oluşturucusu.  
  
13. Adımda 10 dönüştürme başarısız olursa tarafından döndürülen adımları 7 ila 12 dize dizisi kalan her öğe için yineleyin <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği.  
  
14. Dönüştürme yine başarısız olursa veya dize dizisi tarafından döndürülen <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği boşsa, tarafından döndürülen sabit kültür kullanarak dizeyi ayrıştırmak <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> özelliği. Ardından 7 ila 12. adımları tekrarlayın.  
  
 Sonuç bir <xref:System.DateTimeOffset> Web sayfanızın kullanıcının yerel saati temsil eden nesne. Ardından çağırarak eşdeğer UTC belirleyebilirsiniz <xref:System.DateTimeOffset.ToUniversalTime%2A> yöntemi. Ayrıca denk tarih ve saati Web sunucunuzda çağırarak belirleyebilirsiniz <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> yöntemi ve bir değerini geçirme <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> zaman dönüştürülecek saat dilimi olarak.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, HTML kaynağını hem giriş tarih ve saat değeri için kullanıcıdan bir ASP.NET Web formu için kod içerir. İstemci tarafı komut dosyası, gizli bir alan için UTC'den yerel tarih ve saate kullanıcının isteği ve kullanıcının saat dilimi uzaklığı hakkında bilgi de yazar. Bu bilgiler daha sonra döndüren kullanıcının girişi görüntüleyen bir Web sayfası sunucusu tarafından ayrıştırılır. Ayrıca, kullanıcının yerel saati, saati, sunucu ve UTC kullanarak kullanıcının isteği, saat ve tarihi görüntüler.  
  
 [!code-aspx-csharp[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/cs/GetDateInfo.aspx#1)]
 [!code-aspx-vb[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/vb/GetDateInfo.aspx#1)]
  
 İstemci tarafı komut dosyası JavaScript çağrı `toLocaleString` yöntemi. Bu sunucu üzerinde başarıyla ayrıştırılmak büyük olasılıkla kullanıcının yerel ayarlarına biçimlendirme kurallarını takip eden bir dize oluşturur.  
  
 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> Özelliği bulunan kültür adları doldurulur `Accept-Language` bir HTTP isteğinde üstbilgileri. Ancak, tüm tarayıcılar dahil `Accept-Language` üst bilgilerini kendi isteklerini ve kullanıcılar de gösterme üstbilgileri tamamen. Önemli kullanıcı girişi ayrıştırılırken bir geri dönüş kültürü olmasını sağlar. Genellikle geri dönüş kültürü tarafından döndürülen sabit kültür olan <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Kullanıcılar aynı zamanda Internet Explorer kültür adları ile kültür adları geçerli olmayabilir olasılığını oluşturur ve metin kutusu içinde giriş sağlar. Bu örneği oluşturulurken özel durum işleme kullanmak önemli sağlar bir <xref:System.Globalization.CultureInfo> nesne.  
  
 Internet Explorer tarafından gönderilen HTTP isteğinden alınırken <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> dizisi, kullanıcı tercih sırasına göre doldurulur. Kullanıcının birincil kültür/bölge adı dizideki ilk öğe içerir. Dizi herhangi bir ek öğeler varsa, Internet Explorer bunları rasgele kültür adı, noktalı virgülle ayrılmış bir kalite belirticisi atar. Örneğin, fr-FR kültürü için bir giriş formu sürebilir `fr-FR;q=0.7`.  
  
 Örnek aramalar <xref:System.Globalization.CultureInfo.%23ctor%2A> oluşturucuyla kendi `useUserOverride` parametresini `false` yeni bir <xref:System.Globalization.CultureInfo> nesne. Kültür adı varsayılan kültür adı sunucu üzerinde ise bu, sağlar yeni <xref:System.Globalization.CultureInfo> sınıfı Oluşturucu tarafından oluşturulan nesne bir kültürün varsayılan ayarlarını içerir ve sunucunun kullanılarak herhangi bir ayarı yansıtmaz  **Bölge ve Dil Seçenekleri** uygulama. Sunucu üzerindeki herhangi bir geçersiz kılınan ayarı değerleri, kullanıcının sistemde yok veya kullanıcının girişinde yansıtılması düşüktür.  
  
 Bu örnek bir tarih ve saat (kullanıcı tarafından diğer depolanan gizli bir alan için bir giriş) iki dize temsillerini ayrıştırmak için olası tanımladığı <xref:System.Globalization.CultureInfo> nesneleri önceden gerekli olabilir. Bir dizi oluşturur <xref:System.Globalization.CultureInfo> tarafından döndürülen öğe sayısından daha büyük bir nesneler <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> özelliği. Ardından örnekleyen bir <xref:System.Globalization.CultureInfo> nesne her dil/bölge dizesi için ve ayrıca oluşturur bir <xref:System.Globalization.CultureInfo> temsil eden nesne <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.  
  
 Kodunuzu ya da çağırabilir <xref:System.DateTime.Parse%2A> veya <xref:System.DateTime.TryParse%2A> kullanıcının bir tarihin dize gösterimine dönüştürmek ve süresi için yöntemi bir <xref:System.DateTime> değeri. Parse yöntemi yinelenen çağrıları tek bir ayrıştırma işleminde gerekli olabilir. Sonuç olarak, <xref:System.DateTime.TryParse%2A> yöntemi olduğundan daha iyi döndürür `false` bir ayrıştırma işlemi başarısız olursa. Buna karşılık, tarafından oluşturulabilir yinelenen bir özel durum işleme <xref:System.DateTime.Parse%2A> yöntemi, bir Web uygulamasındaki çok pahalı bir teklifi olabilir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Kodu derlemek için oluşturun bir [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] arka plan kod olmadan Web sayfası. Tüm mevcut kodlar değiştirir, böylece örnek Web sayfasına kopyalayın. [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web sayfası aşağıdaki denetimleri içermelidir:  
  
-   A <xref:System.Web.UI.WebControls.Label> kodda başvurulmuyor denetimi. Ayarlama, <xref:System.Web.UI.WebControls.TextBox.Text%2A> özelliğini "bir sayı girin:".  
  
-   A <xref:System.Web.UI.WebControls.TextBox> adlı Denetim `DateString`.  
  
-   A <xref:System.Web.UI.WebControls.Button> adlı Denetim `OKButton`. Ayarlama, <xref:System.Web.UI.WebControls.Button.Text%2A> özelliği için "Tamam".  
  
-   A <xref:System.Web.UI.WebControls.HiddenField> adlı Denetim `DateInfo`.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 HTML akışına betik ekleme gelen bir kullanıcı önlemek için kullanıcı girişi hiçbir zaman doğrudan ve sunucu yanıtında yansıtılması gerekir. Bunun yerine, bunu kullanarak kodlanması gereken <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType> yöntemi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme İşlemlerini Gerçekleştirme](../../../docs/standard/base-types/performing-formatting-operations.md)
- [Standart Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [Özel Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
- [Tarih ve Saat Dizelerini Ayrıştırma](../../../docs/standard/base-types/parsing-datetime.md)
