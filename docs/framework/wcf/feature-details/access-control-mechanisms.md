---
title: Erişim Denetimi Mekanizmaları
ms.date: 03/30/2017
helpviewer_keywords:
- WCF security
- access control [WCF]
ms.assetid: 9d576122-3f55-4425-9acf-b23d0781e966
ms.openlocfilehash: b423dac4d8324069eb1825666419b23b5afdca63
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185500"
---
# <a name="access-control-mechanisms"></a>Erişim Denetimi Mekanizmaları
Windows Communication Foundation (WCF) ile erişimi çeşitli şekillerde denetleyebilirsiniz. Bu konu, çeşitli mekanizmaları kısaca tartışır ve her birinin ne zaman kullanılacağı na ilişkin öneriler sunar; kullanılacak doğru mekanizmayı seçmenize yardımcı olmak için tasarlanmıştır. Erişim teknolojileri karmaşıklık sırasına göre listelenir. En <xref:System.Security.Permissions.PrincipalPermissionAttribute>basiti; en karmaşık kimlik modelidir.  
  
 Bu mekanizmalara ek olarak, WCF ile kimliğe bürünme ve delegasyon [Delegasyon ve Kimliğe Bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)açıklanmıştır.  
  
## <a name="principalpermissionattribute"></a>PrincipalPermissionAttribute  
 Bir <xref:System.Security.Permissions.PrincipalPermissionAttribute> hizmet yöntemine erişimi kısıtlamak için kullanılır. Öznitelik bir yönteme uygulandığında, belirli bir arayanın kimliğini veya Windows grubuna veya ASP.NET rolüne üyeliğini istemek için kullanılabilir. İstemci X.509 sertifikası kullanılarak kimlik doğrulanırsa, bu sertifikaya özne adı ve sertifikanın parmak izinden oluşan birincil kimlik verilir.  
  
 Hizmetin <xref:System.Security.Permissions.PrincipalPermissionAttribute> çalıştığı bilgisayardaki kaynaklara erişimi denetlemek için ve hizmetin kullanıcıları her zaman hizmetin çalıştığı aynı Windows etki alanının bir parçası olacaksa kullanın. Belirtilen erişim düzeylerine sahip Windows grupları (bunlara ait hiçbiri, salt okunur veya okuyup yazma gibi) kolayca oluşturabilirsiniz.  
  
 Öznitelik kullanma hakkında daha fazla bilgi için [bkz: PrincipalPermissionAttribute Class ile Erişimi Kısıtlayın.](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md) Kimlik hakkında daha fazla bilgi için [Hizmet Kimliği ve Kimlik Doğrulama'ya](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)bakın.  
  
## <a name="aspnet-membership-provider"></a>ASP.NET Üyelik Sağlayıcısı  
 ASP.NET bir özelliği üyelik sağlayıcısıdır. Üyelik sağlayıcısı teknik olarak bir erişim denetim mekanizması olmasa da, hizmetin bitiş noktasına erişebilecek olası kimlikkümesini sınırlayarak hizmete erişimi denetlemeye olanak tanır. Üyelik özelliği, bir Web sitesinin kullanıcılarının siteyle hesap lar kurmasını sağlayan kullanıcı adı/parola birleşimleriyle doldurulabilecek bir veritabanı içerir. Üyelik sağlayıcısını kullanan bir hizmete erişmek için, kullanıcının kullanıcı adı ve parolasıyla oturum açması gerekir.  
  
> [!NOTE]
> Bir WCF hizmetinin yetkilendirme amacıyla kullanabilmesi için önce veritabanını ASP.NET özelliğini kullanarak doldurmanız gerekir.  
  
 Mevcut bir ASP.NET Web sitesinden zaten bir üyelik veritabanınız varsa ve aynı kullanıcıların aynı kullanıcı adları ve parolalarla yetkilendirilen hizmetinizi kullanmasını sağlamak istiyorsanız, üyelik özelliğini de kullanabilirsiniz.  
  
 Bir WCF hizmetinde üyelik özelliğini kullanma hakkında daha fazla bilgi için bkz [ASP.NET.](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
  
## <a name="aspnet-role-provider"></a>ASP.NET Rol Sağlayıcısı  
 ASP.NET bir diğer özelliği de rolleri kullanarak yetkilendirmeyi yönetebilme yeteneğidir. ASP.NET rol sağlayıcısı, bir geliştiricinin kullanıcılar için roller oluşturmasına ve her kullanıcıyı bir role veya role atamasına olanak tanır. Üyelik sağlayıcısında olduğu gibi, roller ve atamalar bir veritabanında depolanır ve ASP.NET rol sağlayıcısının belirli bir uygulaması tarafından sağlanan araçlar kullanılarak doldurulabilir. Üyelik özelliğinde olduğu gibi, WCF geliştiricileri de veritabanındaki bilgileri hizmet kullanıcılarını rollere göre yetkilendirmek için kullanabilir. Örneğin, rol sağlayıcısını yukarıda açıklanan `PrincipalPermissionAttribute` erişim denetim mekanizmasıyla birlikte kullanabilirler.  
  
 Varolan bir ASP.NET rol sağlayıcısı veritabanınız varsa ve WCF hizmetinizde aynı kural ve kullanıcı atamaları kümesini kullanmak istiyorsanız, ASP.NET rol sağlayıcısını da kullanabilirsiniz.  
  
 Rol sağlayıcısı özelliğini kullanma hakkında daha fazla bilgi için [bkz: Hizmetle ASP.NET Rol Sağlayıcısı'nı kullanın.](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
  
## <a name="authorization-manager"></a>Yetkilendirme Yöneticisi  
 Başka bir özellik yetkilendirme yöneticisi (AzMan) istemcileri yetkilendirmek için ASP.NET rol sağlayıcısı ile birleştirir. ASP.NET bir Web hizmeti barındırdığında, AzMan uygulamaya entegre edilebilir, böylece hizmete yetki azman üzerinden yapılır. ASP.NET rol yöneticisi, uygulama rollerini yönetmeninize, kullanıcıları rollerden eklemenize ve kaldırmanıza ve rol üyeliğini denetlemenize olanak tanıyan bir API sağlar, ancak kullanıcının adlandırılmış bir görev veya işlemi gerçekleştirmeyetkisi olup olmadığını sorgulamanıza izin vermez. AzMan, tek tek işlemleri tanımlamanızı ve bunları görevlerde birleştirmenizi sağlar. AZMan ile, rol denetimlerine ek olarak, kullanıcının bir görevi gerçekleştirip gerçekleştiremeyeceğini de denetleyebilirsiniz. Rol ataması ve görev yetkilendirmesi uygulama dışında yapılandırılabilir veya uygulama içinde programlı olarak gerçekleştirilebilir. AzMan yönetimi Microsoft Yönetim Konsolu (MMC) snap-in yöneticileri bir rolün çalışma zamanında gerçekleştirebileceği görevleri değiştirmek ve her kullanıcının rollerin üyeliğini yönetmek için izin verir.  
  
 Zaten varolan bir AzMan yüklemesine erişiminiz varsa ve AzMan/rol sağlayıcısı kombinasyonunun özelliklerini kullanarak servis kullanıcılarınızı yetkilendirmek istiyorsanız, AzMan ve ASP.NET rol sağlayıcısını da kullanabilirsiniz.  
  
 AzMan ve ASP.NET rol sağlayıcısı hakkında daha fazla bilgi için bkz [ASP.NET.](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10)) AzMan ve WCF hizmetleri için rol sağlayıcısının kullanımı hakkında daha fazla bilgi için [bkz: Hizmetli ASP.NET Yetkilendirme Yöneticisi Rol Sağlayıcısı'nı kullanın.](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
  
## <a name="identity-model"></a>Kimlik Modeli  
 Kimlik Modeli, istemcileri yetkilendirmek için talepleri ve ilkeleri yönetmenize olanak tanıyan bir API kümesidir. Kimlik Modeli ile, arayanın kendisini hizmete doğrulamak için kullandığı kimlik bilgilerinde bulunan her talebi inceleyebilir, talepleri hizmet için ilkeler kümesiyle karşılaştırabilir ve karşılaştırmaya dayalı erişim verebilir veya reddedebilirsiniz.  
  
 İyi denetime ve erişim vermeden önce belirli ölçütleri ayarlama yeteneğine ihtiyacınız varsa Kimlik Modelini kullanın. Örneğin, <xref:System.Security.Permissions.PrincipalPermissionAttribute>, ölçüt kullanırken sadece kullanıcının kimliğinin doğrulanmış ve belirli bir role ait olmasıdır. Buna karşılık, Kimlik Modeli'ni kullanarak, kullanıcının 18 yaşından büyük olması gerektiğini ve belgeyi görüntülemesine izin verilmeden önce geçerli bir sürücü ehliyetine sahip olduğunu belirten bir ilke oluşturabilirsiniz.  
  
 Kimlik Modeli talep tabanlı erişim denetiminden yararlanabileceğiniz bir örnek, verilen belirteç senaryosunda federasyon kimlik bilgilerini kullanırken elde edilir. Federasyon ve verilen belirteçler hakkında daha fazla bilgi için [Federasyon ve İhraç Jetonları'na](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)bakın.  
  
 Kimlik Modeli hakkında daha fazla bilgi için, [Kimlik Modeli ile Talepleri ve Yetkilendirmeyi Yönetme'ye](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [Nasıl yapılır: PrincipalPermissionAttribute Sınıfı ile Erişimi Kısıtlama](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol Sağlayıcısını Bir Hizmetle Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)
- [Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Temsilcilik ve Kimliğe Bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
