---
title: Yayınlayıcı Adı Kaydını Doğrulama
ms.date: 03/30/2017
ms.assetid: c4644dd1-dead-48ff-abeb-7bffae69a6ac
ms.openlocfilehash: dc7da9d3dc4ab696d8c27d8e12583b8d06e747fe
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045307"
---
# <a name="validating-issuer-name-registry"></a>Yayınlayıcı Adı Kaydını Doğrulama
Windows Identity Foundation için Doğrulama Verenin Adı Kayıt Defteri (VINR), çok kiracılı uygulamaların güvenilen bir kiracı ve kimlik sağlayıcısı tarafından gelen bir belirtecin yayınlanmasını sağlamasına olanak verir. Bu işlev, Microsoft Azure AD tarafından verilen tüm belirteçler aynı sertifika ile imzalanmış olduğundan, Microsoft Azure Active Directory kullanan çok kiracılı uygulamalar için özellikle yararlıdır. Uygulamanız, aynı sertifikayı (ve sonuç olarak aynı parmak izini) kullanan birden çok kiracının istekleri arasında ayırım yapmak amacıyla, her kiracının doğrulama mantığını gerçekleştirmesi için yayınlayıcı adını kalıcı tutmalıdır. VINR bu işlevi sağlar ve ayrıca özel doğrulama mantığı eklemenize ve yayınlayanın kayıt defteri verilerini bir yapılandırma dosyasından başka bir konuma depolamanıza olanak verir. Uzantı uygulamanızın WIF kanalına eklenebilir veya bağımsız olarak kullanılabilir.  
  
 VINR, bir NuGet paketi olarak kullanılabilir. Daha fazla bilgi için bkz. [doğrulama verenin adı kayıt defteri paketi indiriliyor](downloading-the-validating-issuer-name-registry-package.md) .  
  
## <a name="scenarios"></a>Senaryolar  
 VINR aşağıdaki anahtar senaryoyu olanaklı kılar:  
  
- **Çok kiracılı bir uygulamada belirteç doğrulama**: Bu senaryoda, Litwlar adlı bir şirket, Windows Azure AD gibi bir kimlik sağlayıcısı kullanan çok kiracılı bir uygulama geliştirmiştir. Bu uygulama iki müşteriye hizmet eder: Contoso ve fabrikam. Fabrikam kullanıcısı Litware'ın uygulama kimliğini doğruladığında, Microsoft Azure AD'den elde edilen belirteç standart sertifikası kullanılarak imzalanır ve istek Fabrikam tarafından verilir. Uygulamanın, hem verenin adının hem de belirtecin geçerli olduğunu doğrulaması ve Microsoft Azure AD'deki sertifika kullanılarak imzalanmış Contoso'dan gelen istekleri ayırt etmesi gerekir. VINR, Litware uygulamasının Contoso ve Fabrikam gibi birden çok kiracıdan gelen istekleri ayırt etmesini ve doğrulamasını kolaylaştırır.  
  
## <a name="features"></a>Özellikler  
 VINR aşağıdaki özellikleri sağlar:  
  
- **Çok kiracılı uygulamalar Için verenin adı ve belirteç doğrulama**: Verenin adını (kiracı) doğrulayarak gelen belirteci doğrular ve belirtecin kimlik sağlayıcısından geçerli bir sertifika kullanarak imzalanıp imzalanmadığını doğrular.  
  
- **Özel doğrulama mantığı ve veri depoları Için genişletilebilirlik**: Kendi doğrulama mantığınızı eklemek ve varsayılan yapılandırma dosyasından farklı bir veri deposu belirtmek için genişletilebilirlik sağlar.
