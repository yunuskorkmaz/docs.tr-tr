---
title: Bir WCF Kitaplık Projesini Dağıtma
ms.date: 03/30/2017
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
ms.openlocfilehash: 0400fc9ec5a5629139348709bbd3a5554ce251c7
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593349"
---
# <a name="deploying-a-wcf-library-project"></a>Bir WCF Kitaplık Projesini Dağıtma
Bu konuda, bir Windows Communication Foundation (WCF) hizmet kitaplığı projesi nasıl dağıtabileceğiniz açıklanmıştır.  
  
## <a name="deploying-a-wcf-service-library"></a>Bir WCF hizmet kitaplığı dağıtma  
 Bir WCF hizmet kitaplığı bir dinamik bağlantı kitaplığı (DLL) ' dir. Bu nedenle, kendi kendine yürütülemez. Bir barındırma ortamına dağıtılması gerekir. Bu işlem hakkında daha fazla bilgi için bkz. [barındırma ve WCF hizmetleri kullanma](https://go.microsoft.com/fwlink/?LinkId=99932).  
  
 Bir WCF hizmet kitaplığı gibi başka bir WCF hizmeti olarak dağıtılabilir. Ancak, .NET Framework dll dosyaları için yapılandırma desteklemediğini unutmayın. <xref:System.Configuration> uygulama etki alanı başına bir yapılandırma dosyasını destekler. WCF hizmet kitaplığı projesi, geliştirme sırasında bir App.config dosyası kitaplığı sağlayarak bu sınırlama azaltır. Ancak, App.config dosyasına dağıtımdan sonra tanınmıyor.  
  
 Yapılandırma kodunuzu barındırma ortamınıza tarafından tanınan yapılandırma dosyasına taşımak zorunda. Kendi kendine barındırma için App.config dosyasının içeriğini barındırma yürütülebilir App.config dosyasına kopyalamanız gerekir. Hizmetinizi barındırmak için IIS kullanırsanız, sanal dizin Web.config dosyasına App.config dosyasının içeriğini kopyalamanız gerekir.
