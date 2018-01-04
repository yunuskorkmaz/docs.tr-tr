---
title: "Asıl ve Kimlik Nesneleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 02c8b4b9f46f051e42fb2ae85a39b6ff48ad2f1a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="principal-and-identity-objects"></a>Asıl ve Kimlik Nesneleri
Yönetilen kod Bul kimliğini ya da rolü bir asıl bir <xref:System.Security.Principal.IPrincipal> bir başvuru içeren bir nesne, bir <xref:System.Security.Principal.IIdentity> nesnesi. Kullanıcı ve grup hesaplarını gibi bilinen kavramlarını kimlik ve asıl nesneleri karşılaştırmak faydalı olabilir. Kullanıcılar ve bunlar sahip olduğu haklar belirli kategorilerini grup hesaplarını temsil ederken çoğu ağ ortamlarında, kullanıcı hesapları kişiler veya programları temsil eder. Benzer şekilde, rol üyeliklerini ve güvenlik kapsamları temsil ederken .NET Framework kimlik nesneleri kullanıcılar, temsil eder. .NET Framework'teki asıl nesne bir rolü ve bir kimlik nesne yalıtır. .NET framework uygulamaları kimliğini veya daha çok rolü üyeliğine göre asıl hakları.  
  
## <a name="identity-objects"></a>Kimlik nesneleri  
 Identity nesnesi kullanıcı veya Doğrulanmakta olan varlık hakkındaki bilgileri yalıtır. Bunların en temel düzeyde bir ad ve bir kimlik doğrulama türü kimlik nesneleri içerir. Kimlik doğrulama türü bir desteklenen oturum açma protokolü, Kerberos V5 gibi veya özel bir değer olabileceği adı ya da bir kullanıcının adını veya bir Windows hesabı adı olabilir. .NET Framework tanımlayan bir <xref:System.Security.Principal.GenericIdentity> çoğu özel oturum açma senaryoları ve daha özelleştirilmiş için kullanılan nesne <xref:System.Security.Principal.WindowsIdentity> Windows kimlik doğrulamasını kullanan uygulamanıza istediğinizde kullanılabilir nesne. Ayrıca, özel kullanıcı bilgileri yalıtan kendi kimlik sınıfı tanımlayabilirsiniz.  
  
 <xref:System.Security.Principal.IIdentity> Arabirimi için bir ad ve Kerberos V5 veya NTLM gibi bir kimlik doğrulama türü erişme özelliklerini tanımlar. Tüm **kimlik** sınıfları uygulama **IIdentity** arabirimi. Gerekli bir ilişkisi yok arasında bir **kimlik** nesne ve Windows NT İşlem belirteci, bir iş parçacığı şu anda yürütülmekte altında. Ancak, varsa **kimlik** nesne bir **WindowsIdentity** nesne kimliği, bir Windows NT güvenlik belirteci temsil etmek için varsayılır.  
  
## <a name="principal-objects"></a>Asıl nesneler  
 Asıl nesne kodu altında çalıştığı güvenlik bağlamını temsil eder. Rol tabanlı güvenlik kullanan uygulamalar asıl bir nesneyle ilişkili role göre hakları. Kimlik nesneleri benzeyen, .NET Framework sağlayan bir <xref:System.Security.Principal.GenericPrincipal> nesne ve <xref:System.Security.Principal.WindowsPrincipal> nesne. Kendi özel asıl sınıflar tanımlayabilir.  
  
 <xref:System.Security.Principal.IPrincipal> Arabirimi tanımlar ilişkili bir erişmek için bir özellik **kimlik** nesne kullanıcı tarafından tanımlanan olup olmadığını belirlemek için bir yöntem yanı sıra **asıl** nesne üyesi olduğu bir belirli bir roldür. Tüm **asıl** sınıfları uygulama **IPrincipal** yanı ek özellikleri ve gerekli yöntemleri arabirim. Örneğin, ortak dil çalışma zamanı sağlar **WindowsPrincipal** Windows NT veya Windows 2000 Grup üyeliği rollerine eşlemek için ek işlevler uygulayan sınıfı.  
  
 A **asıl** nesnesi bir çağrı bağlamına bağlı (<xref:System.Runtime.Remoting.Messaging.CallContext>) uygulama etki alanı içinde nesne (<xref:System.AppDomain>). Varsayılan çağrı içeriği her zaman her yeni oluşturulan **AppDomain**kabul etmek bir çağrı içeriği her zaman gelir **asıl** nesnesi. Yeni bir iş parçacığı oluşturulurken bir **CallContext** nesnesi iş parçacığı için de oluşturulur. **Asıl** nesne başvurusu otomatik olarak kopyalanır oluşturma iş parçacığından yeni iş parçacığının için **CallContext**. Çalışma zamanı hangi belirleyemiyorsa **asıl** nesnenin iş parçacığı oluşturan kişiye ait, için varsayılan ilke izleyen **asıl** ve **kimlik** nesnesi oluşturma.  
  
 Ne tür karar verme kuralları yapılandırılabilir uygulama etki alanına özgü İlkesi tanımlar **asıl** yeni bir uygulama etki alanı ile ilişkilendirmek için nesne. Güvenlik İlkesi izin verir. Burada, çalışma zamanı oluşturabilirsiniz **asıl** ve **kimlik** işletim sistemi belirteci yansıtacak nesneleri geçerli yürütme iş parçacığı ile ilişkilendirilmiş. Varsayılan olarak, çalışma zamanı kullanır **asıl** ve **kimlik** kimliği doğrulanmamış kullanıcıların temsil eden nesne. Çalışma zamanı bu varsayılan oluşturmaz **asıl** ve **kimlik** kodu bunlara erişim girişiminde bulunmadan nesneleri.  
  
 Uygulama etki alanı oluşturur kod varsayılan yapımı denetimleri uygulama etki alanı ilkesi ayarlayabilirsiniz güvenilen **asıl** ve **kimlik** nesneleri. Bu uygulama etki alanındaki tüm yürütme iş parçacığı için bu uygulama etki alanına özgü ilke uygulanır. Yönetilmeyen, güvenilir bir ana kendiliğinden Bu ilke ayarlama özelliği vardır, ancak bu ilke ayarlar yönetilen kod gerekir <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> etki alanı ilkesi denetleme.  
  
 İletirken bir **asıl** nesne uygulama etki alanları arasında ancak aynı işlem içinde (ve bu nedenle aynı bilgisayarda), bir başvuru remoting altyapı kopyalar **asıl** Arayanın çağıranın bağlam bağlamına ilişkili nesne.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: WindowsPrincipal Nesnesi Oluşturma](../../../docs/standard/security/how-to-create-a-windowsprincipal-object.md)  
 [Nasıl yapılır: GenericPrincipal ve GenericIdentity Nesneleri Oluşturma](../../../docs/standard/security/how-to-create-genericprincipal-and-genericidentity-objects.md)  
 [Sorumlu Nesnesini Değiştirme](../../../docs/standard/security/replacing-a-principal-object.md)  
 [Kimliğe Bürünme ve Geri Dönme](../../../docs/standard/security/impersonating-and-reverting.md)  
 [Rol Tabanlı Güvenlik](../../../docs/standard/security/role-based-security.md)  
 [Temel Güvenlik Kavramları](../../../docs/standard/security/key-security-concepts.md)
