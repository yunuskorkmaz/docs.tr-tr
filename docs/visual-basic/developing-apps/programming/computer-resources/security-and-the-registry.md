---
title: Güvenlik ve Kayıt Defteri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
ms.openlocfilehash: ddfe8f88763ee2db78d25d72e6c9cb3456ccd13f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="security-and-the-registry-visual-basic"></a>Güvenlik ve Kayıt Defteri (Visual Basic)
Bu sayfa verileri kayıt defterinde depolama güvenlik etkilerini açıklar.  
  
## <a name="permissions"></a>İzinler  
 Kayıt defteri anahtarı ACL (erişim denetim listeleri) tarafından korunan olsa bile düz metin olarak kayıt defterinde parolalar gibi gizli depolamak için güvenli değildir.  
  
 Kayıt defteri ile çalışma sistem kaynaklarına uygun erişime izin vererek güvenliği tehlikeye atabilir veya bilgi korumalı. Bu özellikleri kullanmak için olmalıdır okuma ve yazma izinlerinin <xref:System.Security.Permissions.RegistryPermissionAccess> kayıt defteri değişkenlerini erişimi denetleyen numaralandırması. Tam güven ile çalışan herhangi bir kod (varsayılan güvenlik ilkesi altında kullanıcının yerel sabit diskinde yüklü herhangi bir kod budur) kayıt defterine erişim için gerekli izinlere sahip. Daha fazla bilgi için bkz: <xref:System.Security.Permissions.RegistryPermission> sınıfı.  
  
 Kayıt defteri değişkenlerini bellek konumlarda değil depolanmalıdır burada olmadan kod <xref:System.Security.Permissions.RegistryPermission> dosyalara erişebilirsiniz. Benzer şekilde, izinleri verme, işin tamamlanması için gereken en düşük ayrıcalıkları verin.  
  
 Kayıt defteri izni erişim değerleri tarafından tanımlanan <xref:System.Security.Permissions.RegistryPermissionAccess> numaralandırması. Aşağıdaki tabloda üyeleri ayrıntılarını verir.  
  
|Değer|Kayıt defteri değişkenlerini erişimi|  
|-----------|----------------------------------|  
|`AllAccess`|Oluşturma, okuma ve yazma|  
|`Create`|Create|  
|`NoAccess`|Erişim yok|  
|`Read`|Oku|  
|`Write`|Write|  
  
## <a name="checking-values-in-registry-keys"></a>Kayıt defteri anahtarlarını değerlerde denetleniyor  
 Bir kayıt defteri değeri oluşturduğunuzda, bu değer zaten varsa yapmanız gerekenler karar vermeniz gerekir. Başka bir işlem, belki de kötü amaçlı bir değer önceden oluşturduğunuz ve buna erişiminiz. Kayıt defteri değerindeki veri geçirdiğinizde, verileri başka bir işlem mevcut değil. Bunu önlemek için kullanmak `GetValue` yöntemi. Döndürdüğü `Nothing` anahtarı zaten mevcut değilse.  
  
> [!IMPORTANT]
>  Kayıt defteri bir Web uygulamasından okurken, geçerli kullanıcının kimliğini kimlik doğrulaması ve kimliğe bürünme Web uygulamasında uygulanan bağlıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 [Kayıt Defterinden Okuma ve Kayıt Defterine Yazma](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
