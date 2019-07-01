---
title: HTTP Taşıma Güvenliği
ms.date: 03/30/2017
ms.assetid: d3439262-c58e-4d30-9f2b-a160170582bb
ms.openlocfilehash: 456df42848c009dcf42022ac674a1d27e5b33972
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487027"
---
# <a name="http-transport-security"></a>HTTP Taşıma Güvenliği
HTTP taşıma kullanırken, güvenlik, Güvenli Yuva Katmanı (SSL) uygulaması tarafından sağlanır. SSL yaygın olarak Internet'te bir hizmete istemcinin kimliğini doğrulamak için kullanılır ve kanala gizliliği (şifreleme) sağlamak için. Bu konuda, SSL nasıl çalıştığını ve Windows Communication Foundation (WCF) nasıl uygulandığı açıklanmaktadır.  
  
## <a name="basic-ssl"></a>Temel SSL  
 Tipik bir senaryo nasıl SSL en iyi çalıştığını bank'ın Web sitesi bu durumda, açıklanmıştır. Bir kullanıcı adı ve parola ile oturum açmak bir müşteri sitesi sağlar. Kimlik doğrulaması gerçekleştirilen sonra kullanıcı görünümü hesabını bakiyeleri gibi işlemleri gerçekleştirmek, fatura ödemek ve para bir hesaptan diğerine taşıma.  
  
 Bir kullanıcı ilk sitesini ziyaret ettiğinde, bir dizi olarak adlandırılan anlaşmaları, SSL mekanizması başlar bir *el sıkışması*, kullanıcının istemci (Bu durumda, Internet Explorer). SSL, müşteri banka siteye ilk kimliğini doğrular. Müşteriler ilk gerçek site ve bunları kendi kullanıcı adı ve parolanızı yazmaya içine çekici yöntemlerle çekmeye çalıştığında sızma değil kurduğu olduğunu bilmesi gerektiğinden önemli bir adımdır. SSL, VeriSign gibi güvenilir bir yetkili tarafından sağlanan SSL sertifikası kullanarak bu kimlik doğrulaması yapar. Mantıksal şöyle geçer: VeriSign, banka sitesinin kimliğini onaylayan. Internet Explorer VeriSign güvendiği için güvenilen bir sitedir. VeriSign ile denetlemek istiyorsanız, bu nedenle de VeriSign logolardan birine tıklayarak yapabilirsiniz. Bitiş tarihi ve (banka siteye) verilen bir deyim Orijinallik sunan.  
  
 Güvenli bir oturum başlatmak için sunucu, oturum, karmaları oluşturmak için kullanın ve şifrelemek ve şifresini ile şifreleme algoritmaları listesi ile birlikte bir "hello" denk istemci gönderir. Yanıt olarak, site geri bildirim ve algoritmaları paketlerinden birini kendi tercih ettiğiniz gönderir. Bu ilk el sıkışması sırasında her iki taraf gönderip nonce öğelerinin. A *nonce* , sitenin ortak anahtarı ile birlikte bir karma değer oluşturmak için kullanılan verileri rastgele oluşturulmuş bir parçasıdır. A *karma* SHA1 gibi standart bir algoritma kullanarak iki sayı türetilen yeni bir sayıdır. (İstemci ve site de kullanmak için hangi karma algoritması kabul etmek için mesaj alışverişi.) Karma benzersiz olan ve yalnızca istemci ve site arasında oturumu için şifreleme ve şifre çözme iletileri için kullanılır. Her iki tarafında da aynı karma oluşturabilmek özgün nonce ve sertifikanın ortak anahtarı, hem istemci hem de hizmet vardır. Bu nedenle, istemci, (a) üzerinde anlaşılan algoritması üzerinde karma verilerden hesaplamak için kullanarak ve (b) Bu hizmet tarafından gönderilen karma değerini karşılaştırmak hizmet tarafından gönderilen karma doğrular; iki eşleşirse, istemci ile karma değiştirilmemiş güvencesi sahiptir. İstemci sonra bu karma bir anahtar olarak başka bir yeni karma içeren bir iletiyi şifrelemek için kullanabilirsiniz. Hizmet, karmayı kullanarak iletinin şifresini çözmek ve bu ikinci son karma kurtarın. (Nonce öğelerinin, ortak anahtar ve diğer verileri) birikmiş bilgileri artık için her iki tarafın adı verilir ve son karma (veya ana anahtarı) oluşturulabilir. Bu son anahtar sonraki son karmayı kullanarak şifrelenmiş gönderilir. Ana anahtarı sonra şifreleme ve şifre çözme oturumun geri kalanında iletileri için kullanılır. Hem istemci hem de hizmet aynı anahtar kullandığından, bu da adlandırılır bir *oturum anahtarı*.  
  
 Oturum anahtarını da bir simetrik anahtar ya da "paylaşılan gizlilik." artması şeklindedir Her iki tarafında bir işlem tarafından gerekli hesaplama azaltır çünkü bir simetrik anahtar olması önemlidir. Her ileti nonce öğelerinin karmaları ve yeni bir exchange talep, performans bozulmasına. Bu nedenle, nihai amacı SSL iletileri verimlilik ve güvenlik büyük ölçüde iki taraf arasında serbestçe akış sağlayan bir simetrik anahtar kullanmaktır.  
  
 Siteden siteye iletişim kuralı farklılık gösterebileceğinden önceki açıklama neler olacağını gösteren, Basitleştirilmiş bir sürümüdür. Hem istemci hem de site veri değişimi işlemi için daha fazla karmaşıklık ve bu nedenle protection eklemek üzere el sıkışması sırasında algorithmically birleştirilmiş nonce öğelerinin oluşturmak mümkündür.  
  
### <a name="certificates-and-public-key-infrastructure"></a>Sertifikalar ve ortak anahtar altyapısı  
 Anlaşması sırasında hizmeti SSL sertifikasını da istemciye gönderir. Sertifikayı veren yetkili ve sitenin Tekdüzen Kaynak Tanımlayıcısı (URI), sona erme tarihi gibi bilgileri içerir. İstemci bir eşleşme emin olmak için ilk temas ve tarih ve verme yetkilisi da denetler URI'ye URI karşılaştırır.  
  
 Her sertifikanın iki anahtar, özel anahtarı ve bir ortak anahtar vardır ve ikisi olarak bilinen bir *anahtar çifti exchange*. Kısaca, ortak anahtarı bir sertifikadan okunabilir olmakla birlikte özel anahtar sertifikasının sahibi olarak bilinir. İki anahtarı şifrelemek veya bir Özet, karma, veya diğer anahtarı, ancak yalnızca olarak bulmadýðýný operations şifresini çözmek için kullanılabilir. Örneğin, yalnızca site istemci ortak anahtarla şifreler, özel anahtarı kullanarak ileti şifresini çözebilir. Benzer şekilde, istemcinin site ile özel anahtarı şifreler, ortak anahtar ile şifresini çözebilir. Bu, özel anahtarla şifrelenmiş yalnızca iletileri ortak anahtarla şifresi çözülebilir çünkü yalnızca özel anahtarı kaynağı ile mesajları, istemciye güvence sağlar. Site, genel anahtar kullanılarak şifrelenmiş sahip istemcisi ile ileti değiştiriyor sağlanmıştır. Bu exchange neden olan yalnızca bir ilk el sıkışma için ancak güvenli olduğundan daha gerçek simetrik anahtar oluşturmak için gerçekleştirilir. Bununla birlikte, tüm iletişimler, geçerli bir SSL sertifikasına sahip hizmetine bağlıdır.  
  
## <a name="implementing-ssl-with-wcf"></a>WCF ile SSL uygulama  
 HTTP taşıma güvenliği (veya SSL) WCF'ye harici olarak sağlanır. SSL iki yoldan biriyle uygulayabilirsiniz; uygulamanızı nasıl barındırılıyor faktör şöyledir:  
  
- Internet Information Services (IIS), WCF konağı olarak kullanıyorsanız, bir SSL hizmeti kurmak için IIS Altyapısı'nı kullanın.  
  
- Şirket içinde barındırılan bir WCF uygulaması oluşturuyorsanız, bir SSL sertifikası HttpCfg.exe Aracı'nı kullanarak adresine bağlayabilirsiniz.  
  
### <a name="using-iis-for-transport-security"></a>Aktarım güvenliği için IIS kullanarak  
  
#### <a name="iis-70"></a>IIS 7.0  
 IIS 7. 0 ' (SSL kullanarak) güvenli bir konağı ayarlamak için bkz [IIS 7.0 Güvenli Yuva Katmanı Yapılandırma](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771438(v=ws.10)).  
  
IIS 7. 0'ile kullanım için sertifikaları yapılandırmak için bkz [IIS 7.0 sunucu sertifikalarını yapılandırma](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).  
  
#### <a name="iis-60"></a>IIS 6.0  
 IIS 6. 0 ' (SSL kullanarak) güvenli bir konağı ayarlamak için bkz [Güvenli Yuva Katmanı Yapılandırma](https://go.microsoft.com/fwlink/?LinkId=88601).  
  
 IIS 6.0 ile kullanım için sertifikaları yapılandırmak için bkz [Certificates_IIS_SP1_Ops](https://go.microsoft.com/fwlink/?LinkId=88602).  
  
### <a name="using-httpcfg-for-ssl"></a>SSL için HttpCfg kullanma  
 Şirket içinde barındırılan bir WCF uygulaması oluşturuyorsanız, kullanılabilir HttpCfg.exe aracını indirin [Windows XP Service Pack 2 Destek Araçları site](https://go.microsoft.com/fwlink/?LinkId=29002).  
  
 X.509 sertifikası ile bir bağlantı ayarlamak için HttpCfg.exe aracını kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Bir SSL sertifikası ile bir bağlantı noktası yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Aktarım Güvenliği](../../../../docs/framework/wcf/feature-details/transport-security.md)
- [İleti Güvenliği](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
