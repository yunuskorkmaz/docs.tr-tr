---
title: "Sertifika seçimi ve doğrulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c933aca2-4cd0-4ff1-9df9-267143f25a6f
caps.latest.revision: "15"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: db75c3288b8247f0717c4792c57bfb30bb2e4416
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="certificate-selection-and-validation"></a>Sertifika seçimi ve doğrulama
<xref:System.Net> Sınıflarını destekleyen seçin ve doğrulamak için çeşitli yollar <xref:System.Security.Cryptography.X509Certificates> Güvenli Yuva Katmanı (SSL) bağlantıları için. Bir istemci, kendisi için bir sunucu kimliğini doğrulamak için bir veya daha fazla sertifikaları seçebilirsiniz. Bir istemci sertifikası kimlik doğrulaması için bir veya daha fazla özel özniteliklere sahip bir sunucu gerektirebilir.  
  
## <a name="definition"></a>Tanım  
 Bir sertifika bir ortak anahtar, (örneğin, sürüm numarası, seri numarası ve sona erme tarihi) özniteliklerini ve bir sertifika yetkilisinden bir dijital imza içeren bir ASCII bayt akışıdır. Sertifikalar, şifreli bir bağlantı kurmak için veya bir sunucu için istemci kimlik doğrulaması için kullanılır.  
  
## <a name="client-certificate-selection-and-validation"></a>İstemci sertifika seçimi ve doğrulama  
 Bir istemci belirli bir SSL bağlantısı için bir veya daha fazla sertifikalar seçebilirsiniz. İstemci sertifikalarını bir web sunucusuna veya bir SMTP posta sunucusu SSL bağlantısı ile ilişkili olabilir. Bir istemci sertifikaları koleksiyonuna ekler <xref:System.Security.Cryptography.X509Certificates.X509Certificate> veya <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> sınıfının nesneleri. E-posta bir örnek olarak kullanarak, sertifika koleksiyonunu örneği olan bir <xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection>) ile ilişkili <xref:System.Net.Mail.SmtpClient.ClientCertificates%2A> özelliği <xref:System.Net.Mail.SmtpClient> sınıfı. <xref:System.Net.HttpWebRequest> Sınıfına sahip bir benzer <xref:System.Net.HttpWebRequest.ClientCertificates%2A> özelliği.  
  
 Arasındaki birincil fark <xref:System.Security.Cryptography.X509Certificates.X509Certificate> ve <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> sınıfı, özel anahtarı için sertifika deposunda bulunmalıdır <xref:System.Security.Cryptography.X509Certificates.X509Certificate> sınıfı.  
  
 Sertifikalar bir koleksiyona eklenmesi ve belirli bir SSL bağlantı ile ilişkili olsa bile, sunucunun bunları istemedikçe hiçbir sertifika sunucuya gönderilir. Birden çok istemci sertifikalarını bir bağlantıda ayarlarsanız, kullanılacak olan en iyi eşleşme sunucu ve istemci sertifika verenin adı tarafından sağlanan sertifika verenler listesi arasında göz önünde bulundurur bir algoritma temel.  
  
 <xref:System.Net.Security.SslStream> Sınıfı, SSL el sıkışması üzerinde daha fazla denetim sağlar. Bir istemci kullanmak için hangi istemci sertifikasını almak için temsilci belirleyebilirsiniz.  
  
 Uzak bir sunucuya bir istemci sertifikası geçerli, geçerli ve uygun sertifika yetkilisi tarafından imzalanmış olduğunu doğrulayabilirsiniz. Bir temsilci eklenebilir <xref:System.Net.ServicePointManager.ServerCertificateValidationCallback%2A> sertifika doğrulaması zorlamak için.  
  
## <a name="client-certificate-selection"></a>İstemci sertifika seçimi  
 .NET Framework sunucuya aşağıdaki şekilde sunmak için istemci sertifikası seçer:  
  
1.  Sunucuya bir istemci sertifikası önceden sunulan, sertifikayı ilk sunulduğunda ve sonraki istemci sertifikası istekleri için tekrar önbelleğe alınır.  
  
2.  Her zaman bir temsilci varsa, temsilci sonucundan seçmek için istemci sertifikası olarak kullanın. Mümkün olduğunda önbelleğe alınan bir sertifika kullanmayı deneyin, ancak önbelleğe alınmış anonim kimlik temsilcisi null döndürdü ve sertifika koleksiyonu boş değilse kullanmayın.  
  
3.  Bir istemci sertifikası için ilk sınaması varsa Framework sertifikaları numaralandırır <xref:System.Security.Cryptography.X509Certificates.X509Certificate> veya <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> sınıfı tarafından sağlanan sertifika verenler listesi arasında bir eşleşme aramak bağlantıyla ilişkili nesneler Sunucu ve istemci sertifikası veren adı. Eşleşen ilk sertifika sunucuya gönderilir. Herhangi bir sertifika eşleşme ya da sertifika koleksiyonu boş sonra anonim bir kimlik bilgisi sunucuya gönderilir.  
  
## <a name="tools-for-certificate-configuration"></a>Sertifika yapılandırması için araçları  
 Çok sayıda araç, istemci ve sunucu sertifikası yapılandırması için kullanılabilir.  
  
 *Winhttpcertcfg.exe* aracı, istemci sertifikalarını yapılandırmak için kullanılabilir. *Winhttpcertcfg.exe* aracı, Windows Server 2003 Resource Kit'teki araçlarıyla biri olarak sağlanır. Bu araç, www.microsoft.com Windows Server 2003 Kaynak Seti Araçları'nın bir parçası olarak bir yükleme olarak da kullanılabilir.  
  
 *HttpCfg.exe* aracı, sunucu sertifikalarını yapılandırmak için kullanılabilir <xref:System.Net.HttpListener> sınıfı. *HttpCfg.exe* aracı sağlanır Destek Araçları biri olarak Windows Server 2003 ve Windows XP Service Pack 2. *HttpCfg.exe* ve diğer destek araçları, Windows Server 2003 veya Windows XP üzerinde varsayılan olarak yüklenmez. Windows Server 2003'te. Destek Araçları'nı, ayrıca aşağıdaki klasörü ve Windows Server 2003 CD-ROM dosyada yüklenir:  
  
 \Support\Tools\Suptools.msi  
  
 Windows XP Service Pack 2 ile kullanmak için Windows XP Destek Araçları www.microsoft.com adresinden indirilebilir öğe olarak kullanılabilir.  
  
 Kaynak kodu bir sürümüne *HttpCfg.exe* aracı örnek Windows Server SDK'sı olarak da sağlanır. Kaynak koduna *HttpCfg.exe* örnek yüklü ağ örnekleri varsayılan olarak şu klasörü altında Windows SDK'ın bir parçası olarak:  
  
 *C:\Program Files\Microsoft SDKs\Windows\v1.0\Samples\NetDS\http\serviceconfig*  
  
 Bu araçları yanı sıra <xref:System.Security.Cryptography.X509Certificates.X509Certificate> ve <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> sınıfları dosya sisteminden bir sertifika yüklemek için yöntemler sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenlik ağ programlama](../../../docs/framework/network-programming/security-in-network-programming.md)  
 [.NET Framework'te ağ programlaması](../../../docs/framework/network-programming/index.md)
