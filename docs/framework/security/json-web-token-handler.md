---
title: JSON Web Belirteci İşleyicisi
ms.date: 03/30/2017
ms.assetid: 9968f12e-e05d-4e6a-9b65-6896c0e31ab1
ms.openlocfilehash: 3dc76f3de714fd91d397cc240d02a1a8605fe18b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045327"
---
# <a name="json-web-token-handler"></a>JSON Web Belirteci İşleyicisi
Windows Identity Foundation için JSON Web Belirteci İşleyicisi uzantısı, uygulamalarınızda JSON Web Belirteçleri (JWT) oluşturmanıza ve doğrulamanıza olanak verir. JWT Belirteci İşleyicisi, diğer yerleşik güvenlik belirteci işleyicileri gibi WIF ardışık düzeninde çalışacak şekilde yapılandırılabilir, ancak basit uygulamalarda belirteç doğrulamasını gerçekleştirmek için bağımsız olarak da kullanılabilir. JWT Belirteci İşleyicisi, Microsoft Azure Active Directory kimlik doğrulaması gibi bir OAuth 2.0 taşıyıcı belirteci düzenini kullanırken özellikle yararlıdır.  
  
 JWT Belirteci İşleyicisi bir NuGet paketi olarak kullanılabilir. Daha fazla bilgi için bkz. [JSON Web Token Işleyicisi paketini indirme](downloading-the-json-web-token-handler-package.md) .  
  
## <a name="scenarios"></a>Senaryolar  
 JWT Belirteci İşleyicisi aşağıdaki temel senaryolara olanak tanır:  
  
- **Sunucu UYGULAMASıNDA JWT belirtecini doğrulama**: Bu senaryoda, Litwlar adlı bir şirketin, Web oturum açma isteklerini işlemek için WıF kullanan bir sunucu uygulaması vardır. Litware, uygulamasının kimlik doğrulama için JWT belirteçleri kullanmasını sağlamak istemektedir. Uygulama, JWT Belirteci İşleyicisi ile güncelleştirilir ve ardından uygulama yapılandırması, WIF ardışık düzeni içine JWT belirteci işleyicisi eklenecek şekilde güncelleştirilir. Güncelleştirmeler yapıldıktan ve yeni istek WIF ardışık düzenine girdikten sonra, JWT belirteci yeni işleyiciyi kullanılarak doğrulanır ve kimlik doğrulama başarıyla gerçekleşmiş olur.  
  
- **Rest Web HIZMETINDE JWT belirtecini doğrulama**: Bu senaryoda, Litwlar adlı bir şirketin, Windows Azure Active Directory tarafından güvenliği sağlanmış bir REST Web hizmeti vardır. Web hizmetine yapılan isteklerin kimliği, başarılı bir kimlik doğrulamasında sonra JWT belirtecini veren Microsoft Azure AD tarafından doğrulanmalıdır. Litware, web hizmetine erişmesi gereken bir istemci uygulamasına sahiptir. İstemci web hizmetine bir istekte bulunur ve Microsoft Azure AD'den aldığı JWT belirtecini sunar. Bu belirteç daha sonra JWT Belirteci İşleyicisi kullanılarak web hizmeti tarafından doğrulanır. JWT Belirteci İşleyicisi belirteci doğruladıktan sonra, istenen kaynak web hizmeti tarafından istemciye döndürülür.  
  
## <a name="features"></a>Özellikler  
 JWT Belirteci İşleyicisi aşağıdaki özellikleri sunar:  
  
- **JWT belirtecini doğrulama**: JWT belirteçleri, uygulamanın WıF ardışık düzeninin bir parçası olarak veya WıF 'den bağımsız olarak çağrıldığında, belirteç işleyicisinin doğrulama mantığı tarafından kolayca doğrulanabilir  
  
- **JWT belirteci oluştur**: JWT belirteci Işleyicisi, aşağı akış hizmetlerinde yetkilendirme için JWT belirteçleri oluşturmak üzere kullanılabilir
