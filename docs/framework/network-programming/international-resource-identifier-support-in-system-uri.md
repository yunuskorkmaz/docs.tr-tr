---
title: System.uri'de uluslararası kaynak tanımlayıcı desteği
ms.date: 03/30/2017
ms.assetid: b5e994c3-3535-4aff-8e1b-b69be22e9a22
ms.openlocfilehash: 742ea03a62426506f068a9b9e669278d0d4663ec
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128092"
---
# <a name="international-resource-identifier-support-in-systemuri"></a>System.uri'de uluslararası kaynak tanımlayıcı desteği
<xref:System.Uri?displayProperty=nameWithType> Uluslararası kaynak tanımlayıcı (IRI) ve Uluslararası yapılan etki alanı adı (IDN) desteği sayesinde, sınıf genişletilmişse. Bu iyileştirmeler, .NET Framework 3.5, 3.0 SP1 ve 2.0 SP1'i kullanılabilir.  
  
## <a name="iri-and-idn-support"></a>IRI ve IDN desteği  
 Web adresleri, genellikle Tekdüzen Kaynak Tanımlayıcıları (çok kısıtlı bir karakter kümesi oluşan URI) kullanılarak ifade edilir:  
  
-   Büyük ve küçük ASCII harf İngilizce alfabetik.  
  
-   0'dan 9 basamak.  
  
-   Diğer ASCII simgeleri küçük bir sayı.  
  
 Belirtimleri için URI RFC 2396 ve RFC 3986'ya Internet Engineering Task Force (IETF) tarafından yayınlanan belgelenmiştir.  
  
 Internet büyümesi ile İngilizce dışındaki diller kullanarak kaynakları tanımlamak için artan bir ihtiyacı yoktur. Bunu kolaylaştırmak ve ASCII olmayan karakterler (Unicode/ISO 10646 karakter kümesindeki karakter) izin tanımlayıcılardan uluslararası kaynak tanımlayıcılarda (sınıflandırma) bilinir. Iris belirtimleri RFC IETF tarafından yayımlanan 3987 belgelenmiştir. Iris kullanarak Unicode karakterler içerecek şekilde bir URL sağlar.  
  
 Varolan <xref:System.Uri?displayProperty=nameWithType> sınıfı üzerinde RFC 3987 IRI desteği sağlamak için genişletilmişse. Bunlar özellikle IRI etkinleştirmediğiniz sürece geçerli kullanıcıların .NET Framework 2.0 davranış herhangi bir değişiklik görmezsiniz. Bu, .NET Framework'ün önceki sürümleriyle uygulama uyumluluğu sağlar.  
  
 Bir uygulama etki alanı adlarına uygulanan Uluslararası yapılan etki alanı adı (IDN) ayrıştırma kullanılıp kullanılmayacağını ve IRI ayrıştırma kurallarını uygulanıp belirtebilirsiniz. Bu, machine.config veya app.config dosyasında yapılabilir.  
  
 Bir etki alanı adındaki tüm Unicode etiketleri IDN etkinleştirme Punycode eşdeğerlerine dönüştürür. Zayıf kod adları yalnızca ASCII karakterler içeren ve her zaman xn--önekiyle başlayan. Bunun nedeni çoğu DNS sunucuları yalnızca ASCII karakterleri (bkz. RFC 3940) desteklemediğinden Internet'te mevcut DNS sunucuları desteklemektir.  
  
 IRI ve IDN etkinleştirilmesi, değerini etkiler <xref:System.Uri.DnsSafeHost%2A?displayProperty=nameWithType> özelliği. IRI ve IDN etkinleştirme davranışını da değiştirebilir <xref:System.Uri.Equals%2A?displayProperty=nameWithType>, <xref:System.Uri.OriginalString%2A?displayProperty=nameWithType>, <xref:System.Uri.GetComponents%2A?displayProperty=nameWithType>, ve <xref:System.Uri.IsWellFormedOriginalString%2A> yöntemleri.  
  
 <xref:System.GenericUriParser?displayProperty=nameWithType> Sınıfı da genişletilmişse IRI ve IDN destekleyen özelleştirilebilir bir ayrıştırıcı oluşturma izni. Davranışını bir <xref:System.GenericUriParser?displayProperty=nameWithType> nesnesi Bitsel bir birleşimi kullanılabilir değerler geçirerek belirtildiğinde <xref:System.GenericUriParserOptions?displayProperty=nameWithType> sabit listesine <xref:System.GenericUriParser?displayProperty=nameWithType> Oluşturucusu. <xref:System.GenericUriParserOptions.IriParsing?displayProperty=nameWithType> Türünü belirten ayrıştırıcı RFC 3987 içinde belirtilen uluslararası kaynak tanımlayıcı (IRI) ayrıştırma kurallarını destekler. IRI gerçekten kullanılıp kullanılmadığını IRI etkinleştirilip etkinleştirilmeyeceğini bağlıdır.  
  
 <xref:System.GenericUriParserOptions.Idn?displayProperty=nameWithType> Türü belirten ayrıştırıcı Uluslararası yapılan etki alanı adı (IDN) ana bilgisayar adlarını (IDN) ayrıştırma destekler. IDN gerçekten kullanılıp kullanılmadığını IDN etkinleştirilip etkinleştirilmeyeceğini bağlıdır.  
  
 IRI ayrıştırma normalleştirme ne yapacağını etkinleştirip RFC 3987 karakter göre en son IRI denetleme kuralları. IRI ayrıştırma normalleştirme ve karakter denetimi RFC 2396 ve RFC 3986'ya göre yapılır şekilde devre dışı bırakılması için varsayılan değerdir.  
  
 IRI ve işleme IDN <xref:System.Uri?displayProperty=nameWithType> sınıfı da denetlenebilir kullanarak <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> ve <xref:System.Configuration.IdnElement?displayProperty=nameWithType> yapılandırma ayarı sınıfları. <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> Ayarını etkinleştirir veya işleme IRI devre dışı bırakır <xref:System.Uri?displayProperty=nameWithType> sınıfı. <xref:System.Configuration.IdnElement?displayProperty=nameWithType> Ayarını etkinleştirir veya işleme IDN devre dışı bırakır <xref:System.Uri> sınıfı. <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> IDN denetimleri de dolaylı olarak ayarlama. IRI işleme mümkün olması için işleme IDN için etkinleştirilmesi gerekir. IRI işleme devre dışıysa, IDN işleme burada .NET Framework 2.0 davranışı uyumluluk için kullanılır ve IDN adları kullanılmaz varsayılan ayar olarak ayarlanır.  
  
 Bir yapılandırma ayarı için <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> ve <xref:System.Configuration.IdnElement?displayProperty=nameWithType> yapılandırma sınıfları okuyup kez zaman ilk <xref:System.Uri?displayProperty=nameWithType> sınıf oluşturulur. Bu süreden sonra yapılandırma ayarlarında yapılan değişiklikler yok sayılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Configuration.IdnElement?displayProperty=nameWithType>  
 <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 <xref:System.Uri.DnsSafeHost%2A?displayProperty=nameWithType>
