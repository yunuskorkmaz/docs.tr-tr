---
title: Güvenlik ve Kayıt Defteri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
ms.openlocfilehash: dc0071d1fddf99bd712ebe8aea5c61bbc3522f93
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839364"
---
# <a name="security-and-the-registry-visual-basic"></a>Güvenlik ve Kayıt Defteri (Visual Basic)
Bu sayfa verileri kayıt defterinde depolama güvenlikle ilgili etkileri anlatılmaktadır.  
  
## <a name="permissions"></a>İzinler  
 Kayıt defteri anahtarı ACL (erişim denetim listeleri) tarafından korunuyor olsa bile kayıt defterinde düz metin parolalar gibi gizli dizileri depolamak için güvenli değildir.  
  
 Kayıt defteri ile çalışma, sistem kaynakları için uygun olmayan erişimine izin vererek güvenliği tehlikeye atabilir veya korumalı bilgileri. Bu özellikleri kullanmak için olmalıdır okuma ve Yazma izinlerinden <xref:System.Security.Permissions.RegistryPermissionAccess> kayıt defteri değişkenlerine erişimi denetleyen sabit listesi. Tam güven ile çalışan herhangi bir kod (varsayılan güvenlik ilkesini altında kullanıcının yerel sabit diskinde yüklü herhangi bir kod budur) kayıt defterine erişim için gerekli izinlere sahip. Daha fazla bilgi için <xref:System.Security.Permissions.RegistryPermission> sınıfı.  
  
 Kayıt defteri değişkenleri bellek konumlarda olmayan depolanmalıdır burada olmadan kod <xref:System.Security.Permissions.RegistryPermission> erişebilir. Benzer şekilde, izin verirken, işin tamamlanması için gereken en düşük ayrıcalıkları verin.  
  
 Kayıt defteri izni erişim değerleri tarafından tanımlanan <xref:System.Security.Permissions.RegistryPermissionAccess> sabit listesi. Aşağıdaki tabloda üyelerini ayrıntıları.  
  
|Değer|Kayıt defteri değişkenlerine erişimi|  
|-----------|----------------------------------|  
|`AllAccess`|Oluşturun, okuyun ve yazma|  
|`Create`|Create|  
|`NoAccess`|Erişim yok|  
|`Read`|Oku|  
|`Write`|Write|  
  
## <a name="checking-values-in-registry-keys"></a>Kayıt defteri anahtarlarını değerleri denetleniyor  
 Bir kayıt defteri değeri oluşturduğunuzda, bu değer zaten varsa yapmanız gerekenler karar vermeniz gerekir. Başka bir işlem, belki de kötü amaçlı bir değeri önceden oluşturmuş olabilir ve erişmesini sağlayabilirsiniz. Kayıt defteri değerine veri koyduğunuzda, veriler başka bir işlem için kullanılabilir. Bunu önlemek için `GetValue` yöntemi. Döndürür `Nothing` anahtarı zaten mevcut değilse.  
  
> [!IMPORTANT]
>  Kayıt defterinde bir Web uygulamasından okurken, geçerli kullanıcının kimliğini kimlik doğrulama ve Web uygulamasında gerçekleştirilen kimliğe bürünme bağlıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [Kayıt Defterinden Okuma ve Kayıt Defterine Yazma](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
