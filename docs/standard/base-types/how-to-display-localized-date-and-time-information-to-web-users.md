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
ms.openlocfilehash: 51142a168aba4408e6ce550a032960c4df6c3ae7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138738"
---
# <a name="how-to-display-localized-date-and-time-information-to-web-users"></a>Nasıl yapılır: Web Kullanıcılarına Yerelleştirilmiş Tarih ve Saat Bilgilerini Görüntüleme
Bir Web sayfası dünyanın herhangi bir yerinden görüntülenebildiğinden, tarih ve saat değerlerini ayrıştırır ve biçimlendirir işlemler, kullanıcıyla etkileşim kurarken varsayılan bir biçimde (çoğunlukla Web sunucusunun yerel kültürünün biçimi) değil. Bunun yerine, Kullanıcı tarafından girilen tarih ve saat dizelerini işleyen Web formları, kullanıcının tercih ettiği kültürü kullanarak dizeleri ayrıştırmalıdır. Benzer şekilde, tarih ve saat verileri kullanıcının kültürüne uygun bir biçimde görüntülenir. Bu konuda bunun nasıl yapılacağı gösterilmektedir.  
  
## <a name="to-parse-date-and-time-strings-input-by-the-user"></a>Kullanıcı tarafından girilen tarih ve saat dizelerini ayrıştırmak için  
  
1. <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> özelliği tarafından döndürülen dize dizisinin doldurulup doldurulmadığını belirleme. Değilse, adım 6 ' ya geçin.  
  
2. <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği tarafından döndürülen dize dizisi doldurulduktan sonra ilk öğesini alın. İlk öğe, kullanıcının varsayılan veya tercih edilen dil ve bölge olduğunu gösterir.  
  
3. <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> oluşturucusunu çağırarak kullanıcının tercih ettiği kültürü temsil eden bir <xref:System.Globalization.CultureInfo> nesnesi örneği oluşturun.  
  
4. Dönüştürmeyi denemek için `TryParse` veya <xref:System.DateTime> ya da <xref:System.DateTimeOffset> türünün `Parse` yöntemini çağırın. `TryParse` veya `Parse` yönteminin bir `provider` parametresiyle bir aşırı yüklemesini kullanın ve aşağıdakilerden birini geçirin:  
  
    - Adım 3 ' te oluşturulan <xref:System.Globalization.CultureInfo> nesnesi.  
  
    - Adım 3 ' te oluşturulan <xref:System.Globalization.CultureInfo> nesnesinin <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> özelliği tarafından döndürülen <xref:System.Globalization.DateTimeFormatInfo> nesnesi.  
  
5. Dönüştürme başarısız olursa, <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği tarafından döndürülen dize dizisindeki kalan her öğe için 2 ile 4 arasındaki adımları tekrarlayın.  
  
6. Dönüştürme hala başarısız olursa veya <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği tarafından döndürülen dize dizisi boşsa, <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> özelliği tarafından döndürülen sabit kültür kullanarak dizeyi ayrıştırın.  
  
## <a name="to-parse-the-local-date-and-time-of-the-users-request"></a>Kullanıcının isteğinin yerel tarihini ve saatini ayrıştırmak için  
  
1. Bir Web formuna <xref:System.Web.UI.WebControls.HiddenField> denetimi ekleyin.  
  
2. Geçerli tarih ve saat ve yerel saat diliminin, Eşgüdümlü Evrensel Saat (UTC) ile <xref:System.Web.UI.WebControls.HiddenField.Value%2A> özelliğine olan sapmasını yazarak bir `Submit` düğmenin `onClick` olayını işleyen bir JavaScript işlevi oluşturun. Dizenin iki bileşenini ayırmak için bir sınırlayıcı (noktalı virgül) kullanın.  
  
3. Komut dosyasının metnini <xref:System.Web.UI.ClientScriptManager.RegisterClientScriptBlock%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType> yöntemine geçirerek, işlevi HTML çıkış akışına eklemek için Web formunun <xref:System.Web.UI.Control.PreRender> olayını kullanın.  
  
4. JavaScript işlevinin adını `Submit` düğmesinin `OnClientClick` özniteliğine girerek olay işleyicisini `Submit` düğmenin `onClick` olayına bağlayın.  
  
5. `Submit` düğmenin <xref:System.Web.UI.WebControls.Button.Click> olayı için bir işleyici oluşturun.  
  
6. Olay işleyicisinde, <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> özelliği tarafından döndürülen dize dizisinin doldurulup doldurulmadığını saptayın. Değilse, 14. adıma geçin.  
  
7. <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği tarafından döndürülen dize dizisi doldurulduktan sonra ilk öğesini alın. İlk öğe, kullanıcının varsayılan veya tercih edilen dil ve bölge olduğunu gösterir.  
  
8. <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> oluşturucusunu çağırarak kullanıcının tercih ettiği kültürü temsil eden bir <xref:System.Globalization.CultureInfo> nesnesi örneği oluşturun.  
  
9. Kullanıcının yerel tarih ve saatinin dize gösterimini ve kullanıcının yerel saat dilimi sapmasını ayrı dizi öğelerinde dize gösterimini depolamak için, <xref:System.Web.UI.WebControls.HiddenField.Value%2A> özelliğine atanan dizeyi <xref:System.String.Split%2A> yöntemine geçirin.  
  
10. Kullanıcının isteğinin tarih ve saatini bir <xref:System.DateTime> değere dönüştürmek için <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> veya <xref:System.DateTime.TryParse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%2CSystem.DateTime%40%29?displayProperty=nameWithType> yöntemini çağırın. Bir `provider` parametresiyle yönteminin aşırı yüklemesini kullanın ve aşağıdakilerden birini geçirin:  
  
    - 8\. adımda oluşturulan <xref:System.Globalization.CultureInfo> nesnesi.  
  
    - 8\. adımda oluşturulan <xref:System.Globalization.CultureInfo> nesnesinin <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> özelliği tarafından döndürülen <xref:System.Globalization.DateTimeFormatInfo> nesnesi.  
  
11. Adım 10 ' daki ayrıştırma işlemi başarısız olursa, 13. adıma gidin. Aksi takdirde, kullanıcının saat dilimi kaydırmasına ait dize gösterimini bir tamsayıya dönüştürmek için <xref:System.UInt32.Parse%28System.String%29?displayProperty=nameWithType> yöntemini çağırın.  
  
12. <xref:System.DateTimeOffset.%23ctor%28System.DateTime%2CSystem.TimeSpan%29?displayProperty=nameWithType> oluşturucusunu çağırarak kullanıcının yerel saatini temsil eden bir <xref:System.DateTimeOffset> oluşturun.  
  
13. Adım 10 ' daki dönüştürme başarısız olursa, <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği tarafından döndürülen dize dizisindeki her bir kalan öğe için 7 ile 12 arasındaki adımları tekrarlayın.  
  
14. Dönüştürme hala başarısız olursa veya <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği tarafından döndürülen dize dizisi boşsa, <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> özelliği tarafından döndürülen sabit kültür kullanarak dizeyi ayrıştırın. Sonra 7 ile 12 arasındaki adımları yineleyin.  
  
 Sonuç, Web sayfanızın kullanıcısının yerel saatini temsil eden bir <xref:System.DateTimeOffset> nesnesidir. Daha sonra <xref:System.DateTimeOffset.ToUniversalTime%2A> yöntemini çağırarak eşdeğer UTC 'yi belirleyebilirsiniz. Ayrıca, <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> yöntemini çağırarak ve saati dönüştürmek üzere saat dilimi olarak <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> bir değer geçirerek Web sunucunuzdaki denk tarih ve saati belirleyebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, kullanıcıdan bir tarih ve saat değeri girmesini isteyen bir ASP.NET Web formunun hem HTML kaynağını hem de kodunu içerir. İstemci tarafı komut dosyası Ayrıca, Kullanıcı isteğinin yerel tarih ve saatine ve kullanıcının saat diliminin UTC 'den gizli bir alana olan zamanına ilişkin bilgileri yazar. Bu bilgiler daha sonra, kullanıcının girişini görüntüleyen bir Web sayfası döndüren sunucu tarafından ayrıştırılır. Ayrıca kullanıcının yerel saatini, sunucu saatini ve UTC 'yi kullanarak Kullanıcı isteğinin tarih ve saatini görüntüler.  
  
 [!code-aspx-csharp[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/cs/GetDateInfo.aspx#1)]
 [!code-aspx-vb[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/vb/GetDateInfo.aspx#1)]
  
 İstemci tarafı komut dosyası JavaScript `toLocaleString` yöntemini çağırır. Bu, kullanıcının yerel ayarının biçimlendirme kurallarını izleyen bir dize oluşturur ve bu, sunucuda başarılı bir şekilde ayrıştırılabilen bir olasılıktır.  
  
 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> özelliği, bir HTTP isteğine dahil `Accept-Language` üst bilgilerinde bulunan kültür adlarından doldurulur. Ancak, tüm tarayıcılar isteklerinde `Accept-Language` üst bilgileri içermez ve kullanıcılar üst bilgileri tamamen de engelleyebilir. Bu, Kullanıcı girişini ayrıştırırken bir geri dönüş kültürüne sahip olmanızı önemli hale getirir. Genellikle geri dönüş kültürü, <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>tarafından döndürülen sabit kültürdür. Kullanıcılar ayrıca, bir metin kutusunda girdikleri kültür adları ile Internet Explorer 'ı da sağlayabilir ve bu da kültür adlarının geçerli olma olasılığını oluşturur. Bu, bir <xref:System.Globalization.CultureInfo> nesnesi örneği oluşturulurken özel durum işlemenin kullanılmasını önemli hale getirir.  
  
 Internet Explorer tarafından gönderilen HTTP isteğinden alındığında, <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> dizisi Kullanıcı tercihi sırasıyla doldurulur. Dizideki ilk öğe, kullanıcının birincil kültürünün ve bölgesinin adını içerir. Dizi ek öğe içeriyorsa, Internet Explorer onlara rastgele bir kalite belirleyicisi atar ve bu, kültür adından noktalı virgülle ayrılır. Örneğin, fr-FR kültürü için bir giriş `fr-FR;q=0.7`formunu alabilir.  
  
 Örnek, yeni bir <xref:System.Globalization.CultureInfo> nesnesi oluşturmak için `useUserOverride` parametresi `false` olarak ayarlanmış <xref:System.Globalization.CultureInfo.%23ctor%2A> oluşturucusunu çağırır. Bu sayede, kültür adı sunucuda varsayılan kültür adı ise, sınıf oluşturucusu tarafından oluşturulan yeni <xref:System.Globalization.CultureInfo> nesnesi bir kültürün varsayılan ayarlarını içerir ve sunucunun bölgesel ayarlarını kullanarak geçersiz kılınan ayarları yansıtmaz ve  **Dil seçenekleri** uygulaması. Sunucuda geçersiz kılınan ayarların değerleri, kullanıcının sisteminde veya kullanıcının girişine yansıtılmasının olası bir olasılıktır.  
  
 Bu örnek, bir tarih ve saatin iki dize temsilini (Kullanıcı tarafından bir giriş, gizli alana depolanmış) ayrıştırır, bu, önceden gerekebilecek olası <xref:System.Globalization.CultureInfo> nesnelerini tanımlar. <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> özelliği tarafından döndürülen öğe sayısından daha büyük bir <xref:System.Globalization.CultureInfo> nesneleri dizisi oluşturur. Sonra her bir dil/bölge dizesi için bir <xref:System.Globalization.CultureInfo> nesnesi oluşturur ve ayrıca <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>temsil eden bir <xref:System.Globalization.CultureInfo> nesnesi oluşturur.  
  
 Kodunuz, kullanıcının tarih ve saat dize gösterimini bir <xref:System.DateTime> değere dönüştürmek için <xref:System.DateTime.Parse%2A> ya da <xref:System.DateTime.TryParse%2A> yöntemini çağırabilir. Ayrıştırma yöntemine yinelenen çağrılar tek bir ayrıştırma işlemi için gerekli olabilir. Sonuç olarak, bir ayrıştırma işlemi başarısız olursa `false` döndürdüğünden <xref:System.DateTime.TryParse%2A> yöntemi daha iyidir. Buna karşılık, <xref:System.DateTime.Parse%2A> yöntemi tarafından oluşturulabilecek yinelenen özel durumları işlemek bir Web uygulamasında çok pahalı bir işlem olabilir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Kodu derlemek için, arka plan kodu olmadan bir ASP.NET Web sayfası oluşturun. Daha sonra örneği, mevcut tüm kodun yerini alacak şekilde Web sayfasına kopyalayın. ASP.NET Web sayfası aşağıdaki denetimleri içermelidir:  
  
- Kodda başvurulmayan bir <xref:System.Web.UI.WebControls.Label> denetimi. <xref:System.Web.UI.WebControls.TextBox.Text%2A> özelliğini "bir sayı girin:" olarak ayarlayın.  
  
- `DateString`adlı <xref:System.Web.UI.WebControls.TextBox> denetim.  
  
- `OKButton`adlı <xref:System.Web.UI.WebControls.Button> denetim. <xref:System.Web.UI.WebControls.Button.Text%2A> özelliğini "Tamam" olarak ayarlayın.  
  
- `DateInfo`adlı <xref:System.Web.UI.WebControls.HiddenField> denetim.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bir kullanıcının ekleme betiğine HTML akışına engel olmak için, Kullanıcı girişinin sunucu yanıtında hiçbir şekilde doğrudan yankılanır olması gerekir. Bunun yerine, <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType> yöntemi kullanılarak kodlanmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme İşlemlerini Gerçekleştirme](../../../docs/standard/base-types/performing-formatting-operations.md)
- [Standart Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [Özel Tarih ve Saat Biçim Dizeleri](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
- [Tarih ve Saat Dizelerini Ayrıştırma](../../../docs/standard/base-types/parsing-datetime.md)
