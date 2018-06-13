---
title: Windows Communication Foundation Bağlamaları
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], bindings
- Windows Communication Foundation [WCF], bindings
- bindings [WCF]
ms.assetid: 83639133-89f7-43f0-b4ef-8d9e57c08d25
ms.openlocfilehash: 373f7feb64d69373630c942750f264d559643a63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489670"
---
# <a name="windows-communcation-foundation-bindings"></a>Windows Communication Foundation Bağlamaları
Windows Communication Foundation (WCF) nasıl onu diğer yazılımlarla iletişim kurduğu gelen yazılım bir uygulama için nasıl yazılır ayırır. Bağlamaları Aktarım, kodlama ve istemcileri ve Hizmetleri birbirleri ile iletişim kurması gereken protokol ayrıntılarını belirtmek için kullanılır. WCF bağlamaları bağlama ayrıntıları çoğunu iletişim kuran tarafların üzerinde anlaşmaya varılan gerekir böylece uç noktanın temel alınan hat gösterimine oluşturmak için kullanılır. Bunu elde etmenin en kolay yolu, bir hizmet bağlaması aynı hizmet kullandığı için uç nokta kullanmak istemcileri içindir. Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz: [kullanarak bağlamaları yapılandırma Windows Communication Foundation Hizmetleri ve istemcilere](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb).  
  
 Bir bağlama bağlama öğelerinin koleksiyonu yapılır. Her uç nokta istemcileri ile nasıl iletişim kurduğu, bazı yönlerinin açıklar. Bir bağlama en az bir aktarım bağlama öğesi, (sağlayabilen aktarım bağlama öğesi varsayılan olarak) en az bir ileti kodlama bağlama öğesi içermelidir ve diğer herhangi bir sayıda Protokolü bağlama öğeleri. Bu açıklama dışında bir çalışma zamanı derlemeleri işlem kodu, çalışma zamanının katkıda bulunmak her bağlama öğesi sağlar.  
  
 WCF bağlama öğelerinin ortak seçimleri içeren bağlamaları sağlar. Bu varsayılan ayarlarla kullanılabilir veya kullanıcı gereksinimlerine göre bu varsayılan değerleri değiştirebilirsiniz. Bu sistem tarafından sağlanan bağlamalar bağlama öğelerini ve ayarlarını doğrudan denetime izin veren özelliklere sahiptir. Bağlama her sürümü vererek yana birimi bağlaması birden çok sürümü ile de kolayca çalışabilirsiniz kendi adı. Ayrıntılar için bkz [Configuring System-Provided bağlamaları](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md).  
  
 Bir koleksiyonu gerekiyorsa bağlama öğeleri sağlanmamış bu sistem tarafından sağlanan bağlamalar biri tarafından bağlama gerekli öğelerinin koleksiyonunu içeren özel bir bağlama oluşturabilirsiniz. Bu özel bağlama oluşturma yapmak kolaydır ve yeni bir sınıf gerekmez, ancak özellikleri bağlama öğeleri veya ayarlarını denetlemek için sağladıkları değil. Bağlama öğeleri erişmek ve onları içeren koleksiyonu aracılığıyla ayarlarını değiştirin. Ayrıntılar için bkz [özel bağlamaları](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 Ortak senaryoları desteklemek için WCF sağlar bağlamaları değiştirmek ve nasıl kullanılacağı açıklanmaktadır.  
  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 Hizmetler ve istemcileri için Windows Communication Foundation (WCF) bağlamaları imperatively kodu ve bildirimli olarak Yapılandırması'nı kullanarak nasıl tanımlanacağını açıklar.  
  
 [Özel Bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 Ne açıklayan bir <xref:System.ServiceModel.Channels.CustomBinding> olduğu ve ne zaman kullanılır.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ServiceModel.Channels.Binding>  
  
 <xref:System.ServiceModel.Channels.BindingElement>  
  
 <xref:System.ServiceModel.Channels.CustomBinding>  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Bağlamaları Genişletme](../../../../docs/framework/wcf/extending/extending-bindings.md)
