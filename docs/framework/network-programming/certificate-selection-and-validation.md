---
title: Sertifika seçimi ve doğrulama
ms.date: 03/30/2017
ms.assetid: c933aca2-4cd0-4ff1-9df9-267143f25a6f
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: fe3b10e17c3cdf181f0b33b4305008655047fb0f
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45590701"
---
# <a name="certificate-selection-and-validation"></a>Sertifika seçimi ve doğrulama
<xref:System.Net> Sınıfları seçin ve doğrulamak için birkaç yol destekler <xref:System.Security.Cryptography.X509Certificates> Güvenli Yuva Katmanı (SSL) bağlantıları için. Bir istemci, kendisi için bir sunucu kimliğini doğrulamak için bir veya daha fazla sertifikaları seçebilirsiniz. Bir istemci sertifikası kimlik doğrulaması için bir veya daha fazla belirli özniteliklere sahip bir sunucu gerektirebilir.  
  
## <a name="definition"></a>Tanım  
 Bir ortak anahtar, (örneğin, sürüm numarası, seri numarası ve sona erme tarihi) özniteliklerini ve bir sertifika yetkilisinden bir dijital imza içeren bir ASCII bayt akışı bir sertifikadır. Şifreli bir bağlantı kurmak için veya bir sunucu için istemci kimlik doğrulaması için sertifikalar kullanılır.  
  
## <a name="client-certificate-selection-and-validation"></a>İstemci sertifika seçimi ve doğrulama  
 Bir istemci belirli bir SSL bağlantısı için bir veya daha fazla sertifikalar seçebilirsiniz. İstemci sertifikaları, bir web sunucusu veya bir SMTP posta sunucusunu SSL bağlantı ile ilişkili olabilir. Bir istemci sertifikaları koleksiyonuna ekler. <xref:System.Security.Cryptography.X509Certificates.X509Certificate> veya <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> sınıf nesneleri. Örneğin e-posta kullanarak sertifika koleksiyonunu örneğidir bir <xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection>) ile ilişkili <xref:System.Net.Mail.SmtpClient.ClientCertificates%2A> özelliği <xref:System.Net.Mail.SmtpClient> sınıfı. <xref:System.Net.HttpWebRequest> Sınıfında benzer <xref:System.Net.HttpWebRequest.ClientCertificates%2A> özelliği.  
  
 Arasındaki birincil fark <xref:System.Security.Cryptography.X509Certificates.X509Certificate> ve <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> sınıfı, özel anahtarı için sertifika deposunda bulunmalıdır <xref:System.Security.Cryptography.X509Certificates.X509Certificate> sınıfı.  
  
 Sertifikaları bir koleksiyona eklenmiş ve belirli bir SSL bağlantı ile ilişkili bile, bunları sunucu istekleri sürece hiçbir sertifika sunucuya gönderilir. Bir bağlantıda birden fazla istemci sertifikası ayarlarsanız, sunucu ve istemci sertifika verenin adı tarafından sağlanan sertifika verenler listesi arasında bir eşleşme olarak değerlendirir bir algoritma kullanılacak olan en iyi temel.  
  
 <xref:System.Net.Security.SslStream> Sınıfı SSL el sıkışması üzerinde daha fazla denetim sağlar. Bir istemci kullanmak için hangi istemci sertifikasını seçmek için bir temsilci belirtebilirsiniz.  
  
 Uzak bir sunucuya bir istemci sertifikası geçerli, geçerli ve uygun sertifika yetkilisi tarafından imzalanmış olduğunu doğrulayabilirsiniz. Bir temsilci eklenebilir <xref:System.Net.ServicePointManager.ServerCertificateValidationCallback%2A> sertifika doğrulamasını zorunlu kılmak için.  
  
## <a name="client-certificate-selection"></a>İstemci sertifika seçimi  
 .NET Framework sunucuya aşağıdaki şekilde sunmak için istemci sertifikası seçer:  
  
1.  Bir istemci sertifikası, daha önce sunucuya gösterilen, sertifikayı ilk sunulduğunda ve sonraki istemci sertifika istekleri için tekrar önbelleğe alınır.  
  
2.  Her zaman bir temsilci varsa, sonuç temsilci seçmek için istemci sertifikası olarak kullanın. Mümkün olduğunda önbelleğe alınan bir sertifika kullanmayı denediğinizde, ancak önbelleğe alınmış anonim kimlik bilgileri temsilcisi null döndürdü ve sertifika koleksiyonunu boş değilse kullanmayın.  
  
3.  Bir istemci sertifikası için ilk testten buysa, Framework sertifikaları numaralandırır <xref:System.Security.Cryptography.X509Certificates.X509Certificate> veya <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> sınıfı tarafından sağlanan sertifika verenler listesi arasında bir eşleşme aranıyor bağlantıyla ilişkili nesneleri Sunucu ve istemci sertifika verenin adı. Eşleşen ilk sertifikayı sunucuya gönderilir. Sertifika eşleşme yok ya da sertifika koleksiyonu boş sonra anonim bir kimlik bilgisi sunucuya gönderilir.  
  
## <a name="tools-for-certificate-configuration"></a>Sertifika yapılandırması için Araçlar  
 Araçlar, istemci ve sunucu sertifika yapılandırması için kullanılabilir.  
  
 *Winhttpcertcfg.exe* aracı, istemci sertifikaları yapılandırmak için kullanılabilir. *Winhttpcertcfg.exe* aracı, Windows Server 2003 Resource Kit'teki araçlarıyla biri olarak sağlanır. Bu araç ayrıca Windows Server 2003 Kaynak Seti Araçları bir parçası olarak bir indirme olarak kullanılabilir [www.microsoft.com](https://www.microsoft.com).  
  
*HttpCfg.exe* aracı için sunucu sertifikaları yapılandırmak için kullanılabilir <xref:System.Net.HttpListener> sınıfı. *HttpCfg.exe* aracı sağlanan destek araçlarından biri olarak Windows Server 2003 ve Windows XP Service Pack 2 '. *HttpCfg.exe* ve diğer destek araçları Windows Server 2003 veya Windows XP üzerinde varsayılan olarak yüklenmez. Windows Server 2003'te. Destek Araçları'nı aşağıdaki klasör ve dosya Windows Server 2003 CD-ROM üzerinde ayrı olarak yüklenir:  
  
 \Support\Tools\Suptools.msi  
  
 Windows XP Service Pack 2 ile kullanım için Windows XP Destek Araçları'nı yükleme yoluyla kullanılabilir [www.microsoft.com](https://www.microsoft.com).  
  
 Kaynak kodu bir sürümüne *HttpCfg.exe* aracı Windows Server SDK'sı ile bir örnek olarak da sağlanır. Kaynak koduna *HttpCfg.exe* örnek yüklü ağ örnekleri ile varsayılan olarak şu klasörü altında Windows SDK'ın bir parçası olarak:  
  
 *C:\Program Files\Microsoft SDKs\Windows\v1.0\Samples\NetDS\http\serviceconfig*  
  
 Bu araçların yanı sıra <xref:System.Security.Cryptography.X509Certificates.X509Certificate> ve <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> sınıfları dosya sisteminden bir sertifika yüklemek için yöntemler sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ağ Programlama Güvenliği](../../../docs/framework/network-programming/security-in-network-programming.md)  
 [.NET Framework'te Ağ Programlaması](../../../docs/framework/network-programming/index.md)
