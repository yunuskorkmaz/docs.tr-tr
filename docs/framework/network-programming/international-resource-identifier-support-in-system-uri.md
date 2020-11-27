---
title: System.Uri’de Uluslararası Kaynak Tanımlayıcı Desteği
ms.date: 03/30/2017
ms.assetid: b5e994c3-3535-4aff-8e1b-b69be22e9a22
ms.openlocfilehash: a3670c40a7a78e2ac8b521a4cb95477381848f36
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253368"
---
# <a name="international-resource-identifier-support-in-systemuri"></a>System.Uri’de Uluslararası Kaynak Tanımlayıcı Desteği

<xref:System.Uri?displayProperty=nameWithType>Sınıfı uluslararası kaynak tanımlayıcı (IRI) ve uluslararası etki alanı adları (IDN) desteğiyle genişletildi. Bu geliştirmeler .NET Framework 3,5, 3,0 SP1 ve 2,0 SP1 'de sunulmaktadır.  
  
## <a name="iri-and-idn-support"></a>IRI ve ıDN desteği  

 Web adresleri genellikle, çok kısıtlanmış bir karakter kümesinden oluşan Tekdüzen Kaynak tanımlayıcıları (URI) kullanılarak ifade edilir:  
  
- Ingilizce alfabesinden büyük ve küçük harf ASCII harfleri.  
  
- 0 ile 9 arasındaki rakamlar.  
  
- Az sayıda ASCII sembolleri.  
  
 URI belirtimleri, RFC 2396 ' de ve Internet Mühendisliği görev gücü (IETF) tarafından yayımlanan RFC 3986 ' de belgelenmiştir.  
  
 Internet 'in büyümesi sayesinde, Ingilizce dışındaki dilleri kullanarak kaynakları belirlemek için büyüyen bir ihtiyacı vardır. Bu gereksinimi kolaylaştıran ve ASCII olmayan karakterlere izin veren tanımlayıcılar (Unicode/ISO 10646 karakter kümesindeki karakterler) uluslararası kaynak tanımlayıcıları (Iris) olarak bilinir. Iris belirtimleri, IETF tarafından yayımlanan RFC 3987 ' de belgelenmiştir. Iris kullanımı, URL 'nin Unicode karakterler içermesini sağlar.  
  
 Mevcut <xref:System.Uri?displayProperty=nameWithType> sınıf, RFC 3987 ' i temel alan IRI desteği sağlamak üzere genişletilmiştir. .NET Framework 2,0 davranışından, IRI özel olarak etkinleştirilmedikleri takdirde geçerli kullanıcılar hiçbir değişikliği görmez. Bu, uygulamanın .NET Framework önceki sürümleriyle uyumluluğunu sağlar.  
  
 Bir uygulama, etki alanı adlarına uygulanan uluslararası etki alanı adı (ıDN) ayrıştırma kullanılıp kullanılmayacağını ve IRI ayrıştırma kurallarının uygulanıp uygulanamayacağını belirtebilir. Bu, machine.config veya app.config dosyasında yapılabilir.  
  
 IDN 'yi etkinleştirmek, bir etki alanı adındaki tüm Unicode etiketlerini atlama kodu eşdeğerlerine dönüştürür. Puni Code adları yalnızca ASCII karakterleri içerir ve her zaman xn--önekiyle başlar. Bunun nedeni, DNS sunucularının çoğu yalnızca ASCII karakterlerini desteklediği için Internet 'teki mevcut DNS sunucularını desteklemedir (bkz. RFC 3940).  
  
 IRI ve ıDN 'nin etkinleştirilmesi, özelliğin değerini etkiler <xref:System.Uri.DnsSafeHost%2A?displayProperty=nameWithType> . IRI ve IDN 'nin etkinleştirilmesi,,, <xref:System.Uri.Equals%2A?displayProperty=nameWithType> <xref:System.Uri.OriginalString%2A?displayProperty=nameWithType> <xref:System.Uri.GetComponents%2A?displayProperty=nameWithType> ve yöntemlerinin davranışını de değiştirebilir <xref:System.Uri.IsWellFormedOriginalString%2A> .  
  
 <xref:System.GenericUriParser?displayProperty=nameWithType>Sınıfı ayrıca IRI ve IDN 'yi destekleyen özelleştirilebilir bir Ayrıştırıcı oluşturulmasına olanak tanımak için genişletilmiştir. Bir nesnenin davranışı, <xref:System.GenericUriParser?displayProperty=nameWithType> numaralandırmada bulunan değerlerin bit düzeyinde birleşimini oluşturucuya geçirerek belirtilir <xref:System.GenericUriParserOptions?displayProperty=nameWithType> <xref:System.GenericUriParser?displayProperty=nameWithType> . <xref:System.GenericUriParserOptions.IriParsing?displayProperty=nameWithType>Tür, ayrıştırıcısının uluslararası kaynak tanımlayıcıları (IRI) IÇIN RFC 3987 ' de belirtilen ayrıştırma kurallarını desteklediğini gösterir. IRI 'in gerçekten kullanılıp kullanılmadığını belirtir, IRI etkinse değişir.  
  
 <xref:System.GenericUriParserOptions.Idn?displayProperty=nameWithType>Türü, ayrıştırıcısının ana bilgisayar adlarının uluslararası etki alanı adı (IDN) ayrıştırmayı (IDN) desteklediğini gösterir. IDN 'nin gerçekten kullanılıp kullanılmadığını belirtir, ıDN 'nin etkin olup olmamasına bağlıdır.  
  
 IRI ayrıştırmayı etkinleştirmek, RFC 3987 ' deki en son IRI kurallarına göre normalleştirme ve karakter denetimi yapar. Varsayılan değer, IRI ayrıştırma 'nin devre dışı bırakılması ve RFC 2396 ve RFC 3986 ' e göre normalleştirme ve karakter denetimi yapılması için kullanılır.  
  
 Sınıfında IRI ve ıDN işleme <xref:System.Uri?displayProperty=nameWithType> , <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> ve <xref:System.Configuration.IdnElement?displayProperty=nameWithType> yapılandırma ayarı sınıfları kullanılarak da denetlenebilir. <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>Ayar, SıNıFıNDA IRI işlemesini etkinleştirilir veya devre dışı bırakır <xref:System.Uri?displayProperty=nameWithType> . <xref:System.Configuration.IdnElement?displayProperty=nameWithType>Ayar, SıNıFıNDA IDN işlemesini etkinleştirilir veya devre dışı bırakır <xref:System.Uri> . <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>Ayar, IDN 'yi de dolaylı olarak denetler. IDN işleminin mümkün olması için IRI işleme etkinleştirilmelidir. IRI işleme devre dışıysa, ıDN işleme, uyumluluk için .NET Framework 2,0 davranışının kullanıldığı ve ıDN adları kullanılmayan varsayılan ayar olarak ayarlanır.  
  
 Ve yapılandırma sınıfları için yapılandırma ayarı, <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> <xref:System.Configuration.IdnElement?displayProperty=nameWithType> ilk sınıf oluşturulduğunda bir kez okunacaktır <xref:System.Uri?displayProperty=nameWithType> . Yapılandırma ayarlarındaki değişiklikler bu süreden sonra yoksayılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- <xref:System.Uri.DnsSafeHost%2A?displayProperty=nameWithType>
