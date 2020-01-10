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
ms.openlocfilehash: c2fadc2d5bb3a787123678a93fa96f8966debbd5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705957"
---
# <a name="principal-and-identity-objects"></a>Asıl ve Kimlik Nesneleri
Yönetilen kod, bir <xref:System.Security.Principal.IIdentity> nesnesine yönelik bir başvuru içeren <xref:System.Security.Principal.IPrincipal> nesnesi aracılığıyla bir Sorumlunun kimliğini veya rolünü bulabilir. Kimlik ve asıl nesneleri kullanıcı ve grup hesapları gibi tanıdık kavramlarla karşılaştırmak faydalı olabilir. Çoğu ağ ortamında, Kullanıcı hesapları kişileri veya programları temsil ederken grup hesapları bazı kullanıcı kategorilerini ve sahip oldukları hakları temsil eder. Benzer şekilde, .NET Framework kimlik nesneleri kullanıcıları temsil ederken, roller üyelikleri ve güvenlik bağlamlarını temsil eder. .NET Framework, Principal nesnesi hem bir kimlik nesnesini hem de bir rolü kapsar. .NET Framework uygulamalar, kimlik veya daha yaygın olarak rolün üyeliği temelinde sorumlu için haklar verir.  
  
## <a name="identity-objects"></a>Kimlik nesneleri  
 Identity nesnesi doğrulanan kullanıcı veya varlıkla ilgili bilgileri kapsüller. En temel seviyesindeki kimlik nesnelerinde bir ad ve kimlik doğrulama türü bulunur. Ad, bir kullanıcının adı ya da bir Windows hesabının adı olabilir, ancak kimlik doğrulama türü Kerberos V5 gibi desteklenen bir oturum açma Protokolü veya özel bir değer olabilir. .NET Framework, uygulamanızın Windows kimlik doğrulamasına dayanmasını istediğinizde kullanılabilecek, çok sayıda özel oturum açma senaryosu ve daha özelleştirilmiş bir <xref:System.Security.Principal.WindowsIdentity> nesnesi için kullanılabilecek bir <xref:System.Security.Principal.GenericIdentity> nesnesi tanımlar. Ayrıca, Özel Kullanıcı bilgilerini kapsülleyen kendi kimlik sınıfınızı tanımlayabilirsiniz.  
  
 <xref:System.Security.Principal.IIdentity> arabirimi, Kerberos V5 veya NTLM gibi bir ad ve kimlik doğrulama türüne erişim özelliklerini tanımlar. Tüm **kimlik** sınıfları **IIdentity** arabirimini uygular. Bir iş parçacığının çalıştırıldığı bir **kimlik** nesnesi ve Windows NT işlem belirteci arasında gerekli bir ilişki yoktur. Ancak, **kimlik** nesnesi bir **WindowsIdentity** Nesnecidir, kimliğin bir Windows NT güvenlik belirtecini temsil ettiği varsayılır.  
  
## <a name="principal-objects"></a>Principal nesneleri  
 Principal nesnesi, kodun çalıştığı güvenlik bağlamını temsil eder. Rol tabanlı güvenlik uygulayan uygulamalar, bir asıl nesneyle ilişkili role dayalı olarak haklar verir. Kimlik nesnelerine benzer şekilde, .NET Framework bir <xref:System.Security.Principal.GenericPrincipal> nesnesi ve bir <xref:System.Security.Principal.WindowsPrincipal> nesnesi sağlar. Ayrıca, kendi özel asıl sınıflarınızı tanımlayabilirsiniz.  
  
 <xref:System.Security.Principal.IPrincipal> arabirimi, ilişkili bir **kimlik** nesnesine erişmek için bir özelliği ve **asıl** nesne tarafından tanımlanan kullanıcının belirli bir rolün üyesi olup olmadığını belirlemek için bir yöntemi tanımlar. Tüm **asıl** sınıflar, gereken ek özellikleri ve yöntemleri de, **IPrincipal** arabirimini ve uygular. Örneğin, ortak dil çalışma zamanı, Windows NT veya Windows 2000 Grup üyeliğini rollere eşlemek için ek işlevsellik uygulayan **WindowsPrincipal** sınıfını sağlar.  
  
 Bir **Principal** nesnesi bir uygulama etki alanındaki (<xref:System.AppDomain>) bir çağrı bağlamı (<xref:System.Runtime.Remoting.Messaging.CallContext>) nesnesine bağlanır. Her yeni **AppDomain**ile her zaman bir varsayılan çağrı bağlamı oluşturulur, bu nedenle **asıl** nesneyi kabul etmek için her zaman bir çağrı bağlamı bulunur. Yeni bir iş parçacığı oluşturulduğunda iş parçacığı için bir **CallContext** nesnesi de oluşturulur. **Asıl** nesne başvurusu, oluşturma iş parçacığından yeni Iş parçacığının **CallContext**'e otomatik olarak kopyalanır. Çalışma zamanı hangi **asıl** nesnenin iş parçacığı oluşturucusuna ait olduğunu Belirleyeleyemiyorsa, **asıl** ve **kimlik** nesnesi oluşturma için varsayılan ilkeyi izler.  
  
 Yapılandırılabilir bir uygulama etki alanına özgü ilke, yeni bir uygulama etki alanıyla hangi tür **asıl** nesnenin ilişkilendirileceğine karar verme kurallarını tanımlar. Güvenlik ilkesinin izin verdiği durumlarda çalışma zamanı, yürütmenin geçerli iş parçacığıyla ilişkili işletim sistemi belirtecini yansıtan **asıl** ve **kimlik** nesneleri oluşturabilir. Varsayılan olarak, çalışma zamanı kimliği doğrulanmamış kullanıcıları temsil eden **asıl** ve **kimlik** nesnelerini kullanır. Çalışma zamanı, kod onlara erişmeye çalışana kadar bu varsayılan **sorumlusu** ve **kimlik** nesnelerini oluşturmaz.  
  
 Bir uygulama etki alanı oluşturan güvenilir kod, varsayılan **asıl** ve **kimlik** nesnelerinin oluşturulmasını denetleyen uygulama etki alanı ilkesini ayarlayabilir. Bu uygulama etki alanına özgü ilke, bu uygulama etki alanındaki tüm yürütme iş parçacıkları için geçerlidir. Yönetilmeyen ve güvenilen bir ana bilgisayar doğal olarak bu ilkeyi ayarlayabilme özelliğine sahiptir, ancak bu ilkeyi ayarlayan yönetilen kodun etki alanı ilkesini denetlemek için <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> olması gerekir.  
  
 **Ana** nesne, uygulama etki alanları arasında, ancak aynı işlem içinde (ve dolayısıyla aynı bilgisayarda) iletilirken, uzaktan iletişim altyapısı, çağıran bağlamı Ile ilişkili **Principal** nesnesine bir başvuru kopyalar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: WindowsPrincipal Nesnesi Oluşturma](../../../docs/standard/security/how-to-create-a-windowsprincipal-object.md)
- [Nasıl yapılır: GenericPrincipal ve GenericIdentity Nesneleri Oluşturma](../../../docs/standard/security/how-to-create-genericprincipal-and-genericidentity-objects.md)
- [Sorumlu Nesnesini Değiştirme](../../../docs/standard/security/replacing-a-principal-object.md)
- [Kimliğe Bürünme ve Geri Dönme](../../../docs/standard/security/impersonating-and-reverting.md)
- [Rol Tabanlı Güvenlik](../../../docs/standard/security/role-based-security.md)
- [Temel Güvenlik Kavramları](../../../docs/standard/security/key-security-concepts.md)
