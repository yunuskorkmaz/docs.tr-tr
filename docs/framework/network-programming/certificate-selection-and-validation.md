---
title: Sertifika Seçimi ve Doğrulama
ms.date: 03/30/2017
ms.assetid: c933aca2-4cd0-4ff1-9df9-267143f25a6f
ms.openlocfilehash: aea47360ab1bb9dad446a5a7b19a91ea688953c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048743"
---
# <a name="certificate-selection-and-validation"></a>Sertifika Seçimi ve Doğrulama
Sınıflar, <xref:System.Net> Güvenli Soket Katmanı <xref:System.Security.Cryptography.X509Certificates> (SSL) bağlantıları için seçme ve doğrulama nın çeşitli yollarını destekler. İstemci, kendisini bir sunucuya doğrulamak için bir veya daha fazla sertifika seçebilir. Sunucu, istemci sertifikasının kimlik doğrulaması için bir veya daha fazla özel özniteliklerine sahip olduğunu gerektirebilir.  
  
## <a name="definition"></a>Tanım  
 Sertifika, ortak anahtar, öznitelikler (sürüm numarası, seri numarası ve son kullanma tarihi gibi) ve Sertifika Yetkilisi'nin dijital imzalarını içeren bir ASCII bayt akışıdır. Sertifikalar, şifreli bir bağlantı kurmak veya istemcinin bir sunucuya kimliğini doğrulamak için kullanılır.  
  
## <a name="client-certificate-selection-and-validation"></a>Müşteri Sertifikası Seçimi ve Doğrulama  
 İstemci belirli bir SSL bağlantısı için bir veya daha fazla sertifika seçebilir. İstemci sertifikaları, bir web sunucusuna veya Bir SMTP posta sunucusuna SSL bağlantısıyla ilişkilendirilebilir. İstemci, bir koleksiyona <xref:System.Security.Cryptography.X509Certificates.X509Certificate> <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> veya sınıf nesnelerine sertifika ekler. Örnek olarak e-posta yı kullanan sertifika <xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection>koleksiyonu, <xref:System.Net.Mail.SmtpClient> sınıfın <xref:System.Net.Mail.SmtpClient.ClientCertificates%2A> özelliğiyle ilişkili bir ) örneğidir. Sınıfın <xref:System.Net.HttpWebRequest> benzer <xref:System.Net.HttpWebRequest.ClientCertificates%2A> bir özelliği vardır.  
  
 Sınıf <xref:System.Security.Cryptography.X509Certificates.X509Certificate> ve sınıf arasındaki temel fark, özel anahtarın <xref:System.Security.Cryptography.X509Certificates.X509Certificate> sınıf için sertifika deposunda yer alması gerektiğidir. <xref:System.Security.Cryptography.X509Certificates.X509Certificate2>  
  
 Sertifikalar bir koleksiyona eklense ve belirli bir SSL bağlantısıyla ilişkilendirilse bile, sunucu bunları istemediği sürece sunucuya sertifika gönderilmez. Bir bağlantıda birden çok istemci sertifikası ayarlanmışsa, en iyisi, sunucu tarafından sağlanan sertifika verenler listesi ile istemci sertifikası veren kuruluş adı arasındaki eşleşmeyi dikkate alan bir algoritmaya göre kullanılır.  
  
 Sınıf, <xref:System.Net.Security.SslStream> SSL el sıkışması üzerinde daha fazla kontrol sağlar. İstemci, hangi istemci sertifikasının kullanılacağını seçmek için bir temsilci belirleyebilir.  
  
 Uzak bir sunucu, istemci sertifikasının geçerli, geçerli ve ilgili Sertifika Yetkilisi tarafından imzalanmış olduğunu doğrulayabilir. Sertifika doğrulaması zorlamak <xref:System.Net.ServicePointManager.ServerCertificateValidationCallback%2A> için bir temsilci eklenebilir.  
  
## <a name="client-certificate-selection"></a>Müşteri Sertifikası Seçimi  
 .NET Framework, sunucuya sunmak üzere aşağıdaki şekilde sunacak istemci sertifikasını seçer:  
  
1. İstemci sertifikası sunucuya daha önce sunulduysa, sertifika ilk sunulduğunda önbelleğe alınır ve sonraki istemci sertifikası istekleri için yeniden kullanılır.  
  
2. Bir temsilci varsa, her zaman seçilecek istemci sertifikası olarak temsilciden gelen sonucu kullanın. Mümkün olduğunda önbelleğe alınmış bir sertifika kullanmayı deneyin, ancak temsilci null döndüyse ve sertifika koleksiyonu boş değilse önbelleğe alınmış anonim kimlik bilgilerini kullanmayın.  
  
3. Bu, istemci sertifikası için ilk sorunsa, Çerçeve, sunucu <xref:System.Security.Cryptography.X509Certificates.X509Certificate> tarafından <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> sağlanan sertifika verenler listesi ile istemci sertifikası veren kuruluş adı arasında eşleşme arayarak, bağlantıyla ilişkili sertifikaları veya sınıf nesnelerini listeler. Eşleşen ilk sertifika sunucuya gönderilir. Sertifika eşleşmez veya sertifika koleksiyonu boşsa, sunucuya anonim bir kimlik bilgisi gönderilir.  
  
## <a name="tools-for-certificate-configuration"></a>Sertifika Yapılandırması için Araçlar  
 İstemci ve sunucu sertifikası yapılandırması için çok sayıda araç kullanılabilir.  
  
 *Winhttpcertcfg.exe* aracı istemci sertifikalarını yapılandırmak için kullanılabilir. *Winhttpcertcfg.exe* aracı, Windows Server 2003 Kaynak Kiti'nin araçlarından biri olarak sağlanır. Bu araç, Windows Server 2003 Kaynak Kiti Araçları'nın bir parçası olarak [www.microsoft.com](https://www.microsoft.com)de indirilebilir.  
  
*HttpCfg.exe* <xref:System.Net.HttpListener> aracı, sınıf için sunucu sertifikalarını yapılandırmak için kullanılabilir. *HttpCfg.exe* aracı, Windows Server 2003 ve Windows XP Service Pack 2 için destek araçlarından biri olarak sağlanır. *HttpCfg.exe* ve diğer destek araçları varsayılan olarak Windows Server 2003 veya Windows XP'de yüklenmez. Windows Server 2003'te. destek araçları, Windows Server 2003 CD-ROM'da aşağıdaki klasör ve dosyadan ayrı olarak yüklenir:  
  
 \Destek\Araçlar\Suptools.msi  
  
 Windows XP Service Pack 2 ile kullanım için, Windows XP Destek Araçları [www.microsoft.com'dan](https://www.microsoft.com)indirilebilir.  
  
 *HttpCfg.exe* aracının bir sürümünün kaynak kodu da Windows Server SDK ile örnek olarak sağlanır. *HttpCfg.exe* örneğinin kaynak kodu varsayılan olarak aşağıdaki klasörün altındaki Windows SDK'nın bir parçası olarak ağ örnekleriyle yüklenir:  
  
 *C:\Program Files\Microsoft SDKs\Windows\v1.0\Samples\NetDS\http\serviceconfig*  
  
 Bu araçlara ek <xref:System.Security.Cryptography.X509Certificates.X509Certificate> olarak, ve <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> sınıflar dosya sisteminden bir sertifika yükleme yöntemleri sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Programlama Güvenliği](security-in-network-programming.md)
- [.NET Framework'te Ağ Programlaması](index.md)
