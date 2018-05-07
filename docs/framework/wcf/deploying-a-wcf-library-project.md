---
title: Bir WCF Kitaplık Projesini Dağıtma
ms.date: 03/30/2017
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
ms.openlocfilehash: 08a1d794aeeea1a41cd1eb3abf298f3f4a0f6d15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="deploying-a-wcf-library-project"></a>Bir WCF Kitaplık Projesini Dağıtma
Bu konuda, bir Windows Communication Foundation (WCF) hizmetini kitaplığı projesi nasıl dağıtılacağı açıklanmaktadır.  
  
## <a name="deploying-a-wcf-service-library"></a>Bir WCF Hizmeti kitaplığı dağıtma  
 A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet kitaplığıdır dinamik bağlantı kitaplığı (DLL). Bu nedenle, bu, kendi yürütülemez. Bir barındırma ortamına dağıtılması gerekir. Bu işlem hakkında daha fazla bilgi için bkz: [barındırma ve WCF hizmetlerini tüketen](http://go.microsoft.com/fwlink/?LinkId=99932).  
  
 A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet kitaplığı gibi diğer dağıtılabilir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet. Ancak, farkında olması, [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] yapılandırmasını DLL'ler için desteklemez. <xref:System.Configuration> uygulama etki alanı başına bir yapılandırma dosyası destekler. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Hizmet kitaplığı projesi, geliştirme sırasında bir App.config dosyası kitaplığın sağlayarak bu sınırlamaya ortadan kaldırır. Ancak, App.config dosyasını dağıtımdan sonra tanınmıyor.  
  
 Barındırma ortamı tarafından tanınan yapılandırma dosyasına yapılandırma kodunuzu taşıyın gerekir. Kendi kendine barındırma için barındırma yürütülebilir App.config dosyasına App.config dosyasının içeriğini kopyalamanız gerekir. Hizmetinizi barındırmak için IIS kullanıyorsanız, sanal dizin Web.config dosyasına App.config dosyasının içeriğini kopyalamanız gerekir.
