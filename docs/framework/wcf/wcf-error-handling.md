---
title: WCF Hata İşleme
ms.date: 03/30/2017
ms.assetid: 1e4b1e0f-9598-449d-9d73-90bda62305b8
ms.openlocfilehash: 72db5db9f6b4a3cd2ba62fe938fcfeed2dfda1e5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96240946"
---
# <a name="wcf-error-handling"></a>WCF Hata İşleme

Bir WCF uygulaması tarafından karşılaşılan hatalar üç gruptan birine aittir:  
  
1. İletişim hataları  
  
2. Ara sunucu/kanal hataları  
  
3. Uygulama hataları  
  
 İletişim hataları, bir ağ kullanılamadığında, bir istemci yanlış bir adres kullandığında veya hizmet ana bilgisayarı gelen iletileri dinlemediğinde oluşur. Bu tür hatalar istemciye <xref:System.ServiceModel.CommunicationException> ya da <xref:System.ServiceModel.CommunicationException> türetilmiş sınıflar olarak döndürülür.  
  
 Ara sunucu/kanal hataları, kanal veya proxy içinde oluşan hatalardır. Bu tür hatalar şunlardır: kapatılmış bir proxy veya kanal kullanılmaya çalışılıyor, istemci ile hizmet arasında bir anlaşma uyumsuzluğu var veya istemcinin kimlik bilgileri hizmet tarafından reddedildi. Bu kategoride çok fazla sayıda farklı hata türü var, burada listelemek için çok fazla. Bu tür hatalar istemciye olduğu gibi döndürülür (özel durum nesnelerinde hiçbir dönüşüm gerçekleştirilmez).  
  
 Uygulama hataları, bir hizmet işleminin yürütülmesi sırasında oluşur. Bu tür hatalar istemciye veya olarak gönderilir <xref:System.ServiceModel.FaultException> <xref:System.ServiceModel.FaultException%601> .  
  
 WCF 'de hata işleme, aşağıdakilerden biri veya birkaçı tarafından gerçekleştirilir:  
  
- Oluşturulan özel durumu doğrudan işleme. Bu yalnızca iletişim ve proxy/kanal hataları için yapılır.  
  
- Hata sözleşmelerini kullanma  
  
- Arabirimi uygulama <xref:System.ServiceModel.Dispatcher.IErrorHandler>  
  
- <xref:System.ServiceModel.ServiceHost>Olayları işleme  
  
## <a name="fault-contracts"></a>Hata sözleşmeleri  

 Hata sözleşmeleri, hizmet işlemi sırasında platformdan bağımsız bir şekilde oluşabilecek hataları tanımlamanızı sağlar. Varsayılan olarak, bir hizmet işlemi içinden oluşturulan tüm özel durumlar istemciye bir nesne olarak döndürülür <xref:System.ServiceModel.FaultException> . <xref:System.ServiceModel.FaultException>Nesne çok az bilgi içerecektir. Bir hata sözleşmesi tanımlayarak ve hatayı bir olarak döndürerek istemciye gönderilen bilgileri kontrol edebilirsiniz <xref:System.ServiceModel.FaultException%601> . Daha fazla bilgi için bkz. [anlaşmalar ve hizmetlerde hataları belirtme ve işleme](specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="ierrorhandler"></a>IErrorHandler  

 <xref:System.ServiceModel.Dispatcher.IErrorHandler>Arabirim, WCF uygulamanızın hatalara nasıl yanıt vereceğini daha fazla kontrol etmenizi sağlar.  İstemciye döndürülen hata iletisi üzerinde tam denetim sağlar ve günlüğe kaydetme gibi özel hata işleme gerçekleştirmenize olanak tanır.  <xref:System.ServiceModel.Dispatcher.IErrorHandler> [Hata Işleme ve raporlama üzerinde denetim](./samples/extending-control-over-error-handling-and-reporting.md) hakkında daha fazla bilgi için  
  
## <a name="servicehost-events"></a>ServiceHost olayları  

 <xref:System.ServiceModel.ServiceHost>Sınıfı Hizmetleri barındırır ve hataları işlemek için gerekebilecek birkaç olayı tanımlar. Örneğin:  
  
1. <xref:System.ServiceModel.Channels.CommunicationObject.Faulted>
  
2. <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived>
  
 Daha fazla bilgi için bkz. <xref:System.ServiceModel.ServiceHost>.
