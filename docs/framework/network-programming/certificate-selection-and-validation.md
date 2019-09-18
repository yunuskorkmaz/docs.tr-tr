---
title: Sertifika Seçimi ve Doğrulama
ms.date: 03/30/2017
ms.assetid: c933aca2-4cd0-4ff1-9df9-267143f25a6f
ms.openlocfilehash: aea47360ab1bb9dad446a5a7b19a91ea688953c4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048743"
---
# <a name="certificate-selection-and-validation"></a>Sertifika Seçimi ve Doğrulama
Sınıflar <xref:System.Net> , Güvenli Yuva Katmanı (SSL) bağlantılarını <xref:System.Security.Cryptography.X509Certificates> seçmek ve doğrulamak için çeşitli yollar destekler. İstemci, bir sunucuda kimliğini doğrulamak için bir veya daha fazla sertifika seçebilir. Bir sunucu, bir istemci sertifikasının kimlik doğrulaması için bir veya daha fazla belirli özniteliğe sahip olmasını gerektirebilir.  
  
## <a name="definition"></a>Tanım  
 Sertifika, bir ortak anahtar, öznitelikler (sürüm numarası, seri numarası ve sona erme tarihi gibi) ve bir sertifika yetkilisinden dijital imza içeren bir ASCII bayt akışıdır. Sertifikalar, şifrelenmiş bir bağlantı kurmak veya bir istemcinin kimliğini bir sunucuya doğrulamak için kullanılır.  
  
## <a name="client-certificate-selection-and-validation"></a>İstemci sertifikası seçimi ve doğrulaması  
 İstemci, belirli bir SSL bağlantısı için bir veya daha fazla sertifika seçebilir. İstemci sertifikaları, bir Web sunucusuyla veya SMTP posta sunucusuyla SSL bağlantısıyla ilişkilendirilebilir. İstemci, <xref:System.Security.Cryptography.X509Certificates.X509Certificate> veya <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> sınıf nesneleri koleksiyonuna sertifikalar ekler. E-postayı örnek olarak kullanarak, sertifika koleksiyonu, <xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection> <xref:System.Net.Mail.SmtpClient> sınıfının <xref:System.Net.Mail.SmtpClient.ClientCertificates%2A> özelliği ile ilişkili bir bir örneğidir. <xref:System.Net.HttpWebRequest> Sınıfın benzer<xref:System.Net.HttpWebRequest.ClientCertificates%2A> bir özelliği vardır.  
  
 Ve sınıfı arasındaki birincil fark, özel anahtarın <xref:System.Security.Cryptography.X509Certificates.X509Certificate> sınıf için sertifika deposunda bulunması gerektiğidir. <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> <xref:System.Security.Cryptography.X509Certificates.X509Certificate>  
  
 Sertifikalar bir koleksiyona eklenmiş ve belirli bir SSL bağlantısıyla ilişkili olsa da, sunucu tarafından istekte yoksa sunucuya sertifika gönderilmez. Bağlantıda birden çok istemci sertifikası ayarlandıysa, sunucu tarafından sunulan sertifika verenler ve istemci sertifikası verenin adı arasındaki eşleşmeyi dikkate alan bir algoritmaya göre en iyi yöntem kullanılır.  
  
 <xref:System.Net.Security.SslStream> Sınıfı, SSL el sıkışması üzerinde daha fazla denetim sağlar. İstemci, hangi istemci sertifikasını kullanacağınızı seçmek için bir temsilci belirtebilir.  
  
 Uzak bir sunucu, bir istemci sertifikasının geçerli, geçerli ve uygun sertifika yetkilisi tarafından imzalanmış olduğunu doğrulayabilirler. Sertifika doğrulamasını zorlamak <xref:System.Net.ServicePointManager.ServerCertificateValidationCallback%2A> için öğesine bir temsilci eklenebilir.  
  
## <a name="client-certificate-selection"></a>İstemci sertifikası seçimi  
 .NET Framework sunucuya aşağıdaki şekilde sunmak için istemci sertifikasını seçer:  
  
1. İstemci sertifikası önceden sunucuya sunulursa, ilk sunulursa sertifika önbelleğe alınır ve sonraki istemci sertifikası istekleri için yeniden kullanılır.  
  
2. Bir temsilci mevcutsa, her zaman, seçilecek istemci sertifikası olarak temsilciden sonucu kullanın. Mümkün olduğunda önbelleğe alınmış bir sertifika kullanmayı deneyin, ancak temsilci null döndürdüğünden ve sertifika koleksiyonu boş değilse önbelleğe alınmış anonim kimlik bilgilerini kullanmayın.  
  
3. Bu, bir istemci sertifikası için ilk zorluk söz konusu ise Framework, içindeki <xref:System.Security.Cryptography.X509Certificates.X509Certificate> sertifikaları <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> veya bağlantı ile ilişkili sınıf nesnelerini numaralandırır ve bu, tarafından sunulan sertifika verenler listesi arasında bir eşleşme arar. sunucu ve istemci sertifikası verenin adı. Eşleşen ilk sertifika sunucusuna gönderilir. Bir sertifika eşleşmesi veya sertifika koleksiyonu boşsa, sunucuya bir anonim kimlik bilgisi gönderilir.  
  
## <a name="tools-for-certificate-configuration"></a>Sertifika yapılandırması için Araçlar  
 İstemci ve sunucu sertifikası yapılandırması için bir dizi araç vardır.  
  
 *WinHttpCertCfg. exe* Aracı, istemci sertifikalarını yapılandırmak için kullanılabilir. *WinHttpCertCfg. exe* Aracı, Windows Server 2003 Resource Kit ile araçlardan biri olarak sağlanır. Bu araç, [www.Microsoft.com](https://www.microsoft.com)adresindeki Windows Server 2003 Resource Kit araçlarının bir parçası olarak da indirilebilir.  
  
*Httpcfg. exe* Aracı, <xref:System.Net.HttpListener> sınıf için sunucu sertifikalarını yapılandırmak üzere kullanılabilir. *Httpcfg. exe* Aracı, windows Server 2003 ve Windows XP Service Pack 2 için destek araçlarından biri olarak sağlanır. *Httpcfg. exe* ve diğer destek araçları, windows Server 2003 veya Windows XP 'de varsayılan olarak yüklenmez. Windows Server 2003 ' de. Destek Araçları, Windows Server 2003 CD-ROM ' da aşağıdaki klasörden ve dosyadan ayrı olarak yüklenir:  
  
 \Support\Tools\Suptools.msi  
  
 Windows XP Service Pack 2 ile kullanım için Windows XP destek araçları, [www.Microsoft.com](https://www.microsoft.com)adresinden bir indirme olarak sunulmaktadır.  
  
 *Httpcfg. exe* aracının bir sürümüne kaynak kodu, WINDOWS Server SDK ile örnek olarak da sağlanır. *Httpcfg. exe* örneğine yönelik kaynak kodu, varsayılan olarak, aşağıdaki klasör altındaki Windows SDK bir parçası olarak ağ örneklerine yüklenir:  
  
 *C:\Program Files\Microsoft SDKs\Windows\v1.0\Samples\NetDS\http\serviceconfig*  
  
 Bu araçlara <xref:System.Security.Cryptography.X509Certificates.X509Certificate> ek olarak, ve <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> sınıfları dosya sisteminden bir sertifika yüklemek için yöntemler sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ağ Programlama Güvenliği](security-in-network-programming.md)
- [.NET Framework'te Ağ Programlaması](index.md)
