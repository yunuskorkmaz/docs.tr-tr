---
title: HTTP Taşıma Güvenliği
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d3439262-c58e-4d30-9f2b-a160170582bb
caps.latest.revision: 14
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 2787c38603fd0f88878596a809d7e3c5cfdfb350
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="http-transport-security"></a>HTTP Taşıma Güvenliği
HTTP taşıma olarak kullanırken, güvenlik Güvenli Yuva Katmanı (SSL) uygulaması tarafından sağlanır. SSL yaygın olarak Internet'te bir hizmete bir istemci kimlik doğrulaması için kullanılır ve ardından kanal gizliliği (şifreleme) sağlamak için. Bu konuda SSL nasıl çalıştığı ve nasıl şu uygulanan açıklanmaktadır [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## <a name="basic-ssl"></a>Temel SSL  
 Nasıl SSL works en iyi tipik bir senaryo, bu durumda, bir bankanın Web sitesi açıklanmıştır. Bir kullanıcı adı ve parola ile oturum açmak bir müşteri sitesi sağlar. Kimlik doğrulaması gerçekleştirilen sonra kullanıcı görünümü hesap bakiyelerini gibi işlemler gerçekleştirmek, fatura ödeme ve para bir hesaptan taşıyın.  
  
 Bir kullanıcı ilk sitesini ziyaret ettiğinde SSL mekanizması olarak adlandırılan anlaşmaları, bir dizi başlar bir *el sıkışma*, kullanıcının istemci (Bu durumda, Internet Explorer). SSL, müşteri banka siteye ilk kimliğini doğrular. Müşteriler ilk gerçek site ve bunları, kullanıcı adı ve parolasını yazarak içine çekici yöntemlerle çekmeye dener sızma değil kurduğu olduğunu bilmeniz gerekir çünkü bu önemli bir adımdır. SSL, VeriSign gibi güvenilir bir yetkili tarafından sağlanan bir SSL sertifikası kullanarak bu kimlik doğrulaması yapar. Mantığı şöyle gider: VeriSign onaylayan banka site kimliği için. Internet Explorer VeriSign güvendiği için güvenilen bir sitedir. VeriSign ile denetlemek istiyorsanız, VeriSign logosunu tıklayarak bu nedenle de yapabilirsiniz. Sona erme tarihini ve (banka siteye) verilen bir deyim Orijinallik gösterir.  
  
 Güvenli bir oturum başlatmak için bir "hello" denk istemci, oturum, karmaları oluşturmak için kullanabilir ve şifrelemek ve ile şifresini şifreleme algoritmaları listesini birlikte sunucusuna gönderir. Yanıt olarak, site geri bildirim ve dilediği algoritmaları paketlerinden birinin gönderir. Bu ilk el sıkışması sırasında her iki taraf gönderip nonce öğelerinin. A *nonce* , sitenin ortak anahtarı ile birlikte bir karma oluşturmak için kullanılan veri rastgele oluşturulmuş bir parçasıdır. A *karma* SHA1 gibi standart bir algoritma kullanarak iki sayının türetilen yeni bir sayıdır. (İstemci ve site de kullanmak için karma algoritmayı kabul iletileri exchange.) Karma benzersizdir ve yalnızca istemci ve site arasındaki oturumu şifrelemek ve iletilerin şifresini çözmek için kullanılır. İki tarafı da aynı karma oluşturabilir şekilde hem istemci hem de hizmet özgün nonce ve sertifikanın ortak anahtarı var. Bu nedenle, istemci (a) üzerinde anlaşılan verileri karması hesaplanamıyor algoritmasıyla ve (b), hizmet tarafından gönderilen karmayla karşılaştırın tarafından hizmeti tarafından gönderilen karma doğrular; iki eşleşen istemci ile karma değiştirilmemiş güvencesi yoktur. İstemci sonra bu karma bir anahtar olarak henüz başka bir yeni karma içeren bir iletiyi şifrelemek için kullanabilirsiniz. Hizmet karma kullanarak iletinin şifresini çözmek ve bu ikinci son karma kurtarma. (Nonce öğelerinin, ortak anahtar ve diğer verileri) birikmiş bilgileri şimdi iki tarafı bilinir ve son karma (veya ana anahtar) oluşturulabilir. Bu son anahtar sonraki son karma kullanılarak şifrelenmiş gönderilir. Ana anahtar sonra şifrelemek ve oturum sıfırlama için iletilerin şifresini çözmek için kullanılır. Hem istemci hem de hizmet aynı anahtar kullandığından, bu da adlandırılır bir *oturum anahtarı*.  
  
 Oturum anahtarını da bir simetrik anahtar ya da "paylaşılan gizlilik." belirlenir Her iki tarafında işlem tarafından gerekli hesaplama azalttığı için simetrik anahtar sahip olmak önemlidir. Her ileti nonce öğelerinin karmaları ve yeni bir exchange talep, performans bozulmasına. Bu nedenle, SSL nihai amacıyla güvenlik büyük ölçüde iki kenara ve verimliliği arasında serbestçe akış iletilere izin vermesi bir simetrik anahtar kullanmaktır.  
  
 Siteden siteye iletişim kuralı farklılık gösterebileceğinden önceki açıklama neler, Basitleştirilmiş bir sürümüdür. Hem istemci hem de site daha fazla karmaşıklık ve bu nedenle koruma, veri değişimi işlemi eklemek için el sıkışması sırasında algorithmically birleştirilmiş nonce öğelerinin oluşturmak mümkündür.  
  
### <a name="certificates-and-public-key-infrastructure"></a>Sertifikalar ve ortak anahtar altyapısı  
 Anlaşması sırasında hizmeti SSL sertifikasını da istemciye gönderir. Sertifikayı veren yetkili ve sitenin Tekdüzen Kaynak Tanımlayıcısı (URI), sona erme tarihi gibi bilgileri içerir. İstemci ilk olarak bir eşleşme emin olmak için bağlantı kurulan ve aynı zamanda tarih ve verme yetkilisi denetler URI URI'si karşılaştırır.  
  
 Her sertifika iki anahtarları, özel anahtarı ve bir ortak anahtar içerir ve iki olarak da bilinir bir *anahtar çifti exchange*. Kısaca, ortak anahtar sertifikası okunabilir durumdayken özel anahtar yalnızca sertifika sahibinin adı verilir. Her iki anahtarı şifreleme veya şifrelerini çözme bir Özet, karma değeri veya başka bir anahtar, ancak yalnızca olarak bulmadýðýný işlemleri için kullanılabilir. Örneğin, istemci ortak anahtarla şifreler, yalnızca site özel anahtarı kullanarak ileti şifresini çözebilir. Benzer şekilde, istemci site özel anahtarla şifreler, ortak anahtar ile şifresini çözebilir. Bu özel anahtar ile şifrelenmiş yalnızca iletileri ortak anahtarla şifresi çözülebilir olduğundan yalnızca özel anahtarı sahibi ile değiştirilen mesajları, istemciye güvence sağlar. Site, ortak anahtar kullanılarak şifrelenmiş sahip bir istemci iletilerle değiştiriyor emin olur. Bu exchange neden olan yalnızca bir ilk el sıkışma için ancak güvenli daha pek çok gerçek simetrik anahtar oluşturmak için yapılır. Bununla birlikte, tüm iletişimler geçerli bir SSL sertifikası sahip hizmetine bağlıdır.  
  
## <a name="implementing-ssl-with-wcf"></a>WCF ile SSL uygulama  
 HTTP taşıma güvenliği (veya SSL) sağlanan harici olarak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. SSL iki yoldan biriyle uygulayabilirsiniz; uygulamanızı nasıl barındırılan belirleyici faktör şöyledir:  
  
-   Internet Information Services (IIS) olarak kullanıyorsanız, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ana bilgisayar, bir SSL hizmetini kurma için IIS altyapısını kullanır.  
  
-   Kendini barındıran oluşturuyorsanız [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama, bir SSL sertifikası HttpCfg.exe aracını kullanarak adresine bağlayabilirsiniz.  
  
### <a name="using-iis-for-transport-security"></a>Taşıma güvenliği için IIS kullanma  
  
#### <a name="iis-70"></a>IIS 7.0  
 Ayarlamak için [!INCLUDE[iisver](../../../../includes/iisver-md.md)] (SSL kullanarak) güvenli bir konak olarak bkz [IIS 7.0 Beta: Güvenli Yuva Katmanı'nı yapılandırma IIS 7.0](http://go.microsoft.com/fwlink/?LinkId=88600).  
  
 Sertifikalar ile kullanılmak üzere yapılandırmak için [!INCLUDE[iisver](../../../../includes/iisver-md.md)], bkz: [IIS 7.0 Beta: IIS 7.0 sunucu sertifikalarını yapılandırma](http://go.microsoft.com/fwlink/?LinkID=88595).  
  
#### <a name="iis-60"></a>IIS 6.0  
 Ayarlamak için [!INCLUDE[iis601](../../../../includes/iis601-md.md)] (SSL kullanarak) güvenli bir konak olarak bkz [Güvenli Yuva Katmanı'nı yapılandırma](http://go.microsoft.com/fwlink/?LinkId=88601).  
  
 Sertifikalar ile kullanılmak üzere yapılandırmak için [!INCLUDE[iis601](../../../../includes/iis601-md.md)], bkz: [Certificates_IIS_SP1_Ops](http://go.microsoft.com/fwlink/?LinkId=88602).  
  
### <a name="using-httpcfg-for-ssl"></a>SSL için HttpCfg kullanma  
 Kendini barındıran oluşturuyorsanız [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama adresinde HttpCfg.exe Aracı'nı indirme [Windows XP Service Pack 2 Destek Araçları site](http://go.microsoft.com/fwlink/?LinkId=29002).  
  
 X.509 sertifikası ile bir bağlantı ayarlamak için HttpCfg.exe aracını kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir SSL sertifikası ile bir bağlantı noktası yapılandırın](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Aktarım Güvenliği](../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [İleti Güvenliği](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
