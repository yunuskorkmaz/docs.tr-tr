---
title: JSON Web Belirteci İşleyicisi
ms.date: 03/30/2017
ms.assetid: 9968f12e-e05d-4e6a-9b65-6896c0e31ab1
ms.openlocfilehash: 27c01a3d0ce0f2891b00ad28526d4753b9be4ce0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399044"
---
# <a name="json-web-token-handler"></a>JSON Web Belirteci İşleyicisi
Windows Identity Foundation için JSON Web Belirteci İşleyicisi uzantısı, uygulamalarınızda JSON Web Belirteçleri (JWT) oluşturmanıza ve doğrulamanıza olanak verir. JWT Belirteci İşleyicisi, diğer yerleşik güvenlik belirteci işleyicileri gibi WIF ardışık düzeninde çalışacak şekilde yapılandırılabilir, ancak basit uygulamalarda belirteç doğrulamasını gerçekleştirmek için bağımsız olarak da kullanılabilir. JWT Belirteci İşleyicisi, Microsoft Azure Active Directory kimlik doğrulaması gibi bir OAuth 2.0 taşıyıcı belirteci düzenini kullanırken özellikle yararlıdır.  
  
 JWT Belirteci İşleyicisi bir NuGet paketi olarak kullanılabilir. Bkz: [JSON Web belirteci işleyicisi paketini indirme](../../../docs/framework/security/downloading-the-json-web-token-handler-package.md) daha fazla bilgi için.  
  
## <a name="scenarios"></a>Senaryolar  
 JWT Belirteci İşleyicisi aşağıdaki temel senaryolara olanak tanır:  
  
-   **Bir JWT belirteci bir sunucu uygulaması, doğrulama**: Bu senaryoda, oturum açma web isteklerini işlemek için WIF kullanan bir sunucu uygulaması Lıtware adlı şirketin sahiptir. Litware, uygulamasının kimlik doğrulama için JWT belirteçleri kullanmasını sağlamak istemektedir. Uygulama, JWT Belirteci İşleyicisi ile güncelleştirilir ve ardından uygulama yapılandırması, WIF ardışık düzeni içine JWT belirteci işleyicisi eklenecek şekilde güncelleştirilir. Güncelleştirmeler yapıldıktan ve yeni istek WIF ardışık düzenine girdikten sonra, JWT belirteci yeni işleyiciyi kullanılarak doğrulanır ve kimlik doğrulama başarıyla gerçekleşmiş olur.  
  
-   **Bir JWT belirteci REST Web hizmeti doğrulamak**: Bu senaryoda, Lıtware adlı bir şirket, Windows Azure Active Directory tarafından güvenliği sağlanan bir REST web hizmeti sahiptir. Web hizmetine yapılan isteklerin kimliği, başarılı bir kimlik doğrulamasında sonra JWT belirtecini veren Microsoft Azure AD tarafından doğrulanmalıdır. Litware, web hizmetine erişmesi gereken bir istemci uygulamasına sahiptir. İstemci web hizmetine bir istekte bulunur ve Microsoft Azure AD'den aldığı JWT belirtecini sunar. Bu belirteç daha sonra JWT Belirteci İşleyicisi kullanılarak web hizmeti tarafından doğrulanır. JWT Belirteci İşleyicisi belirteci doğruladıktan sonra, istenen kaynak web hizmeti tarafından istemciye döndürülür.  
  
## <a name="features"></a>Özellikler  
 JWT Belirteci İşleyicisi aşağıdaki özellikleri sunar:  
  
-   **Bir JWT belirteci doğrulamak**: JWT belirteçleri kolayca uygulamanın WIF ardışık bir parçası olarak ya da belirteci işleyicinin Doğrulama mantığı tarafından doğrulanan veya WIF bağımsız olarak çağrılır  
  
-   **Bir JWT belirteci oluşturma**: JWT belirteci işleyicisi, aşağı akış Hizmetleri'nde yetkilendirme için JWT belirteçleri oluşturmak için kullanılabilir
