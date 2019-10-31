---
title: 'Nasıl yapılır: Web Denetimlerindeki Sayısal Kullanıcı Girişlerini Sayıya Dönüştürme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- parsing strings [.NET Framework], numeric strings
- converting numeric user input to number
- numbers [.NET Framework], converting numeric user input to number
ms.assetid: f27ddfb8-7479-4b79-8879-02a3bd8402d4
ms.openlocfilehash: 78ba284ad2e75b39c0fb1001b0f65b48c519dbb5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140100"
---
# <a name="how-to-convert-numeric-user-input-in-web-controls-to-numbers"></a>Nasıl yapılır: Web Denetimlerindeki Sayısal Kullanıcı Girişlerini Sayıya Dönüştürme
Bir Web sayfası dünyanın herhangi bir yerinden görüntülenebildiğinden, kullanıcılar neredeyse sınırsız sayıda biçimdeki <xref:System.Web.UI.WebControls.TextBox> denetimine sayısal veri girişi yapabilir. Sonuç olarak, Web sayfası kullanıcısının yerel ayar ve kültürünü belirlenmesi çok önemlidir. Kullanıcı girişini ayrıştırdığınızda, kullanıcının yerel ayarı ve kültürü tarafından tanımlanan biçimlendirme kurallarını uygulayabilirsiniz.  
  
### <a name="to-convert-numeric-input-from-a-web-textbox-control-to-a-number"></a>Bir Web TextBox denetiminden sayısal girişi bir sayıya dönüştürmek için  
  
1. <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> özelliği tarafından döndürülen dize dizisinin doldurulup doldurulmadığını belirleme. Değilse, adım 6 ' ya geçin.  
  
2. <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği tarafından döndürülen dize dizisi doldurulduktan sonra ilk öğesini alın. İlk öğe, kullanıcının varsayılan veya tercih edilen dil ve bölge olduğunu gösterir.  
  
3. <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> oluşturucusunu çağırarak kullanıcının tercih ettiği kültürü temsil eden bir <xref:System.Globalization.CultureInfo> nesnesi örneği oluşturun.  
  
4. Kullanıcı girişini dönüştürmek istediğiniz sayısal türün `TryParse` ya da `Parse` yöntemini çağırın. `TryParse` veya `Parse` yönteminin bir `provider` parametresiyle bir aşırı yüklemesini kullanın ve aşağıdakilerden birini geçirin:  
  
    - Adım 3 ' te oluşturulan <xref:System.Globalization.CultureInfo> nesnesi.  
  
    - Adım 3 ' te oluşturulan <xref:System.Globalization.CultureInfo> nesnesinin <xref:System.Globalization.CultureInfo.NumberFormat%2A> özelliği tarafından döndürülen <xref:System.Globalization.NumberFormatInfo> nesnesi.  
  
5. Dönüştürme başarısız olursa, <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği tarafından döndürülen dize dizisindeki kalan her öğe için 2 ile 4 arasındaki adımları tekrarlayın.  
  
6. Dönüştürme hala başarısız olursa veya <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği tarafından döndürülen dize dizisi boşsa, <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> özelliği tarafından döndürülen sabit kültür kullanarak dizeyi ayrıştırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir Web formu için, kullanıcıdan <xref:System.Web.UI.WebControls.TextBox> denetimine sayısal bir değer girmesini ve bir sayıya dönüştürmelerini isteyen tam arka plan kod sayfasıdır. Bu sayı daha sonra, özgün girişle aynı biçimlendirme kuralları kullanılarak iki katına çıkar ve görüntülenir.  
  
 [!code-csharp[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/cs/NumericUserInput1.aspx.cs#1)]
 [!code-vb[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/vb/NumericUserInput1.aspx.vb#1)]  
  
 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> özelliği, bir HTTP isteğine dahil `Accept-Language` üst bilgilerinde bulunan kültür adlarından doldurulur. Ancak, tüm tarayıcılar isteklerinde `Accept-Language` üst bilgileri içermez ve kullanıcılar üst bilgileri tamamen de engelleyebilir. Bu, Kullanıcı girişini ayrıştırırken bir geri dönüş kültürüne sahip olmanızı önemli hale getirir. Genellikle, geri dönüş kültürü <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>tarafından döndürülen sabit kültürdür. Kullanıcılar ayrıca, bir metin kutusunda girdikleri kültür adları ile Internet Explorer 'ı da sağlayabilir ve bu da kültür adlarının geçerli olma olasılığını oluşturur. Bu, bir <xref:System.Globalization.CultureInfo> nesnesi örneği oluşturulurken özel durum işlemenin kullanılmasını önemli hale getirir.  
  
 Internet Explorer tarafından gönderilen HTTP isteğinden alındığında, <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> dizisi Kullanıcı tercihi sırasıyla doldurulur. Dizideki ilk öğe, kullanıcının birincil kültürünün ve bölgesinin adını içerir. Dizi ek öğe içeriyorsa, Internet Explorer onlara rastgele bir kalite belirleyicisi atar ve bu, kültür adından noktalı virgülle ayrılır. Örneğin, fr-FR kültürü için bir giriş `fr-FR;q=0.7`formunu alabilir.  
  
 Örnek, yeni bir <xref:System.Globalization.CultureInfo> nesnesi oluşturmak için `useUserOverride` parametresi `false` olarak ayarlanmış <xref:System.Globalization.CultureInfo.%23ctor%2A> oluşturucusunu çağırır. Bu sayede, kültür adı sunucuda varsayılan kültür adı ise, sınıf oluşturucusu tarafından oluşturulan yeni <xref:System.Globalization.CultureInfo> nesnesi bir kültürün varsayılan ayarlarını içerir ve sunucunun bölgesel ayarlarını kullanarak geçersiz kılınan ayarları yansıtmaz ve  **Dil seçenekleri** uygulaması. Sunucuda geçersiz kılınan ayarların değerleri, kullanıcının sisteminde veya kullanıcının girişine yansıtılmasının olası bir olasılıktır.  
  
 Kodunuz `Parse` veya Kullanıcı girişinin dönüştürülecek sayısal türde `TryParse` yöntemini çağırabilir. Ayrıştırma yöntemine yinelenen çağrılar tek bir ayrıştırma işlemi için gerekli olabilir. Sonuç olarak, bir ayrıştırma işlemi başarısız olursa `false` döndürdüğünden `TryParse` yöntemi daha iyidir. Buna karşılık, `Parse` yöntemi tarafından oluşturulabilecek yinelenen özel durumları işlemek bir Web uygulamasında çok pahalı bir işlem olabilir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Kodu derlemek için, mevcut tüm kodun yerine ASP.NET bir arka plan kod sayfasına kopyalayın. ASP.NET Web sayfası aşağıdaki denetimleri içermelidir:  
  
- Kodda başvurulmayan bir <xref:System.Web.UI.WebControls.Label> denetimi. <xref:System.Web.UI.WebControls.TextBox.Text%2A> özelliğini "bir sayı girin:" olarak ayarlayın.  
  
- `NumericString`adlı <xref:System.Web.UI.WebControls.TextBox> denetim.  
  
- `OKButton`adlı <xref:System.Web.UI.WebControls.Button> denetim. <xref:System.Web.UI.WebControls.Button.Text%2A> özelliğini "Tamam" olarak ayarlayın.  
  
 `NumericUserInput` sınıfının adını, ASP.NET sayfasının `Page` yönergesinin `Inherits` özniteliği tarafından tanımlanan sınıfın adına değiştirin. `NumericInput` Nesne başvurusunun adını, ASP.NET sayfasının `form` etiketinin `id` özniteliğiyle tanımlanan ada değiştirin.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bir kullanıcının ekleme betiğine HTML akışına engel olmak için, Kullanıcı girişinin sunucu yanıtında hiçbir şekilde doğrudan yankılanır olması gerekir. Bunun yerine, <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType> yöntemi kullanılarak kodlanmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme İşlemlerini Gerçekleştirme](../../../docs/standard/base-types/performing-formatting-operations.md)
- [Sayısal Dizeleri Ayrıştırma](../../../docs/standard/base-types/parsing-numeric.md)
