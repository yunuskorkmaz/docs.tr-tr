---
title: "Windows Communication Foundation Bağlamaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], bindings
- Windows Communication Foundation [WCF], bindings
- bindings [WCF]
ms.assetid: 83639133-89f7-43f0-b4ef-8d9e57c08d25
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 22b7b8f568b3350972ace128fdc3164c4f3ba179
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="windows-communcation-foundation-bindings"></a>Windows Communication Foundation Bağlamaları
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]bir uygulama için yazılım nasıl onu diğer yazılımlarla iletişim kurduğu gelen nasıl yazılmış ayırır. Bağlamaları Aktarım, kodlama ve istemcileri ve Hizmetleri birbirleri ile iletişim kurması gereken protokol ayrıntılarını belirtmek için kullanılır. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]temel alınan hat gösterimine uç noktanın bağlama ayrıntıları çoğunu iletişim kuran tarafların üzerinde anlaşmaya varılan gerekir böylece oluşturmak için bağlamaları kullanır. Bunu elde etmenin en kolay yolu, bir hizmet bağlaması aynı hizmet kullandığı için uç nokta kullanmak istemcileri içindir. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Bunu yapmak için bkz: nasıl [kullanarak bağlamaları yapılandırma Windows Communication Foundation Hizmetleri ve istemcilere](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb).  
  
 Bir bağlama bağlama öğelerinin koleksiyonu yapılır. Her uç nokta istemcileri ile nasıl iletişim kurduğu, bazı yönlerinin açıklar. Bir bağlama en az bir aktarım bağlama öğesi, (sağlayabilen aktarım bağlama öğesi varsayılan olarak) en az bir ileti kodlama bağlama öğesi içermelidir ve diğer herhangi bir sayıda Protokolü bağlama öğeleri. Bu açıklama dışında bir çalışma zamanı derlemeleri işlem kodu, çalışma zamanının katkıda bulunmak her bağlama öğesi sağlar.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]bağlama öğelerinin ortak seçimleri içeren bağlamaları sağlar. Bu varsayılan ayarlarla kullanılabilir veya kullanıcı gereksinimlerine göre bu varsayılan değerleri değiştirebilirsiniz. Bu sistem tarafından sağlanan bağlamalar bağlama öğelerini ve ayarlarını doğrudan denetime izin veren özelliklere sahiptir. Bağlama her sürümü vererek yana birimi bağlaması birden çok sürümü ile de kolayca çalışabilirsiniz kendi adı. Ayrıntılar için bkz [Configuring System-Provided bağlamaları](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md).  
  
 Bir koleksiyonu gerekiyorsa bağlama öğeleri sağlanmamış bu sistem tarafından sağlanan bağlamalar biri tarafından bağlama gerekli öğelerinin koleksiyonunu içeren özel bir bağlama oluşturabilirsiniz. Bu özel bağlama oluşturma yapmak kolaydır ve yeni bir sınıf gerekmez, ancak özellikleri bağlama öğeleri veya ayarlarını denetlemek için sağladıkları değil. Bağlama öğeleri erişmek ve onları içeren koleksiyonu aracılığıyla ayarlarını değiştirin. Ayrıntılar için bkz [özel bağlamaları](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Sistem tarafından sağlanan bağlamaları yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 Kullanın ve bağlamaları değiştirmek açıklar, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] senaryoları desteklemek için sağlar.  
  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 Nasıl tanımlanacağını açıklar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmetler ve istemcileri imperatively kodu ve bildirimli olarak Yapılandırması'nı kullanarak bağlamaları.  
  
 [Özel bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 Ne açıklayan bir <xref:System.ServiceModel.Channels.CustomBinding> olduğu ve ne zaman kullanılır.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel.Channels.Binding>  
  
 <xref:System.ServiceModel.Channels.BindingElement>  
  
 <xref:System.ServiceModel.Channels.CustomBinding>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Bağlamaları genişletme](../../../../docs/framework/wcf/extending/extending-bindings.md)
