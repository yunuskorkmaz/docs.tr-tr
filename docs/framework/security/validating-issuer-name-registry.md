---
title: Yayınlayıcı Adı Kaydını Doğrulama
ms.date: 03/30/2017
ms.assetid: c4644dd1-dead-48ff-abeb-7bffae69a6ac
ms.openlocfilehash: fc10181a142fd8ca4ebd8250869d49a046623564
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64910778"
---
# <a name="validating-issuer-name-registry"></a>Yayınlayıcı Adı Kaydını Doğrulama
Windows Identity Foundation için Doğrulama Verenin Adı Kayıt Defteri (VINR), çok kiracılı uygulamaların güvenilen bir kiracı ve kimlik sağlayıcısı tarafından gelen bir belirtecin yayınlanmasını sağlamasına olanak verir. Bu işlev, Microsoft Azure AD tarafından verilen tüm belirteçler aynı sertifika ile imzalanmış olduğundan, Microsoft Azure Active Directory kullanan çok kiracılı uygulamalar için özellikle yararlıdır. Uygulamanız, aynı sertifikayı (ve sonuç olarak aynı parmak izini) kullanan birden çok kiracının istekleri arasında ayırım yapmak amacıyla, her kiracının doğrulama mantığını gerçekleştirmesi için yayınlayıcı adını kalıcı tutmalıdır. VINR bu işlevi sağlar ve ayrıca özel doğrulama mantığı eklemenize ve yayınlayanın kayıt defteri verilerini bir yapılandırma dosyasından başka bir konuma depolamanıza olanak verir. Uzantı uygulamanızın WIF kanalına eklenebilir veya bağımsız olarak kullanılabilir.  
  
 VINR, bir NuGet paketi olarak kullanılabilir. Bkz: [doğrulama verenin adı kaydı paketini doğrulamayı indirme](../../../docs/framework/security/downloading-the-validating-issuer-name-registry-package.md) daha fazla bilgi için.  
  
## <a name="scenarios"></a>Senaryolar  
 VINR aşağıdaki anahtar senaryoyu olanaklı kılar:  
  
- **Çok Kiracılı bir uygulama bir belirteç doğrulama**: Bu senaryoda, Litware adlı bir şirketin Azure AD Windows gibi bir kimlik sağlayıcısı kullanan çok kiracılı bir uygulama geliştirmiştir. Bu uygulama iki müşteriye hizmet eder: Contoso ve Fabrikam. Fabrikam kullanıcısı Litware'ın uygulama kimliğini doğruladığında, Microsoft Azure AD'den elde edilen belirteç standart sertifikası kullanılarak imzalanır ve istek Fabrikam tarafından verilir. Uygulamanın, hem verenin adının hem de belirtecin geçerli olduğunu doğrulaması ve Microsoft Azure AD'deki sertifika kullanılarak imzalanmış Contoso'dan gelen istekleri ayırt etmesi gerekir. VINR, Litware uygulamasının Contoso ve Fabrikam gibi birden çok kiracıdan gelen istekleri ayırt etmesini ve doğrulamasını kolaylaştırır.  
  
## <a name="features"></a>Özellikler  
 VINR aşağıdaki özellikleri sağlar:  
  
- **Verenin adı ve çok Kiracılı uygulamalar için belirteç doğrulama**: Gelen belirteci, verenin adını (Kiracı) ve belirtecin kimlik sağlayıcısından alınan geçerli bir sertifika kullanarak olup imzalandığı doğrulayarak doğrular.  
  
- **Özel Doğrulama mantığı ve veri depoları için genişletilebilirlik**: Kendi doğrulama mantığınızı eklemek ve varsayılan yapılandırma dosyası farklı bir veri deposu belirtmek için genişletilebilirlik sağlar.
