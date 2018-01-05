---
title: "Erişim Denetimi Mekanizmaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF security
- access control [WCF]
ms.assetid: 9d576122-3f55-4425-9acf-b23d0781e966
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1d856af12269416b3303e617338165771ae4f2b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="access-control-mechanisms"></a>Erişim Denetimi Mekanizmaları
Erişimi ile birkaç şekilde denetleyebilirsiniz [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Bu konu, kısa bir süre çeşitli mekanizmalar açıklar ve zaman her kullanılacağı hakkında öneriler sağlar; kullanılacak doğru mekanizması seçmenize yardımcı olmak için tasarlanmıştır. Erişim teknolojileri karmaşıklık sırada listelenir. En kolayıdır <xref:System.Security.Permissions.PrincipalPermissionAttribute>; en karmaşık kimlik modelidir.  
  
 Bu mekanizmalar, kimliğe bürünme ve temsilci ile yanı sıra [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] içinde açıklanan [temsilcilik ve kimliğe bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="principalpermissionattribute"></a>PrincipalPermissionAttribute  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> Bir hizmet yöntemi için erişimi kısıtlamak için kullanılır. Öznitelik bir yönteme uygulandığında, bu belirli arayanın kimliği veya bir Windows grubu üyeliği talep için kullanılabilir veya [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rol. İstemci bir X.509 sertifikası kullanılarak kimlik doğrulaması gerekiyorsa, konu adı ve sertifikanın parmak izi karakterlerinden oluşur birincil bir kimlik verilir.  
  
 Kullanım <xref:System.Security.Permissions.PrincipalPermissionAttribute> üzerinde çalıştığı bilgisayar üzerindeki kaynaklara erişimi denetlemek için ve hizmet kullanıcılarının her zaman Hizmeti'nin çalıştığı aynı Windows etki alanının parçası olur. Erişim düzeyleri belirttiğiniz Windows grupları kolayca oluşturabilirsiniz (none, salt okunur gibi ya da okuma ve yazma).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]özniteliğini kullanarak bkz [nasıl yapılır: PrincipalPermissionAttribute sınıfı ile erişimi kısıtla](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]kimlik, bkz: [hizmet kimliği ve kimlik doğrulama](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="aspnet-membership-provider"></a>ASP.NET üyelik sağlayıcısı  
 Bir özellik olan [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] üyelik sağlayıcısı'dır. Üyelik sağlayıcısı teknik bir erişim denetimi mekanizması olmamasına karşın, hizmetin uç noktasına erişebildiğinden olası kimlikleri kümesi sınırlayarak hizmetine erişimi denetleme sağlar. Üyelik özelliği site hesaplarını oluşturmak üzere kullanıcıların bir Web sitesinin kullanıcı adı/parola birleşimleri ile doldurulan bir veritabanı içerir. Üyelik sağlayıcısı kullanan bir hizmete erişmek için bir kullanıcı kendi kullanıcı adı ve parola ile oturum açmalısınız.  
  
> [!NOTE]
>  Veritabanını kullanan ilk doldurmanız gerekir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] önce özelliği bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti, yetkilendirme amacıyla da kullanabilirsiniz.  
  
 Varolan bir üyelik veritabanı zaten varsa üyelik özelliğini de kullanabilirsiniz [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web sitesi ve aynı kullanıcı adları ve parolalar yetkili hizmetinizi aynı kullanıcıların kullanmasını istediğinizde.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Üyelik özelliğini kullanarak bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet için bkz: [nasıl yapılır: ASP.NET üyelik sağlayıcıyı kullanacak](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).  
  
## <a name="aspnet-role-provider"></a>ASP.NET rol sağlayıcısı  
 Başka bir özelliği olan [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rolleri kullanarak yetkilendirmeyi yönetme yeteneği. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Rol sağlayıcısı kullanıcıları için roller oluşturmak için ve her kullanıcının bir rol veya rolleri atamak için bir geliştirici sağlar. Üyelik sağlayıcısı ile rollerini ve atamalarını bir veritabanında depolanır ve belirli bir uygulama tarafından sağlanan araçları kullanarak doldurulabilir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rol sağlayıcısı. Üyelik özelliğiyle olduğu gibi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] geliştiriciler bilgileri veritabanında rolleri tarafından service Kullanıcıları yetkilendirmek için kullanabilirsiniz. Örneğin, rol sağlayıcısı ile birlikte kullanabileceklerini `PrincipalPermissionAttribute` erişim denetimi mekanizmasını yukarıda açıklanan.  
  
 Aynı zamanda [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] varolan varsa rol sağlayıcısı [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rol sağlayıcı veritabanı ve kuralları ve kullanıcı atamalarını aynı kümesini kullanmak istiyorsanız, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]rol sağlayıcı özelliği bkz [nasıl yapılır: ASP.NET rol sağlayıcısını bir hizmetle kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).  
  
## <a name="authorization-manager"></a>Yetkilendirme Yöneticisi  
 Yetkilendirme Yöneticisi'ni (AzMan) başka bir özellik birleştirir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] istemcileri yetkilendirmek için rol sağlayıcısı. Zaman [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] konakları AzMan bir Web hizmeti yetkilendirme hizmetine AzMan yapılır böylece uygulamasına tümleştirilebilir. [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Rol Yöneticisi uygulama rolleri yönetmek, Ekle ve kullanıcıların rollerini kaldırın ve rol üyeliğini denetleyin olanak tanıyan bir API sağlar, ancak, bir kullanıcı bir adlandırılmış görevi veya işlemi gerçekleştirmek için yetkili olup olmadığını sorgulamaya izin vermez. AzMan, tek tek işlemleri tanımlayın ve görevlere birleştirip olanak sağlar. AZMan ile rol denetimlerini ek olarak, ayrıca bir kullanıcı bir görevi gerçekleştirmek olup olmadığını kontrol edebilirsiniz. Rol atama ve görev yetkilendirme uygulama dışında yapılandırılan veya uygulama içinde program aracılığıyla gerçekleştirilir. Yöneticilerin bir rolü çalışma zamanında gerçekleştirebileceğiniz görevler değiştirmek ve her kullanıcının üyelik rolleri yönetmek için Microsoft Yönetim Konsolu (MMC) ek bileşenini AzMan yönetim sağlar.  
  
 AzMan de kullanabilirsiniz ve [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] zaten var olan bir AzMan yüklemesi erişiminiz ve AzMan/rol sağlayıcısı birleşimi özelliklerini kullanarak hizmet kullanıcılarınızın yetkilendirmek istediğiniz rol sağlayıcısı.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]AzMan ve [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] rol sağlayıcısı bkz [nasıl yapılır: ASP.NET 2.0 ile kullanım Yetkilendirme Yöneticisi (AzMan)](http://go.microsoft.com/fwlink/?LinkId=88951). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]AzMan ve rol sağlayıcısı kullanarak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri, bkz: [nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol sağlayıcısını bir hizmetle kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md).  
  
## <a name="identity-model"></a>Kimlik modeli  
 Kimlik modelinde, talepler ve ilkeleri istemcileri yetkilendirmek için yönetmenize olanak tanıyan API kümesidir. Kimlik modeliyle hizmete kendi kimliğini doğrulamak, talepleri ilkeleri kümesine hizmet için karşılaştırın ve erişim vermek veya reddetmek için kullanılan çağıran karşılaştırma üzerine dayalı kimlik bilgilerini içinde yer alan her talep inceleyebilirsiniz.  
  
 Denetim ve erişim vermeden önce belirli ölçütleri ayarlamanıza olanak ince varsa kimlik modeli kullanır. Örneğin, kullanırken <xref:System.Security.Permissions.PrincipalPermissionAttribute>, yalnızca kullanıcının kimliği doğrulanır ve belirli bir role ait ölçüttür. Buna karşılık, kimlik modeli kullanarak, kullanıcı 18 yaşın üzerinde olmalıdır ve bir belgeyi görüntülemek için izin verilen önce geçerli bir sürücünün lisansına sahip bildiren bir ilke oluşturabilirsiniz.  
  
 Burada kimlik modeli talebine dayalı erişim denetiminden yararlanabilirsiniz bir Federasyon kimlik bilgilerini verilen belirteç senaryosunda kullanırken örnektir. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Federasyon ve verilen belirteçleri bkz [Federasyon ve verilen belirteçleri](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Kimlik modelinde, bkz: [yönetme beyanlar ve yetkilendirmeyi kimlik modeliyle](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 [Nasıl yapılır: PrincipalPermissionAttribute Sınıfı ile Erişimi Kısıtlama](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 [Nasıl yapılır: ASP.NET Rol Sağlayıcısını Bir Hizmetle Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 [Nasıl yapılır: ASP.NET Yetkilendirme Yöneticisi Rol Sağlayıcısını Bir Hizmetle Kullanma](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 [Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [Temsilcilik ve Kimliğe Bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
