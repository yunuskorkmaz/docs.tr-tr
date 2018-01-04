---
title: "Nasıl yapılır: Web Denetimlerindeki Sayısal Kullanıcı Girişlerini Sayıya Dönüştürme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c93f1cda765b5f25fccddcfc27442b857262605f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-convert-numeric-user-input-in-web-controls-to-numbers"></a>Nasıl yapılır: Web Denetimlerindeki Sayısal Kullanıcı Girişlerini Sayıya Dönüştürme
Bir Web sayfası dünyanın her yerden görüntülenebilir olduğundan, kullanıcılar sayısal verisine girebilirsiniz bir <xref:System.Web.UI.WebControls.TextBox> biçimlerinin neredeyse sınırsız sayıda denetiminde. Sonuç olarak, yerel ayar ve Web sayfasının kullanıcı kültürü belirlemek çok önemlidir. Kullanıcı girişini ayrıştırmasına, daha sonra kullanıcının yerel ayarı ve kültür tarafından tanımlanan biçimlendirme kuralları uygulayabilirsiniz.  
  
### <a name="to-convert-numeric-input-from-a-web-textbox-control-to-a-number"></a>Sayısal girişi bir Web TextBox denetimi bir sayıya dönüştürme  
  
1.  Dize dizisi tarafından döndürülen olup olmadığını belirlemek <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> özelliği doldurulur. Değilse, 6. adıma geçin.  
  
2.  Dize dizisi olarak döndürülürse <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği doldurulur, ilk alt öğesi alın. İlk öğesi, kullanıcının varsayılan veya tercih edilen dil ve bölge gösterir.  
  
3.  Örneği bir <xref:System.Globalization.CultureInfo> kullanıcıyı temsil eden nesne tercih edilen kültür çağırarak <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> Oluşturucusu.  
  
4.  Ya da çağrısı `TryParse` veya `Parse` kullanıcı dönüştürmek istediğiniz sayısal türü yöntemi için girdisini. Bir aşırı yüklemesini kullanın `TryParse` veya `Parse` yöntemi ile bir `provider` parametresi ve aşağıdakilerden birini geçirin:  
  
    -   <xref:System.Globalization.CultureInfo> 3. adımda oluşturulan nesne.  
  
    -   <xref:System.Globalization.NumberFormatInfo> Tarafından döndürülen nesne <xref:System.Globalization.CultureInfo.NumberFormat%2A> özelliği <xref:System.Globalization.CultureInfo> 3. adımda oluşturulan nesne.  
  
5.  Dönüştürme başarısız olursa, tarafından döndürülen 2 ile 4 dize dizisi kalan her öğe için adımları yineleyin <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği.  
  
6.  Dönüştürme yine başarısız olursa veya dize dizisi olarak döndürülürse <xref:System.Web.HttpRequest.UserLanguages%2A> özelliği boşsa, dize sabit kültür tarafından döndürülen kullanarak XML'in <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> özelliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir sayısal değer girmesini ister Web formu tam arka plan kodu sayfasıdır bir <xref:System.Web.UI.WebControls.TextBox> denetlemek ve bir sayıya dönüştürür. Bu sayıyı sonra iki katına ve özgün giriş olarak aynı biçimlendirme kuralları kullanılarak görüntülenir.  
  
 [!code-csharp[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/cs/NumericUserInput1.aspx.cs#1)]
 [!code-vb[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/vb/NumericUserInput1.aspx.vb#1)]  
  
 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> Özelliği bulunan kültür adlarından doldurulur `Accept-Language` bir HTTP isteğine dahil üstbilgileri. Ancak, tüm tarayıcılar dahil `Accept-Language` üstbilgileri kendi isteklerini ve kullanıcılar da bastırmak üstbilgileri tamamen. Bu, kullanıcı girişi ayrıştırırken bir geri dönüş kültür sağlamak önemli kolaylaştırır. Genellikle, geri dönüş tarafından döndürülen sabit kültür kültürdür <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Kullanıcılar ayrıca Internet Explorer kültür adlarıyla kültür adları geçerli olmayabilir olasılığı oluşturan bir metin kutusunda giriş sağlayabilirsiniz. Bu örneği oluşturulurken özel durum işleme kullanmak önemli kılar bir <xref:System.Globalization.CultureInfo> nesnesi.  
  
 Internet Explorer tarafından gönderilen HTTP isteğinden alınırken <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> dizi kullanıcı tercih sırasına göre doldurulur. Dizinin ilk öğesi, kullanıcının birincil kültür/bölge adını içerir. Dizi ek öğeler içeriyorsa, Internet Explorer bunları rasgele kültür adı noktalı virgülle ayrılmış bir kalite belirticisi atar. Örneğin, fr-FR kültür için bir giriş form alabilir `fr-FR;q=0.7`.  
  
 Örnek aramalar <xref:System.Globalization.CultureInfo.%23ctor%2A> Oluşturucu kendi `useUserOverride` parametre kümesine `false` yeni <xref:System.Globalization.CultureInfo> nesnesi. Kültür adı sunucusundaki varsayılan kültür adı ise bu, sağlar yeni <xref:System.Globalization.CultureInfo> sınıfı oluşturucusu tarafından oluşturulan nesne bir kültürün varsayılan ayarları içerir ve sunucunun kullanarak geçersiz kılınmış herhangi bir ayarı yansıtmaz  **Bölge ve Dil Seçenekleri** uygulama. Sunucudaki tüm geçersiz kılınmış ayarları değerleri, kullanıcının sistemde yok veya kullanıcının giriş yansıtılması düşüktür.  
  
 Kodunuzu ya da çağırabilirsiniz `Parse` veya `TryParse` kullanıcı girişi sayısal türü yöntemi dönüştürülür. Parse yöntemi yinelenen çağrıları için tek bir ayrıştırma işlemi gerekli olabilir. Sonuç olarak, `TryParse` yöntemi olduğundan daha iyi döndürdüğü `false` ayrıştırma işlemi başarısız olursa. Buna karşılık, tarafından oluşturulan yinelenen özel durumları işleme `Parse` yöntemi, bir Web uygulaması çok pahalı bir teklifinde olabilir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Kodu derlemek için bu dosyaya kopyalayın bir [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] olan tüm var olan kodu değiştirir için arka plan kod sayfası. [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web sayfası aşağıdaki denetimleri içermelidir:  
  
-   A <xref:System.Web.UI.WebControls.Label> kodunda başvurulmuyor denetim. Ayarlama, <xref:System.Web.UI.WebControls.TextBox.Text%2A> özelliğine "bir sayı girin:".  
  
-   A <xref:System.Web.UI.WebControls.TextBox> adlı Denetim `NumericString`.  
  
-   A <xref:System.Web.UI.WebControls.Button> adlı Denetim `OKButton`. Ayarlama, <xref:System.Web.UI.WebControls.Button.Text%2A> "Tamam" özelliğine.  
  
 Sınıfından adını değiştirmek `NumericUserInput` tarafından tanımlanan sınıf adını `Inherits` özniteliği [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] sayfanın `Page` yönergesi. Adını değiştirmek `NumericInput` nesnesi tarafından tanımlanan adına başvuru `id` özniteliği [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] sayfanın `form` etiketi.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bir kullanıcının HTML akışa betik injecting önlemek için kullanıcı girişi hiçbir zaman doğrudan sunucu yanıtta yansıtılması gerekir. Bunun yerine, bunu kullanarak kodlanması gereken <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType> yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Biçimlendirme İşlemlerini Gerçekleştirme](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [Sayısal Dizeleri Ayrıştırma](../../../docs/standard/base-types/parsing-numeric.md)
