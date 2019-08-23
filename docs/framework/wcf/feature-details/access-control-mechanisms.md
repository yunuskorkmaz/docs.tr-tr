---
title: Erişim Denetimi Mekanizmaları
ms.date: 03/30/2017
helpviewer_keywords:
- WCF security
- access control [WCF]
ms.assetid: 9d576122-3f55-4425-9acf-b23d0781e966
ms.openlocfilehash: 14f348300d8ab9276a86b4cf8d91823d39b9aba3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964996"
---
# <a name="access-control-mechanisms"></a>Erişim Denetimi Mekanizmaları
Windows Communication Foundation (WCF) ile erişimi çeşitli şekilde denetleyebilirsiniz. Bu konu, çeşitli mekanizmaları kısaca ele alır ve her birinin ne zaman kullanılacağı konusunda öneriler sağlar; kullanılacak doğru mekanizmayı seçmenize yardımcı olmak için tasarlanmıştır. Erişim teknolojileri karmaşıklık sırasına göre listelenmiştir. En basit <xref:System.Security.Permissions.PrincipalPermissionAttribute>, kimlik modelidir.  
  
 Bu mekanizmaların yanı sıra, WCF ile kimliğe bürünme ve temsil etme, [temsil ve kimliğe bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)konusunda açıklanmaktadır.  
  
## <a name="principalpermissionattribute"></a>PrincipalPermissionAttribute  
 , <xref:System.Security.Permissions.PrincipalPermissionAttribute> Bir hizmet yöntemine erişimi kısıtlamak için kullanılır. Özniteliği bir yönteme uygulandığında, belirli bir arayanın kimliğini veya bir Windows grubu veya ASP.NET rolü üyeliğini talep etmek için kullanılabilir. İstemcinin kimliği bir X. 509.952 sertifikası kullanılarak doğrulandıysa, bu, konu adının yanı sıra sertifikanın parmak izini içeren bir birincil kimlik verilir.  
  
 Hizmetin üzerinde çalıştığı bilgisayardaki kaynaklara erişimi denetlemek içinöğesinikullanınvehizmetkullanıcılarıherzamanhizmetinüzerindeçalıştığıWindowsetkialanınınbirparçasıolur.<xref:System.Security.Permissions.PrincipalPermissionAttribute> Belirli erişim düzeylerine sahip olan (hiçbiri, salt okuma veya okuma ve yazma gibi) Windows gruplarını kolayca oluşturabilirsiniz.  
  
 Özniteliğini kullanma hakkında daha fazla bilgi için bkz [. nasıl yapılır: PrincipalPermissionAttribute sınıfıyla](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)erişimi kısıtlayın. Kimlik hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="aspnet-membership-provider"></a>ASP.NET üyelik sağlayıcısı  
 ASP.NET 'in bir özelliği üyelik sağlayıcıdır. Üyelik sağlayıcısı Teknik olarak bir erişim denetimi mekanizmasına rağmen, hizmetin uç noktasına erişebilen olası kimlikler kümesini sınırlayarak hizmete erişimi denetlemeye izin verir. Üyelik özelliği, bir Web sitesi kullanıcılarının sitesiyle hesap kurmasını sağlayan Kullanıcı adı/parola birleşimleri ile doldurulabilen bir veritabanı içerir. Üyelik sağlayıcısını kullanan bir hizmete erişmek için, bir kullanıcının Kullanıcı adı ve parolasıyla oturum açması gerekir.  
  
> [!NOTE]
> WCF hizmetinin yetkilendirme amacıyla kullanabilmesi için önce ASP.NET özelliğini kullanarak veritabanını doldurmanız gerekir.  
  
 Ayrıca, var olan bir ASP.NET Web sitesinde bir üyelik veritabanınız varsa ve aynı kullanıcı adları ve parolalarla yetkilendirilmiş aynı kullanıcıların hizmetinizi kullanmasını sağlamak istiyorsanız üyelik özelliğini de kullanabilirsiniz.  
  
 Bir WCF hizmetinde üyelik özelliğini kullanma hakkında daha fazla bilgi için bkz [. nasıl yapılır: ASP.NET üyelik sağlayıcısını](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)kullanın.  
  
## <a name="aspnet-role-provider"></a>ASP.NET rol sağlayıcısı  
 Diğer bir ASP.NET özelliği, rolleri kullanarak Yetkilendirmeyi Yönetme olanağıdır. ASP.NET rol sağlayıcısı, bir geliştiricinin kullanıcılara roller oluşturmasını ve her kullanıcıyı bir rol ya da rollere atamasını sağlar. Üyelik sağlayıcısında olduğu gibi, roller ve atamalar bir veritabanında depolanır ve ASP.NET rol sağlayıcısının belirli bir uygulamasıyla sunulan araçlar kullanılarak doldurulabilir. Üyelik özelliğinde olduğu gibi, WCF geliştiricileri, hizmet kullanıcılarını rollere göre yetkilendirmek için veritabanındaki bilgileri kullanabilir. Örneğin, yukarıda açıklanan `PrincipalPermissionAttribute` erişim denetimi mekanizmasıyla birlikte rol sağlayıcısını kullanabilirsiniz.  
  
 ASP.NET rol sağlayıcısını, var olan bir ASP.NET rol sağlayıcısı veritabanınız varsa ve WCF hizmetinizde aynı kural ve Kullanıcı atamaları kümesini kullanmak istiyorsanız da kullanabilirsiniz.  
  
 Rol sağlayıcısı özelliğini kullanma hakkında daha fazla bilgi için bkz [. nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)birlikte kullanın.  
  
## <a name="authorization-manager"></a>Yetkilendirme Yöneticisi  
 Başka bir özellik, istemcileri yetkilendirmek için Yetkilendirme Yöneticisi 'Ni (AzMan) ASP.NET rol sağlayıcısıyla birleştirir. ASP.NET bir Web hizmeti barındırdığınızda, AzMan, hizmet yetkilendirmesinin AzMan aracılığıyla gerçekleştirilmesi için uygulamayla tümleştirilebilir. ASP.NET rol yöneticisi, uygulama rollerini yönetmenize, rollere kullanıcı eklemenize ve kaldırmanıza ve rol üyeliğini denetlemeye olanak tanıyan bir API sağlar, ancak kullanıcının adlandırılmış bir görevi veya işlemi gerçekleştirme yetkisine sahip olup olmadığını sorgulamanıza izin vermez. AzMan, tek tek işlemleri tanımlamanızı ve bunları görevlere birleştirmenizi sağlar. AZMan ile, rol denetimlerine ek olarak, bir kullanıcının bir görevi gerçekleştirip gerçekleştiremeyeceğini de denetleyebilirsiniz. Rol ataması ve görev yetkilendirmesi uygulama dışında yapılandırılabilir veya uygulama içinde programlı olarak gerçekleştirilebilir. AzMan Yönetimi Microsoft Yönetim Konsolu (MMC) ek bileşeni, yöneticilerin bir rolün çalışma zamanında gerçekleştirebileceği görevleri değiştirmesine ve her kullanıcının rol üyeliğini yönetmesine olanak tanır.  
  
 Zaten var olan bir AzMan yüklemesine erişiminiz varsa ve AzMan/rol sağlayıcısı birleşiminin özelliklerini kullanarak hizmet kullanıcılarınıza yetki vermek istiyorsanız AzMan ve ASP.NET rol sağlayıcısını da kullanabilirsiniz.  
  
 Azman ve ASP.NET rol sağlayıcısı hakkında daha fazla bilgi için bkz [. nasıl yapılır: ASP.NET 2,0](https://go.microsoft.com/fwlink/?LinkId=88951)Ile Yetkilendirme Yöneticisi 'Ni (azman) kullanın. Azman ve WCF Hizmetleri rol sağlayıcısını kullanma hakkında daha fazla bilgi için bkz [. nasıl yapılır: ASP.NET Authorization Manager rol sağlayıcısını bir hizmetle](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)birlikte kullanın.  
  
## <a name="identity-model"></a>Kimlik modeli  
 Kimlik modeli, istemcileri yetkilendirmek için talepleri ve ilkeleri yönetmenizi sağlayan bir API kümesidir. Kimlik modeliyle, arayanın hizmette kimliğini doğrulamak için kullandığı kimlik bilgilerinde bulunan her talebi inceleyebilir, talepleri hizmet için ilke kümesiyle karşılaştırabilir ve karşılaştırmaya göre erişim izni verebilir veya vermeyebilirsiniz.  
  
 Hassas denetime ihtiyacınız varsa ve erişim vermeden önce belirli kriterleri ayarlamanıza olanak varsa kimlik modelini kullanın. Örneğin, kullanırken <xref:System.Security.Permissions.PrincipalPermissionAttribute>, ölçütü Kullanıcı kimliğinin kimliğinin doğrulanması ve belirli bir role ait olması yeterlidir. Bunun aksine, kimlik modelini kullanarak, kullanıcının bir belgeyi görüntülemesine izin verilmeden önce 18 yaşından fazla olması gerektiğini belirten bir ilke oluşturabilirsiniz.  
  
 Kimlik modeli talep tabanlı erişim denetiminden faydalanabilecek bir örnek, verilen belirteç senaryosunda Federasyon kimlik bilgileri kullanılırken olur. Federasyon ve verilen belirteçler hakkında daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
 Kimlik modeli hakkında daha fazla bilgi için bkz. [kimlik modeliyle talepleri ve Yetkilendirmeyi Yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [Nasıl yapılır: PrincipalPermissionAttribute sınıfı ile erişimi kısıtlama](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [Nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Nasıl yapılır: ASP.NET Authorization Manager rol sağlayıcısını bir hizmetle kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)
- [Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Temsilcilik ve Kimliğe Bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
