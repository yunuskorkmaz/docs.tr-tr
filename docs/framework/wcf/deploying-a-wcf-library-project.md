---
title: Bir WCF Kitaplık Projesini Dağıtma
ms.date: 03/30/2017
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
ms.openlocfilehash: fb400a4d1ebba691222ad7fc9d2c09f1051591da
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803029"
---
# <a name="deploying-a-wcf-library-project"></a>Bir WCF Kitaplık Projesini Dağıtma
Bu konuda, bir Windows Communication Foundation (WCF) hizmetini kitaplığı projesi nasıl dağıtılacağı açıklanmaktadır.  
  
## <a name="deploying-a-wcf-service-library"></a>Bir WCF Hizmeti kitaplığı dağıtma  
 Bir WCF hizmeti bir dinamik bağlantı kitaplığı (DLL) kitaplıktır. Bu nedenle, bu, kendi yürütülemez. Bir barındırma ortamına dağıtılması gerekir. Bu işlem hakkında daha fazla bilgi için bkz: [barındırma ve WCF hizmetlerini tüketen](http://go.microsoft.com/fwlink/?LinkId=99932).  
  
 Bir WCF Hizmeti kitaplığı gibi başka bir WCF Hizmeti dağıtılabilir. Ancak, farkında olması, [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] yapılandırmasını DLL'ler için desteklemez. <xref:System.Configuration> uygulama etki alanı başına bir yapılandırma dosyası destekler. WCF hizmet kitaplığı projesi, geliştirme sırasında bir App.config dosyası kitaplığın sağlayarak bu sınırlamaya azaltır. Ancak, App.config dosyasını dağıtımdan sonra tanınmıyor.  
  
 Barındırma ortamı tarafından tanınan yapılandırma dosyasına yapılandırma kodunuzu taşıyın gerekir. Kendi kendine barındırma için barındırma yürütülebilir App.config dosyasına App.config dosyasının içeriğini kopyalamanız gerekir. Hizmetinizi barındırmak için IIS kullanıyorsanız, sanal dizin Web.config dosyasına App.config dosyasının içeriğini kopyalamanız gerekir.
