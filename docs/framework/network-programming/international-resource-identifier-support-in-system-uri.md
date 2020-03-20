---
title: System.Uri’de Uluslararası Kaynak Tanımlayıcı Desteği
ms.date: 03/30/2017
ms.assetid: b5e994c3-3535-4aff-8e1b-b69be22e9a22
ms.openlocfilehash: f78fff250aae177b5f0360e77a1c41a2f2bb0527
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "64647345"
---
# <a name="international-resource-identifier-support-in-systemuri"></a>System.Uri’de Uluslararası Kaynak Tanımlayıcı Desteği
Sınıf, <xref:System.Uri?displayProperty=nameWithType> Uluslararası Kaynak Tanımlayıcısı (IRI) ve Uluslararası Alan Adları (IDN) desteği ile genişletilmiştir. Bu geliştirmeler .NET Framework 3.5, 3.0 SP1 ve 2.0 SP1'de kullanılabilir.  
  
## <a name="iri-and-idn-support"></a>IRI ve IDN Desteği  
 Web adresleri genellikle çok sınırlı bir karakter kümesinden oluşan Tek düzen Kaynak Tanımlayıcıları (URI) kullanılarak ifade edilir:  
  
- İngiliz alfabesinden büyük ve küçük harfLI ASCII harfleri.  
  
- 0'dan 9'a kadar olan sayılar.  
  
- Diğer ASCII sembolleri az sayıda.  
  
 URI'lerin özellikleri, Internet Engineering Task Force (IETF) tarafından yayınlanan RFC 2396 ve RFC 3986'da belgelenmiştir.  
  
 Internet'in büyümesi ile, İngilizce dışındaki dilleri kullanarak kaynakları tanımlamak için büyüyen bir ihtiyaç vardır. Bu ihtiyacı kolaylaştıran ve ASCII olmayan karakterlere (Unicode/ISO 10646 karakter kümesindeki karakterler) izin veren tanımlayıcılar Uluslararası Kaynak Tanımlayıcıları (IRI'ler) olarak bilinir. IRI'lerin özellikleri IETF tarafından yayınlanan RFC 3987'de belgelenmiştir. IRI'ler kullanmak, bir URL'nin Unicode karakterleri içermesine olanak tanır.  
  
 Mevcut <xref:System.Uri?displayProperty=nameWithType> sınıf RFC 3987 dayalı IRI desteği sağlamak için genişletilmiştir. Geçerli kullanıcılar, IRI'yi özel olarak etkinleştirmedikçe .NET Framework 2.0 davranışında herhangi bir değişiklik görmezler. Bu, .NET Framework'ün önceki sürümleriyle uygulama uyumluluğu sağlar.  
  
 Bir uygulama, etki alanı adlarına uygulanan Uluslararası Alan Adı (IDN) ayrıştırma kullanıp kullanmayacağını ve IRI ayrıştırma kurallarının uygulanıp uygulanmayacağını belirtebilir. Bu makine.config veya app.config dosyasında yapılabilir.  
  
 IDN'yi etkinleştirmek, bir etki alanı adındaki tüm Unicode etiketlerini Punycode eşdeğerlerine dönüştürür. Punycode adları yalnızca ASCII karakterleri içerir ve her zaman xn ile başlar-- önek. Bunun nedeni, çoğu DNS sunucusu yalnızca ASCII karakterlerini desteklediğinden, Internet'teki varolan DNS sunucularını desteklemektir (bkz. RFC 3940).  
  
 IRI ve IDN'yi etkinleştirmek <xref:System.Uri.DnsSafeHost%2A?displayProperty=nameWithType> özelliğin değerini etkiler. IRI ve IDN'yi etkinleştirmek, <xref:System.Uri.Equals%2A?displayProperty=nameWithType>", <xref:System.Uri.GetComponents%2A?displayProperty=nameWithType>, <xref:System.Uri.IsWellFormedOriginalString%2A> <xref:System.Uri.OriginalString%2A?displayProperty=nameWithType>" ve yöntemlerinin davranışını da değiştirebilir.  
  
 Sınıf, <xref:System.GenericUriParser?displayProperty=nameWithType> IRI ve IDN'i destekleyen özelleştirilebilir bir benzetme oluşturmaya da izin verecek şekilde genişletildi. Bir <xref:System.GenericUriParser?displayProperty=nameWithType> nesnenin <xref:System.GenericUriParserOptions?displayProperty=nameWithType> <xref:System.GenericUriParser?displayProperty=nameWithType> davranışı, numaralandırmada bulunan değerlerin bitwise bir leşiminin oluşturucuya geçirilmesiyle belirtilir. Tür, <xref:System.GenericUriParserOptions.IriParsing?displayProperty=nameWithType> ayrıştırıcının Uluslararası Kaynak Tanımlayıcıları (IRI) için RFC 3987'de belirtilen ayrıştırma kurallarını desteklediğini gösterir. IRI'nin gerçekten kullanılıp kullanılmadığına, IRI'nin etkin olup olmadığına bağlıdır.  
  
 Tür, <xref:System.GenericUriParserOptions.Idn?displayProperty=nameWithType> arayıcın ana bilgisayar adlarının Uluslararası Laştırılmış Etki Alanı Adı (IDN) ayrıştırma (IDN) desteklemesini gösterir. IDN'nin gerçekten kullanılıp kullanılmadığına, IDN'nin etkin olup olmadığına bağlıdır.  
  
 IRI ayrıştırmayı etkinleştirmek, RFC 3987'deki en son IRI kurallarına göre normalleştirme ve karakter denetimi yapar. Varsayılan değer IRI ayrıştırmanın devre dışı olması içindir, böylece normalleştirme ve karakter denetimi RFC 2396 ve RFC 3986'ya göre yapılır.  
  
 Sınıftaki <xref:System.Uri?displayProperty=nameWithType> IRI ve IDN işleme, <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> <xref:System.Configuration.IdnElement?displayProperty=nameWithType> yapılandırma ayarı sınıfları kullanılarak da denetlenebilir. Ayar, <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> sınıfta IRI işlemeyi <xref:System.Uri?displayProperty=nameWithType> etkinleştirir veya devre dışı kılabilir. Ayar, <xref:System.Configuration.IdnElement?displayProperty=nameWithType> sınıfta IDN işlemeyi <xref:System.Uri> etkinleştirir veya devre dışı kılabilir. Ayar, <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> IDN'yi dolaylı olarak da denetler. IDN işleminin mümkün olabilmesi için IRI işleme nin etkinleştirilmesi gerekir. IRI işleme devre dışı bırakılırsa, IDN işleme ,NET Framework 2.0 davranışının uyumluluk için kullanıldığı ve IDN adlarının kullanılmadığı varsayılan ayarına ayarlanır.  
  
 Birinci <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> <xref:System.Uri?displayProperty=nameWithType> sınıf oluşturulduğunda <xref:System.Configuration.IdnElement?displayProperty=nameWithType> yapılandırma sınıfları ve yapılandırma sınıfları için yapılandırma ayarı bir kez okunur. Bu süre den sonra yapılandırma ayarlarında yapılan değişiklikler yoksayılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- <xref:System.Uri.DnsSafeHost%2A?displayProperty=nameWithType>
