---
title: Bir WCF Kitaplık Projesini Dağıtma
ms.date: 03/30/2017
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
ms.openlocfilehash: 186ce5ae3087fd9b4c7e5c32e110de4bc7d5e578
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801988"
---
# <a name="deploying-a-wcf-library-project"></a>Bir WCF Kitaplık Projesini Dağıtma
Bu konu, bir Windows Communication Foundation (WCF) hizmet kitaplığı projesini nasıl dağıtabileceğinizi açıklamaktadır.  
  
## <a name="deploying-a-wcf-service-library"></a>WCF hizmet kitaplığı dağıtma  
 Bir WCF hizmet kitaplığı, dinamik bağlantı kitaplığı (DLL). Bu nedenle, kendi üzerinde yürütülemez. Barındırma ortamına dağıtılması gerekir. Bu işlem hakkında daha fazla bilgi için bkz. [WCF hizmetleri barındırma ve](https://docs.microsoft.com/previous-versions/dotnet/articles/bb332338(v=msdn.10))kullanma.  
  
 Bir WCF hizmet kitaplığı, diğer herhangi bir WCF hizmeti gibi dağıtılabilir. Ancak, .NET Framework dll yapılandırmalarını desteklemediğini unutmayın. <xref:System.Configuration>, her uygulama etki alanı için bir yapılandırma dosyasını destekler. WCF hizmet kitaplığı projesi, geliştirme sırasında kitaplık için bir App. config dosyası sağlayarak bu sınırlamayı konuma almayı azaltır. Ancak, Deployment sonrasında App. config dosyası tanınmaz.  
  
 Yapılandırma kodunuzu Barındırma ortamınız tarafından tanınan yapılandırma dosyasına taşımanız gerekir. Kendi kendine barındırma için, App. config dosyasının içeriğini barındırma yürütülebilirinin App. config dosyasına kopyalamanız gerekir. Hizmetinizi barındırmak için IIS kullanıyorsanız, App. config dosyasının içeriğini sanal dizinin Web. config dosyasına kopyalamanız gerekir.
