---
title: Güvenlik ve Kayıt Defteri
ms.date: 07/20/2015
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
ms.openlocfilehash: 454180207d6432e80d87941d1f329f2a4ea7a801
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345478"
---
# <a name="security-and-the-registry-visual-basic"></a>Güvenlik ve Kayıt Defteri (Visual Basic)

Bu sayfada, kayıt defterinde veri depolamanın güvenlik sonuçları anlatılmaktadır.  
  
## <a name="permissions"></a>İzinler  

 Kayıt defteri anahtarı ALA'lar (erişim denetim listeleri) tarafından korunsa bile, parolalar gibi sırları kayıt defterinde düz metin olarak depolamak güvenli değildir.  
  
 Kayıt defteriyle çalışmak, sistem kaynaklarına veya korunan bilgilere uygunsuz erişime izin vererek güvenliği tehlikeye atabilir. Bu özellikleri kullanmak için, kayıt defteri değişkenlerine <xref:System.Security.Permissions.RegistryPermissionAccess> erişimi denetleyen numaralandırmadan izinleri okuma ve yazma nız gerekir. Tam güvenle çalışan herhangi bir kod (varsayılan güvenlik ilkesi altında, bu kullanıcının yerel sabit diskine yüklenen herhangi bir koddur) kayıt defterine erişmek için gerekli izinlere sahiptir. Daha fazla bilgi <xref:System.Security.Permissions.RegistryPermission> için sınıfa bakın.  
  
 Kayıt defteri değişkenleri, kodun <xref:System.Security.Permissions.RegistryPermission> erişilebileceği bellek konumlarında depolanmamalıdır. Benzer şekilde, izin verirken, işi yapmak için gereken minimum ayrıcalıkları tanıyın.  
  
 Kayıt defteri izni erişim değerleri <xref:System.Security.Permissions.RegistryPermissionAccess> numaralandırma ile tanımlanır. Aşağıdaki tablo üyeleri ayrıntıları.  
  
|Değer|Kayıt Defteri Değişkenlerine Erişim|  
|-----------|----------------------------------|  
|`AllAccess`|Oluşturma, okuma ve yazma|  
|`Create`|Oluşturma|  
|`NoAccess`|Erişim yok|  
|`Read`|Okuma|  
|`Write`|Yazma|  
  
## <a name="checking-values-in-registry-keys"></a>Kayıt Defteri Anahtarlarında Değerleri Denetleme  

 Bir kayıt defteri değeri oluşturduğunuzda, bu değer zaten varsa ne yapacağınız gerektiğine karar vermeniz gerekir. Başka bir işlem, belki de kötü niyetli bir, zaten değer yarattı ve ona erişimi olabilir. Verileri kayıt defteri değerine koyduğunuzda, veriler diğer işlem için kullanılabilir. Bunu önlemek için `GetValue` yöntemi kullanın. Anahtar `Nothing` zaten yoksa döndürür.  
  
> [!IMPORTANT]
> Bir Web uygulamasından kayıt defterini okurken, geçerli kullanıcının kimliği Web uygulamasında uygulanan kimlik doğrulama ve kimliğe bürünme bağlıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [Kayıt Defterinden Okuma ve Kayıt Defterine Yazma](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
