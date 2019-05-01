---
title: JSON Web Belirteci İşleyicisi
ms.date: 03/30/2017
ms.assetid: 9968f12e-e05d-4e6a-9b65-6896c0e31ab1
ms.openlocfilehash: 27c01a3d0ce0f2891b00ad28526d4753b9be4ce0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790136"
---
# <a name="json-web-token-handler"></a>JSON Web Belirteci İşleyicisi
Windows Identity Foundation için JSON Web Belirteci İşleyicisi uzantısı, uygulamalarınızda JSON Web Belirteçleri (JWT) oluşturmanıza ve doğrulamanıza olanak verir. JWT Belirteci İşleyicisi, diğer yerleşik güvenlik belirteci işleyicileri gibi WIF ardışık düzeninde çalışacak şekilde yapılandırılabilir, ancak basit uygulamalarda belirteç doğrulamasını gerçekleştirmek için bağımsız olarak da kullanılabilir. JWT Belirteci İşleyicisi, Microsoft Azure Active Directory kimlik doğrulaması gibi bir OAuth 2.0 taşıyıcı belirteci düzenini kullanırken özellikle yararlıdır.  
  
 JWT Belirteci İşleyicisi bir NuGet paketi olarak kullanılabilir. Bkz: [JSON Web belirteci işleyicisi paketini indirme](../../../docs/framework/security/downloading-the-json-web-token-handler-package.md) daha fazla bilgi için.  
  
## <a name="scenarios"></a>Senaryolar  
 JWT Belirteci İşleyicisi aşağıdaki temel senaryolara olanak tanır:  
  
- **Bir sunucu uygulamasında JWT belirtecini doğrulama**: Bu senaryoda, Litware adlı bir şirketin WIF oturum açma web isteklerini işlemek için kullandığı bir sunucu uygulaması vardır. Litware, uygulamasının kimlik doğrulama için JWT belirteçleri kullanmasını sağlamak istemektedir. Uygulama, JWT Belirteci İşleyicisi ile güncelleştirilir ve ardından uygulama yapılandırması, WIF ardışık düzeni içine JWT belirteci işleyicisi eklenecek şekilde güncelleştirilir. Güncelleştirmeler yapıldıktan ve yeni istek WIF ardışık düzenine girdikten sonra, JWT belirteci yeni işleyiciyi kullanılarak doğrulanır ve kimlik doğrulama başarıyla gerçekleşmiş olur.  
  
- **JWT belirtecini REST Web hizmetinde doğrulama**: Bu senaryoda, Litware adlı bir şirketin Windows Azure Active Directory tarafından güvenli hale getirilmiş bir REST web hizmeti vardır. Web hizmetine yapılan isteklerin kimliği, başarılı bir kimlik doğrulamasında sonra JWT belirtecini veren Microsoft Azure AD tarafından doğrulanmalıdır. Litware, web hizmetine erişmesi gereken bir istemci uygulamasına sahiptir. İstemci web hizmetine bir istekte bulunur ve Microsoft Azure AD'den aldığı JWT belirtecini sunar. Bu belirteç daha sonra JWT Belirteci İşleyicisi kullanılarak web hizmeti tarafından doğrulanır. JWT Belirteci İşleyicisi belirteci doğruladıktan sonra, istenen kaynak web hizmeti tarafından istemciye döndürülür.  
  
## <a name="features"></a>Özellikler  
 JWT Belirteci İşleyicisi aşağıdaki özellikleri sunar:  
  
- **JWT belirteci doğrulama**: JWT belirteçlerinin kolayca belirteç işleyicisinin Doğrulama mantığı, bir uygulamanın WIF ardışık düzeninin parçası olarak ya da doğrulayan veya wıf'den bağımsız  
  
- **Oluşturma bir JWT belirteci**: JWT belirteci işleyicisi, aşağı akış hizmetlerinde yetkilendirme için JWT belirteçleri oluşturmak için kullanılabilir
