---
title: Asıl ve Kimlik Nesneleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- WindowsIdentity objects
- GenericIdentity objects
- GenericPrincipal objects
- identity objects, about identity objects
- security [.NET Framework], identity objects
- principal objects, about principal objects
- security [.NET Framework], principals
- WindowsPrincipal objects
ms.assetid: aa5930ad-f3d7-40aa-b6f6-c6edcd5c64f7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b8c7616a3187cd5fa28f231dffd15b0bfeea4b7f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43872549"
---
# <a name="principal-and-identity-objects"></a>Asıl ve Kimlik Nesneleri
Yönetilen kod kimliği veya sorumlu rolünü bulabilir bir <xref:System.Security.Principal.IPrincipal> başvuru içeren bir nesne bir <xref:System.Security.Principal.IIdentity> nesne. Kullanıcı ve grup hesapları gibi tanıdık kavramları kimlik ve asıl nesneleri karşılaştırmak yararlı olabilir. Grup hesapları belirli kullanıcıları ve bunların sahip hakları kategorilerini temsil ederken çoğu ağ ortamlarında, kullanıcı hesaplarını kişiler veya programları temsil eder. Benzer şekilde, rol üyeliğini ve güvenlik kapsamlarını temsil ederken kullanıcılar, .NET Framework kimlik nesneleri temsil eder. .NET Framework'teki asıl nesne bir rolü ve bir kimlik nesne kapsüller. .NET framework uygulamaları kimliğini veya daha çok rolü üyeliğine göre sorumlu hakları vermek mümkündür.  
  
## <a name="identity-objects"></a>Kimlik nesneleri  
 Kimlik nesne Doğrulanmakta olan varlık ve kullanıcı hakkındaki bilgileri yalıtır. Bunların en temel düzeyde, bir ad ve kimlik doğrulama türü kimlik nesneleri içerir. Kimlik doğrulaması türünü, Kerberos V5 gibi bir desteklenen oturum açma protokol veya özel bir değer olabilir, ancak adı bir kullanıcının adını veya bir Windows hesabının adını ya da olabilir. .NET Framework tanımlayan bir <xref:System.Security.Principal.GenericIdentity> çoğu özel oturum açma senaryoları ve daha fazla özelleştirilmiştir için kullanılan nesne <xref:System.Security.Principal.WindowsIdentity> üzerinde Windows kimlik doğrulaması için uygulamanızı istediğinizde, kullanılabilen bir nesne. Ayrıca, özel kullanıcı bilgileri yalıtan kendi kimlik sınıfınızı tanımlayabilirsiniz.  
  
 <xref:System.Security.Principal.IIdentity> Arabirim bir ad ve bir kimlik doğrulama türü, Kerberos V5 veya NTLM gibi erişmek için özellikleri tanımlar. Tüm **kimlik** sınıfları uygulama **IIdentity** arabirimi. Arasında gerekli bir ilişki yoktur bir **kimlik** nesne ve Windows NT İşlem belirteci, bir iş parçacığı anda yürütülmekte olan altında. Ancak, varsa **kimlik** nesnesi bir **WindowsIdentity** nesne kimliğini bir Windows NT güvenlik belirteci temsil etmek için varsayılır.  
  
## <a name="principal-objects"></a>Asıl nesneler  
 Asıl nesne kodu altında çalıştığı güvenlik bağlamını temsil eder. Rol tabanlı güvenlik kullanan uygulamalar, asıl nesneyle ilişkili rolüne dayalı hakkı. Benzer şekilde kimlik nesneleri, .NET Framework sağlar bir <xref:System.Security.Principal.GenericPrincipal> nesnesi ve bir <xref:System.Security.Principal.WindowsPrincipal> nesne. Kendi özel asıl sınıflar da tanımlayabilirsiniz.  
  
 <xref:System.Security.Principal.IPrincipal> Arabirimi tanımlar, ilişkili bir erişmek için bir özellik **kimlik** nesne kullanıcı tarafından tanımlanmış olup olmadığını belirlemek için bir yöntem yanı sıra **asıl** nesne üyesi olduğu bir belirli bir roldür. Tüm **asıl** sınıfları uygulama **IPrincipal** yanı sıra tüm ek özellikleri ve gerekli yöntemleri arabirim. Örneğin, ortak dil çalışma zamanı sağlar **WindowsPrincipal** sınıfını, Windows NT veya Windows 2000 Grup üyeliği rollerine eşlemek için ek işlevselliğini uygular.  
  
 A **asıl** nesne bir çağrı bağlamına bağlı (<xref:System.Runtime.Remoting.Messaging.CallContext>) bir uygulama etki alanı içinde nesne (<xref:System.AppDomain>). Varsayılan arama bağlamı her zaman her biri yeni oluşturulan **AppDomain**, böylelikle her zaman kabul etmek bir çağrı bağlamı **asıl** nesne. Yeni bir iş parçacığı oluşturulduğunda bir **CallContext** nesnesi iş parçacığı da oluşturulur. **Asıl** nesne başvurusu yeni iş parçacığının için oluşturma iş parçacığından otomatik olarak kopyalanır **CallContext**. Çalışma zamanının hangi belirleyemiyorsa **asıl** nesne iş parçacığı oluşturan kişiye ait, için varsayılan ilke takip eden **asıl** ve **kimlik** nesnesi oluşturma.  
  
 Yapılandırılabilir uygulama etki alanına özel ilkesi için ne tür karar verme kuralları tanımlar; **asıl** yeni bir uygulama etki alanı ile ilişkilendirilecek bir nesne. Güvenlik İlkesi verir yerlerde, çalışma zamanı oluşturabilirsiniz **asıl** ve **kimlik** işletim sistemi belirteç yansıtan nesneleri geçerli yürütme iş parçacığı ile ilişkili. Varsayılan olarak, çalışma zamanı kullanan **asıl** ve **kimlik** kimliği doğrulanmamış kullanıcılar temsil eden nesneleri. Bu varsayılan çalışma zamanı oluşturmaz **asıl** ve **kimlik** kod erişim girişiminde bulunmadan nesneleri.  
  
 Güvenilen uygulama etki alanı oluşturan kodu, oluşumunu varsayılan denetleyen bir uygulama etki alanı ilkesi ayarlayabilirsiniz **asıl** ve **kimlik** nesneleri. Bu uygulama etki alanına özel ilke, uygulama etki alanındaki tüm yürütme iş parçacığı için geçerlidir. Yönetilmeyen, güvenilen bir ana doğası gereği Bu ilke ayarlama özelliğini var, ancak bu ilkenin ayarlar yönetilen kod gerekir <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> etki alanı ilkesi denetleme.  
  
 İletirken bir **asıl** nesnenin uygulama etki alanları arasında ancak aynı işlem içinde (ve bu nedenle aynı bilgisayarda), uzak altyapı başvuru kopyalar **asıl** Arayanın bağlamına çağrıyı yapanın bağlam ile ilişkili nesne.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: WindowsPrincipal Nesnesi Oluşturma](../../../docs/standard/security/how-to-create-a-windowsprincipal-object.md)  
- [Nasıl yapılır: GenericPrincipal ve GenericIdentity Nesneleri Oluşturma](../../../docs/standard/security/how-to-create-genericprincipal-and-genericidentity-objects.md)  
- [Sorumlu Nesnesini Değiştirme](../../../docs/standard/security/replacing-a-principal-object.md)  
- [Kimliğe Bürünme ve Geri Dönme](../../../docs/standard/security/impersonating-and-reverting.md)  
- [Rol Tabanlı Güvenlik](../../../docs/standard/security/role-based-security.md)  
- [Temel Güvenlik Kavramları](../../../docs/standard/security/key-security-concepts.md)
