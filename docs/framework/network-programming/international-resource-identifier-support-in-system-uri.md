---
title: System.Uri uluslararası kaynak tanımlayıcısı desteği
ms.date: 03/30/2017
ms.assetid: b5e994c3-3535-4aff-8e1b-b69be22e9a22
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: bf26f98773383ee6671162a53b84f155c18b5adf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398259"
---
# <a name="international-resource-identifier-support-in-systemuri"></a>System.Uri uluslararası kaynak tanımlayıcısı desteği
<xref:System.Uri?displayProperty=nameWithType> Sınıfı genişletilmişse uluslararası kaynak tanımlayıcısı (IRI) ve Uluslararası yapılan etki alanı adları (IDN) desteği. Bu geliştirmeler, .NET Framework 3.5, 3.0 SP1 ve 2.0 SP1'de kullanılabilir.  
  
## <a name="iri-and-idn-support"></a>IRI ve IDN desteği  
 Web adresleri genellikle Tekdüzen Kaynak Tanımlayıcıları (çok kısıtlı bir karakter kümesi oluşur URI) kullanarak belirtilmiştir:  
  
-   Büyük ve küçük ASCII harf İngilizce alfabesinde.  
  
-   9 basamak 0.  
  
-   Diğer ASCII simgelerini küçük sayısı.  
  
 RFC 2396 ve RFC 3986 Internet Engineering Task Force (IETF) tarafından yayımlanan URI'ler belirtimleri belgelenmiştir.  
  
 Internet büyümesi ile İngilizce dışındaki dilleri kullanarak kaynakları tanımlamak için büyüyen bir gereksinimi yoktur. Bu gereksinim kolaylaştırmak ve ASCII olmayan karakterler (karakter Unicode/ISO 10646 karakter kümesinde) izin tanımlayıcılarını uluslararası kaynak tanımlayıcıları (IRIS) bilinir. IRIs belirtimleri RFC IETF tarafından yayımlanan 3987 belgelenmiştir. IRIs kullanarak Unicode karakterler içeren bir URL sağlar.  
  
 Varolan <xref:System.Uri?displayProperty=nameWithType> sınıfı genişletilmişse RFC 3987 üzerinde IRI desteği sağlamak için. Bunlar IRI özellikle etkinleştirmediğiniz sürece geçerli kullanıcılar .NET Framework 2.0 davranış herhangi bir değişiklik görmez. Bu, .NET Framework'ün önceki sürümler ile uygulama uyumluluğunu sağlar.  
  
 Uygulama etki alanı adlarına uygulanan Uluslararası yapılan etki alanı adı (IDN) ayrıştırma kullanılıp kullanılmayacağını ve kuralları ayrıştırma IRI uygulanıp belirtebilirsiniz. Machine.config veya app.config dosyasında yapılabilir.  
  
 Bir etki alanı adındaki tüm Unicode etiketleri IDN etkinleştirme Punycode eşdeğerlerine dönüştürür. Zayıf kod adları yalnızca ASCII karakterler içeren ve her zaman xn--önekiyle başlatın. Bunun nedeni çoğu DNS sunucuları, yalnızca ASCII karakterleri (RFC 3940 bakın) destekler beri Internet'te var olan DNS sunucuları desteklemektir.  
  
 IRI ve IDN etkinleştirilmesi etkiler değerini <xref:System.Uri.DnsSafeHost%2A?displayProperty=nameWithType> özelliği. IRI ve IDN etkinleştirme davranışını da değiştirebilir <xref:System.Uri.Equals%2A?displayProperty=nameWithType>, <xref:System.Uri.OriginalString%2A?displayProperty=nameWithType>, <xref:System.Uri.GetComponents%2A?displayProperty=nameWithType>, ve <xref:System.Uri.IsWellFormedOriginalString%2A> yöntemleri.  
  
 <xref:System.GenericUriParser?displayProperty=nameWithType> Sınıfı ayrıca genişletilmişse IRI ve IDN destekleyen özelleştirilebilir ayrıştırıcı oluşturma izin vermek için. Davranışını bir <xref:System.GenericUriParser?displayProperty=nameWithType> nesne bulunan değerlerin Bitsel bir birleşimi geçirerek belirtilen <xref:System.GenericUriParserOptions?displayProperty=nameWithType> numaralandırma <xref:System.GenericUriParser?displayProperty=nameWithType> Oluşturucusu. <xref:System.GenericUriParserOptions.IriParsing?displayProperty=nameWithType> Türünü gösteren ayrıştırıcı RFC 3987 uluslararası kaynak tanımlayıcıları (IRI) için belirtilen ayrıştırma kuralları destekler. IRI gerçekten kullanılıp kullanılmadığını IRI etkin olup olmadığını bağlıdır.  
  
 <xref:System.GenericUriParserOptions.Idn?displayProperty=nameWithType> Türünü gösteren ayrıştırıcı Uluslararası yapılan etki alanı adı (IDN) ana bilgisayar adlarını (IDN) ayrıştırma destekler. IDN gerçekte kullanılıp kullanılmadığını IDN etkin olup olmadığını bağlıdır.  
  
 IRI etkinleştirme ayrıştırma normalleştirme ne yapacağını ve RFC 3987 göre en son IRI denetimi karakter kuralları. Normalleştirme ve karakter denetimi RFC 2396 ve RFC 3986 göre yapılan şekilde devre dışı bırakılması ayrıştırma IRI için varsayılan değerdir.  
  
 IRI ve içinde işleme IDN <xref:System.Uri?displayProperty=nameWithType> sınıfı da denetlenebilir kullanarak <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> ve <xref:System.Configuration.IdnElement?displayProperty=nameWithType> yapılandırma ayarı sınıflarını. <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> Ayarını etkinleştirir veya içinde işleme IRI devre dışı bırakır <xref:System.Uri?displayProperty=nameWithType> sınıfı. <xref:System.Configuration.IdnElement?displayProperty=nameWithType> Ayarını etkinleştirir veya içinde işleme IDN devre dışı bırakır <xref:System.Uri> sınıfı. <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> Da dolaylı olarak ayarlama IDN denetler. IRI işleme olabilmesi için işleme IDN için etkinleştirilmesi gerekir. IRI işleme devre dışıysa, IDN işleme burada .NET Framework 2.0 davranışı uyumluluk için kullanılır ve IDN adları kullanılmayan varsayılan ayar olarak ayarlanır.  
  
 İçin yapılandırma ayarı <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType> ve <xref:System.Configuration.IdnElement?displayProperty=nameWithType> yapılandırma sınıfları okunabilir bir kez zaman ilk <xref:System.Uri?displayProperty=nameWithType> sınıfı yapılandırılmıştır. Bu süre sonunda yapılandırma ayarlarında yapılan değişiklikler göz ardı edilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Configuration.IdnElement?displayProperty=nameWithType>  
 <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 <xref:System.Uri.DnsSafeHost%2A?displayProperty=nameWithType>
