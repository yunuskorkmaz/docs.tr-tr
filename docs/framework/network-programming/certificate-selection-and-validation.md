---
title: Sertifika Seçimi ve Doğrulama
description: System.Net sınıfların SSL/TLS bağlantıları için sertifikaları seçme ve doğrulama için sunduğu çeşitli yollar hakkında bilgi edinin.
ms.date: 03/30/2017
ms.assetid: c933aca2-4cd0-4ff1-9df9-267143f25a6f
ms.openlocfilehash: 2dc63413f5c3a5fadd0d62ad61f0b887697c6a45
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502658"
---
# <a name="certificate-selection-and-validation"></a>Sertifika Seçimi ve Doğrulama
<xref:System.Net>Sınıflar, <xref:System.Security.Cryptography.X509Certificates> Güvenli Yuva KATMANı (SSL) bağlantılarını seçmek ve doğrulamak için çeşitli yollar destekler. İstemci, bir sunucuda kimliğini doğrulamak için bir veya daha fazla sertifika seçebilir. Bir sunucu, bir istemci sertifikasının kimlik doğrulaması için bir veya daha fazla belirli özniteliğe sahip olmasını gerektirebilir.  
  
## <a name="definition"></a>Tanım  
 Sertifika, bir ortak anahtar, öznitelikler (sürüm numarası, seri numarası ve sona erme tarihi gibi) ve bir sertifika yetkilisinden dijital imza içeren bir ASCII bayt akışıdır. Sertifikalar, şifrelenmiş bir bağlantı kurmak veya bir istemcinin kimliğini bir sunucuya doğrulamak için kullanılır.  
  
## <a name="client-certificate-selection-and-validation"></a>İstemci sertifikası seçimi ve doğrulaması  
 İstemci, belirli bir SSL bağlantısı için bir veya daha fazla sertifika seçebilir. İstemci sertifikaları, bir Web sunucusuyla veya SMTP posta sunucusuyla SSL bağlantısıyla ilişkilendirilebilir. İstemci, <xref:System.Security.Cryptography.X509Certificates.X509Certificate> veya sınıf nesneleri koleksiyonuna sertifikalar ekler <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> . E-postayı örnek olarak kullanarak, sertifika koleksiyonu, <xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection> sınıfının özelliği ile ilişkili bir bir örneğidir <xref:System.Net.Mail.SmtpClient.ClientCertificates%2A> <xref:System.Net.Mail.SmtpClient> . <xref:System.Net.HttpWebRequest>Sınıfın benzer bir özelliği vardır <xref:System.Net.HttpWebRequest.ClientCertificates%2A> .  
  
 Ve sınıfı arasındaki birincil fark, <xref:System.Security.Cryptography.X509Certificates.X509Certificate> <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> özel anahtarın sınıf için sertifika deposunda bulunması gerektiğidir <xref:System.Security.Cryptography.X509Certificates.X509Certificate> .  
  
 Sertifikalar bir koleksiyona eklenmiş ve belirli bir SSL bağlantısıyla ilişkili olsa da, sunucu tarafından istekte yoksa sunucuya sertifika gönderilmez. Bağlantıda birden çok istemci sertifikası ayarlandıysa, sunucu tarafından sunulan sertifika verenler ve istemci sertifikası verenin adı arasındaki eşleşmeyi dikkate alan bir algoritmaya göre en iyi yöntem kullanılır.  
  
 <xref:System.Net.Security.SslStream>Sınıfı, SSL el sıkışması üzerinde daha fazla denetim sağlar. İstemci, hangi istemci sertifikasını kullanacağınızı seçmek için bir temsilci belirtebilir.  
  
 Uzak bir sunucu, bir istemci sertifikasının geçerli, geçerli ve uygun sertifika yetkilisi tarafından imzalanmış olduğunu doğrulayabilirler. <xref:System.Net.ServicePointManager.ServerCertificateValidationCallback%2A>Sertifika doğrulamasını zorlamak için öğesine bir temsilci eklenebilir.  
  
## <a name="client-certificate-selection"></a>İstemci sertifikası seçimi  
 .NET Framework sunucuya aşağıdaki şekilde sunmak için istemci sertifikasını seçer:  
  
1. İstemci sertifikası önceden sunucuya sunulursa, ilk sunulursa sertifika önbelleğe alınır ve sonraki istemci sertifikası istekleri için yeniden kullanılır.  
  
2. Bir temsilci mevcutsa, her zaman, seçilecek istemci sertifikası olarak temsilciden sonucu kullanın. Mümkün olduğunda önbelleğe alınmış bir sertifika kullanmayı deneyin, ancak temsilci null döndürdüğünden ve sertifika koleksiyonu boş değilse önbelleğe alınmış anonim kimlik bilgilerini kullanmayın.  
  
3. Bu, bir istemci sertifikası için ilk zorluk söz konusu ise çerçeve, içindeki sertifikaları <xref:System.Security.Cryptography.X509Certificates.X509Certificate> veya <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> bağlantı ile ilişkili sınıf nesnelerini numaralandırır ve sunucu tarafından sunulan sertifika verenler listesi ve istemci sertifikası verenin adı arasında bir eşleşme arar. Eşleşen ilk sertifika sunucusuna gönderilir. Bir sertifika eşleşmesi veya sertifika koleksiyonu boşsa, sunucuya bir anonim kimlik bilgisi gönderilir.  
  
## <a name="tools-for-certificate-configuration"></a>Sertifika yapılandırması için Araçlar  
 İstemci ve sunucu sertifikası yapılandırması için bir dizi araç vardır.  
  
 *WinHttpCertCfg. exe* Aracı, istemci sertifikalarını yapılandırmak için kullanılabilir. *WinHttpCertCfg. exe* Aracı, Windows Server 2003 Resource Kit ile araçlardan biri olarak sağlanır. Bu araç, [www.Microsoft.com](https://www.microsoft.com)adresindeki Windows Server 2003 Resource Kit araçlarının bir parçası olarak da indirilebilir.  
  
*Httpcfg. exe* Aracı, sınıf için sunucu sertifikalarını yapılandırmak üzere kullanılabilir <xref:System.Net.HttpListener> . *Httpcfg. exe* Aracı, windows Server 2003 ve Windows XP Service Pack 2 için destek araçlarından biri olarak sağlanır. *Httpcfg. exe* ve diğer destek araçları, windows Server 2003 veya Windows XP 'de varsayılan olarak yüklenmez. Windows Server 2003 ' de. Destek Araçları, Windows Server 2003 CD-ROM ' da aşağıdaki klasörden ve dosyadan ayrı olarak yüklenir:  
  
 \Support\Tools\Suptools.msi  
  
 Windows XP Service Pack 2 ile kullanım için Windows XP destek araçları, [www.Microsoft.com](https://www.microsoft.com)adresinden bir indirme olarak sunulmaktadır.  
  
 *Httpcfg. exe* aracının bir sürümüne kaynak kodu, WINDOWS Server SDK ile örnek olarak da sağlanır. *Httpcfg. exe* örneğine yönelik kaynak kodu, varsayılan olarak, aşağıdaki klasör altındaki Windows SDK bir parçası olarak ağ örneklerine yüklenir:  
  
 *C:\Program Files\Microsoft SDKs\Windows\v1.0\Samples\NetDS\http\serviceconfig*  
  
 Bu araçlara ek olarak, <xref:System.Security.Cryptography.X509Certificates.X509Certificate> ve <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> sınıfları dosya sisteminden bir sertifika yüklemek için yöntemler sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Programlama Güvenliği](security-in-network-programming.md)
- [.NET Framework'te Ağ Programlaması](index.md)
