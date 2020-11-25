---
title: "Son değişiklik: Linux 'ta .NET için varsayılan TLS şifre paketleri"
description: Linux 'ta .NET 5,0 ' deki önemli değişiklik hakkında bilgi edinmek için, artık TLS/SSL yaparken varsayılan şifre paketleri için OpenSSL yapılandırmasına saygı görürsünüz.
ms.date: 10/16/2020
ms.openlocfilehash: f1c23517161ac213a9cd7cf6e7da8eebeb91583b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761321"
---
# <a name="default-tls-cipher-suites-for-net-on-linux"></a>Linux 'ta .NET için varsayılan TLS şifre paketleri

.NET, Linux 'ta, sınıf <xref:System.Net.Security.SslStream> veya daha yüksek düzey işlemler aracılığıyla (örneğin, sınıfı aracılığıyla) TLS/SSL yaparken varsayılan şifre paketleri Için OpenSSL yapılandırmasına uyar <xref:System.Net.Http.HttpClient> . Varsayılan şifre paketleri açık olarak yapılandırılmamışsa, Linux üzerinde .NET, izin verilen şifre paketlerinin sıkı bir listesini kullanır.

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, .NET varsayılan şifre paketlerinin sistem yapılandırmasına uymaz. Linux 'ta .NET için varsayılan şifre paketi listesi çok daha fazla izne sahiptir.

.NET 5,0 ' den başlayarak, Linux 'ta .NET, *OpenSSL. cnf* dosyasında belirtildiğinde varsayılan şifre paketleri Için OpenSSL yapılandırmasına uyar. Şifre paketleri açık olarak yapılandırılmamışsa, izin verilen şifre paketleri aşağıdaki gibidir:

- TLS 1,3 şifre paketleri
- TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384
- TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256
- TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
- TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256
- TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384
- TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256
- TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384
- TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256

Bu geri dönüş varsayılanı TLS 1,0 veya TLS 1,1 ile uyumlu herhangi bir şifre paketi içermediğinden, bu eski protokol sürümleri varsayılan olarak etkin bir şekilde devre dışıdır.

Belirli bir oturumun SslStream 'e CipherSuitePolicy değeri sağlamak hala yapılandırma dosyası içeriğini ve/veya .NET geri dönüş varsayılanını değiştirecek.

## <a name="reason-for-change"></a>Değişiklik nedeni

Linux üzerinde .NET çalıştıran kullanıcılar, varsayılan yapılandırmasının <xref:System.Net.Security.SslStream> üçüncü taraf değerlendirme araçlarından yüksek bir güvenlik derecelendirmesi sağlayan bir olarak değiştirilmesini istedi.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="recommended-action"></a>Önerilen eylem

Yeni varsayılanlar, modern istemcilerle veya sunucularla iletişim kurarken çalışıyor olabilir. Eski istemcileri kabul etmek için (veya eski sunucularla iletişim kurmak için) varsayılan şifre paketi listesini genişletmeniz gerekiyorsa, bir `CipherSuitePolicy` değer belirtin veya OpenSSL yapılandırma dosyasını değiştirin. Birçok Linux dağıtımlarında, OpenSSL yapılandırma dosyası */etc/SSL/OpenSSL.exe. cnf*' de bulunur.

Bu örnek *OpenSSL. cnf* dosyası, Linux üzerinde .NET 5,0 ve üzeri için varsayılan şifre paketleri ilkesi ile eşdeğer olan minimal bir dosyadır. Sistem dosyasını değiştirmek yerine, bu kavramları sisteminizde bulunan dosyayla birleştirin.

```ini
openssl_conf = default_conf

[default_conf]
ssl_conf = ssl_sect

[ssl_sect]
system_default = system_default_sect

[system_default_sect]
CipherString = ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256
```

Red Hat Enterprise Linux, CentOS ve Fedora dağıtımları, .NET uygulamaları, sistem genelinde şifreleme ilkeleri tarafından izin verilen şifre paketlerine varsayılan olarak yapılır. Bu dağıtımlardan, *OpenSSL. cnf* yerine şifre ilkeleri yapılandırmasını kullanın.

## <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılayıcısı yok.

<!--

### Affected APIs

- Not detectible via API analysis.

### Category

- Cryptography
- Security

-->
