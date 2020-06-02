---
title: Bağlantı Bilgilerini Koruma
description: Bağlantı dizelerindeki güvenlik açıkları hakkında bilgi edinin. Bu, bağlantı dizelerinin oluşturulması ve kalıcı olması ve kimlik doğrulama türü nedeniyle ortaya çıkabilir.
ms.date: 03/30/2017
ms.assetid: 1471f580-bcd4-4046-bdaf-d2541ecda2f4
ms.openlocfilehash: 0e693fd99384a2808a621b358f8e70c6777c3930
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286656"
---
# <a name="protecting-connection-information"></a>Bağlantı Bilgilerini Koruma
Veri kaynağınıza erişimi korumak, bir uygulamayı güvenli hale getirirken en önemli amaçlardan biridir. Bir bağlantı dizesi güvenli değilse olası bir güvenlik açığı sunar. Bağlantı bilgilerini düz metin olarak depolama veya sisteminizin tamamında güvenliği ihlal eden bellek risklerini kalıcı hale getirme. Kaynak kodunuzda gömülü bağlantı dizeleri, derlenmiş bir derlemede Microsoft ara dili 'ni (MSIL) görüntülemek için [ıldadsm. exe (IL Disassembler)](../../tools/ildasm-exe-il-disassembler.md) kullanılarak okunabilir.  
  
 Bağlantı dizelerini içeren güvenlik açıkları, kullanılan kimlik doğrulaması türüne, bağlantı dizelerine bellekte ve diskte nasıl kalıcı hale getirilir ve çalışma zamanında bunları oluşturmak için kullanılan teknikleri temel alınarak ortaya çıkabilir.  
  
## <a name="use-windows-authentication"></a>Windows Kimlik Doğrulaması kullan  
 Veri kaynağınıza erişimi sınırlamaya yardımcı olması için, Kullanıcı KIMLIĞI, parola ve veri kaynağı adı gibi bağlantı bilgilerini güvenli hale getirin. Kullanıcı bilgilerini açığa çıkarmamak için, mümkün olan yerlerde Windows kimlik doğrulaması (bazen *Tümleşik güvenlik*olarak adlandırılır) kullanmanızı öneririz. Windows kimlik doğrulaması, veya anahtar kelimeleri kullanılarak bir bağlantı dizesinde `Integrated Security` belirtilir `Trusted_Connection` ve Kullanıcı kimliği ve parola kullanma gereksinimini ortadan kaldırır. Windows kimlik doğrulaması kullanılırken, kullanıcıların kimliği Windows tarafından doğrulanır ve sunucu ve veritabanı kaynaklarına erişim, Windows kullanıcıları ve grupları için izinler verilerek belirlenir.  
  
 Windows kimlik doğrulamasının kullanılması mümkün olmadığı durumlarda, bağlantı dizesinde kullanıcı kimlik bilgileri sunulduğundan, ek dikkatli olmanız gerekir. Bir ASP.NET uygulamasında, bir Windows hesabını veritabanlarına ve diğer ağ kaynaklarına bağlanmak için kullanılan bir sabit kimlik olarak yapılandırabilirsiniz. **Web. config** dosyasındaki kimlik öğesinde kimliğe bürünme özelliğini etkinleştirin ve bir Kullanıcı adı ve parola belirtin.  
  
```xml  
<identity impersonate="true"
        userName="MyDomain\UserAccount"
        password="*****" />  
```  
  
 Sabit kimlik hesabı, veritabanında yalnızca gerekli izinlere izin verilen düşük ayrıcalıklı bir hesap olmalıdır. Ayrıca, Kullanıcı adı ve parolanın şifresiz metin olarak gösterilmemesi için yapılandırma dosyasını şifrelemeniz gerekir.  
  
## <a name="do-not-use-universal-data-link-udl-files"></a>Evrensel veri bağlantısı (UDL) dosyalarını kullanma  
 Bir <xref:System.Data.OleDb.OleDbConnection> evrensel veri bağlantısı (UDL) dosyasında bir için bağlantı dizelerini saklamaktan kaçının. UDLs 'ler şifresiz metin halinde depolanır ve şifrelenemez. Bir UDL dosyası, uygulamanıza yönelik harici dosya tabanlı bir kaynaktır ve .NET Framework kullanılarak güvenli veya şifreli olamaz.  
  
## <a name="avoid-injection-attacks-with-connection-string-builders"></a>Bağlantı dizesi oluşturucuları ile ekleme saldırılarına karşı kaçının  
 Bir bağlantı dizesi ekleme saldırısı, kullanıcı girişine göre bağlantı dizeleri oluşturmak için dinamik dize birleştirme kullanıldığında meydana gelebilir. Kullanıcı girişi doğrulanmaz ve kötü amaçlı metin veya karakterler kaçmaz, bir saldırgan sunucudaki hassas verilere veya diğer kaynaklara erişebilir. Bu sorunu gidermek için, ADO.NET 2,0 bağlantı dizesi sözdizimini doğrulamak üzere yeni bağlantı dizesi Oluşturucu sınıfları sunmuştur ve ek parametrelerin tanıtılmadığından emin olun. Daha fazla bilgi için bkz. [bağlantı dizesi oluşturucuları](connection-string-builders.md).  
  
## <a name="use-persist-security-infofalse"></a>Kalıcı güvenlik bilgilerini kullan = yanlış  
 İçin varsayılan değer `Persist Security Info` false 'dur; bu varsayılanı tüm bağlantı dizelerinde kullanmanızı öneririz. `Persist Security Info` `true` `yes` Kullanıcı kimliği ve parola dahil olmak üzere güvenliğe duyarlı bilgilerin, açıldıktan sonra bir bağlantıdan alınabilmesi için ayarını yapın veya buna izin verir. `Persist Security Info`Veya olarak ayarlandığında `false` `no` , güvenlik bilgileri bağlantıyı açmak için kullanıldıktan sonra atılır ve bu, güvenilmeyen bir kaynağın güvenlik duyarlı bilgilere erişiminin olmadığından emin olur.  
  
## <a name="encrypt-configuration-files"></a>Yapılandırma dosyalarını şifreleme  
 Ayrıca, bağlantı dizelerini uygulamanızın koduna ekleme gereksinimini ortadan kaldıran yapılandırma dosyalarında da saklayabilirsiniz. Yapılandırma dosyaları, .NET Framework ortak bir öğe kümesini tanımladığı standart XML dosyalarıdır. Yapılandırma dosyalarındaki bağlantı dizeleri, genellikle bir **\<connectionStrings>** Windows uygulaması için **app. config** içinde veya bir ASP.NET uygulamasının **Web. config** dosyasında bulunan öğesinin içinde depolanır. Yapılandırma dosyalarından bağlantı dizelerini depolama, alma ve şifreleme hakkında daha fazla bilgi için bkz. [bağlantı dizeleri ve yapılandırma dosyaları](connection-strings-and-configuration-files.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](securing-ado-net-applications.md)
- [Korumalı yapılandırma kullanarak yapılandırma bilgilerini şifreleme](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100))
- [.NET içinde güvenlik](../../../standard/security/index.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
