---
title: "Bağlantı bilgileri koruma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1471f580-bcd4-4046-bdaf-d2541ecda2f4
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 31196697a606b3edbc0b3aa00b01e5eacb66cb03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="protecting-connection-information"></a>Bağlantı bilgileri koruma
Veri kaynağınıza erişimi korumaya yönelik en önemli hedeflerini uygulama hale getirirken biridir. Güvenli olmayan, bir bağlantı dizesi olası bir güvenlik açığı gösterir. Bağlantı bilgilerini düz metin olarak depolanması veya tüm sisteminizin belleği riskleri kalıcı yapma. Kaynak kodunuz katıştırılmış bağlantı dizeleri kullanılarak okunabilir [Ildasm.exe (IL ayrıştırıcı)](../../../../docs/framework/tools/ildasm-exe-il-disassembler.md) derlenmiş bir bütünleştirilmiş kodunda Microsoft Ara dili (MSIL) görüntülemek için.  
  
 Kimlik doğrulama türüne göre içeren bağlantı dizeleri ortaya çıkabilecek güvenlik açıkları bellek ve disk ve çalışma zamanında oluşturmak için kullanılan teknikleri bağlantı dizeleri nasıl kalıcı kullanılır.  
  
## <a name="use-windows-authentication"></a>Windows kimlik doğrulamasını kullan  
 Erişim sınırı yardımcı olmak için veri kaynağı bağlantı bilgilerini kullanıcı kimliği, parola ve veri kaynağı adı gibi güvenli hale getirmenize gerekir. Kullanıcı bilgilerinin kullanılmasını önlemek için Windows kimlik doğrulaması kullanmanızı öneririz (bazen denir *tümleşik güvenlik*) mümkün olduğunda. Windows kimlik doğrulaması, bir bağlantı dizesi kullanılarak belirtildiğinden `Integrated Security` veya `Trusted_Connection` anahtar sözcükler, bir kullanıcı kimliği ve parolası kullanacak gereğini ortadan kaldırır. Windows kimlik doğrulaması kullanırken, kullanıcılar Windows tarafından doğrulanır ve sunucu ve veritabanı kaynaklarına erişimi Windows kullanıcıları ve grupları için izin verme tarafından belirlenir.  
  
 Burada Windows kimlik doğrulaması kullanmak mümkün olmadığı durumlar için kullanıcı kimlik bilgileri bağlantı dizesinde gösterilir çünkü fazladan dikkatli kullanmanız gerekir. Bir ASP.NET uygulamasındaki veritabanları ve diğer ağ kaynaklarına bağlanmak için kullanılan bir sabit kimlik bir Windows hesabı yapılandırabilirsiniz. Kimliğe bürünme kimlik öğesinde etkinleştirmek **web.config** dosyası ve bir kullanıcı adı ve parola belirtin.  
  
```xml  
<identity impersonate="true"   
        userName="MyDomain\UserAccount"   
        password="*****" />  
```  
  
 Sabit kimliği hesabı veritabanında yalnızca gerekli izinleri verilmiş olan bir düşük ayrıcalıklı hesap olması gerekir. Ayrıca, yapılandırma dosyasını şifreleyin, böylece kullanıcı adı ve parola düz metin olarak açık değildir.  
  
## <a name="do-not-use-universal-data-link-udl-files"></a>Değil kullanım evrensel veri bağlantısı (UDL) dosyaları  
 Bağlantı dizeleri için depolama kaçının bir <xref:System.Data.OleDb.OleDbConnection> bir evrensel veri bağlantısı (UDL) dosyasında. UDLs düz metin olarak depolanır ve şifrelenemez. Dış dosya tabanlı kaynak uygulamanıza UDL dosyasıdır ve korunamıyor veya .NET Framework kullanılarak şifrelenir.  
  
## <a name="avoid-injection-attacks-with-connection-string-builders"></a>Bağlantı dizesi oluşturucular ile ekleme saldırıları önlemek  
 Dinamik dize birleştirme kullanıcı girişini temel alarak bağlantı dizelerini oluşturmak için kullanılan bağlantı dizesi ekleme saldırı ortaya çıkabilir. Kullanıcı girişi doğrulanmış ve kötü amaçlı metin veya değil kaçış karakterleri değilse, bir saldırganın olası hassas verileri veya sunucudaki diğer kaynakları erişebilirsiniz. Bu sorunu gidermek için bağlantı dizesi söz dizimini doğrulayın ve ek parametreler değil sunulan sağlamak için yeni bağlantı dizesi Oluşturucu sınıflar ADO.NET 2.0 kullanıma sunuldu. Daha fazla bilgi için bkz: [bağlantı dizesi oluşturucular](../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
## <a name="use-persist-security-infofalse"></a>Kullanım kalıcı Security Info = False  
 İçin varsayılan değer `Persist Security Info` False; Bu varsayılan tüm bağlantı dizeleri kullanmanızı öneririz. Ayarı `Persist Security Info` için `true` veya `yes` kullanıcı kimliği ve parolası, onu açıldıktan sonra bir bağlantıdan alınabilmesi için gibi güvenlik bakımından hassas bilgiler sağlar. Zaman `Persist Security Info` ayarlanır `false` veya `no`, güvenilmeyen bir kaynağa güvenlik bakımından hassas bilgilere erişimi yok sağlayarak bu bağlantıyı açmak için kullanılan sonra güvenlik bilgileri atılır.  
  
## <a name="encrypt-configuration-files"></a>Yapılandırma dosyalarını şifrelemek  
 Aynı zamanda bağlantı dizelerini yapılandırma dosyalarında, uygulamanızın kodda katıştırmak için ortadan kaldırır saklayabilirsiniz. Yapılandırma dosyaları .NET Framework öğeleri ortak bir dizi tanımlanmış standart XML dosyalarıdır. Bağlantı dizelerini yapılandırma dosyalarında içinde saklanır genellikle  **\<connectionStrings >** öğesinde **app.config** bir Windows uygulaması için veya  **Web.config** bir ASP.NET uygulaması için dosya. Bağlantı dizelerini yapılandırma dosyalarını şifrelemek ve alma depolama temel kavramları hakkında daha fazla bilgi için bkz: [bağlantı dizeleri ve yapılandırma dosyalarını](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET uygulamalarının güvenliğini sağlama](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Yapılandırma bilgilerini korumalı Yapılandırması'nı kullanarak şifreleme](http://msdn.microsoft.com/library/51cdfe5b-9d82-458c-94ff-c551c4f38ed1)  
 [Yerel Güvenlik ve .NET Framework kodu PAVE](http://msdn.microsoft.com/en-us/bd61be84-c143-409a-a75a-44253724f784)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
