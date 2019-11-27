---
title: Güvenlik ve Kayıt Defteri
ms.date: 07/20/2015
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
ms.openlocfilehash: 454180207d6432e80d87941d1f329f2a4ea7a801
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345478"
---
# <a name="security-and-the-registry-visual-basic"></a>Güvenlik ve Kayıt Defteri (Visual Basic)

Bu sayfada, verileri kayıt defterine depolamanın güvenlik etkileri ele alınmaktadır.  
  
## <a name="permissions"></a>İzinler  

 Kayıt defteri anahtarı ACL 'Ler (erişim denetim listeleri) tarafından korunsa bile, parolalar gibi gizli dizileri, kayıt defterindeki düz metin olarak depolamak güvenli değildir.  
  
 Kayıt defteriyle çalışma, sistem kaynaklarına veya korunan bilgilere uygunsuz erişime izin vererek güvenliği tehlikeye atabilir. Bu özellikleri kullanmak için, kayıt defteri değişkenlerine erişimi denetleyen <xref:System.Security.Permissions.RegistryPermissionAccess> numaralandırmasından okuma ve yazma izinlerine sahip olmanız gerekir. Tam güvenle çalışan tüm kodlar (varsayılan güvenlik ilkesi altında, kullanıcının yerel sabit diskinde yüklü olan tüm kodlar), kayıt defterine erişmek için gerekli izinlere sahiptir. Daha fazla bilgi için bkz. <xref:System.Security.Permissions.RegistryPermission> sınıfı.  
  
 Kayıt defteri değişkenleri <xref:System.Security.Permissions.RegistryPermission> olmayan kodun bunlara erişebilmesi için bellek konumlarında depolanmamalıdır. Benzer şekilde, izin verirken işi almak için gereken en düşük ayrıcalıklara izin verin.  
  
 Kayıt defteri izin erişim değerleri <xref:System.Security.Permissions.RegistryPermissionAccess> numaralandırması tarafından tanımlanır. Aşağıdaki tabloda üyelerinin ayrıntıları verilmiştir.  
  
|Değer|Kayıt defteri değişkenlerine erişim|  
|-----------|----------------------------------|  
|`AllAccess`|Oluşturma, okuma ve yazma|  
|`Create`|Create|  
|`NoAccess`|Erişim yok|  
|`Read`|Oku|  
|`Write`|Write|  
  
## <a name="checking-values-in-registry-keys"></a>Kayıt defteri anahtarlarındaki değerler denetleniyor  

 Bir kayıt defteri değeri oluşturduğunuzda, bu değer zaten varsa ne yapılacağını belirlemeniz gerekir. Belki de kötü amaçlı olan bir işlem, değeri zaten oluşturmuş ve ona erişime sahip olabilir. Verileri kayıt defteri değerine yerleştirdiğinizde, veriler diğer işlem tarafından kullanılabilir. Bunu engellemek için `GetValue` yöntemini kullanın. Anahtar zaten yoksa `Nothing` döndürür.  
  
> [!IMPORTANT]
> Bir Web uygulamasından kayıt defteri okunurken geçerli kullanıcının kimliği, Web uygulamasında uygulanan kimlik doğrulama ve kimliğe bürünme özelliğine bağlıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [Kayıt Defterinden Okuma ve Kayıt Defterine Yazma](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
