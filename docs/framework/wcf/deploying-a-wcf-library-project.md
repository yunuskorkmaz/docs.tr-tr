---
title: "Bir WCF Kitaplık Projesini Dağıtma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bbbbff1d88559f8ab35caa48fcb04ff1cd7bf015
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-a-wcf-library-project"></a>Bir WCF Kitaplık Projesini Dağıtma
Bu konuda, nasıl dağıtılacağı açıklanmaktadır bir [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] hizmet kitaplığı projesi.  
  
## <a name="deploying-a-wcf-service-library"></a>Bir WCF Hizmeti kitaplığı dağıtma  
 A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet kitaplığıdır dinamik bağlantı kitaplığı (DLL). Bu nedenle, bu, kendi yürütülemez. Bir barındırma ortamına dağıtılması gerekir. Bu işlem hakkında daha fazla bilgi için bkz: [barındırma ve WCF hizmetlerini tüketen](http://go.microsoft.com/fwlink/?LinkId=99932).  
  
 A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet kitaplığı gibi diğer dağıtılabilir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet. Ancak, farkında olması, [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] yapılandırmasını DLL'ler için desteklemez. <xref:System.Configuration>uygulama etki alanı başına bir yapılandırma dosyası destekler. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Hizmet kitaplığı projesi, geliştirme sırasında bir App.config dosyası kitaplığın sağlayarak bu sınırlamaya ortadan kaldırır. Ancak, App.config dosyasını dağıtımdan sonra tanınmıyor.  
  
 Barındırma ortamı tarafından tanınan yapılandırma dosyasına yapılandırma kodunuzu taşıyın gerekir. Kendi kendine barındırma için barındırma yürütülebilir App.config dosyasına App.config dosyasının içeriğini kopyalamanız gerekir. Hizmetinizi barındırmak için IIS kullanıyorsanız, sanal dizin Web.config dosyasına App.config dosyasının içeriğini kopyalamanız gerekir.
