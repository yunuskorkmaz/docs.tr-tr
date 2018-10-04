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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 663f9d88315f396b187cca874c930179f1dea523
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48777938"
---
# <a name="how-to-convert-numeric-user-input-in-web-controls-to-numbers"></a>Nasıl yapılır: Web Denetimlerindeki Sayısal Kullanıcı Girişlerini Sayıya Dönüştürme
Kullanıcıların dünyanın herhangi bir Web sayfası görüntülenebileceğinden sayısal verileri girebilirsiniz bir <xref:System.Web.UI.WebControls.TextBox> neredeyse sınırsız sayıda biçimleri denetimi. Sonuç olarak, yerel ve Web sayfasının kullanıcı kültürü belirlemek çok önemlidir. Kullanıcı girişini ayrıştırmasına, daha sonra kullanıcının yerel ayar ve kültür tarafından tanımlanan biçimlendirme kurallarını uygulayabilirsiniz.  
  
### <a name="to-convert-numeric-input-from-a-web-textbox-control-to-a-number"></a>Bir Web TextBox denetimi bir sayıyı sayısal giriş dönüştürülemiyor  
  
1.  Dize dizisi tarafından döndürülen olup olmadığını belirlemek <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> özelliği doldurulur. Yüklü değilse, 6. adıma devam edin.  
  
2.  Dize dizisi olarak döndürülürse <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği eklendiğinden, ilk öğesi alın. Kullanıcının varsayılan veya tercih edilen dil ve bölge ilk öğeyi gösterir.  
  
3.  Örneği bir <xref:System.Globalization.CultureInfo> kullanıcıyı temsil eden bir nesne tercih edilen kültür çağırarak <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> Oluşturucusu.  
  
4.  Çağırın ya da `TryParse` veya `Parse` kullanıcı dönüştürmek istediğiniz sayısal türü yöntemi için giriş. Bir aşırı yüklemesini kullanmanız `TryParse` veya `Parse` yöntemi ile bir `provider` parametresi, aşağıdakilerden birini geçirin:  
  
    -   <xref:System.Globalization.CultureInfo> 3. adımda oluşturulan nesne.  
  
    -   <xref:System.Globalization.NumberFormatInfo> Tarafından döndürülen nesne <xref:System.Globalization.CultureInfo.NumberFormat%2A> özelliği <xref:System.Globalization.CultureInfo> 3. adımda oluşturulan nesne.  
  
5.  Dönüştürme başarısız olursa tarafından döndürülen 2 dize dizisi kalan her öğe için 4 arasındaki adımları yineleyin <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği.  
  
6.  Dönüştürme yine başarısız olursa veya dize dizisi tarafından döndürülen <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği boşsa, tarafından döndürülen sabit kültür kullanarak dizeyi ayrıştırmak <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> özelliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek sayısal bir değer girmesini ister Web formu tam arka plan kod sayfasıdır bir <xref:System.Web.UI.WebControls.TextBox> denetlemek ve bir sayıya dönüştürür. Ardından bu sayıyı iki katına ve özgün giriş olarak aynı biçimlendirme kurallarını kullanarak görüntülenir.  
  
 [!code-csharp[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/cs/NumericUserInput1.aspx.cs#1)]
 [!code-vb[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/vb/NumericUserInput1.aspx.vb#1)]  
  
 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> Özelliği bulunan kültür adları doldurulur `Accept-Language` bir HTTP isteğinde üstbilgileri. Ancak, tüm tarayıcılar dahil `Accept-Language` üst bilgilerini kendi isteklerini ve kullanıcılar de gösterme üstbilgileri tamamen. Önemli kullanıcı girişi ayrıştırılırken bir geri dönüş kültürü olmasını sağlar. Genellikle, geri dönüş kültürü tarafından döndürülen sabit kültür olan <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Kullanıcılar aynı zamanda Internet Explorer kültür adları ile kültür adları geçerli olmayabilir olasılığını oluşturur ve metin kutusu içinde giriş sağlar. Bu örneği oluşturulurken özel durum işleme kullanmak önemli sağlar bir <xref:System.Globalization.CultureInfo> nesne.  
  
 Internet Explorer tarafından gönderilen HTTP isteğinden alınırken <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> dizisi, kullanıcı tercih sırasına göre doldurulur. Kullanıcının birincil kültür/bölge adı dizideki ilk öğe içerir. Dizi herhangi bir ek öğeler varsa, Internet Explorer bunları rasgele kültür adı, noktalı virgülle ayrılmış bir kalite belirticisi atar. Örneğin, fr-FR kültürü için bir giriş formu sürebilir `fr-FR;q=0.7`.  
  
 Örnek aramalar <xref:System.Globalization.CultureInfo.%23ctor%2A> oluşturucuyla kendi `useUserOverride` parametresini `false` yeni bir <xref:System.Globalization.CultureInfo> nesne. Kültür adı varsayılan kültür adı sunucu üzerinde ise bu, sağlar yeni <xref:System.Globalization.CultureInfo> sınıfı Oluşturucu tarafından oluşturulan nesne bir kültürün varsayılan ayarlarını içerir ve sunucunun kullanılarak herhangi bir ayarı yansıtmaz  **Bölge ve Dil Seçenekleri** uygulama. Sunucu üzerindeki herhangi bir geçersiz kılınan ayarı değerleri, kullanıcının sistemde yok veya kullanıcının girişinde yansıtılması düşüktür.  
  
 Kodunuzu ya da çağırabilir `Parse` veya `TryParse` kullanıcının girişinin sayısal türün yöntemi dönüştürülür. Parse yöntemi yinelenen çağrıları tek bir ayrıştırma işleminde gerekli olabilir. Sonuç olarak, `TryParse` yöntemi daha iyidir, çünkü bu döndürür `false` bir ayrıştırma işlemi başarısız olursa. Buna karşılık, tarafından oluşturulabilir yinelenen bir özel durum işleme `Parse` yöntemi, bir Web uygulamasındaki çok pahalı bir teklifi olabilir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Kodu derlemek için dosyaya kopyalayın bir [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] olan tüm mevcut kodlar değiştirir. Bu nedenle arka plan kod sayfası. [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web sayfası aşağıdaki denetimleri içermelidir:  
  
-   A <xref:System.Web.UI.WebControls.Label> kodda başvurulmuyor denetimi. Ayarlama, <xref:System.Web.UI.WebControls.TextBox.Text%2A> özelliğini "bir sayı girin:".  
  
-   A <xref:System.Web.UI.WebControls.TextBox> adlı Denetim `NumericString`.  
  
-   A <xref:System.Web.UI.WebControls.Button> adlı Denetim `OKButton`. Ayarlama, <xref:System.Web.UI.WebControls.Button.Text%2A> özelliği için "Tamam".  
  
 Sınıfın adını değiştirmek `NumericUserInput` tarafından tanımlanan sınıfı adını `Inherits` özniteliği [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] sayfanın `Page` yönergesi. Adını değiştirmek `NumericInput` nesnesi tarafından tanımlanan adına başvuru `id` özniteliği [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] sayfanın `form` etiketi.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 HTML akışına betik ekleme gelen bir kullanıcı önlemek için kullanıcı girişi hiçbir zaman doğrudan ve sunucu yanıtında yansıtılması gerekir. Bunun yerine, bunu kullanarak kodlanması gereken <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType> yöntemi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme İşlemlerini Gerçekleştirme](../../../docs/standard/base-types/performing-formatting-operations.md)  
- [Sayısal Dizeleri Ayrıştırma](../../../docs/standard/base-types/parsing-numeric.md)
