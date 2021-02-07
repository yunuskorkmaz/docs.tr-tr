---
description: 'Daha fazla bilgi edinin: güvenlik ve kayıt defteri (Visual Basic)'
title: Güvenlik ve Kayıt Defteri
ms.date: 07/20/2015
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
ms.openlocfilehash: 2dc6413328bc32c004d281b096ee095d4f827feb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666387"
---
# <a name="security-and-the-registry-visual-basic"></a>Güvenlik ve Kayıt Defteri (Visual Basic)

Bu sayfada, verileri kayıt defterine depolamanın güvenlik etkileri ele alınmaktadır.  
  
## <a name="permissions"></a>İzinler  

 Kayıt defteri anahtarı ACL 'Ler (erişim denetim listeleri) tarafından korunsa bile, parolalar gibi gizli dizileri, kayıt defterindeki düz metin olarak depolamak güvenli değildir.  
  
 Kayıt defteriyle çalışma, sistem kaynaklarına veya korunan bilgilere uygunsuz erişime izin vererek güvenliği tehlikeye atabilir. Bu özellikleri kullanmak için, Numaralandırmadaki okuma ve yazma izinlerine sahip olmanız gerekir ve bu <xref:System.Security.Permissions.RegistryPermissionAccess> , kayıt defteri değişkenlerine erişimi denetler. Tam güvenle çalışan tüm kodlar (varsayılan güvenlik ilkesi altında, kullanıcının yerel sabit diskinde yüklü olan tüm kodlar), kayıt defterine erişmek için gerekli izinlere sahiptir. Daha fazla bilgi için bkz <xref:System.Security.Permissions.RegistryPermission> . sınıf.  
  
 Kayıt defteri değişkenleri, kodun hiçbir şekilde erişebileceği bellek konumlarında depolanmamalıdır <xref:System.Security.Permissions.RegistryPermission> . Benzer şekilde, izin verirken işi almak için gereken en düşük ayrıcalıklara izin verin.  
  
 Kayıt defteri izin erişim değerleri Listeleme tarafından tanımlanır <xref:System.Security.Permissions.RegistryPermissionAccess> . Aşağıdaki tabloda üyelerinin ayrıntıları verilmiştir.  
  
|Değer|Kayıt defteri değişkenlerine erişim|  
|-----------|----------------------------------|  
|`AllAccess`|Oluşturma, okuma ve yazma|  
|`Create`|Oluştur|  
|`NoAccess`|Erişim yok|  
|`Read`|Okuma|  
|`Write`|Yazma|  
  
## <a name="checking-values-in-registry-keys"></a>Kayıt defteri anahtarlarındaki değerler denetleniyor  

 Bir kayıt defteri değeri oluşturduğunuzda, bu değer zaten varsa ne yapılacağını belirlemeniz gerekir. Belki de kötü amaçlı olan bir işlem, değeri zaten oluşturmuş ve ona erişime sahip olabilir. Verileri kayıt defteri değerine yerleştirdiğinizde, veriler diğer işlem tarafından kullanılabilir. Bunu engellemek için `GetValue` yöntemini kullanın. `Nothing`Anahtar zaten mevcut değilse döndürür.  
  
> [!IMPORTANT]
> Bir Web uygulamasından kayıt defteri okunurken geçerli kullanıcının kimliği, Web uygulamasında uygulanan kimlik doğrulama ve kimliğe bürünme özelliğine bağlıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [Kayıt Defterinden Okuma ve Kayıt Defterine Yazma](reading-from-and-writing-to-the-registry.md)
