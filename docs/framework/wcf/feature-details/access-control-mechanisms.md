---
title: Erişim Denetimi Mekanizmaları
ms.date: 03/30/2017
helpviewer_keywords:
- WCF security
- access control [WCF]
ms.assetid: 9d576122-3f55-4425-9acf-b23d0781e966
ms.openlocfilehash: 1de6731591e524080ac4ae7d5b2ec2a25a27f301
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486668"
---
# <a name="access-control-mechanisms"></a>Erişim Denetimi Mekanizmaları
Windows Communication Foundation (WCF) birkaç yolla erişimi denetleyebilirsiniz. Bu konu, kısa bir süre çeşitli mekanizmalar açıklar ve her zaman hakkında öneriler sağlar; kullanılacak doğru mekanizması seçmenize yardımcı olmak için tasarlanmıştır. Erişim teknolojileri karmaşıklığı sırasına göre listelenir. En basit olan <xref:System.Security.Permissions.PrincipalPermissionAttribute>; en karmaşık kimlik modelidir.  
  
 Bu mekanizmalar yanı sıra, kimliğe bürünme ve temsilci ile WCF bölümünde açıklanmıştır [temsilcilik ve kimliğe bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="principalpermissionattribute"></a>PrincipalPermissionAttribute  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> Hizmet yönteme erişimi kısıtlamak için kullanılır. Bir yönteme öznitelik uygulandığında, bu belirli çağrıyı yapanın kimliği veya bir Windows grubu üyeliği talep için kullanılabilir veya [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rol. İstemci bir X.509 sertifikası kullanılarak kimlik doğrulaması gerekiyorsa, konu adı ve sertifikanın parmak izini karakterlerinden oluşan bir birincil kimliği verilir.  
  
 Kullanım <xref:System.Security.Permissions.PrincipalPermissionAttribute> hizmetin üzerinde çalıştığı bilgisayar üzerindeki kaynaklara erişimi denetlemek için ve hizmet kullanıcılarının her zaman hizmetin üzerinde çalıştığı aynı Windows etki alanının parçası olur. Erişim düzeyleri belirttiğiniz Windows grupları kolayca oluşturabilirsiniz (gibi hiçbiri, salt okunur veya okuma ve yazma).  
  
 Öznitelik kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: PrincipalPermissionAttribute sınıfı ile erişimi kısıtla](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md). Kimlik hakkında daha fazla bilgi için bkz: [kimlik doğrulama ile hizmet kimliği](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="aspnet-membership-provider"></a>ASP.NET üyelik sağlayıcısı  
 Bir özellik olan [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] üyelik sağlayıcısı. Üyelik sağlayıcısı teknik bir erişim denetimi mekanizmasını olmasa bile hizmet uç noktasına erişebildiğinden olası kimlikleri kümesi sınırlayarak hizmetine erişimi denetleme sağlar. Üyelik özelliği site hesaplarını oluşturmak üzere bir Web sitesinin kullanıcıların kullanıcı adı/parola birleşimlerini ile doldurulmuş bir veritabanı içerir. Üyelik sağlayıcısı kullanan bir hizmet erişmek için bir kullanıcı kendi kullanıcı adı ve parolayla oturum açmalısınız.  
  
> [!NOTE]
>  Veritabanını kullanarak ilk doldurmanız gerekir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] bir WCF Hizmeti yetkilendirme amacıyla kullanabilmeniz için önce özelliği.  
  
 Mevcut bir üyelik veritabanı zaten varsa üyelik özelliğini de kullanabilirsiniz [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web sitesi ve aynı kullanıcı adları ve parolalar yetkili hizmetinizi kullanmak kullanıcıları etkinleştirmek istiyor.  
  
 Bir WCF hizmeti üyelik özelliğini kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: ASP.NET üyelik sağlayıcıyı kullanacak](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).  
  
## <a name="aspnet-role-provider"></a>ASP.NET rol sağlayıcısını  
 Başka bir özelliği [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] yetkilendirme rolleri kullanarak yönetme olanağı. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Rol sağlayıcısını bir geliştirici kullanıcılar için roller oluşturmak ve her kullanıcı bir rolü veya rolleri atamak için etkinleştirir. Üyelik sağlayıcısı ile rollerini ve atamalarını bir veritabanında depolanır ve belirli bir uygulaması tarafından sağlanan araçları kullanarak doldurulabilir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rol sağlayıcısı. Olarak üyelik özelliğiyle WCF geliştiricileri bilgileri veritabanında rolleri tarafından hizmet Kullanıcıları yetkilendirmek için kullanabilirsiniz. Örneğin, rol sağlayıcısı ile birlikte kullanabileceklerini `PrincipalPermissionAttribute` erişim denetimi mekanizmasını yukarıda açıklanan.  
  
 Ayrıca [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] profiliniz varsa rol sağlayıcısı [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rol sağlayıcı veritabanı ve aynı kuralları ve kullanıcı atamaları kümesini WCF hizmetinizi kullanmak istiyorsanız.  
  
 Rol sağlayıcı özelliğini kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).  
  
## <a name="authorization-manager"></a>Yetkilendirme Yöneticisi  
 Yetkilendirme Yöneticisi'ni (AzMan) başka bir özellik birleştirir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] istemcilere yetki vermek için rol sağlayıcısı. Zaman [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] konakları AzMan bir Web hizmeti yetkilendirme hizmetine AzMan gerçekleştirilir böylece uygulamasına tümleştirilebilir. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Rol Yöneticisi uygulama rollerini yönetme, ekleyin ve kullanıcıların rollerini kaldırın ve rol üyeliğini denetleyin olanak tanıyan bir API sağlar, ancak bu, bir kullanıcı bir adlandırılmış bir görevi veya işlemi gerçekleştirmek için yetkili olup olmadığını sorgulamak izin vermez. AzMan tek işlemler tanımlamak ve görevlere birleştirip sağlar. AZMan ile rol denetimlerini yanı sıra, ayrıca bir kullanıcı bir görev yapıp yapamayacaklarını denetleyebilirsiniz. Rol ataması ve görev yetkilendirmesi uygulama dışında yapılandırılmış veya uygulama içinde program aracılığıyla gerçekleştirilir. Yöneticileri rol çalışma zamanında gerçekleştirebileceğiniz görevler değiştirmek ve rolleri, her kullanıcının üyeliğini yönetmek için Microsoft Yönetim Konsolu (MMC) ek bileşenini AzMan yönetim sağlar.  
  
 AzMan da kullanabilirsiniz ve [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zaten var olan bir AzMan yüklemesini erişimi ve AzMan/rol sağlayıcısı birleşimi özelliklerini kullanarak hizmet kullanıcılarınız yetkilendirmek istediğiniz rol sağlayıcısı.  
  
 AzMan hakkında daha fazla bilgi ve [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rol sağlayıcısı bkz [nasıl yapılır: ASP.NET 2.0 ile kullanım Yetkilendirme Yöneticisi (AzMan)](https://go.microsoft.com/fwlink/?LinkId=88951). AzMan ve rol sağlayıcısı için WCF hizmetleri kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol sağlayıcısını bir hizmetle kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md).  
  
## <a name="identity-model"></a>Kimlik modeli  
 Kimlik modeli istemciler yetkilendirmek için talepler ve ilkeleri yönetmenize olanak tanıyan API'ler kümesidir. Kimlik modeliyle çağıran hizmete kendi kimliğini doğrulamak, hizmeti için ilke kümesini talepleri karşılaştırma ve vermek veya erişimini engellemek için kullanılan karşılaştırma üzerine dayalı kimlik bilgilerinde yer alan her bir talep inceleyebilirsiniz.  
  
 Denetim ve erişim vermeden önce belirli ölçütleri ayarlamanıza olanak ince kimlik modeli kullanın. Örneğin, kullanırken <xref:System.Security.Permissions.PrincipalPermissionAttribute>, yalnızca kullanıcının kimliği doğrulanır ve belirli bir role ait ölçüttür. Buna karşılık, kimlik modeli kullanarak, kullanıcı 18 yıl üzerinden olmalıdır ve bir belgeyi görüntülemek için izin verilen önce geçerli bir sürücünün lisansına sahip olmadığını belirten bir ilke oluşturabilirsiniz.  
  
 Verilen belirteç senaryoda Federasyon kimlik bilgilerini kullanarak burada kimlik modeli talep tabanlı erişim denetiminden yararlanabilirsiniz örnek verilebilir. Federasyon ve verilen belirteçler hakkında daha fazla bilgi için bkz: [Federasyon ve verilen belirteçler](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
 Kimlik modeli hakkında daha fazla bilgi için bkz: [yönetme beyanlar ve yetkilendirmeyi kimlik modeliyle](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 [Nasıl yapılır: PrincipalPermissionAttribute Sınıfı ile Erişimi Kısıtlama](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 [Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 [Nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol Sağlayıcısını Bir Hizmetle Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 [Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [Temsilcilik ve Kimliğe Bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
