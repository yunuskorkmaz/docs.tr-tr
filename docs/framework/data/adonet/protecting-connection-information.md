---
title: Bağlantı Bilgilerini Koruma
ms.date: 03/30/2017
ms.assetid: 1471f580-bcd4-4046-bdaf-d2541ecda2f4
ms.openlocfilehash: 1039d3fd797a16391876b59aa018b30b7f397aeb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149225"
---
# <a name="protecting-connection-information"></a>Bağlantı Bilgilerini Koruma
Veri kaynağınıza erişimi korumak, bir uygulamayı güvence altına alırken en önemli hedeflerden biridir. Bağlantı dizesi güvenli değilse olası bir güvenlik açığı sunar. Bağlantı bilgilerini düz metinde depolamak veya bellekte kalıcı hale almak tüm sisteminizi tehlikeye atayabIlmektedir. Kaynak kodunuza katıştırılmış bağlantı dizeleri, Microsoft ara dilini (MSIL) derlenmiş bir derlemede görüntülemek için [Ildasm.exe (IL Disassembler)](../../tools/ildasm-exe-il-disassembler.md) kullanılarak okunabilir.  
  
 Bağlantı dizeleri içeren güvenlik açıkları, kullanılan kimlik doğrulama türüne, bağlantı dizelerinin bellekte ve diskte nasıl kalıcı olduğuna ve bunları çalışma zamanında oluşturmak için kullanılan tekniklere bağlı olarak ortaya çıkabilir.  
  
## <a name="use-windows-authentication"></a>Windows Kimlik Doğrulaması kullan  
 Veri kaynağınıza erişimi sınırlamaya yardımcı olmak için, kullanıcı kimliği, parola ve veri kaynağı adı gibi bağlantı bilgilerini korumanız gerekir. Kullanıcı bilgilerinin açığa çıkarılmasını önlemek için, mümkün olan her yerde Windows kimlik doğrulaması (bazen *tümleşik güvenlik*olarak da adlandırılır) kullanmanızı öneririz. Windows kimlik doğrulaması, kullanıcı kimliği `Integrated Security` ve `Trusted_Connection` parola kullanma gereksinimini ortadan kaldırarak, anahtar kelimeleri veya anahtar kelimeleri kullanarak bir bağlantı dizesi içinde belirtilir. Windows kimlik doğrulaması kullanırken, kullanıcılar Windows tarafından kimlik doğrulaması yapılır ve sunucu ve veritabanı kaynaklarına erişim, Windows kullanıcılarına ve gruplarına izin vererek belirlenir.  
  
 Windows kimlik doğrulamasını kullanmanın mümkün olmadığı durumlarda, kullanıcı kimlik bilgileri bağlantı dizesinde açıkolduğundan ek dikkat kullanmanız gerekir. Bir ASP.NET uygulamasında, bir Windows hesabını veritabanlarına ve diğer ağ kaynaklarına bağlanmak için kullanılan sabit bir kimlik olarak yapılandırabilirsiniz. **web.config** dosyasındaki kimlik öğesinde kimliğe bürünme olanağı sağlar ve bir kullanıcı adı ve parola belirtirsiniz.  
  
```xml  
<identity impersonate="true"
        userName="MyDomain\UserAccount"
        password="*****" />  
```  
  
 Sabit kimlik hesabı, veritabanında yalnızca gerekli izinler verilmiş düşük ayrıcalıklı bir hesap olmalıdır. Ayrıca, kullanıcı adı ve parolanın açık metinolarak açık lanmaması için yapılandırma dosyasını şifrelemeniz gerekir.  
  
## <a name="do-not-use-universal-data-link-udl-files"></a>Evrensel Veri Bağlantısı (UDL) dosyalarını kullanmayın  
 Evrensel Veri Bağlantısı (UDL) dosyasında bağlantı <xref:System.Data.OleDb.OleDbConnection> dizeleri depolamaktan kaçının. UDL'ler açık metinde depolanır ve şifrelenemez. UDL dosyası, uygulamanız için harici bir dosya tabanlı kaynaktır ve .NET Framework kullanılarak güvenli veya şifrelenemez.  
  
## <a name="avoid-injection-attacks-with-connection-string-builders"></a>Bağlantı String Üreticileri ile Enjeksiyon Saldırıları kaçının  
 Dinamik dize concatenation kullanıcı girişine dayalı bağlantı dizeleri oluşturmak için kullanıldığında bir bağlantı dize enjeksiyon saldırısı oluşabilir. Kullanıcı girişi doğrulanmadıysa ve kötü amaçlı metin veya karakterler kaçmazsa, saldırgan hassas verilere veya sunucudaki diğer kaynaklara erişebilir. Bu sorunu gidermek için, ADO.NET 2.0 bağlantı dize sözdizimini doğrulamak ve ek parametrelerin kullanılmadığından emin olmak için yeni bağlantı dize oluşturucu sınıfları tanıttı. Daha fazla bilgi için [Bağlantı Dize Oluşturucuları'na](connection-string-builders.md)bakın.  
  
## <a name="use-persist-security-infofalse"></a>Kalıcı Güvenlik Bilgilerini Kullan=Yanlış  
 Varsayılan değer `Persist Security Info` yanlıştır; tüm bağlantı dizelerinde bu varsayılanı kullanmanızı öneririz. Kullanıcı kimliği `yes` ve parola da dahil olmak üzere güvenliğe duyarlı bilgilerin, `Persist Security Info` açıldıktan sonra bir bağlantıdan alınmasına izin verir veya ayarlama. `true` Ne `Persist Security Info` zaman `false` ayarlanır `no`veya, güvenlik bilgileri, güvenilmeyen bir kaynağın güvenliğe duyarlı bilgilere erişimi olmamasını sağlayarak bağlantıyı açmak için kullanıldıktan sonra atılır.  
  
## <a name="encrypt-configuration-files"></a>Yapılandırma Dosyalarını Şifreleme  
 Bağlantı dizelerini yapılandırma dosyalarında da depolayabilirsiniz ve bu da bunları uygulamanızın koduna yerleştirme gereksinimini ortadan kaldırır. Yapılandırma dosyaları, .NET Framework'ün ortak bir öğe kümesi tanımladığı standart XML dosyalarıdır. Yapılandırma dosyalarındaki bağlantı dizeleri genellikle ** \<bir** Windows uygulaması için **app.config** veya ASP.NET bir uygulama için **web.config** dosyasında bağlantıStrings>öğesi içinde saklanır. Bağlantı dizelerini yapılandırma dosyalarından depolama, alma ve şifreleme temelleri hakkında daha fazla bilgi için [Bağlantı Dizeleri ve Yapılandırma Dosyaları](connection-strings-and-configuration-files.md)bölümüne bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](securing-ado-net-applications.md)
- [Korumalı Yapılandırmayı Kullanarak Yapılandırma Bilgilerini Şifreleme](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100))
- [.NET içinde güvenlik](../../../standard/security/index.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
