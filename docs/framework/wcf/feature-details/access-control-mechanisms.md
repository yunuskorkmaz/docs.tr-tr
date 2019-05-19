---
title: Erişim Denetimi Mekanizmaları
ms.date: 03/30/2017
helpviewer_keywords:
- WCF security
- access control [WCF]
ms.assetid: 9d576122-3f55-4425-9acf-b23d0781e966
ms.openlocfilehash: 9ebd1489c35bb3b023ed73cd86fac1b6a352012b
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882178"
---
# <a name="access-control-mechanisms"></a>Erişim Denetimi Mekanizmaları
Windows Communication Foundation (WCF) birkaç yolla erişimi denetleyebilirsiniz. Bu konu, kısa bir süre çeşitli mekanizmalar açıklar ve her zaman hakkında öneriler sağlar; kullanılacak doğru mekanizması seçmenize yardımcı olmak için tasarlanmıştır. Erişim teknolojileri karmaşıklığı sırasına göre listelenir. En basit olan <xref:System.Security.Permissions.PrincipalPermissionAttribute>; en karmaşık kimlik modelidir.  
  
 Bu mekanizmalar yanı sıra, kimliğe bürünme ve temsilci ile WCF bölümünde açıklanmıştır [temsilcilik ve kimliğe bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="principalpermissionattribute"></a>PrincipalPermissionAttribute  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> Hizmet yönteme erişimi kısıtlamak için kullanılır. Bir yönteme öznitelik uygulandığında, belirli bir çağıranının kimliğini veya bir Windows grubu üyeliği veya ASP.NET rol için kullanılabilir. İstemci bir X.509 sertifikası kullanılarak kimlik doğrulaması gerekiyorsa, konu adı ve sertifikanın parmak izini karakterlerinden oluşan bir birincil kimliği verilir.  
  
 Kullanım <xref:System.Security.Permissions.PrincipalPermissionAttribute> hizmetin üzerinde çalıştığı bilgisayar üzerindeki kaynaklara erişimi denetlemek için ve hizmet kullanıcılarının her zaman hizmetin üzerinde çalıştığı aynı Windows etki alanının parçası olur. Erişim düzeyleri belirttiğiniz Windows grupları kolayca oluşturabilirsiniz (gibi hiçbiri, salt okunur veya okuma ve yazma).  
  
 Öznitelik kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: PrincipalPermissionAttribute sınıfı ile erişimi kısıtlama](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md). Kimlik hakkında daha fazla bilgi için bkz: [kimlik doğrulama ile hizmet kimliği](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="aspnet-membership-provider"></a>ASP.NET üyelik sağlayıcısı  
 ASP.NET üyelik sağlayıcısı özelliğidir. Üyelik sağlayıcısı teknik bir erişim denetimi mekanizmasını olmasa bile hizmet uç noktasına erişebildiğinden olası kimlikleri kümesi sınırlayarak hizmetine erişimi denetleme sağlar. Üyelik özelliği site hesaplarını oluşturmak üzere bir Web sitesinin kullanıcıların kullanıcı adı/parola birleşimlerini ile doldurulmuş bir veritabanı içerir. Üyelik sağlayıcısı kullanan bir hizmet erişmek için bir kullanıcı kendi kullanıcı adı ve parolayla oturum açmalısınız.  
  
> [!NOTE]
>  Ayrıca, bir WCF Hizmeti yetkilendirme amacıyla kullanabilmeniz için önce ASP.NET özelliğini kullanarak veritabanını öncelikle doldurmanız gerekir.  
  
 Ayrıca, mevcut bir ASP.NET Web sitesinden bir üyelik veritabanı zaten varsa ve aynı kullanıcı adları ve parolaları ile yetkili hizmetinizi kullanmak kullanıcıları etkinleştirmek istediğiniz üyelik özelliği kullanabilirsiniz.  
  
 Bir WCF hizmeti üyelik özelliğini kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: ASP.NET üyelik sağlayıcıyı kullanacak](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).  
  
## <a name="aspnet-role-provider"></a>ASP.NET rol sağlayıcısını  
 Başka bir ASP.NET yetkilendirme rolleri kullanarak yönetme olanağı özelliğidir. ASP.NET rol sağlayıcısını bir geliştirici kullanıcılar için roller oluşturmak ve her kullanıcı bir rolü veya rolleri atamak için etkinleştirir. Üyelik sağlayıcısı olarak, bir veritabanında depolanır ve rollerini ve atamalarını ASP.NET rol sağlayıcıyı belirli bir uygulama tarafından sağlanan araçları kullanılarak doldurulabilir. Olarak üyelik özelliğiyle WCF geliştiricileri bilgileri veritabanında rolleri tarafından hizmet Kullanıcıları yetkilendirmek için kullanabilirsiniz. Örneğin, rol sağlayıcısı ile birlikte kullanabileceklerini `PrincipalPermissionAttribute` erişim denetimi mekanizmasını yukarıda açıklanan.  
  
 Varolan ASP.NET rol sağlayıcısını veritabanına sahip ve aynı kuralları ve kullanıcı atamaları kümesini WCF hizmetinizi kullanmak istiyorsanız, ASP.NET rol sağlayıcıyı kullanabilirsiniz.  
  
 Rol sağlayıcı özelliğini kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).  
  
## <a name="authorization-manager"></a>Yetkilendirme Yöneticisi  
 Başka bir özellik ile ASP.NET rol sağlayıcıyı istemcilere yetki vermek için Yetkilendirme Yöneticisi'ni (AzMan) birleştirir. ASP.NET Web hizmeti barındırdığında, yetkilendirme hizmetine AzMan gerçekleştirilir böylece AzMan uygulamasına tümleştirilebilir. ASP.NET Rol Yöneticisi uygulama rolleri yönetmenize olanak sağlayan bir API eklemek ve kullanıcı rollerini kaldırın ve rol üyeliğini denetleyin sağlar ancak bu, bir kullanıcı bir adlandırılmış bir görevi veya işlemi gerçekleştirmek için yetkili olup olmadığını sorgulamak izin vermez. AzMan tek işlemler tanımlamak ve görevlere birleştirip sağlar. AZMan ile rol denetimlerini yanı sıra, ayrıca bir kullanıcı bir görev yapıp yapamayacaklarını denetleyebilirsiniz. Rol ataması ve görev yetkilendirmesi uygulama dışında yapılandırılmış veya uygulama içinde program aracılığıyla gerçekleştirilir. Yöneticileri rol çalışma zamanında gerçekleştirebileceğiniz görevler değiştirmek ve rolleri, her kullanıcının üyeliğini yönetmek için Microsoft Yönetim Konsolu (MMC) ek bileşenini AzMan yönetim sağlar.  
  
 Zaten var olan bir AzMan yüklemesini erişimi ve AzMan/rol sağlayıcısı birleşimi özelliklerini kullanarak, hizmet Kullanıcıları yetkilendirmek istiyorsanız AzMan ve ASP.NET rol sağlayıcıyı kullanabilirsiniz.  
  
 AzMan ve ASP.NET rol sağlayıcıyı hakkında daha fazla bilgi için bkz. [nasıl yapılır: Yetkilendirme Yöneticisi'ni (AzMan) ASP.NET 2.0 ile](https://go.microsoft.com/fwlink/?LinkId=88951). AzMan ve rol sağlayıcısı için WCF hizmetleri kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol sağlayıcısını bir hizmetle kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md).  
  
## <a name="identity-model"></a>Kimlik modeli  
 Kimlik modeli istemciler yetkilendirmek için talepler ve ilkeleri yönetmenize olanak tanıyan API'ler kümesidir. Kimlik modeliyle çağıran hizmete kendi kimliğini doğrulamak, hizmeti için ilke kümesini talepleri karşılaştırma ve vermek veya erişimini engellemek için kullanılan karşılaştırma üzerine dayalı kimlik bilgilerinde yer alan her bir talep inceleyebilirsiniz.  
  
 Denetim ve erişim vermeden önce belirli ölçütleri ayarlamanıza olanak ince kimlik modeli kullanın. Örneğin, kullanırken <xref:System.Security.Permissions.PrincipalPermissionAttribute>, yalnızca kullanıcının kimliği doğrulanır ve belirli bir role ait ölçüttür. Buna karşılık, kimlik modeli kullanarak, kullanıcı 18 yıl üzerinden olmalıdır ve bir belgeyi görüntülemek için izin verilen önce geçerli bir sürücünün lisansına sahip olmadığını belirten bir ilke oluşturabilirsiniz.  
  
 Verilen belirteç senaryoda Federasyon kimlik bilgilerini kullanarak burada kimlik modeli talep tabanlı erişim denetiminden yararlanabilirsiniz örnek verilebilir. Federasyon ve verilen belirteçler hakkında daha fazla bilgi için bkz: [Federasyon ve verilen belirteçler](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
 Kimlik modeli hakkında daha fazla bilgi için bkz: [yönetme beyanlar ve yetkilendirmeyi kimlik modeliyle](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [Nasıl yapılır: PrincipalPermissionAttribute sınıfı ile erişimi kısıtlama](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [Nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol sağlayıcısını bir hizmetle kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)
- [Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Temsilcilik ve Kimliğe Bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
