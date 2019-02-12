---
title: Bağlantı bilgilerini koruma
ms.date: 03/30/2017
ms.assetid: 1471f580-bcd4-4046-bdaf-d2541ecda2f4
ms.openlocfilehash: 4c8992abc30690be8e9ef9c208b0a0bd3ddf6116
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56091961"
---
# <a name="protecting-connection-information"></a>Bağlantı bilgilerini koruma
Veri kaynağı erişimi korumaya en önemli hedeflerinden bir uygulamanın güvenliğini sağlama andır. Güvenli olmayan, bir bağlantı dizesi olası bir güvenlik açığı sunar. Bağlantı bilgilerini düz metin halinde depolanmasını veya sisteminizin ödün bellek riskleri kalıcı. Bağlantı dizeleri gömülü kaynak kodunuzu kullanarak okunabilir [Ildasm.exe (IL ayrıştırıcı)](../../../../docs/framework/tools/ildasm-exe-il-disassembler.md) derlenmiş derlemede Microsoft Ara dilini (MSIL) görüntülemek için.  
  
 Kimlik doğrulama türüne göre güvenlik açıklarını içeren bağlantı dizeleri ortaya çıkabilecek bellek ve disk ve bunları çalışma zamanında oluşturmak için kullanılan teknikleri bağlantı dizeleri nasıl kalıcı kullanılır.  
  
## <a name="use-windows-authentication"></a>Windows kimlik doğrulaması kullan  
 Erişimi sınırlamaya yardımcı olması için veri kaynağı, bağlantı bilgilerini kullanıcı Kimliğinizi, parolanızı ve veri kaynağı adı gibi güvenlik altına almanız gerekir. Kullanıcı bilgilerinin kullanılmasını önlemek için Windows kimlik doğrulaması kullanmanızı öneririz (bazen denir *tümleşik güvenliği*) mümkün olan her yerde. Windows kimlik doğrulaması kullanarak bir bağlantı dizesinde belirtilir `Integrated Security` veya `Trusted_Connection` anahtar sözcükler, bir kullanıcı kimliği ve parola kullanma gereksinimini ortadan kaldırır. Windows kimlik doğrulaması kullanırken, kullanıcılar tarafından Windows kimlik doğrulaması ve erişim sunucusu ve veritabanı kaynaklarını Windows kullanıcılarına ve gruplarına izinler verme tarafından belirlenir.  
  
 Burada Windows kimlik doğrulaması kullanmak mümkün olmadığı durumlar için kullanıcı kimlik bilgileri bağlantı dizesinde açık olduğundan çok dikkatli kullanmanız gerekir. Bir ASP.NET uygulamasında, veritabanları ve diğer ağ kaynaklarına bağlanmak için kullanılan sabit bir kimlik olarak bir Windows hesabı yapılandırabilirsiniz. Kimliğe bürünme kimlik öğesinde, etkinleştirme **web.config** dosyası ve bir kullanıcı adı ve parola belirtin.  
  
```xml  
<identity impersonate="true"   
        userName="MyDomain\UserAccount"   
        password="*****" />  
```  
  
 Sabit kimlik hesap veritabanında yalnızca gerekli izinleri verilmiş olan düşük ayrıcalıklı bir hesap olmalıdır. Ayrıca, yapılandırma dosyası şifreleyin, böylece kullanıcı adı ve parola düz metin olarak açık değildir.  
  
## <a name="do-not-use-universal-data-link-udl-files"></a>Değil kullanım evrensel veri bağlantısı (UDL) dosyaları  
 İçin bağlantı dizelerini depolanmasını önlemek bir <xref:System.Data.OleDb.OleDbConnection> evrensel veri bağlantısı (UDL) dosyasında. Udl'ler düz metin olarak depolanır ve şifrelenemez. Uygulamanız için bir dış dosya tabanlı kaynak UDL dosyası olduğunu ve korunamıyor veya .NET Framework kullanılarak şifrelenir.  
  
## <a name="avoid-injection-attacks-with-connection-string-builders"></a>Bağlantı dizesi oluşturucular ile ekleme saldırılarını kaçının  
 Dinamik dize birleştirme kullanıcı girişini temel alarak bağlantı dizeleri oluşturmak için kullanılan bir bağlantı dizesi ekleme saldırısına oluşabilir. Kullanıcı girişini doğrulanmış ve kötü amaçlı bir metin veya kaçış karakteri değil ise, bir saldırganın hassas verileri veya sunucudaki diğer kaynakları içeriklerine erişebilir. Bu sorunu gidermek için bağlantı dizesi söz dizimi doğrulamak ve ek parametreler değil sunulan emin olmak için yeni bağlantı dizesi Oluşturucusu sınıflar ADO.NET 2.0 kullanılmaya başlandı. Daha fazla bilgi için [bağlantı dizesi oluşturucular](../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
## <a name="use-persist-security-infofalse"></a>Kalıcı güvenlik bilgisi kullan = False  
 İçin varsayılan değer `Persist Security Info` yanlış; bu varsayılan tüm bağlantı dizeleri kullanmanızı öneririz. Ayarı `Persist Security Info` için `true` veya `yes` , açıldıktan sonra bir bağlantıdan alınacağı kullanıcı kimliği ve parola gibi güvenlik bakımından hassas bilgiler sağlar. Zaman `Persist Security Info` ayarlanır `false` veya `no`, güvenilmeyen bir kaynağa güvenlik bakımından hassas bilgilere erişimi yok sağlayarak bu bağlantıyı açmak için kullanılan sonra güvenlik bilgileri atılır.  
  
## <a name="encrypt-configuration-files"></a>Yapılandırma dosyaları şifreleyin  
 Da bağlantı dizelerini yapılandırma dosyalarında, uygulamanızın kodunda eklemek gereğini ortadan kaldırır depolayabilirsiniz. Yapılandırma dosyaları .NET Framework, ortak bir öğe kümesini tanımladığı standart XML dosyalarıdır. Bağlantı dizelerini yapılandırma dosyaları içinde depolanan genellikle  **\<connectionStrings >** öğesinde **app.config** bir Windows uygulaması için veya  **Web.config** ASP.NET uygulaması için dosya. Alma ve yapılandırma dosyaları, bağlantı dizeleri şifreleme depolamak temelleri hakkında daha fazla bilgi için bkz: [bağlantı dizeleri ve yapılandırma dosyalarını](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [Şifreleme yapılandırma bilgilerini kullanarak korumalı yapılandırma](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100))
- [.NET içinde güvenlik](../../../standard/security/index.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
